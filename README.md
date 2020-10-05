# utilitatios

Projeto Maven: Leitor de arquivo CSV

	public static void main(String[] args) {
		Reader reader = null;
		try {

			reader = Files.newBufferedReader(
					Paths.get("<caminho do arquivo>));

		} catch (IOException e) {
			e.printStackTrace();
		}
		CSVReader csvReader = new CSVReaderBuilder(reader).withSkipLines(1).build();

		List<String[]> dados = null;
		try {

			dados = csvReader.readAll();

		} catch (IOException e) {
			e.printStackTrace();
		}

		
		for (String[] dado : dados) {
			System.out.println(dado[0] + "," + dado[1] + ",'" + dado[2]);
		}
	}
}

Projeto Maven: Leitor de arquivo CSV - gerando arquivo:

	public static void main(String[] args) {
		Reader reader = null;
		try {

			reader = Files.newBufferedReader(Paths.get(
					"CAMINHO"));

		} catch (IOException e) {
			e.printStackTrace();
		}
		CSVReader csvReader = new CSVReaderBuilder(reader).withSkipLines(1).build();

		List<String[]> dados = null;
		try {

			dados = csvReader.readAll();

		} catch (IOException e) {
			e.printStackTrace();
		}

		try {
			BufferedWriter buffWrite = new BufferedWriter(
					new FileWriter("CAMINHO\NOME_ARQUIVO"));
			int seq = 0; //SEQUENCE
			for (String[] dado : dados) {
				buffWrite.append(
						"INSERT INTO ssp_dados_poco (<CAMPOS>) VALUES ("+ seq +", '"
								+ dado[0] + "', STR_TO_DATE('" + dado[1] + "','%d/%m /%Y'),'" + dado[2] + "'"
								+ ",'P',1);" + "\n");
				seq++;
			}
			buffWrite.close();

		} catch (IOException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}

	}

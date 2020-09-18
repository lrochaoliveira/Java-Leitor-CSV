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

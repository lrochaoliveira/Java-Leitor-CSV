# utilitatios

public class App {
	public static void main(String[] args) {
		Reader reader = null;
		try {

			reader = Files.newBufferedReader(
					Paths.get("C:\\Users\\nilda\\Desktop\\Gensis\\Supervisório\\ProximaOperacao.csv"));

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
			System.out.println("INSERT INTO monitoracao_proximaoperacao (ID_LISTOP, ID_LISTOP_PX, TIPO_OP) VALUES ( " + dado[0] + "," + dado[1] + ",'" + dado[2]+ "');" );
		}
	}
}

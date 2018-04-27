# HelloWorld
It's a collaborative project.


class CheckWord{
	public final int basicAmount = 85;
	String advertisement;
	int amount;
	public CheckWord(String advertisement) {
		this.advertisement = advertisement;
	}
	public void setChargeAmount(){
		amount = advertisement.length() + basicAmount;
	}
	public int getAmount() {
		return amount;
	}
}

class Charge{
	public final int basicCharge = 12;
	CheckWord checkWord;
	Charge (CheckWord checkWord){
		this.checkWord = checkWord;
	}
	public void giveCharge() {
		int charge = checkWord.getAmount() * basicCharge;
		System.out.println("广告费用："+charge+"元");
	}
}

class TypeSeting{
	String advertisement;
	public TypeSeting(String advertisement) {
		this.advertisement = advertisement;
	}
	public void typeSeting() {
		System.out.println("广告排版格式：");
		System.out.println("********");
		System.out.println(advertisement);
		System.out.println("********");
	}
}

class ClientServerFacade{
	private CheckWord checkWord;
	private Charge charge;
	private TypeSeting typeSeting;
	String advertisement;
	public ClientServerFacade(String advertisement) {
		this.advertisement = advertisement;
		checkWord = new CheckWord(advertisement);
		charge = new Charge(checkWord);
		typeSeting = new TypeSeting(advertisement);
	}
	public void doAdvertisement() {
		checkWord.setChargeAmount();
		charge.giveCharge();
		typeSeting.typeSeting();
	}		
}






public class Application {

	public static void main(String[] args) {
		ClientServerFacade clientFacade;
		String clientAdvertisement = "月光电脑，价格6356元，联系电话：1234567";
		clientFacade = new ClientServerFacade(clientAdvertisement);
		clientFacade.doAdvertisement();
	}

}






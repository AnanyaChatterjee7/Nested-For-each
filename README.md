# Nested-For-each
{
  "q": "qval",
  "a": [
    {
      "id": 1,
      "name": "ABC",
      "age": "23"
    },
    {
      "id": 2,
      "name": "XYZ",
      "age": "20"
    }
  ],
   "b": [
    {
      "id": 1,
      "address": "KOL",
      "city": "Kol"
    },
    {
      "id": 2,
      "address": "DEL",
      "city": "del"
    }
  ],
  "p":["p1","p2"]
}


==================

@PostMapping("/api")
	public List<C> testApi(@RequestBody D d) {

		List<A> aList = d.getA();
		List<B> bList = d.getB();
		List<C> cList = new ArrayList<>();
		List<C> cList1 = new ArrayList<>();

		//////

		// OR

		aList.stream().forEach((a) -> {
			C obj = new C();
			obj.setId(a.getId());
			obj.setName(a.getName());
			obj.setAge(a.getAge());
			bList.stream().forEach((b) -> {
 
				obj.setAddress(b.getAddress());
				obj.setCity(b.getCity());
				// cList1.add(obj);

			});
			cList.add(obj);

			 System.out.println(cList);
			// System.out.println(cList1);

		});

		//System.out.println(cList);

		// System.out.println(cList1);

		return cList;
	}
	
	
	=======================================================
	V2 working version:
	List<A> aList = d.getA();
		List<B> bList = d.getB();
		List<C> cList = new ArrayList<>();
		List<C> cList1 = new ArrayList<>();
		
		    //C obj=new C();
		aList.stream().forEach((a) -> {
			C obj = new C();
			obj.setId(a.getId());
			obj.setName(a.getName());
			obj.setAge(a.getAge());
			bList.stream().forEach((b) -> {

				 if(a.getId()==b.getId()){
				obj.setAddress(b.getAddress());
				obj.setCity(b.getCity());
				
				 }
			});
			
			cList.add(obj);

			 System.out.println(cList);
			// System.out.println(cList1);

		});

		//System.out.println(cList);

		// System.out.println(cList1);

		return cList;
	
	===========================================
	

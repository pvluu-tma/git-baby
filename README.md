// Nếu 1 class không define 1 constructor --> JS tự động tạo 1 default constructor
class Person {
  //default access modifier: public
  firstName?: string;
  lastName: string;
  age: number;
  address: Array<any>;

  //Sử dụng public để TS tự động tạo field cho phone (parameter property declaration)
  constructor(
    fName: string,
    lName: string,
    age: number = 0,
    public phone: string = "",
    address: Array<any> = []
  ) {
    console.log("Parent firstName: ", this.firstName);
    console.log("Parent lastName: ", this.lastName);
    console.log("Parent age: ", this.age);
    console.log("Parent phone: ", this.phone);
    console.log("Parent address: ", this.address);


    this.firstName = fName;
  }
}

class Employee extends Person {

    constructor(firstName: string, lastName: string, private badgeId: string) {
        //child class phải gọi constructor của parent
        //gọi super trước khi sử dụng this
        super(firstName, lastName); // call parent class constructor

        this.badgeId = badgeId;
        console.log(this.badgeId);
        console.log("Child firstName: ", this.firstName);
        console.log("Child lastName: ", this.lastName);
        console.log("Child age: ", this.age);
        console.log("Child phone: ", this.phone);
        console.log("Child address: ", this.address);
    }

    get FirstName() {
      return this.firstName;
    }

    set FirstName(fName: string) {
      this.firstName = fName;
    }
}

let e = new Employee("Jon", "Snow", "219889");
console.log(e);
console.log("dfgdfg", e.FirstName);
e.FirstName = 'lulu';
console.log('aaaaaaaa', e.FirstName);
//let p= new Person("Jon","Snow", 10, '03456789');
//console.log(p.phone);

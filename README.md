# Library-Management-System
from tkinter import *
from tkinter import ttk
import mysql.connector
from tkinter import messagebox
import datetime





class LibraryManagementSystem:
    def __init__(self, root):
        self.root = root
        self.root.title("Library Management System")
        self.root.geometry("1550x800+0+0")
        
        
        #variables
        self.MemberType_var=StringVar()
        self.PRNNo_var=StringVar()
        self.IDNo_var=StringVar()
        self.FirstName_var=StringVar()
        self.LastName_var=StringVar()
        self.Redg_No_var=StringVar()
        self.Mobile_var=StringVar()
        self.EMail_var=StringVar()
        self.Department_var=StringVar()
        self.Address_var=StringVar()
        self.BookID_var=StringVar()
        self.BookTitle_var=StringVar()
        self.AuthorName_var=StringVar()
        self.DateBorrowed_var=StringVar()
        self.DateDue_var=StringVar()
        self.DaysonBook_var=StringVar()
        self.DueFine_var=StringVar()
        self.Price_var=StringVar()
        self.YearofPublish_var=StringVar()
        
        

        lbltitle = Label(self.root, text="LIBRARY MANAGEMENT SYSTEM", bg="powder blue", fg="green", bd=20, relief=RIDGE,
                         font=("times new roman", 50, "bold"), padx=2, pady=6)
        lbltitle.pack(side=TOP, fill=X)

        frame = Frame(self.root, bd=12, relief=RIDGE, padx=28, bg="powder blue")
        frame.place(x=0, y=130, width=1530, height=480)

        
      # DataFrameLeft
        DataFrameLeft = LabelFrame(frame, text="Library Membership Information", bg="powder blue", bd=12, relief=RIDGE,
                                   font=("times new roman", 12, "bold"))
        DataFrameLeft.place(x=8, y=5, width=868, height=350)

        lblMember = Label(DataFrameLeft, bg="powder blue",  text="Member Type",font=("times new roman", 15, "bold"))
        lblMember.grid(row=0, column=0, sticky=W)

        comMember = ttk.Combobox(DataFrameLeft,textvariable=self.MemberType_var, font=("times new roman", 15, "bold"), width=27, state="readonly")
        comMember["values"] = ("Admin Staff", "Student", "Lecturer")
        comMember.grid(row=0, column=1)

        lblPRN_No = Label(DataFrameLeft, bg="powder blue",  text="PRN_No",font=("times new roman", 15, "bold"))
        lblPRN_No.grid(row=1, column=0, sticky=W)
        txtPRN_NO = Entry(DataFrameLeft, font=("times new roman", 15, "bold"), textvariable=self.PRNNo_var,width=29)
        txtPRN_NO.grid(row=1, column=1)

        lblID_No = Label(DataFrameLeft, bg="powder blue", text="ID_No", font=("times new roman", 15, "bold"))
        lblID_No.grid(row=2, column=0, sticky=W)
        txtID_NO = Entry(DataFrameLeft, font=("times new roman", 15, "bold"), textvariable=self.IDNo_var,width=29)
        txtID_NO.grid(row=2, column=1)

        lblF_name = Label(DataFrameLeft, bg="powder blue",  text="First Name",
                          font=("times new roman", 15, "bold"))
        lblF_name.grid(row=3, column=0, sticky=W)
        txtF_Name = Entry(DataFrameLeft, font=("times new roman", 15, "bold"), textvariable=self.FirstName_var,width=29)
        txtF_Name.grid(row=3, column=1)

        lblL_name = Label(DataFrameLeft, bg="powder blue",  text="Last Name",
                          font=("times new roman", 15, "bold"))
        lblL_name.grid(row=4, column=0, sticky=W)
        txtL_Name = Entry(DataFrameLeft, font=("times new roman", 15, "bold"), textvariable=self.LastName_var,width=29)
        txtL_Name.grid(row=4, column=1)

        lblRedg_no = Label(DataFrameLeft, bg="powder blue",  text="Redg_No",
                           font=("times new roman", 15, "bold"))
        lblRedg_no.grid(row=5, column=0, sticky=W)
        txtRedg_No = Entry(DataFrameLeft, font=("times new roman", 15, "bold"),textvariable=self.Redg_No_var, width=29)
        txtRedg_No.grid(row=5, column=1)

        lblph_no = Label(DataFrameLeft, bg="powder blue", text="Mobile",
                         font=("times new roman", 15, "bold"))
        lblph_no.grid(row=6, column=0, sticky=W)
        txtph_No = Entry(DataFrameLeft, font=("times new roman", 15, "bold"), textvariable=self.Mobile_var, width=29)
        txtph_No.grid(row=6, column=1)

        lble_mail = Label(DataFrameLeft, bg="powder blue",  text="E-Mail",
                          font=("times new roman", 15, "bold"))
        lble_mail.grid(row=7, column=0, sticky=W)
        txte_Mail = Entry(DataFrameLeft, font=("times new roman", 15, "bold"), textvariable=self.EMail_var,width=29)
        txte_Mail.grid(row=7, column=1)

        lblDep_c = Label(DataFrameLeft, bg="powder blue",  text="Department",
                         font=("times new roman", 15, "bold"))
        lblDep_c.grid(row=8, column=0, sticky=W)
        txtDep_C = Entry(DataFrameLeft, font=("times new roman", 15, "bold"), textvariable=self.Department_var,width=29)
        txtDep_C.grid(row=8, column=1)

        lblA_d = Label(DataFrameLeft, bg="powder blue", text="Address",
                       font=("times new roman", 15, "bold"))
        lblA_d.grid(row=9, column=0, sticky=W)
        txtA_D = Entry(DataFrameLeft, font=("times new roman", 15, "bold"), textvariable=self.Address_var, width=29)
        txtA_D.grid(row=9, column=1)

        lblBook_id = Label(DataFrameLeft, bg="powder blue",  text="Book ID:",
                           font=("times new roman", 15, "bold"))
        lblBook_id.grid(row=0, column=2, sticky=W)
        txtBook_ID = Entry(DataFrameLeft, font=("times new roman", 15, "bold"), textvariable=self.BookID_var,width=29)
        txtBook_ID.grid(row=0, column=3)

        lblBook_tit = Label(DataFrameLeft, bg="powder blue",  text="Book Title:",
                            font=("times new roman", 15, "bold"))
        lblBook_tit.grid(row=1, column=2, sticky=W)
        txtBook_Tit = Entry(DataFrameLeft, font=("times new roman", 15, "bold"), textvariable=self.BookTitle_var,width=29)
        txtBook_Tit.grid(row=1, column=3)

        lblaut = Label(DataFrameLeft, bg="powder blue", text="Author Name:",
                       font=("times new roman", 15, "bold"))
        lblaut.grid(row=2, column=2, sticky=W)
        txtAut = Entry(DataFrameLeft, font=("times new roman", 15, "bold"), textvariable=self.AuthorName_var, width=29)
        txtAut.grid(row=2, column=3)

        lbld_b = Label(DataFrameLeft, bg="powder blue", text="Date Borrowed:",
                       font=("times new roman", 15, "bold"))
        lbld_b.grid(row=3, column=2, sticky=W)
        txtD_B = Entry(DataFrameLeft, font=("times new roman", 15, "bold"), textvariable=self.DateBorrowed_var, width=29)
        txtD_B.grid(row=3, column=3)

        lbld_d = Label(DataFrameLeft, bg="powder blue",  text="Date Due:",
                       font=("times new roman", 15, "bold"))
        lbld_d.grid(row=4, column=2, sticky=W)
        txtD_D = Entry(DataFrameLeft, font=("times new roman", 15, "bold"),textvariable=self.DateDue_var, width=29)
        txtD_D.grid(row=4, column=3)

        lbld_book = Label(DataFrameLeft, bg="powder blue",  text="Days on Book:",
                          font=("times new roman", 15, "bold"))
        lbld_book.grid(row=5, column=2, sticky=W)
        txtD_Book = Entry(DataFrameLeft, font=("times new roman", 15, "bold"),textvariable=self.DaysonBook_var, width=29)
        txtD_Book.grid(row=5, column=3)

        lbld_f = Label(DataFrameLeft, bg="powder blue",  text="Due Fine:",
                       font=("times new roman", 15, "bold"))
        lbld_f.grid(row=6, column=2, sticky=W)
        txtD_F = Entry(DataFrameLeft, font=("times new roman", 15, "bold"),textvariable=self.DueFine_var, width=29)
        txtD_F.grid(row=6, column=3)

        lbld_p = Label(DataFrameLeft, bg="powder blue", text="Price:",
                       font=("times new roman", 15, "bold"))
        lbld_p.grid(row=7, column=2, sticky=W)
        txtD_P = Entry(DataFrameLeft, font=("times new roman", 15, "bold"),textvariable=self.Price_var,  width=29)
        txtD_P.grid(row=7, column=3)

        lbld_pu = Label(DataFrameLeft, bg="powder blue",  text="Year of Publish:",
                        font=("times new roman", 15, "bold"))
        lbld_pu.grid(row=8, column=2, sticky=W)
        txtD_Pu = Entry(DataFrameLeft, font=("times new roman", 15, "bold"), textvariable=self.YearofPublish_var,width=29)
        txtD_Pu.grid(row=8, column=3)


        
        
        #DataFrameRight
        
        
        DataFrameRight = LabelFrame(frame, bd=12, padx=20, relief=RIDGE, bg="powder blue",
                                    font=("arial", 12, "bold"), text="Book Details")
        DataFrameRight.place(x=870, y=5, width=580, height=350)
        
        self.txtBox=Text(DataFrameRight, font=("arial",12,"bold"),width=32,height=16,padx=2,pady=6)
        self.txtBox.grid(row=0,column=2)
        
        
        listScrollbar=Scrollbar(DataFrameRight)
        listScrollbar.grid(row=0,column=1,sticky="ns")
        listBooks=["Python Crash Course","Automate the Boring Stuff with Python","Learning Python","Fluent Python","Python Cookbook" ,"Effective Python: 59 Specific Ways to Write Better Python","Python for Data Analysis","Python Programming: An Introduction to Computer Science","Python Pocket Reference","Python Testing with pytest","Structure and Interpretation of Computer Programs","Head First Design Patterns","Refactoring: Improving the Design of Existing Code","Effective Java","Cracking the Coding Interview: 189 Programming Questions and Solutions","Design Patterns: Elements of Reusable Object-Oriented Software","Introduction to Algorithms","Code Complete: A Practical Handbook of Software Construction","The Pragmatic Programmer: Your Journey to Mastery","Clean Code: A Handbook of Agile Software Craftsmanship","Algorithms to Live By: The Computer Science of Human Decisions","The Art of Computer Programming","The Mythical Man-Month: Essays on Software Engineering","Head First Java","JavaScript: The Good Parts","Practical Object-Oriented Design in Ruby: An Agile Primer","The Clean Coder: A Code of Conduct for Professional Programmers" ,"Refactoring to Patterns"]
        def SelectBook(event=""):
            value = str(listBox.get(listBox.curselection())) # Call the get method
            x = value
            if x == "Python Crash Course":
                self.BookID_var.set("BKID5455")
                self.BookTitle_var.set("Python")
                self.AuthorName_var.set("White")

                d1 = datetime.datetime.today()
                d2 = datetime.timedelta(days=15)
                d3 = d1 + d2
                self.DateBorrowed_var.set(d1)
                self.DateDue_var.set(d3)
                self.DaysonBook_var.set(15)
                self.DueFine_var.set("Rs. 50")
                self.Price_var.set("Rs. 766")
                self.YearofPublish_var.set(2010)

        listBox = Listbox(DataFrameRight, font=("arial", 10, "bold"), width=20, height=16)
        listBox.bind("<<ListboxSelect>>", SelectBook)
        listBox.grid(row=0, column=0, padx=4)

        listScrollbar.config(command=listBox.yview)

        for item in listBooks:
            listBox.insert(END, item)

        
        
        # Button Frame
        FrameButton = Frame(self.root, bd=10, relief=RIDGE, padx=20, bg="powder blue")
        FrameButton.place(x=0, y=530, width=1530, height=70)
        
        btnAddData=Button(FrameButton,command=self.add_data,text="Add Data",font=("arial",12,"bold"),width=23,bg="blue",fg="white")
        btnAddData.grid(row=0,column=0)
        
        btnShowData=Button(FrameButton,text="Show Data",font=("arial",12,"bold"),width=23,bg="blue",fg="white")
        btnShowData.grid(row=0,column=1)
        
        btnUpdate=Button(FrameButton,text="Update",font=("arial",12,"bold"),width=23,bg="blue",fg="white")
        btnUpdate.grid(row=0,column=2)
        
        btnDelete=Button(FrameButton,text="Delete",font=("arial",12,"bold"),width=23,bg="blue",fg="white")
        btnDelete.grid(row=0,column=3)
        
        btnReset=Button(FrameButton,text="Reset",font=("arial",12,"bold"),width=23,bg="blue",fg="white")
        btnReset.grid(row=0,column=4)
        
        btnExit=Button(FrameButton,text="Exit",font=("arial",12,"bold"),width=23,bg="blue",fg="white")
        btnExit.grid(row=0,column=5)
        
        
        
        
        # Information Details
        FrameDetails = Frame(self.root, bd=10, relief=RIDGE, padx=20, bg="powder blue")
        FrameDetails.place(x=0, y=600, width=1530, height=195)
        
        
        Table_frame=Frame(FrameDetails,bd=6, relief=RIDGE, bg="powder blue")
        Table_frame.place(x=0, y=2, width=1460, height=190)
        
        
        xscroll=ttk.Scrollbar(Table_frame,orient=HORIZONTAL)
        yscroll=ttk.Scrollbar(Table_frame,orient=VERTICAL)
        
        self.library_table=ttk.Treeview(Table_frame,column=("Member Type","PRN_No","First Name","Last Name","Redg_No","Mobile","E-Mail","Department","Address","Book ID","Book Title","Author Name","Date Borrowed","Date Due","Days on Book","Due Fine","Price","Year of Publish"),xscrollcommand=xscroll.set,yscrollcommand=yscroll.set)
        
        
        xscroll.pack(side=BOTTOM,fill=X)
        yscroll.pack(side=RIGHT,fill=Y)
        xscroll.config(command=self.library_table.xview)
        yscroll.config(command=self.library_table.yview)
        
        
        self.library_table.heading("Member Type",text="Member Type")
        self.library_table.heading("PRN_No",text="PRN_No")
        self.library_table.heading("First Name",text="First Name")
        self.library_table.heading("Last Name",text="Last Name")
        self.library_table.heading("Redg_No",text="Redg_No")
        self.library_table.heading("Mobile",text="Mobile")
        self.library_table.heading("E-Mail",text="E-Mail")
        self.library_table.heading("Department",text="Department")
        self.library_table.heading("Address",text="Address")
        self.library_table.heading("Book ID",text="Book ID")
        self.library_table.heading("Book Title",text="Book Title")
        self.library_table.heading("Author Name",text="Author Name")
        self.library_table.heading("Date Borrowed",text="Date Borrowed")
        self.library_table.heading("Date Due",text="Date Due")
        self.library_table.heading("Days on Book",text="Days on Book")
        self.library_table.heading("Due Fine",text="Due Fine")
        self.library_table.heading("Price",text="Price")
        self.library_table.heading("Year of Publish",text="Year of Publish")
        
        
        self.library_table["show"]="headings"
        self.library_table.pack(fill=BOTH,expand=1)
        
        
        
        self.library_table.column("Member Type",width=100)
        self.library_table.column("PRN_No",width=100)
        self.library_table.column("First Name",width=100)
        self.library_table.column("Last Name",width=100)
        self.library_table.column("Redg_No",width=100)
        self.library_table.column("Mobile",width=100)
        self.library_table.column("E-Mail",width=100)
        self.library_table.column("Department",width=100)
        self.library_table.column("Address",width=100)
        self.library_table.column("Book ID",width=100)
        self.library_table.column("Book Title",width=100)
        self.library_table.column("Author Name",width=100)
        self.library_table.column("Date Borrowed",width=100)
        self.library_table.column("Date Due",width=100)
        self.library_table.column("Days on Book",width=100)
        self.library_table.column("Due Fine",width=100)
        self.library_table.column("Price",width=100)
        self.library_table.column("Year of Publish",width=100)
        
        
    def add_data(self):
        conn=mysql.connector.connect(host="localhost",username="root",password="2003",database="project1")
        my_cursor=conn.cursor()
        my_cursor.execute("INSERT INTO lib values(%s,%s,%s,%s,%s,%s,%s,%s,%s,%s,%s,%s,%s,%s,%s,%s,%s,%s)",(
            self.MemberType_var.get(),
            self.PRNNo_var.get(),
            self.IDNo_var.get(),
            self.FirstName_var.get(),
            self.LastName_var.get(),
            self.Redg_No_var.get(),
            self.Mobile_var.get(),
            self.EMail_var.get(),
            self.Department_var.get(),
            self.Address_var.get(),
            self.BookID_var.get(),
            self.BookTitle_var.get(),
            self.AuthorName_var.get(),
            self.DateBorrowed_var.get(),
            self.DateDue_var.get(),
            self.DaysonBook_var.get(),
            self.DueFine_var.get(),
            self.Price_var.get(),
            self.YearofPublish_var.get()
        ))

        conn.comit()
        conn.close()
        messagebox.showinfo("Success","Member has been inserted successfully")

        
        
        
    
        
       


                                                                                            
        
        
                                        
if __name__ == "__main__":
    root = Tk()
    obj = LibraryManagementSystem(root)
    root.mainloop()

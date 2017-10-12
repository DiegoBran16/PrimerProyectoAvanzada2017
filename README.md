# PrimerProyectoAvanzada2017
###  Diego Bran:       1087217
### Walter Ruiz Erazo: 1028916

# Codigo Class: 

## Grupo.cs


public class Grupo
    {
        string nombre;
        
        Usuario parlamentario;
        
        Usuario[] asesores = new Usuario[8];
       
        string[] bajoprestamo = new string[2];
        
        int contador = 0;
        
        string usuarioAcargo1;
        
        string usuarioAcargo2;
        
        string usuarioAcargoLote;
        
        string primerPrestamo;
        
        string segundoPrestamo;
        
        public string getPrimerPrestamo()
        
        {
            return primerPrestamo;
        }
        public void setPrimerPrestamo(string p)
        {
            this.primerPrestamo = p;
        }
        public string getSegundoPrestamo()
        {
            return segundoPrestamo;
        }
        public void setSegundoPrestamo(string p)
        {
            this.segundoPrestamo = p;
        }
        public void setUsuarioAcargo1( string u)
        {
            this.usuarioAcargo1 = u;
        }
        public void setUsuarioAcargo2(string u)
        {
            this.usuarioAcargo2 = u;
        }
        public string getUsuarioAcargo1()
        {
            return usuarioAcargo1;
        }
        public string getUsuarioAcargo2()
        {
            return usuarioAcargo2;
        }



        public int getContador()
        {
            return contador; ;
        }
        public void setNombre(string n)
        {
            this.nombre = n;
        }
        public string getNombre()
        {
            return nombre;
        }
        public void setParlamentario(Usuario p)
        {
            this.parlamentario = p;
        }
        public Usuario getParlamentario()
        {
            return parlamentario;
        }
        public void asignarAsesor(Usuario a)
        {

            for (int i = 0; i < 8; i++)
            {
                if (asesores[i] == a)
                {
                    
                    break;
                }
                if (asesores[i] == null)
                {
                    asesores[i] = a;
                    break;
                    
                }
              

            }
        }
            public bool VerificarAsesor(Usuario a)
        {
            for (int i = 0; i < 8; i++)
            {
                if (asesores[i]!= null&& asesores[i] == a)
                {
                    return true;
                    break;
                }
               
            }
            return false;
            }
      
        public void eliminarAsesores()
        {
            asesores = null;
        }

        public void eliminarAsesor(string id)
        {
            for (int i = 0; i < 8; i++)
            {
                if (asesores[i] != null)
                {
                    if (asesores[i].getId() == id)
                    {
                        asesores[i] = null;
                        contador--;
                        break;
                    }
                }
            }

        }

        public string[] getLeyesBajoPrestamo()
        {
            return bajoprestamo;
        }
        public void setBajoPrestamo(string [] bp)
        {
            this.bajoprestamo = bp;
        }
        }
    }
    
    
    ## Ley.cs
     public class Ley
    {
       
        private string infoDeLey;
        private  string contenidoDeLey;
        private int numReglamentos=0;
        queue copiasLey = new queue();
      
        private int copaiasDisponibles = 5;
        Reglamentos[] reg = new Reglamentos[5];

        
        public int getCopiasDisponibles()
        {
            return copaiasDisponibles;
        }

        public string getinfoDeLey()
        {
            return infoDeLey;
        }
        public void setinfoDeLey(string nombreDeLey)
        {
            this.infoDeLey = nombreDeLey;

        }

        public int numerodereglamentos (){
            for (int i =0; 1<5; i++)
            {
                if (reg[i] != null)
                {
                    numReglamentos += 1;
                }
            }
  
            return numReglamentos;

                    
            }

        public void crearReglamento(string info)
        {
            Reglamentos r = new Reglamentos();
            r.setInfoReglamento(info);
            for (int i =0; i<5; i++)
            {
                if (reg[i] == null)
                {
                    reg[i] = r;
                    break;
                }
            }
        }
        public void modificarReglamento(int num, string mod)
        {
            if (reg[num] != null)
            {
                reg[num].setInfoReglamento(mod);
            }else
            {
                MessageBox.Show("NO existe el reglamento No. " + num);
            }
        }
        public void eliminarReglamento(int num)
        {
            if(reg[num]!=null)
            {
                reg[num] = null;
            }
            else
            {
                MessageBox.Show("NO existe el reglamento No. "+ num);
            }
           
        }

        public void asignarCopias()
        {
            for (int i = 0; i < 5; i++)
            {
                copiasLey.enqueue(infoDeLey);

            }
        }
             public void asignarCopiasReg()
             {
            for (int i = 0; i < 5; i++)
            {
                if (reg[i] != null)
                {
                    reg[i].asignarCopiasR();
                }

            }
         }
        public Reglamentos[] getReglamentos()
        {
            return reg;
        }

        public void setReglamentos(Reglamentos[] rglmts)
        {
            this.reg = rglmts;
        }

        public queue getQueue()
        {
            return copiasLey;
        }
        public void setQueue(queue copias)
        {
            this.copiasLey = copias;
        }
    }
}

## Program.cs

 static class Program
    {
        /// <summary>
        /// Punto de entrada principal para la aplicación.
        /// </summary>
        [STAThread]
        static void Main()
        {

            Application.EnableVisualStyles();
            Application.SetCompatibleTextRenderingDefault(false);
            Application.Run(new Form1());
           


    }
        
    }
}

## queue.cs
 public class queue
    {
        public int CAPACITY = 5;
        private string[] cLeyes;
        private int f = -1;
        public int l = -1;
        private int sz = 0;
        public queue()
        {
  
            cLeyes = new string[CAPACITY];


        }

        public Boolean isEmpty()
        {
            if (sz == 0)
            {
                return true;
            }
            else
            {
                return false;

            }

        }
        public Boolean isFull()
        {
            if (sz == (CAPACITY))
            {
                return true;
            }
            else
            {
                return false;

            }
        }
        public void enqueue( string ley)
        {

           if (isFull()== true)
            {
                MessageBox.Show("las copias estan llenas");
            }
            else
            {
                l += 1;
                cLeyes[l] = ley;
                sz++;
                if (l == 0)
                {
                    f= 0;
                }
                
            }
              
        }

        public string dequeue()
        {
            string lt = "";
            if (isEmpty() == true)
            {
                MessageBox.Show("no hay más leyes en el sistema");

                return lt;
            }
            else
            {
                lt = cLeyes[f];
                if (f == l)
                {
                    f = -1;
                    l = -1;

                }
                else
                {
                    f+=1;
                    sz -= 1;
                   
                }
                return lt;
            }
        }

    }
}


## Reglamentos.cs

 public class queue
    {
        public int CAPACITY = 5;
        private string[] cLeyes;
        private int f = -1;
        public int l = -1;
        private int sz = 0;
        public queue()
        {
  
            cLeyes = new string[CAPACITY];


        }

        public Boolean isEmpty()
        {
            if (sz == 0)
            {
                return true;
            }
            else
            {
                return false;

            }

        }
        public Boolean isFull()
        {
            if (sz == (CAPACITY))
            {
                return true;
            }
            else
            {
                return false;

            }
        }
        public void enqueue( string ley)
        {

           if (isFull()== true)
            {
                MessageBox.Show("las copias estan llenas");
            }
            else
            {
                l += 1;
                cLeyes[l] = ley;
                sz++;
                if (l == 0)
                {
                    f= 0;
                }
                
            }
              
        }

        public string dequeue()
        {
            string lt = "";
            if (isEmpty() == true)
            {
                MessageBox.Show("no hay más leyes en el sistema");

                return lt;
            }
            else
            {
                lt = cLeyes[f];
                if (f == l)
                {
                    f = -1;
                    l = -1;

                }
                else
                {
                    f+=1;
                    sz -= 1;
                   
                }
                return lt;
            }
        }

    }
}


## Usuario.cs

public class Usuario
    {
        private string id;
        private string cargo;
        private string grupo;
        private string contra;

        Ley[] bajoPrestamo = new Ley[8];
        public string getContra()
        {
            return this.contra;
        }
        public void setContra(string contra)
        {
            this.contra = contra;
        }
        public void setId(string id)
        {
            this.id = id;
        }
        public string getId()
        {
            return this.id;
        }
        public string getCargo()
        {
            return this.cargo;
        }
        public void setCargo(string cargo)
        {
            this.cargo = cargo;
        }
        public void setGrupo(string grupo)
        {
            this.grupo = grupo;
        }
        public string getGrupo()
        {
            return grupo;
        }
    }
}


# Codigo Forms:

## CrerU.cs

 public partial class CrearU : Form
    {
        Grupo[] grupos = new Grupo[200];
        Usuario[] users = new Usuario[999];
        string grup;
        bool verificado = false;
        public CrearU(Usuario[] u, Grupo[] g)
        {
            InitializeComponent();
            users = u;
            grupos = g;

        }
        private void label1_Click(object sender, EventArgs e)
        {

        }

        private void button1_Click(object sender, EventArgs e)
        {

            if (txtId.Text == "" && txtGrupo.Text == "" && txtContra.Text == "" && txtCargo.Text == "")
            {
                MessageBox.Show("Por Favor llenar todos los cuadros de texto.");

            }
            else
            {
                if (txtCargo.Text == "")
                {
                    MessageBox.Show("Ingresar Cargo que desempaña.");

                }
                else
                {
                    if (txtContra.Text == "")
                    {
                        MessageBox.Show("Ingresar Contraseña.");
                    }
                    else
                    {
                        if (txtGrupo.Text == "")
                        {
                            MessageBox.Show("Ingresar el Grupo que pertenece.");
                        }
                        else
                        {
                            if (txtId.Text == "")
                            {
                                MessageBox.Show("Ingresar ID.");
                            }
                        }
                    }
                }
            }


            Usuario user = new Usuario();
            user.setId(txtId.Text);
            user.setCargo(txtCargo.Text);
            user.setGrupo(txtGrupo.Text);
            user.setContra(txtContra.Text);
            grup = txtGrupo.Text;
            Grupo nuevog = new Grupo();
            nuevog.setParlamentario(user);
            nuevog.setNombre(user.getGrupo());
           


                if (txtCargo.Text == "parlamentario" || txtCargo.Text == "Parlamentario")
            {
                    if (verificarGrupo() == false)

                    {
                    MessageBox.Show(" EL nombre de grupo ya fue utilizado");
                }
                if (verificarId() == false)
                {
                    MessageBox.Show(" EL nombre de usuario ya fue utilizado");
                }
                while (verificarGrupo() == true && verificarId() == true)
                {


                    añadirGrupo(nuevog);
                    añadirUsuario(user);
                    MessageBox.Show(" EL usuario y grupo fueron creados");
                    Form1 f1 = new Form1(users, grupos);
                    f1.Show();
                    this.Hide();

                    break;


                }
            }


            else if (txtCargo.Text == "asesor" || txtCargo.Text == "asesor")
            {
                if (verificarGrupo() == true)

                {
                    MessageBox.Show(" Usted fue asignado al gurpo desado" );
                }
                if (verificarId() == false)
                {
                    MessageBox.Show(" EL nombre de usuario ya fue utilizado");
                }
                while (verificarGrupo() == true && verificarId() == true)
                {


                    for (int i=0; i < 200; i++)
                    {
                        if (grupos[i] != null)
                        {
                            if(grupos[i].getNombre()== txtGrupo.Text)
                            {
                                grupos[i].asignarAsesor(user);
                            }
                        }

                    }
                    añadirUsuario(user);
                    MessageBox.Show(" EL usuario fue creado y añadido al grupo");
                    Form1 f1 = new Form1(users, grupos);
                    f1.Show();
                    this.Hide();

                    break;


                }

            }
        }
        

        private void textBox2_TextChanged(object sender, EventArgs e)
        {

        }

        private void CrearU_Load(object sender, EventArgs e)
        {

        }

        private void button2_Click(object sender, EventArgs e)
        {
            Form1 f1 = new Form1(users, grupos);
            f1.Show();
            this.Hide();
        }

        private void añadirUsuario(Usuario u)
        {
            for (int i = 0; i < 999; i++)
            {
                if (users[i] == null)
                {
                    users[i] = u;
                    break;
                }


            }
        }

        private void añadirGrupo(Grupo g)
        {
            for (int i = 0; i < 200; i++)
            {
                if (grupos[i] == null)
                {
                    grupos[i] = g;
                    break;
                }

            }
        }
        private bool verificarGrupo()
        {
            for (int n = 0; n < 200; n++)
            {
                if (grupos[n] != null)
                {
                    if (grupos[n].getNombre() == txtGrupo.Text)
                    {
                        return false;
                        break;
                    }
                }
            }

            return true;
        }
        private bool verificarId()
        {
            for (int n = 0; n < 999; n++)
            {
                if (users[n] != null)
                {
                    if (users[n].getId() == txtId.Text)
                    {
                        return false;
                        break;
                    }
                }
            }

            return true;
        }
        
    }
}

## devolucioncs.cs

 public partial class devolucioncs : Form
    {
        Grupo[] grupos = new Grupo[200];
        Usuario[] users = new Usuario[999];
        Ley[] biblioLeyes = new Ley[500];
        string usuarioActualM;
        Reglamentos[] tmp = new Reglamentos[5];
        ArrayList mostrar = new ArrayList();
        queue copias = new queue();
        queue copiasR = new queue();
        string[] traspaso = new string[2];
        public devolucioncs(Usuario[] u, Grupo[] g, string us, Ley[] bl = null)
        {
            InitializeComponent();

            InitializeComponent();
            InitializeComponent();
            users = u;
            grupos = g;
            usuarioActualM = us;
            biblioLeyes = bl;

            traspaso = grupos[obtenerPosicionDelGrupo()].getLeyesBajoPrestamo();
            for (int i =0; i<2; i++)
            {
                if (traspaso[i]!=null)
                {
                    listBox1.Items.Add(traspaso[i]);

                }
            }



        }

        private void label1_Click(object sender, EventArgs e)
        {

        }

        private void textBox1_TextChanged(object sender, EventArgs e)
        {

        }

        private void devolucioncs_Load(object sender, EventArgs e)
        {

        }
        private bool verificarLey()
        {
            for (int n = 0; n < 500; n++)
            {
                if (biblioLeyes[n] != null)
                {
                    if (biblioLeyes[n].getinfoDeLey() == txtLey.Text)
                    {
                        return false;
                        break;
                    }
                }
            }

            return true;
        }

        private int obtenerPosicionDelGrupo()
        {
            int n = 0;
            string g = users[obtenerPosUsuario()].getGrupo();
            for (int i = 0; i < 200; i++)
            {
                if (grupos[i] != null && grupos[i].getNombre() == g)
                {
                    return i;
                }
            }
            return n;
        }


        private int ObtenerPosicionLey()
        {
            int n = 0;
            for (int i = 0; i < 500; i++)
            {
                if (biblioLeyes[i] != null && biblioLeyes[i].getinfoDeLey() == txtLey.Text)
                {
                    return i;
                }
            }
            return n;
        }
        private int obtenerPosUsuario()
        {
            int a = 0;
            for (int i = 0; i < 999; i++)
            {

                if (users[i] != null && users[i].getId() == usuarioActualM)
                {
                    return i;
                }

            }
            return a;
        }
        private bool verificarReg()
        {
            if (verificarLey() == false)
            {
                for (int n = 0; n < 500; n++)
                {
                    if (biblioLeyes[n] != null)
                    {
                        tmp = biblioLeyes[n].getReglamentos();
                        if (tmp[posicionReg()].getInfoReglamento() == txtReg.Text)
                        {
                            return true;
                            break;
                        }

                    }
                }
            }


            return false;
        }
        public int posicionReg()
        {
            int num = 0;
            for (int i = 0; i < 5; i++)
            {
                if (tmp[i] != null)
                {
                    if (tmp[i].getInfoReglamento() == txtReg.Text)
                    {
                        return i;
                    }
                }
            }
            return num;
        }

        private void label4_Click(object sender, EventArgs e)
        {

        }

        private void textBox2_TextChanged(object sender, EventArgs e)
        {

        }

        private void listBox1_SelectedIndexChanged(object sender, EventArgs e)
        {

        }

        private void button2_Click(object sender, EventArgs e)
        {
            if(verificarLey()==false && txtReg.Text == "")
            {
               copias= biblioLeyes[ObtenerPosicionLey()].getQueue();

                for(int i=0; i<2; i++)
                {
                    if (traspaso[i] != null && traspaso[i] == txtLey.Text)
                    {
                        copias.enqueue(traspaso[i]);
                        traspaso[i] = null;
                        if (grupos[obtenerPosicionDelGrupo()].getPrimerPrestamo() == traspaso[i])
                        {
                            grupos[obtenerPosicionDelGrupo()].setUsuarioAcargo1("");
                        }
                        else if (grupos[obtenerPosicionDelGrupo()].getSegundoPrestamo() == traspaso[i])
                        {
                            grupos[obtenerPosicionDelGrupo()].setUsuarioAcargo2("");
                        }

                        
                       
                            MessageBox.Show("Dato devuelto con exito");
                        menu m = new menu(users, grupos, usuarioActualM, biblioLeyes);
                        m.Show();
                        this.Hide();

                        break;

                    }
                    else
                    {
                        MessageBox.Show("no xisten datos para devolver");
                    }
                }
                
            }
            if( verificarLey()==false&& verificarReg() == true)
            {

                tmp = biblioLeyes[ObtenerPosicionLey()].getReglamentos();
                copiasR = tmp[posicionReg()].getQueue();
                traspaso = grupos[obtenerPosicionDelGrupo()].getLeyesBajoPrestamo();
                for (int i = 0; i < 2; i++)
                {
                    if (traspaso[i] != null && traspaso[i] == txtReg.Text)
                    {
                        copiasR.enqueue(traspaso[i]);
                        traspaso[i] = null;
                        if (grupos[obtenerPosicionDelGrupo()].getPrimerPrestamo() == traspaso[i])
                        {
                            grupos[obtenerPosicionDelGrupo()].setUsuarioAcargo1("");
                        }
                        else if(grupos[obtenerPosicionDelGrupo()].getSegundoPrestamo()== traspaso[i])
                        {
                            grupos[obtenerPosicionDelGrupo()].setUsuarioAcargo2("");
                        }


                        MessageBox.Show("Dato devuelto con exito");
                        menu m = new menu(users, grupos, usuarioActualM, biblioLeyes);
                        m.Show();
                        this.Hide();


                        break;

                    }
                    else
                    {
                        MessageBox.Show("no existen datos para devolver");
                    }
                }
            }
        }

        private void button1_Click(object sender, EventArgs e)
        {
            menu m = new menu(users, grupos, usuarioActualM, biblioLeyes);
            m.Show();
            this.Hide();
        }
    }
}


## Forms1.cs

 public partial class Form1 : Form
    {
        Usuario[] users = new Usuario[999];
        Grupo[] grupos = new Grupo[200];
        string usuarioActual;
        public Form1()
        {
            InitializeComponent();
        }
        public Form1(Usuario[] u, Grupo[]g = null)
        {
            InitializeComponent();
            users = u;
            grupos = g;



        }
        string user;
        string pasw;
        private void Form1_Load(object sender, EventArgs e)
        {

        }

        private void label1_Click(object sender, EventArgs e)
        {

        }

        private void button2_Click(object sender, EventArgs e)
        {

        }

        private void button1_Click(object sender, EventArgs e)
        {
          
        }

        private void button3_Click(object sender, EventArgs e)
        {
          
        }

        private void tableLayoutPanel1_Paint(object sender, PaintEventArgs e)
        {

        }

        private void button2_Click_1(object sender, EventArgs e)
        {
            CrearU fcu = new CrearU( users, grupos);
            fcu.Show();
            this.Hide();

            
            
        }

        private void button1_Click_1(object sender, EventArgs e)
        {

                    if (txtContra.Text == "" && txtUsuario.Text == "")
                    {
                        MessageBox.Show("Favor llenar los espacios vacios.");
                    }
                
            
            user = txtUsuario.Text;
            pasw = txtContra.Text;

            while (verificarId() == false)
            {
                for (int a = 0; a < users.Length; a++)
                {
                    if (users[a] != null && users[a].getId() == txtUsuario.Text && users[a].getId() == user && users[a].getContra() == pasw)
                    {
                        usuarioActual = user;
                        menu mod = new menu(users, grupos, usuarioActual);
                        mod.Show();
                        this.Hide();
                        break;
                    }
                    else
                    {
                        MessageBox.Show("usuario o contraseña incorrectos");
                        break;
                    }
                }
                break;
            }

            if (verificarId() == true)
            {
                MessageBox.Show("El usuario no se encontro en el sistema");
            }       
               
              
            }
        

        private void txtContra_TextChanged(object sender, EventArgs e)
        {

        }
        private bool verificarId()
        {
            for (int n = 0; n < 999; n++)
            {
                if (users[n] != null)
                {
                    if (users[n].getId() == txtUsuario.Text)
                    {
                        return false;
                        break;
                    }
                }
            }

            return true;
        }
    }
}

## FormCLey.cs

public partial class FormCLey : Form
    {
        Grupo[] grupos = new Grupo[200];
        Usuario[] users = new Usuario[999];
        Ley[] biblioLeyes = new Ley[500];
        string usuarioactual = "";
        
        public FormCLey(Usuario[] u, Grupo[] g, string ua)
        {
            InitializeComponent();
            users = u;
            grupos = g;
            usuarioactual = ua;
        }

        private void label1_Click(object sender, EventArgs e)
        {

        }

        private void button1_Click(object sender, EventArgs e)
        {

            string IngreseLey;
            IngreseLey = txtIngreseLey.Text;

            if (IngreseLey == "")
            {
                MessageBox.Show("Ingrese Nueva Ley.");
            }
            else
            {
                if (IngreseLey != "")
                {
                    Ley nuevaLey = new Ley();
                    nuevaLey.setinfoDeLey(IngreseLey);
                    nuevaLey.asignarCopias();
                    for (int i = 0; i < 500; i++)
                    {
                        if (biblioLeyes[i] == null)
                        {
                            biblioLeyes[i] = nuevaLey;
                            break;

                        }
                        else
                        {
                            MessageBox.Show("no hay espacio para una nueva ley");
                        }

                    }


                    MessageBox.Show("Ley Creada con Exito.");
                    menu m = new menu(users,grupos,usuarioactual,biblioLeyes);
                    m.Show();
                    this.Hide();
                    
                }
            }
        }

        private void FormCLey_Load(object sender, EventArgs e)
        {

        }

        private void button2_Click(object sender, EventArgs e)
        {

            menu m = new menu(users, grupos, usuarioactual, biblioLeyes);
            m.Show();
            this.Hide();

        }
    }
}

## FormCReg.cs

public partial class FormCReg : Form
    {

        Grupo[] grupos = new Grupo[200];
        Usuario[] users = new Usuario[999];
        Ley[] biblioLeyes = new Ley[500];
        queue copiasReg = new queue();
        ArrayList mostrar = new ArrayList();
        string usuarioActualM;
        
            
   
        public FormCReg(Usuario[] u, Grupo[] g, string ua="",Ley[] bl=null)
        {
            InitializeComponent();
            users = u;
            grupos = g;
            usuarioActualM = ua;
            biblioLeyes = bl;
        for (int i = 0; i < 500; i++)
        {
            if (biblioLeyes[i] != null)
            {
                mostrar.Add(biblioLeyes[i].getinfoDeLey());
            }
        }

        for (int i = 0; i < mostrar.Count; i++)
        {
            listBox1.Items.Add(mostrar[i]);
        }
    }

        private void FormCReg_Load(object sender, EventArgs e)
        {

        }

        private void label1_Click(object sender, EventArgs e)
        {

        }

        private void button1_Click(object sender, EventArgs e)
        {
            string ingreseReglamento;
            ingreseReglamento = txtInfoReg.Text;
            if (ingreseReglamento == "" && txtLey.Text == "")
            {
                MessageBox.Show("Debe ingresar el reglamento y la ley a la que pertenece");
            }
            else if (ingreseReglamento != "")
            {
                while (verificarLey() == false)
                {
                    for (int i = 0; i < 5; i++)
                    {
                        if (biblioLeyes[i].getinfoDeLey() == txtLey.Text)
                        {
                            biblioLeyes[i].crearReglamento(txtInfoReg.Text);
                            biblioLeyes[i].asignarCopiasReg();
                            break;
                        }


                        break;
                    }
                    if (verificarLey() == true)
                    {
                        MessageBox.Show("No se encontro la ley a la cual desea asignar un reglamento");
                    }

                    MessageBox.Show("Reglamento Creado con Exito.");
                    menu m = new menu(users, grupos, usuarioActualM, biblioLeyes);
                    m.Show();
                    this.Hide();
                    break;

                }
            }
        }  

        

        private void label2_Click(object sender, EventArgs e)
        {
            
        }

        private void btnRegresar_Click(object sender, EventArgs e)
        {
            menu m = new menu(users, grupos, usuarioActualM, biblioLeyes);
            m.Show();
            this.Hide();

        }
        private bool verificarLey()
        {
            for (int n = 0; n < 500; n++)
            {
                if (biblioLeyes[n] != null)
                {
                    if (biblioLeyes[n].getinfoDeLey() == txtLey.Text)
                    {
                        return false;
                        break;
                    }
                }
            }

            return true;
        }
    }
}

## FormPrestamo.cs

 public partial class FormPrestamo : Form
    {

        Grupo[] grupos = new Grupo[200];
        Usuario[] users = new Usuario[999];
        Ley[] biblioLeyes = new Ley[500];
        string usuarioActualM;


        public FormPrestamo(Usuario[] u, Grupo[] g, string us, Ley[] bl = null)
        {
            InitializeComponent();
            users = u;
            grupos = g;
            usuarioActualM = us;
            biblioLeyes = bl;
        }

        private void btnLey_Click(object sender, EventArgs e)
        {
            PrestarLey pl = new PrestarLey(users, grupos, usuarioActualM, biblioLeyes);
            pl.Show();
            this.Hide();

        }

        private void FormPrestamo_Load(object sender, EventArgs e)
        {

        }

        private void btnReglamento_Click(object sender, EventArgs e)
        {
            FormPrestarReg pr = new FormPrestarReg(users, grupos, usuarioActualM, biblioLeyes);
            pr.Show();
            this.Hide();
        }

        private void button1_Click(object sender, EventArgs e)
        {

            menu m = new menu(users, grupos, usuarioActualM, biblioLeyes);
            m.Show();
            this.Hide();

        }

        private void button2_Click(object sender, EventArgs e)
        {

            

            
            
    }
    }
}

## FormPrestarReg.cs

public partial class FormPrestarReg : Form
    {

        Grupo[] grupos = new Grupo[200];
        Usuario[] users = new Usuario[999];
        Ley[] biblioLeyes = new Ley[500];
        string usuarioActualM;
        Reglamentos[] tmp = new Reglamentos[5];
        ArrayList mostrar = new ArrayList();
        ArrayList mostrarReg = new ArrayList();
        queue copias = new queue();
        string[] traspaso = new string[2];
        
        public FormPrestarReg(Usuario[] u, Grupo[] g, string us, Ley[] bl = null)
        {
            InitializeComponent();
            InitializeComponent();
            users = u;
            grupos = g;
            usuarioActualM = us;
            biblioLeyes = bl;
            for (int i = 0; i < 500; i++)
            {
                if (biblioLeyes[i] != null)
                {
                    mostrar.Add(biblioLeyes[i].getinfoDeLey());
                }
            }

            for (int i = 0; i < mostrar.Count; i++)
            {
                listBox1.Items.Add(mostrar[i]);
            }

        }

        private void listBox1_SelectedIndexChanged(object sender, EventArgs e)
        {

        }

        private void FormPrestarReg_Load(object sender, EventArgs e)
        {

        }

        private void button1_Click(object sender, EventArgs e)
        {
            FormPrestamo m = new FormPrestamo(users, grupos, usuarioActualM, biblioLeyes);
            m.Show();
            this.Hide();
        }

        private void listBox2_SelectedIndexChanged(object sender, EventArgs e)
        {

        }

        private void btnMostrar_Click(object sender, EventArgs e)
        {
            if (verificarLey() == true || txtLey.Text == "")
            {
                MessageBox.Show(" la ley no esta disponible");
            }
            if (verificarLey() == false)
            {
                for (int i = 0; i < 500; i++)
                {
                    while (biblioLeyes[i] != null && biblioLeyes[i].getinfoDeLey() == txtLey.Text)
                    {
                        Reglamentos[] reg = new Reglamentos[5];
                        reg = biblioLeyes[i].getReglamentos();
                        for (int a = 0; a < 5; a++)
                        {
                            if (reg[a] != null)
                            {
                                mostrarReg.Add(reg[a].getInfoReglamento());

                            }

                        }
                        for (int l = 0; l < mostrar.Count; l++)
                        {
                            listBox2.Items.Add(mostrarReg[l]);
                        }
                        break;

                    }
                }
            }
        }

        private void txtIngMod_TextChanged(object sender, EventArgs e)
        {

        }
        private bool verificarLey()
        {
            for (int n = 0; n < 500; n++)
            {
                if (biblioLeyes[n] != null)
                {
                    if (biblioLeyes[n].getinfoDeLey() == txtLey.Text)
                    {
                        return false;
                        break;
                    }
                }
            }

            return true;
        }

        private int obtenerPosicionDelGrupo()
        {
            int n = 0;
            string g = users[obtenerPosUsuario()].getGrupo();
            for (int i = 0; i < 200; i++)
            {
                if (grupos[i] != null && grupos[i].getNombre() == g)
                {
                    return i;
                }
            }
            return n;
        }


        private int ObtenerPosicionLey()
        {
            int n = 0;
            for (int i = 0; i < 500; i++)
            {
                if (biblioLeyes[i] != null && biblioLeyes[i].getinfoDeLey() == txtLey.Text)
                {
                    return i;
                }
            }
            return n;
        }
        private int obtenerPosUsuario()
        {
            int a = 0;
            for (int i = 0; i < 999; i++)
            {

                if (users[i] != null && users[i].getId() == usuarioActualM)
                {
                    return i;
                }

            }
            return a;
        }
        private bool verificarReg()
        {
            if (verificarLey() == false)
            {
                for (int n = 0; n < 500; n++)
                {
                    if (biblioLeyes[n] != null)
                    {
                        tmp = biblioLeyes[n].getReglamentos();
                        if (tmp[posicionReg()].getInfoReglamento() == txtReg.Text)
                        {
                            return true;
                            break;
                        }

                    }
                }
            }


            return false;
        }
        public int posicionReg()
        {
            int num = 0;
            for (int i = 0; i < 5; i++)
            {
                if (tmp[i] != null)
                {
                    if (tmp[i].getInfoReglamento() == txtReg.Text)
                    {
                        return i;
                    }
                }
            }
            return num;
        }

        private void button2_Click(object sender, EventArgs e)
        {
            if (verificarLey() == false && verificarReg() == true)
            {
                tmp = biblioLeyes[ObtenerPosicionLey()].getReglamentos();
                copias = tmp[posicionReg()].getQueue();
                traspaso = grupos[obtenerPosicionDelGrupo()].getLeyesBajoPrestamo();

                for (int i = 0; i < 2; i++)
                {
                    if (traspaso[i] == null)
                    {
                        string info = traspaso[i] = copias.dequeue();
                        if (grupos[obtenerPosicionDelGrupo()].getUsuarioAcargo1() == "")
                        {
                            grupos[obtenerPosicionDelGrupo()].setUsuarioAcargo1(usuarioActualM);
                            grupos[obtenerPosicionDelGrupo()].setPrimerPrestamo(info);
                        }
                        if (grupos[obtenerPosicionDelGrupo()].getUsuarioAcargo1() != "" && grupos[obtenerPosicionDelGrupo()].getUsuarioAcargo2() == "")
                        {
                            grupos[obtenerPosicionDelGrupo()].setUsuarioAcargo2(usuarioActualM);
                            grupos[obtenerPosicionDelGrupo()].setSegundoPrestamo(info);

                        }
                        tmp[posicionReg()].setQueue(copias);
                        biblioLeyes[ObtenerPosicionLey()].setReglamentos(tmp);
                        grupos[obtenerPosicionDelGrupo()].setBajoPrestamo(traspaso);

                        MessageBox.Show("Dato devuelto con exito");
                        menu m = new menu(users, grupos, usuarioActualM, biblioLeyes);
                        m.Show();
                        this.Hide();

                        break;
                    }
                    else
                    {
                        MessageBox.Show("Maximo de prestamos alcanzado");
                        break;
                    }
                }
            }



            else
            {
                MessageBox.Show("No se encontro ley para prestar");

            }
                  
               

            }
        }
    }
    
    ## Menu.cs
    
    public partial class menu : Form
    {
        Grupo[] grupos = new Grupo[200];
        Usuario[] users = new Usuario[999];
        Ley[] biblioLeyes = new Ley[500];
        queue copiasLey = new queue();
        string usuarioActualM;
        public menu()
        {
            InitializeComponent();
        }
        public menu(Usuario[] u,Grupo[] g ,string UsuarioActual="", Ley[] bl=null,queue cl=null)
        {
            InitializeComponent();

            users = u;
            usuarioActualM = UsuarioActual;
            grupos = g;
            biblioLeyes = bl;
            copiasLey = cl;
        }


        private void menu_Load(object sender, EventArgs e)
        {

        }

        private void button6_Click(object sender, EventArgs e)
        {
            modificar_usuario mod = new modificar_usuario(users,grupos,usuarioActualM);
            mod.Show();
            this.Hide();
        }

        private void button1_Click(object sender, EventArgs e)
        {
            FormCLey cley = new FormCLey(users, grupos,usuarioActualM);
            cley.Show();
            this.Hide();
        }

        private void button3_Click(object sender, EventArgs e)
        {
            ModLey mley = new ModLey(users,grupos,usuarioActualM,biblioLeyes,copiasLey);
            mley.Show();
            this.Hide();
        }

        private void button5_Click(object sender, EventArgs e)
        {
            FormCReg creg = new FormCReg(users, grupos, usuarioActualM, biblioLeyes);
            creg.Show();
            this.Hide();
        }

        private void button4_Click(object sender, EventArgs e)
        {
            ModReg modificarreglamento = new ModReg(users, grupos, usuarioActualM, biblioLeyes);
            modificarreglamento.Show();
            this.Hide();
        }

        private void button2_Click(object sender, EventArgs e)
        {
            FormPrestamo PrestarLey = new FormPrestamo(users, grupos, usuarioActualM,biblioLeyes);
            PrestarLey.Show();
            this.Hide();
        }

        private void button7_Click(object sender, EventArgs e)
        {
            devolucioncs Devolverley = new devolucioncs(users, grupos, usuarioActualM, biblioLeyes);
            Devolverley.Show();
            this.Hide();
        }

        private void button8_Click(object sender, EventArgs e)
        {
            Form1 SalirSeccion = new Form1();
            SalirSeccion.Show();
            this.Hide();
        }
    }
}

## modificar_usuario.cs

 public partial class modificar_usuario : Form
    {
        Grupo[] grupos = new Grupo[200];
        Usuario[] users = new Usuario[999];
        Ley[] biblioLeyes = new Ley[500];
        string usuarioActualM;
        int numarreglo=0;
        string grupoI;
        string grupoF;
       
        
    
        
        public modificar_usuario( Usuario[] u,Grupo[] g, string usuarioActual="", Ley[] bl=null )
        {
            InitializeComponent();
            users = u;
            grupos = g;

            users = u;
            usuarioActualM = usuarioActual;
            biblioLeyes = bl;

            for(int i =0; i < users.Length; i++)
            {
                if (users[i].getId() == usuarioActual)
                {
                    numarreglo = i;
                    break;
                }
            }
                    if(users[numarreglo].getId()== usuarioActualM)
                    {
                        if(users[numarreglo].getCargo()=="parlamentario"|| users[numarreglo].getCargo() == "Parlamentario")
                        {
                                     txtID.Text = users[numarreglo].getId();
                                     txtCargo.Text = users[numarreglo].getCargo();
                                     txtCargo.Hide();
                                      label4.Hide();
                                       txtGrupo.Text = users[numarreglo].getGrupo();
                                      txtGrupo.Hide();
                                         label1.Hide();
                                     txtContra.Text = users[numarreglo].getContra();
                                       

                        }
                        if (users[numarreglo].getCargo() == "asesor" || users[numarreglo].getCargo() == "Asesor")
                        {
                            txtID.Text = users[numarreglo].getId();
                            txtCargo.Text = users[numarreglo].getCargo();
                            label4.Hide();
                             txtCargo.Hide();
                             grupoI=txtGrupo.Text = users[numarreglo].getGrupo();
                            txtContra.Text = users[numarreglo].getContra();

                        }
                    }
                }
               
              
              
            

        private void modificar_usuario_Load(object sender, EventArgs e)
        {

        }

        private void label2_Click(object sender, EventArgs e)
        {

        }

        private void labID_Click(object sender, EventArgs e)
        {

        }

        private void btnBuscar_Click(object sender, EventArgs e)
        {
          

           
            
        }

        private void panel1_Paint(object sender, PaintEventArgs e)
        {

        }

        private void label6_Click(object sender, EventArgs e)
        {

        }

        private void label3_Click(object sender, EventArgs e)
        {

        }

        private void textBox1_TextChanged(object sender, EventArgs e)
        {

        }

        private void button1_Click(object sender, EventArgs e)
        {
            if ( txtContra.Text != ""  && txtID.Text != "")
            {

                users[numarreglo].setId(txtID.Text);
                users[numarreglo].setCargo(txtCargo.Text);
                users[numarreglo].setContra(txtContra.Text);
                grupoF = txtGrupo.Text;
                if(grupoF != grupoI)
                {
                    for(int i =0; i<200; i++)
                    {
                        if (grupos[i] != null)
                        {
                            if (grupos[i].getNombre() == grupoF)
                            {
                                if (grupos[i].getContador() == 8)
                                {
                                    MessageBox.Show("El grupo al que desea entrar esta lleno");
                                    break;
                                }
                                else
                                {
                                    grupos[i].asignarAsesor(users[numarreglo]);
                                    grupos[posArregloG()].eliminarAsesor(usuarioActualM);
                                    users[numarreglo].setGrupo(grupos[i].getNombre());

        
                                }
                                
                                }
                            }
                        }
                    }
                
                MessageBox.Show("Usuario modificado con exito");
                menu m = new menu(users, grupos, usuarioActualM, biblioLeyes);
                m.Show();
                this.Hide();
            }
            else
            {
                MessageBox.Show("no puede dejar campos vacios");
            }

        }

        private void button2_Click(object sender, EventArgs e)
        {
            string grupoE;
            for (int i = 0; i < 999; i++)
            {
                if (users[i] != null)
                {
                    if (users[i].getId() == usuarioActualM)
                    {
                        if (users[i].getCargo() == "parlamentario" || users[i].getCargo() == "Parlamentario")
                        {
                            grupoE = users[i].getGrupo();
                            for (int a = 0; a < 999; a++)
                            {
                                if (users[a]!= null && users[a].getGrupo() == grupoE)
                                {
                                    users[a] = null;
                                }
                                for (int b = 0; b < 200; b++)
                                {
                                    if (grupos[b] != null&& grupos[b].getNombre() == grupoE)
                                    {
                                        grupos[b] = null;
                                    }
                                }
                            }


                        }
                        if (users[i].getCargo() == "asesor" || users[i].getCargo() == "Asesor")
                        {
                            grupoE = users[i].getGrupo();
                            for (int a = 0; a < 200; a++)
                            {
                                if (grupos[a].getNombre() == grupoE)
                                {
                                    grupos[a].eliminarAsesor(users[i].getId());

                                }

                            }
                        }
                        MessageBox.Show("Usuario Eliminado");
                        Form1 f1 = new Form1(users, grupos);
                    }
                }

            }
        }
            
        

        private void label5_Click(object sender, EventArgs e)
        {

        }

        private void btnRegresar_Click(object sender, EventArgs e)
        {
            menu m = new menu(users, grupos, usuarioActualM, biblioLeyes);
            m.Show();
            this.Hide();

        }
        private int posArregloG()
        { int n = 0;
            for(int i = 0; i < 200; i++)
            {
                if(grupos[i]!=null && grupos[i].getNombre()== grupoI)
                {
                    return n;
                }
            }
            return n;
        }
      
    }
}


## ModLey.cs
public partial class ModLey : Form
    {

        Grupo[] grupos = new Grupo[200];
        Usuario[] users = new Usuario[999];
        Ley[] biblioLeyes = new Ley[500];
        queue copiasLey = new queue();
        string usuarioActualM;
        ArrayList mostrar = new ArrayList();
        
        public ModLey(Usuario[] u, Grupo[] g, string UsuarioActual = "", Ley[] bl = null, queue cl = null)
        {
            InitializeComponent();
            users = u;
            grupos = g;
            usuarioActualM = UsuarioActual;
            biblioLeyes = bl;
            copiasLey = cl;

            for (int i =0; i< 500; i++)
            {
                if (biblioLeyes[i] != null)
                {
                    mostrar.Add(biblioLeyes[i].getinfoDeLey());
                }
            }

            for (int i = 0; i < mostrar.Count; i++)
            {
                listBox1.Items.Add(mostrar[i]);
            }




        }

        private void label1_Click(object sender, EventArgs e)
        {

        }

        private void ModLey_Load(object sender, EventArgs e)
        {

        }

        private void button1_Click(object sender, EventArgs e)
        {
            if (txtIngMod.Text == "" && txtModBox.Text == "")
            {
                MessageBox.Show(" Debe ingresar la ley que desea modificar y el nuevo contenido");
            }
            else
            {
                for (int i = 0; i < 500; i++)
                {
                    if (biblioLeyes[i].getinfoDeLey() == txtIngMod.Text && biblioLeyes[ObtenerPosicionLey()].getCopiasDisponibles() == 5)
                    {
                        biblioLeyes[i].setinfoDeLey(txtModBox.Text);
                        MessageBox.Show("ley modificada con exito");
                        menu m = new menu(users, grupos, usuarioActualM, biblioLeyes, copiasLey);
                        m.Show();
                        this.Hide();
                        break;
                    }
                    else if(biblioLeyes[i].getinfoDeLey() == txtIngMod.Text && biblioLeyes[ObtenerPosicionLey()].getCopiasDisponibles() != 5)
                    {
                        MessageBox.Show("debe de retornar todas las copias para modificar");
                        break;
                    }
                    else
                    {
                        MessageBox.Show("la ley que desea modificar no se encuentra en el sistema");
                        txtIngMod.Clear();
                        txtModBox.Clear();
                        break;
                    }
                }
            }

        }

        private void txtIngMod_TextChanged(object sender, EventArgs e)
        {

        }

        private void txtModBox_TextChanged(object sender, EventArgs e)
        {

        }

        private void btnEliminar_Click(object sender, EventArgs e)
        {

            if (txtIngMod.Text == "")
            {
                MessageBox.Show(" Debe ingresar la ley que desea eliminar");
            }
            else
            {
                for (int i = 0; i < 500; i++)
                {
                    if (biblioLeyes[i].getinfoDeLey() == txtIngMod.Text)
                    {
                        biblioLeyes[i] = null;
                        MessageBox.Show("ley eliminada con exito");
                        menu m = new menu(users, grupos, usuarioActualM, biblioLeyes, copiasLey);
                        m.Show();
                        this.Hide();
                        break;
                    }
                    else
                    {
                        MessageBox.Show("la ley que desea eliminar no se encuentra en el sistema");
                        txtIngMod.Clear();
                        txtModBox.Clear();
                        break;
                    }
                }
            }
        }

        private void button1_Click_1(object sender, EventArgs e)
        {
            menu m = new menu(users, grupos, usuarioActualM, biblioLeyes, copiasLey);
            m.Show();
            this.Hide();
        }

        private void listBox1_SelectedIndexChanged(object sender, EventArgs e)
        {

        }
        private int ObtenerPosicionLey()
        {
            int n = 0;
            for (int i = 0; i < 500; i++)
            {
                if (biblioLeyes[i] != null && biblioLeyes[i].getinfoDeLey() == txtIngMod.Text)
                {
                    return i;
                }
            }
            return n;
        }
    }
}

## ModReg.cs

public partial class ModReg : Form
    {
        Grupo[] grupos = new Grupo[200];
        Usuario[] users = new Usuario[999];
        Ley[] biblioLeyes = new Ley[500];
        string usuarioActualM;
        Reglamentos[] tmp = new Reglamentos[5];
        ArrayList mostrar = new ArrayList();
        ArrayList mostrarReg = new ArrayList();


        public ModReg(Usuario[] u, Grupo[] g, string us, Ley[] bl = null)
        {
            InitializeComponent();
            users = u;
            grupos = g;
            usuarioActualM = us;
            biblioLeyes = bl;

            for (int i = 0; i < 500; i++)
            {
                if (biblioLeyes[i] != null)
                {
                    mostrar.Add(biblioLeyes[i].getinfoDeLey());
                }
            }

            for (int i = 0; i < mostrar.Count; i++)
            {
                listBox1.Items.Add(mostrar[i]);
            }

        }

        private void label3_Click(object sender, EventArgs e)
        {

        }

        private void button2_Click(object sender, EventArgs e)
        {

        }

        private void button3_Click(object sender, EventArgs e)
        {
            menu m = new menu (users, grupos, usuarioActualM, biblioLeyes);
            m.Show();
            this.Hide();
        }

        private void ModReg_Load(object sender, EventArgs e)
        {

        }

        private void button1_Click(object sender, EventArgs e)
        {
            while (verificarLey() == false && verificarReg() == true&& tmp[posicionReg()].getCopiasDisponibles()==5)
            {

                if (verificarReg() == false)
                {
                    MessageBox.Show(" el reglamento  no se encuentra en el sistema");
                    break;
                }
                tmp[posicionReg()].retirarCopiasMod(txtReg.Text);
                tmp[posicionReg()].setInfoReglamento(txtNewReg.Text);
                tmp[posicionReg()].asignarCopiasR();



                menu m = new menu(users, grupos, usuarioActualM, biblioLeyes);
                m.Show();
                this.Hide();
                break;

            }
            if (verificarLey() == true)
            {
                MessageBox.Show(" la ley no se encuentra en el sistema");
            }
            if(tmp[posicionReg()].getCopiasDisponibles() != 5)
            {
                MessageBox.Show(" Deben retornar todas las copias para modificar el reglamento");
            }
          



        }


        private void textBox2_TextChanged(object sender, EventArgs e)
        {

        }

        private bool verificarLey()
        {
            for (int n = 0; n < 500; n++)
            {
                if (biblioLeyes[n] != null)
                {
                    if (biblioLeyes[n].getinfoDeLey() == txtLey.Text)
                    {
                        return false;
                        break;
                    }
                }
            }

            return true;
        }

        private bool verificarReg()
        {
            if (verificarLey() == false)
            {
                for (int n = 0; n < 500; n++)
                {
                    if (biblioLeyes[n] != null)
                    {
                        tmp = biblioLeyes[n].getReglamentos();
                        if (tmp[posicionReg()].getInfoReglamento() == txtReg.Text)
                        {
                            return true;
                                break;
                        }
                           
                    }
                }
            }


            return false;
        }
        public int posicionReg()
        {
            int num = 0;
            for (int i = 0; i < 5; i++)
            {
                if (tmp[i] != null)
                {
                    if (tmp[i].getInfoReglamento() == txtReg.Text)
                    {
                        return i;
                    }
                }
            }
            return num;
        }

        private void txtLey_TextChanged(object sender, EventArgs e)
        {

        }

        private void listBox1_SelectedIndexChanged(object sender, EventArgs e)
        {

        }

        private void label4_Click(object sender, EventArgs e)
        {

        }

        private void button1_Click_1(object sender, EventArgs e)
        {
            if (verificarLey() == true|| txtLey.Text=="")
            {
                MessageBox.Show(" la ley no esta disponible");
            }
            if (verificarLey() == false)
            {
                for (int i = 0; i < 500; i++)
                {
                    while (biblioLeyes[i] != null && biblioLeyes[i].getinfoDeLey() == txtLey.Text)
                    {
                        Reglamentos[] reg = new Reglamentos[5];
                        reg = biblioLeyes[i].getReglamentos();
                        for (int a = 0; a < 5; a++)
                        {
                            if (reg[a] != null)
                            {
                                mostrarReg.Add(reg[a].getInfoReglamento());
                                
                            }

                        }
                        for (int l = 0; l < mostrar.Count; l++)
                        {
                            listBox2.Items.Add(mostrarReg[l]);
                        }
                        break;
                      
                    }
                }
            }
        }
    }
}

## PrestarLey.cs

public partial class PrestarLey : Form
    {
        Grupo[] grupos = new Grupo[200];
        Usuario[] users = new Usuario[999];
        Ley[] biblioLeyes = new Ley[500];
        string usuarioActualM;
        string[] traspaso = new string[2];
        ArrayList mostrar = new ArrayList();
        public PrestarLey(Usuario[] u, Grupo[] g, string us, Ley[] bl = null)
        {
            InitializeComponent();
            users = u;
            grupos = g;
            usuarioActualM = us;
            biblioLeyes = bl;
            for (int i = 0; i < 500; i++)
            {
                if (biblioLeyes[i] != null)
                {
                    mostrar.Add(biblioLeyes[i].getinfoDeLey());
                }
            }

            for (int i = 0; i < mostrar.Count; i++)
            {
                listBox1.Items.Add(mostrar[i]);
            }
        }

        private void listBox1_SelectedIndexChanged(object sender, EventArgs e)
        {

        }

        private void PrestarLey_Load(object sender, EventArgs e)
        {


        }

        private void button1_Click(object sender, EventArgs e)
        {
            FormPrestamo m = new FormPrestamo(users, grupos, usuarioActualM, biblioLeyes);
            m.Show();
            this.Hide();
        }

        private void button2_Click(object sender, EventArgs e)
        {
            if (txtLey.Text == "")
            {
                MessageBox.Show("debe escribir una ley");
            }
            if(verificarLey() == true)
            {
                queue copiasley = new queue();
                string leyprestada = txtLey.Text;
                copiasley = biblioLeyes[ObtenerPosicionLey()].getQueue();
                traspaso = grupos[obtenerPosicionDelGrupo()].getLeyesBajoPrestamo();

                for(int i =0; i < 2; i++)
                {   
                    if(traspaso[i]== null)
                    {

                        traspaso[i] = copiasley.dequeue();

                        if (grupos[obtenerPosicionDelGrupo()].getUsuarioAcargo1() == "")
                        {
                            grupos[obtenerPosicionDelGrupo()].setUsuarioAcargo1(usuarioActualM);
                        }
                        if (grupos[obtenerPosicionDelGrupo()].getUsuarioAcargo1() != "" && grupos[obtenerPosicionDelGrupo()].getUsuarioAcargo2() == ""){
                            grupos[obtenerPosicionDelGrupo()].setUsuarioAcargo2(usuarioActualM);
                        
                        }
                        biblioLeyes[ObtenerPosicionLey()].setQueue(copiasley);
                        grupos[obtenerPosicionDelGrupo()].setBajoPrestamo(traspaso);

                        MessageBox.Show("ley prestada con exito");
                        menu m = new menu(users, grupos, usuarioActualM, biblioLeyes);
                        m.Show();
                        this.Hide();


                        break;
                    }
                    else
                    {
                        MessageBox.Show("Maximo de leyes prestadas alcanzado");
                        break;
                    }

                }
              




            }

        }

        private bool verificarLey()
        {
            for (int n = 0; n < 500; n++)
            {
                if (biblioLeyes[n] != null)
                {
                    if (biblioLeyes[n].getinfoDeLey() == txtLey.Text)
                    {
                        return false;
                        break;
                    }
                }
            }
            
            return true;
        }

        private int obtenerPosUsuario()
        {       int a = 0;
            for(int i =0; i < 999; i++)
            {
                
                if(users[i]!= null&&users[i].getId()== usuarioActualM)
                {
                    return i;
                }
               
            } return a;
        }


        private int obtenerPosicionDelGrupo()
        {
            int n = 0;
           string g= users[obtenerPosUsuario()].getGrupo();
            for(int i=0; i<200; i++)
            {
               if(grupos[i]!=null&& grupos[i].getNombre()== g)
                {
                    return i;
                }
            }
            return n;
        }
        private int ObtenerPosicionLey()
        {
            int n = 0;
            for (int i =0; i<500; i++)
            {
                if (biblioLeyes[i] != null && biblioLeyes[i].getinfoDeLey() == txtLey.Text)
                {
                    return i;
                }
            }
            return n;
        }

        private void button3_Click(object sender, EventArgs e)
        {
            

            
        }
        }
}

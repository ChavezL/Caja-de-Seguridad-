# Caja-de-Seguridad-
Una caja fuerte creada en java mediante interfaces gráficas 
Espero y les sirva de Algo, aqui esta el código fuente :D


package Unidad4;

import java.awt.BorderLayout;
import java.awt.EventQueue;

import javax.swing.JFrame;
import javax.swing.JOptionPane;
import javax.swing.JPanel;
import javax.swing.border.EmptyBorder;
import java.awt.Color;
import javax.swing.JTextField;
import javax.swing.SwingConstants;
import java.awt.Font;

import javax.swing.ImageIcon;
import javax.swing.JButton;
import java.awt.event.ActionListener;
import java.awt.event.ActionEvent;

public class CajadeSeguridad extends JFrame {

	private JPanel contentPane;
	private static JTextField txt1;
	private static JTextField txt2;
	private static JTextField txt3;
	private static JTextField txt4;
	private static JButton btnDefinirArray;
	static int x=0, conta=0;
	static String op="", clave="";
	static String[] Array = new String[4];
	static boolean casilla1=false, casilla2=false, casilla3=false, casilla4=false, Error=false, arr=true;
	/**
	 * Launch the application.
	 */
	
	
		 //Metodo por el cual se hace la comparacion del numero que 
	//uno selecciona y lo compara con los valores del arreglo
	static void M_cont(){
		if (arr==true){
			JOptionPane.showMessageDialog(null, "El arreglo no puede estar vacio ","¡Error!",
					 JOptionPane.ERROR_MESSAGE);
		}else
		 if (casilla1==false){
			 // Si el valor da correcto, permite avanzar a la siguiente casilla y cambia las variables boolenas a True
			 for ( x=0; x<4; x++){
				 if (op.equals(Array[x]) && x==0){
					 txt1.setText(Array[x]);
					 x=4;
					 casilla1=true;
					 
				 }else
				 
					 Error=true;
				 
			 }
			 //Nota: La condición If es para que en caso de que la variable booleana
			 // ya se True no entre a esa opcion
		 }else if (casilla2==false){
			 for ( x=1; x<4; x++){
				 if (op.equals(Array[x])){
					 txt2.setText(Array[x]);
					 x=4;
					 casilla2=true;
					 
				 }else
					 Error=true;
				 
			 }
		 }else if (casilla3==false){
			 for ( x=2; x<4; x++){
				 if (op.equals(Array[x])){
					 txt3.setText(Array[x]);
					 x=4;
					 casilla3=true;
					 
				 }else
					 Error=true;
			 }
		 }else if (casilla4==false){
			 for ( x=3; x<4; x++){
				 if (op.equals(Array[x])){
					 txt4.setText(Array[x]);
					 x=4;
					 casilla4=true;
				 }else
					 Error=true;
				 
			 }
		 }
		
		//En caso de que algunas de las condiciones pasadas no sea correctar, entrara en
		// accion el metodo del error
		if (Error==true){
			M_Error();}
		 
		if (casilla1==true && casilla2==true && casilla3==true && casilla4==true){
			 JOptionPane.showMessageDialog(null, "Abriste la caja ","¡Felicidades!",
					 JOptionPane.INFORMATION_MESSAGE, new ImageIcon("src/Images/Open.png"));
			 txt1.setText("");
			 txt2.setText("");
			 txt3.setText("");
			 txt4.setText("");
	
		}
	
	}
	//El siguiente metodo muestra un mensaje de error cuando se pone un numero que no es
	// Y da solo tres oportunidades
	static void M_Error(){
		conta=conta+1;
		if (conta<3){
			JOptionPane.showMessageDialog(null, "Numero equivocado ","¡Error!",
					 JOptionPane.ERROR_MESSAGE);
			
			casilla1=false;
			casilla2=false;
			casilla3=false;
			casilla4=false;
			arr=false;
			Error=false;
			txt1.setText("");
			txt2.setText("");
			txt3.setText("");
			txt4.setText("");
		
		}else {
			JOptionPane.showMessageDialog(null, "Numero equivocado " + 
		"\n Has agotado tus intentos, ¡Adios!","¡Error!",
					 JOptionPane.ERROR_MESSAGE);
			System.exit(DISPOSE_ON_CLOSE);
		}
		
		}
	public static void main(String[] args) {
		EventQueue.invokeLater(new Runnable() {
			public void run() {
				try {
					CajadeSeguridad frame = new CajadeSeguridad();
					frame.setVisible(true);
				} catch (Exception e) {
					e.printStackTrace();
				}
			}
		});
	}

	/**
	 * Create the frame.
	 */
	
		
	public CajadeSeguridad() {
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		setBounds(100, 100, 491, 513);
		contentPane = new JPanel();
		contentPane.setBackground(Color.BLACK);
		contentPane.setBorder(new EmptyBorder(5, 5, 5, 5));
		setContentPane(contentPane);
		contentPane.setLayout(null);
		
		txt1 = new JTextField();
		txt1.setEditable(false);
		txt1.setForeground(Color.RED);
		txt1.setFont(new Font("Rockwell", Font.PLAIN, 16));
		txt1.setHorizontalAlignment(SwingConstants.CENTER);
		txt1.setText("0");
		txt1.setBounds(77, 25, 38, 40);
		contentPane.add(txt1);
		txt1.setColumns(10);
		txt1.requestFocus();
		
		txt2 = new JTextField();
		txt2.setEditable(false);
		txt2.setForeground(Color.RED);
		txt2.setFont(new Font("Rockwell", Font.PLAIN, 16));
		txt2.setText("0");
		txt2.setHorizontalAlignment(SwingConstants.CENTER);
		txt2.setColumns(10);
		txt2.setBounds(175, 25, 38, 40);
		contentPane.add(txt2);
		
		txt3 = new JTextField();
		txt3.setEditable(false);
		txt3.setForeground(Color.RED);
		txt3.setFont(new Font("Rockwell", Font.PLAIN, 16));
		txt3.setText("0");
		txt3.setHorizontalAlignment(SwingConstants.CENTER);
		txt3.setColumns(10);
		txt3.setBounds(271, 25, 38, 40);
		contentPane.add(txt3);
		
		txt4 = new JTextField();
		txt4.setEditable(false);
		txt4.setForeground(Color.RED);
		txt4.setFont(new Font("Rockwell", Font.PLAIN, 16));
		txt4.setText("0");
		txt4.setHorizontalAlignment(SwingConstants.CENTER);
		txt4.setColumns(10);
		txt4.setBounds(358, 25, 38, 40);
		contentPane.add(txt4);
		
		JButton btn1 = new JButton("1");
		btn1.setFont(new Font("SansSerif", Font.PLAIN, 12));
		
		btn1.setBounds(123, 127, 55, 51);
		contentPane.add(btn1);
		
		JButton btn2 = new JButton("2");
		
		btn2.setFont(new Font("SansSerif", Font.PLAIN, 12));
		btn2.setBounds(220, 127, 55, 51);
		contentPane.add(btn2);
		
		JButton btn3 = new JButton("3");
		
		btn3.setFont(new Font("SansSerif", Font.PLAIN, 12));
		btn3.setBounds(317, 127, 55, 51);
		contentPane.add(btn3);
		
		JButton btn4 = new JButton("4");
		
		btn4.setFont(new Font("SansSerif", Font.PLAIN, 12));
		btn4.setBounds(123, 196, 55, 51);
		contentPane.add(btn4);
		
		JButton btn5 = new JButton("5");
		
		btn5.setFont(new Font("SansSerif", Font.PLAIN, 12));
		btn5.setBounds(220, 196, 55, 51);
		contentPane.add(btn5);
		
		JButton btn6 = new JButton("6");
		
		btn6.setFont(new Font("SansSerif", Font.PLAIN, 12));
		btn6.setBounds(317, 196, 55, 51);
		contentPane.add(btn6);
		
		JButton btn7 = new JButton("7");
		
		btn7.setFont(new Font("SansSerif", Font.PLAIN, 12));
		btn7.setBounds(123, 271, 55, 51);
		contentPane.add(btn7);
		
		JButton btn8 = new JButton("8");
		
		btn8.setFont(new Font("SansSerif", Font.PLAIN, 12));
		btn8.setBounds(220, 271, 55, 51);
		contentPane.add(btn8);
		
		JButton btn9 = new JButton("9");
		
		btn9.setFont(new Font("SansSerif", Font.PLAIN, 12));
		btn9.setBounds(317, 271, 55, 51);
		contentPane.add(btn9);
		
		JButton btn0 = new JButton("0");
		
		btn0.setFont(new Font("SansSerif", Font.PLAIN, 12));
		btn0.setBounds(220, 343, 55, 51);
		contentPane.add(btn0);
		// Este boton define la contraseña que se utilizara
		// para abrir la caja
		btnDefinirArray = new JButton("Definir Array");
		btnDefinirArray.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent arg0) {
			
				txt1.setText("");
				txt2.setText("");
				txt3.setText("");
				txt4.setText("");
				casilla1=false;
				casilla2=false;
				casilla3=false;
				casilla4=false;
				arr=false;
				
				char caracter=0;
				clave = JOptionPane.showInputDialog(null, "Ingresa los 4 números a guardar");
				
				for (int p=0; p<4; p++){
					
					caracter = clave.charAt(p);
					String resul = String.valueOf(caracter);
					Array[p]= resul;
					
				}
			
			}
			
		});
		
		//Dentro de los botones se define el valor que se compara con el del arreglo
		btnDefinirArray.setBounds(186, 434, 123, 29);
		contentPane.add(btnDefinirArray);
		btn1.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent arg0) {
					
				op = btn1.getText();
				M_cont();
				
				
			}
		});
		btn2.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent arg0) {
				
				op = btn2.getText();
				M_cont();
				
			}
		});
		btn3.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent arg0) {
				op = btn3.getText();
				M_cont();
				
			}
		});
		btn4.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent arg0) {
				op = btn4.getText();
				M_cont();
				
			}
		});
		
		btn5.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent arg0) {
				op = btn5.getText();
				M_cont();
				
			}
		});
		btn6.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent arg0) {
				op = btn6.getText();
				M_cont();
				
			}
		});
		btn7.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent arg0) {
				op = btn7.getText();
				M_cont();
				
			}
		});
		btn8.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent arg0) {
				op = btn8.getText();
				M_cont();
				
			}
		});
	
		btn9.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent arg0) {
				op = btn9.getText();
				M_cont();
				
			}
		});
		btn0.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent arg0) {
				op = btn0.getText();
				M_cont();
				
			}
		});
	}
}

import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class PetSelector extends JFrame {
    private JRadioButton birdButton, catButton, dogButton, rabbitButton, pigButton;
    private JLabel imageLabel;
    private ButtonGroup group;

    public PetSelector() {
        setTitle("RadioButtonDemo");

        // Create radio buttons
        birdButton = new JRadioButton("Bird");
        catButton = new JRadioButton("Cat");
        dogButton = new JRadioButton("Dog");
        rabbitButton = new JRadioButton("Rabbit");
        pigButton = new JRadioButton("Pig");

        // Add radio buttons to a group
        group = new ButtonGroup();
        group.add(birdButton);
        group.add(catButton);
        group.add(dogButton);
        group.add(rabbitButton);
        group.add(pigButton);

        // Panel for the radio buttons
        JPanel panel = new JPanel(new GridLayout(5, 1));
        panel.add(birdButton);
        panel.add(catButton);
        panel.add(dogButton);
        panel.add(rabbitButton);
        panel.add(pigButton);

        // Label to display the image
        imageLabel = new JLabel();
        imageLabel.setHorizontalAlignment(JLabel.CENTER);

        // Add an ActionListener to each button
        birdButton.addActionListener(new PetActionListener("bird.png"));
        catButton.addActionListener(new PetActionListener("cat.png"));
        dogButton.addActionListener(new PetActionListener("dog.png"));
        rabbitButton.addActionListener(new PetActionListener("rabbit.png"));
        pigButton.addActionListener(new PetActionListener("pig.png"));

        // Add components to the frame
        add(panel, BorderLayout.WEST);
        add(imageLabel, BorderLayout.CENTER);

        // Setup frame
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setSize(400, 300);
        setVisible(true);
    }

    // Inner class to handle button events
    private class PetActionListener implements ActionListener {
        private String imagePath;

        public PetActionListener(String imagePath) {
            this.imagePath = imagePath;
        }

        @Override
        public void actionPerformed(ActionEvent e) {
            ImageIcon icon = new ImageIcon(imagePath);
            imageLabel.setIcon(icon);
        }
    }

    public static void main(String[] args) {
        new PetSelector();
    }
}

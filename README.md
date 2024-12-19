
       import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class WordCounterApp {
    public static void main(String[] args) {
        
        JFrame frame = new JFrame("Word Counter Application");
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setSize(400, 300);
        frame.setLayout(new BorderLayout());

        
        JTextArea textArea = new JTextArea();
        textArea.setLineWrap(true);
        textArea.setWrapStyleWord(true);
        JScrollPane scrollPane = new JScrollPane(textArea);
        frame.add(scrollPane, BorderLayout.CENTER);

        
        JPanel panel = new JPanel();
        panel.setLayout(new BorderLayout());

    
        JButton countButton = new JButton("Count Words");
        panel.add(countButton, BorderLayout.WEST);

        
        JLabel resultLabel = new JLabel("Word Count: 0");
        resultLabel.setHorizontalAlignment(SwingConstants.CENTER);
        panel.add(resultLabel, BorderLayout.CENTER);

        frame.add(panel, BorderLayout.SOUTH);

    
        countButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                String text = textArea.getText();
                if (text.trim().isEmpty()) {
                    resultLabel.setText("Word Count: 0");
                } else {
                    String[] words = text.trim().split("\\s+");
                    resultLabel.setText("Word Count: " + words.length);
                }
            }
        });

        
        frame.setVisible(true);
    }
}

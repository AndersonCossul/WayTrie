package br.com.unisinos.extruturasdados1.tga;

import javafx.application.Application;
import javafx.collections.FXCollections;
import javafx.collections.ObservableList;
import javafx.scene.Scene;
import javafx.scene.control.ListView;
import javafx.scene.control.TextField;
import javafx.scene.layout.VBox;
import javafx.stage.Stage;

public class Editor extends Application {
	private ObservableList<String> itensAutoComplete;
	private ListView<String> autoComplete;
	private TextField input;
	private WayTrie<String> trie;

	public static void main(String[] args) {
		launch(args);
	}

	@Override
	public void start(Stage primaryStage) throws Exception {
		// Cria e carrega a TRIE
		trie = new WayTrie<>();
		loadDictionary();

		// Componentes para o autocomplete (entrada (textfield) e listview (com
		// as opçoes))
		itensAutoComplete = FXCollections.observableArrayList();
		autoComplete = new ListView<>(itensAutoComplete);

		// Event para quando digitar uma letra
		input = new TextField();
		input.textProperty().addListener((observable, oldValue, newValue) -> {
			autoComplete();
		});

		VBox root = new VBox(input, autoComplete);
		Scene scene = new Scene(root, 800, 800);

		primaryStage.setTitle("Editor Texto - Usando TRIE");
		primaryStage.setScene(scene);
		primaryStage.show();
	}

	private void loadDictionary() {
		trie.clear();
		/*
		trie.insert("MACA", "MACA");
		trie.insert("MESA", "MESA");
		trie.insert("MORTE", "MORTE");
		trie.insert("MOSCA", "MOSCA");
		*/
		trie.insert("foi", "foi");
		trie.insert("fora", "fora");
		trie.insert("fui", "fui");
		trie.insert("vai", "vai");
		trie.insert("ver", "ver");
		trie.insert("veremos", "veremos");
		trie.insert("vi", "vi");
		trie.insert("viu", "viu");
		trie.insert("vimos", "vimos");
	}

	private void autoComplete() {
		itensAutoComplete.clear();
		if (!input.getText().isEmpty()) {
			for (String each : trie.keysWithPrefix(input.getText()))
				itensAutoComplete.add(each);
		}
	}
}

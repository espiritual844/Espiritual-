import React, { useState } from 'react';
import { View, Text, TextInput, TouchableOpacity, ScrollView, StyleSheet, ActivityIndicator } from 'react-native';

export default function App() {
  const [input, setInput] = useState('');
  const [response, setResponse] = useState('');
  const [loading, setLoading] = useState(false);

  const handleAsk = async () => {
    setLoading(true);
    setResponse('');

    // Aqui futuramente entra a chamada à API real
    setTimeout(() => {
      setResponse("A alma fala em silêncio. Confie no que sente, mesmo que ainda não compreenda. A resposta está chegando.");
      setLoading(false);
    }, 2000);
  };

  return (
    <View style={styles.container}>
      <Text style={styles.title}>Guia Espiritual AI</Text>
      
      <TextInput
        placeholder="Descreva sua dúvida espiritual..."
        placeholderTextColor="#ccc"
        multiline
        style={styles.input}
        value={input}
        onChangeText={setInput}
      />

      <TouchableOpacity onPress={handleAsk} style={styles.button} disabled={loading}>
        <Text style={styles.buttonText}>{loading ? 'Meditando...' : 'Perguntar ao Guia'}</Text>
      </TouchableOpacity>

      <ScrollView style={styles.responseBox}>
        {loading && <ActivityIndicator size="large" color="#fff" />}
        {response !== '' && <Text style={styles.response}>{response}</Text>}
      </ScrollView>
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#1b1325',
    padding: 20,
    paddingTop: 60,
  },
  title: {
    fontSize: 28,
    color: '#fff',
    marginBottom: 20,
    fontWeight: 'bold',
    textAlign: 'center'
  },
  input: {
    backgroundColor: '#2e1f45',
    color: '#fff',
    padding: 15,
    borderRadius: 10,
    minHeight: 100,
    textAlignVertical: 'top'
  },
  button: {
    backgroundColor: '#7d5ba6',
    padding: 15,
    borderRadius: 10,
    marginTop: 15,
    alignItems: 'center'
  },
  buttonText: {
    color: '#fff',
    fontWeight: 'bold'
  },
  responseBox: {
    marginTop: 20,
    maxHeight: 300,
  },
  response: {
    color: '#f0e6ff',
    fontStyle: 'italic',
    fontSize: 16
  }
});# Espiritual-

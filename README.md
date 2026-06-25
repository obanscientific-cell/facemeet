# facemeet
messaging app
import React, { useState, useEffect } from 'react';
import { View, Text, FlatList, StyleSheet } from 'react-native';

// Sample data (in real apps, this comes from a backend API)
const samplePosts = [
  { id: '1', user: 'Alice', content: 'Hello world! First post 🎉' },
  { id: '2', user: 'Bob', content: 'Just had coffee ☕' },
  { id: '3', user: 'Charlie', content: 'Working on my new app 🚀' },
];

const NewsFeed = () => {
  const [posts, setPosts] = useState([]);

  useEffect(() => {
    // Simulate fetching posts from server
    setPosts(samplePosts);
  }, []);

  const renderPost = ({ item }) => (
    <View style={styles.post}>
      <Text style={styles.user}>{item.user}</Text>
      <Text style={styles.content}>{item.content}</Text>
    </View>
  );

  return (
    <FlatList
      data={posts}
      keyExtractor={(item) => item.id}
      renderItem={renderPost}
    />
  );
};

const styles = StyleSheet.create({
  post: {
    padding: 15,
    borderBottomWidth: 1,
    borderColor: '#ddd',
  },
  user: {
    fontWeight: 'bold',
    marginBottom: 5,
  },
  content: {
    fontSize: 16,
  },
});

export default NewsFeed;

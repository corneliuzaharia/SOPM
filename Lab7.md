# Lab. 7 - React Native

## Get started with Expo
1. Go to [https://expo.dev](https://expo.dev) and create a free account.

2. Download Expo Go on your phone

3. Go to [https://snack.expo.dev](https://snack.expo.dev)

4. Change the code and follow the changes on your phone and in the expo output window.

## Visual Studio Code with Expo
To initialize a new project, use create-expo-app to run the following command:

<code>npx create-expo-app my-app \
cd my-app</code>

To start the development server, run the following command:

<code> npx expo start</code>

To open the app your device that has Expo Go already installed:

- On your Android device, press Scan QR Code on the Home tab of the Expo Go app and scan the QR code you see in the terminal.

- On your iPhone or iPad, open the default Apple Camera app and scan the QR code you see in the terminal.

## Review the code presented at the React native course
### Basic app
    import React from 'react';
    import {Text, View} from 'react-native';

    const YourApp = () => {
        return (
            <View
            style={{
                flex: 1,
                justifyContent: 'center',
                alignItems: 'center',
            }}>
            <Text>Try editing me! 🎉</Text>
            </View>
        );
    };

    export default YourApp;
Play with the text content, size, alignment.

### Another basic app
    import { StatusBar } from 'expo-status-bar';
    import { StyleSheet, Text, View } from 'react-native';

    export default function App() {
        return (
            <View style={styles.container}>
            <Text>Open up App.js to start working on your app!</Text>
            <StatusBar style="auto" />
            </View>
        );
    }

    const styles = StyleSheet.create({
        container: {
            flex: 1,
            backgroundColor: '#fff',
            alignItems: 'center',
            justifyContent: 'center',
        },
    });
Can you change all the style lines? Be creative!

### Core Components - View, Text, Image, ScrollView, TextInput
    import React from 'react';
    import {View, Text, Image, ScrollView, TextInput} from 'react-native';

    const App = () => {
        return (
            <ScrollView>
            <Text>Some text</Text>
            <View>
                <Text>Some more text</Text>
                <Image
                source={{
                    uri: 'https://reactnative.dev/docs/assets/p_cat2.png',
                }}
                style={{width: 200, height: 200}}
                />
            </View>
            <TextInput
                style={{
                height: 40,
                borderColor: 'gray',
                borderWidth: 1,
                }}
                defaultValue="You can type in me"
            />
            </ScrollView>
        );
    };

    export default App;
### Handling Text Input
    import React, {useState} from 'react';
    import {Text, TextInput, View} from 'react-native';

    const PizzaTranslator = () => {
    const [text, setText] = useState('');
        return (
            <View style={{padding: 10}}>
            <TextInput
                style={{height: 40}}
                placeholder="Type here to translate!"
                onChangeText={newText => setText(newText)}
                defaultValue={text}
            />
            <Text style={{padding: 10, fontSize: 42}}>
                {text
                .split(' ')
                .map(word => word && '🍕')
                .join(' ')}
            </Text>
            </View>
        );
    };

    export default PizzaTranslator;
Can you change the code to put your mark?

### Using a ScrollView
    import React from 'react';
    import {Image, ScrollView, Text} from 'react-native';

    const logo = {
    uri: 'https://reactnative.dev/img/tiny_logo.png',
    width: 64,
    height: 64,
    };

    const App = () => (
    <ScrollView>
        <Text style={{fontSize: 96}}>Scroll me plz</Text>
        <Image source={logo} />
        <Image source={logo} />
        <Image source={logo} />
        <Image source={logo} />
        <Image source={logo} />
        <Text style={{fontSize: 96}}>If you like</Text>
        <Image source={logo} />
        <Image source={logo} />
        <Image source={logo} />
        <Image source={logo} />
        <Image source={logo} />
        <Text style={{fontSize: 96}}>Scrolling down</Text>
        <Image source={logo} />
        <Image source={logo} />
        <Image source={logo} />
        <Image source={logo} />
        <Image source={logo} />
        <Text style={{fontSize: 96}}>What's the best</Text>
        <Image source={logo} />
        <Image source={logo} />
        <Image source={logo} />
        <Image source={logo} />
        <Image source={logo} />
        <Text style={{fontSize: 96}}>Framework around?</Text>
        <Image source={logo} />
        <Image source={logo} />
        <Image source={logo} />
        <Image source={logo} />
        <Image source={logo} />
        <Text style={{fontSize: 80}}>React Native</Text>
    </ScrollView>
    );

    export default App;
### FlatList
    import React from 'react';
    import {FlatList, StyleSheet, Text, View} from 'react-native';

    const styles = StyleSheet.create({
    container: {
        flex: 1,
        paddingTop: 22,
    },
    item: {
        padding: 10,
        fontSize: 18,
        height: 44,
    },
    });

    const FlatListBasics = () => {
    return (
        <View style={styles.container}>
        <FlatList
            data={[
            {key: 'Devin'},
            {key: 'Dan'},
            {key: 'Dominic'},
            {key: 'Jackson'},
            {key: 'James'},
            {key: 'Joel'},
            {key: 'John'},
            {key: 'Jillian'},
            {key: 'Jimmy'},
            {key: 'Julie'},
            ]}
            renderItem={({item}) => <Text style={styles.item}>{item.key}</Text>}
        />
        </View>
    );
    };

    export default FlatListBasics;
### SectionList
    import React from 'react';
    import {SectionList, StyleSheet, Text, View} from 'react-native';

    const styles = StyleSheet.create({
    container: {
        flex: 1,
        paddingTop: 22,
    },
    sectionHeader: {
        paddingTop: 2,
        paddingLeft: 10,
        paddingRight: 10,
        paddingBottom: 2,
        fontSize: 14,
        fontWeight: 'bold',
        backgroundColor: 'rgba(247,247,247,1.0)',
    },	
    item: {
        padding: 10,
        fontSize: 18,
        height: 44,
    },
    });

    const SectionListBasics = () => {
    return (
        <View style={styles.container}>
        <SectionList
            sections={[
            {title: 'D', data: ['Devin', 'Dan', 'Dominic']},
            {
                title: 'J',
                data: [
                'Jackson',
                'James',
                'Jillian',
                'Jimmy',
                'Joel',
                'John',
                'Julie',
                ],
            },
            ]}
            renderItem={({item}) => <Text style={styles.item}>{item}</Text>}
            renderSectionHeader={({section}) => (
            <Text style={styles.sectionHeader}>{section.title}</Text>
            )}
            keyExtractor={item => `basicListEntry-${item}`}
        />
        </View>
    );
    };

    export default SectionListBasics;
### Platform module
Make your previous apps to handle differently for different platforms:

For example, change the background based on the Platform selection:

    import {Platform, StyleSheet} from 'react-native';

    const styles = StyleSheet.create({
        backgroundColor: Platform.OS === 'ios' ? 'rgba(100,247,245,1.0)' : 'rgba(247,247,247,1.0)',
    });
    import {Platform, StyleSheet} from 'react-native';
    const styles = StyleSheet.create({
    container: {
        flex: 1,

        ...Platform.select({
        ios: {
            backgroundColor: 'red',
        },
        android: {
            backgroundColor: 'green',
        },
        default: {
            // other platforms, web for example
            backgroundColor: 'blue',
        },
        }),

    },
    });
### Your app
Start from a counter example:

    import React, { useState } from 'react';
    import { View, Text, Button, StyleSheet, ScrollView} from 'react-native';

    const App = () => {
    const [count, setCount] = useState(0);

    const incrementCount = () => {
        setCount(count + 1);
    };

    const decrementCount = () => {
        if (count > 0) {
        setCount(count - 1);
        }
    };

    return (
        <View style={styles.container}>
        <Text style={styles.text}>Counter: {count}</Text>
        <View style={styles.buttonContainer}>
            <Button title="Increment" onPress={incrementCount} />
            <Button title="Decrement" onPress={decrementCount} />
        </View>
        </View>
    );
    };

    export default App;
1. Create a style for your Counter.
2. Add multiple counters to your app.
3. Create a ScrollView for your many counters.
4. Give each counter a different name.
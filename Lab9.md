# Lab. SOPM - 9
## Why
This lab is focused on understanding the relative layout in React Native.

We will experience several options to allow us to place our components at the needed location on the screen.

## Layout with Flexbox
A component can specify the layout of its children using the Flexbox algorithm. Flexbox is designed to provide a consistent layout on different screen sizes.

You will normally use a combination of flexDirection, alignItems, and justifyContent to achieve the right layout.

CAUTION

Flexbox works the same way in React Native as it does in CSS on the web, with a few exceptions.

The defaults are different, with:

- flexDirection defaulting to column instead of row,

- alignContent defaulting to flex-start instead of stretch,

- flexShrink defaulting to 0 instead of 1,

- the flex parameter only supporting a single number.

### flex
flex will define how your items are going to “fight” over the available space along your primary axis. Most of the time you will want your app container to be flex:1 to take all of the screen height. Space will be divided according to each element flex property. In the following example the red, yellow and the green views are all children in the container view that got flex:1. The red view got flex:1 , the yellow view got flex:2 and the green view got flex:3 . 1+2+3=6 which means that red view will get 1/6 of the space, the yellow 2/6 of the space and the red 3/6 of the space.

✍️ Check the code below. Change the flex values.

        import React, { Component } from 'react';
        import { View, Text } from 'react-native';

        export default class FlexDirectionBasics extends Component {
        render() {
            return (
            // Try setting `flexDirection` to `column`.
            <View style={styles.container}>
                <Text style={styles.headerStyle}>flex</Text>
                <View style={[{flex: 1}, styles.elementsContainer]}>
                <View style={{flex: 1, backgroundColor: '#EE2C38'}} />
                <View style={{flex: 2, backgroundColor: '#FAA030'}} />
                <View style={{flex: 3, backgroundColor: '#32B76C'}} />
                </View>
            </View>
            );
        }
        }

        const styles = {
        container: {
            marginTop: 48,
            flex: 1
        },
        headerStyle: {
            fontSize: 36,
            textAlign: 'center',
            fontWeight: '100',
            marginBottom: 24
        },
        elementsContainer: {
            backgroundColor: '#ecf5fd',
            marginLeft: 24,
            marginRight: 24,
            marginBottom: 24
        }
        }

### flexDirection
Defines the direction of the main axis. Opposite to the web, React Native default flexDirection is column which makes sense, most mobile apps much more vertically oriented.

✍️ Check the code below. Change the flexDirection as explained.

        import React, { Component } from 'react';
        import { View, Text } from 'react-native';

        export default class FlexDirectionBasics extends Component {
        render() {
            return (
            // Try setting `flexDirection` to 'column'/'column-reverse'/'row'/'row-reverse'
            <View style={styles.container}>
                <Text style={styles.headerStyle}>flexDirection: 'row-reverse'</Text>
                <View style={[{flexDirection:'row-reverse'}, styles.elementsContainer]}>
                <View style={{width: 50, height: 50, backgroundColor: '#EE2C38'}} />
                <View style={{width: 50, height: 50, backgroundColor: '#FAA030'}} />
                <View style={{width: 50, height: 50, backgroundColor: '#32B76C'}} />
                </View>
            </View>
            );
        }
        }

        const styles = {
        container: {
            marginTop: 48,
            flex: 1
        },
        headerStyle: {
            fontSize: 24,
            textAlign: 'center',
            fontWeight: '100',
            marginBottom: 24
        },
        elementsContainer: {
            flex: 1,
            backgroundColor: '#ecf5fd',
            marginLeft: 24,
            marginRight: 24,
            marginBottom: 24
        }
        }
### Justify Content​
justifyContent describes how to align children within the main axis of their container. For example, you can use this property to center a child horizontally within a container with flexDirection set to row or vertically within a container with flexDirection set to column.

- flex-start(**default value**) Align children of a container to the start of the container's main axis.

- flex-end Align children of a container to the end of the container's main axis.

- center Align children of a container in the center of the container's main axis.

- space-between Evenly space off children across the container's main axis, distributing the remaining space between the children.

- space-around Evenly space off children across the container's main axis, distributing the remaining space around the children. Compared to space-between, using space-around will result in space being distributed to the beginning of the first child and end of the last child.

- space-evenly Evenly distribute children within the alignment container along the main axis. The spacing between each pair of adjacent items, the main-start edge and the first item, and the main-end edge and the last item, are all the same.

✍️ Use the code above. Change the flexDirection with justifyContent and check all the possible values.

### Align Items​
alignItems describes how to align children along the cross axis of their container. It is very similar to justifyContent but instead of applying to the main axis, alignItems applies to the cross axis.

- stretch (**default value**) Stretch children of a container to match the height of the container's cross axis.

- flex-start Align children of a container to the start of the container's cross axis.

- flex-end Align children of a container to the end of the container's cross axis.

- center Align children of a container in the center of the container's cross axis.

- baseline Align children of a container along a common baseline. Individual children can be set to be the reference baseline for their parents.

✍️ Use the code above. Change the justifyContent with alignItems and check all the possible values.

### Align Self​
alignSelf has the same options and effect as alignItems but instead of affecting the children within a container, you can apply this property to a single child to change its alignment within its parent. alignSelf overrides any option set by the parent with alignItems.

✍️ Use the code above. Change the red box to be self-aligned.

### Flex Wrap​
The flexWrap property is set on containers and it controls what happens when children overflow the size of the container along the main axis. By default, children are forced into a single line (which can shrink elements). If wrapping is allowed, items are wrapped into multiple lines along the main axis if needed.

✍️ Check the code below. Change the flexWrap prop as explained.

        import React, { Component } from 'react';
        import { View, Text } from 'react-native';

        export default class FlexDirectionBasics extends Component {
            render() {
                return (
                    // Try playing with the flexWrap property 'wrap', 'nowrap', 'wrap-reverse'
                    <View style={styles.container}>
                        <Text style={styles.headerStyle}>flexWrap: 'wrap'</Text>
                        <View style={[{flexDirection: 'column', flexWrap: ' wrap'}, styles.elementsContainer]}>
                        <View style={styles.red} />
                        <View style={styles.yellow} />
                        <View style={styles.green} />
                        <View style={styles.blue} />
                        <View style={styles.cyan} />
                        <View style={styles.purple} />
                        <View style={styles.violet} />
                        </View>
                    </View>
                );
            }
        }

            const styles = {
            green : {
                backgroundColor: '#32B76C',
                height: 100,
                width: 50,
            },
            yellow : {
                backgroundColor: '#FAA030',
                height: 100,
                width: 50
            },
            red : {
                backgroundColor: '#EE2C38',
                height: 100,
                width: 50
            },
            blue : {
                backgroundColor: '#4196E0',
                height: 100,
                width: 50
            },
            cyan : {
                backgroundColor: '#32BABC',
                height: 100,
                width: 50
            },
            purple : {
                backgroundColor: '#A0138E',
                height: 100,
                width: 50
            },
            violet : {
                backgroundColor: '#733CA6',
                height: 100,
                width: 50
            },
            container: {
                marginTop: 48,
                flex: 1
            },
            headerStyle: {
                fontSize: 24,
                textAlign: 'center',
                fontWeight: '300',
                marginBottom: 24
            },
            elementsContainer: {
                backgroundColor: '#ecf5fd',
                marginLeft: 24,
                marginRight: 24,
                marginBottom: 24,
                height: 500
            }
        }
### Align Content​
alignContent defines the distribution of lines along the cross-axis. This only has effect when items are wrapped to multiple lines using flexWrap.

- flex-start (**default value**) Align wrapped lines to the start of the container's cross axis.

- flex-end Align wrapped lines to the end of the container's cross axis.

- stretch (default value when using Yoga on the web) Stretch wrapped lines to match the height of the container's cross axis.

- center Align wrapped lines in the center of the container's cross axis.

- space-between Evenly space wrapped lines across the container's cross axis, distributing the remaining space between the lines.

- space-around Evenly space wrapped lines across the container's cross axis, distributing the remaining space around the lines. Compared to space-between, using space-around will result in space being distributed to the beginning of the first line and the end of the last line.

✍️ Use the code above. Add the alignContent prop after flexWrap and verify all the available values.

### Row Gap, Column Gap and Gap​
- rowGap sets the size of the gap (gutter) between an element's rows.

- columnGap sets the size of the gap (gutter) between an element's columns.

- gap sets the size of the gap (gutter) between rows and columns. It is a shorthand for rowGap and columnGap.

✍️ Use the code above. You can use flexWrap and alignContent along with gap to add consistent spacing between items.

### Absolute & Relative Layout​
The position type of an element defines how it is positioned within its parent.

- relative (**default value**) By default, an element is positioned relatively. This means an element is positioned according to the normal flow of the layout, and then offset relative to that position based on the values of top, right, bottom, and left. The offset does not affect the position of any sibling or parent elements.

- absolute When positioned absolutely, an element doesn't take part in the normal layout flow. It is instead laid out independent of its siblings. The position is determined based on the top, right, bottom, and left values.

✍️ Check the code below. Change the position type from absolute to relative

        import React, { Component } from 'react';
        import { View, Text } from 'react-native';

        export default class FlexDirectionBasics extends Component {
        render() {
            return (
            // Try setting `alignItems` to 'flex-start', 'flex-end', 'center', 'stretch'
            <View style={styles.container}>
                <Text style={styles.headerStyle}>position</Text>
                <View style={styles.elementsContainer}>
                <View style={[{position: 'absolute'},styles.red]} />
                <View style={[{position: 'absolute'},styles.yellow]} />
                <View style={[{position: 'absolute'},styles.green]} />
                </View>
            </View>
            );
        }
        }

        const styles = {
        red : {
            backgroundColor: '#EE2C38',
            top: 25,
            left: 25,
            height: 50,
            width: 50
        },
        yellow : {
            backgroundColor: '#FAA030',
            top: 50,
            left: 50,
            height: 50,
            width: 50
        },
        green : {
            backgroundColor: '#32B76C',
            top: 75,
            left: 75,
            height: 50,
            width: 50
        },
        container: {
            marginTop: 48,
            flex: 1
        },
        headerStyle: {
            fontSize: 24,
            textAlign: 'center',
            fontWeight: '300',
            marginBottom: 24
        },
        elementsContainer: {
            flex: 1,
            backgroundColor: '#ecf5fd',
            marginLeft: 24,
            marginRight: 24,
            marginBottom: 24
        }
        }
### zIndex​
You can control which components display on top of others.

✍️ In the example above, set the zIndex of the yellow square to 1.

## Exercise
Now, please use your imagination to create an interesting layout for an application of your choice, to look consistent on web, iOS and Android.
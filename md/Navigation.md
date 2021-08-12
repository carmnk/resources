# Navigation

Navigation components help users to navigate to the content of interest within the current page or via hyperlink. They can be designed and styled very creatively, though it is often reasonable to give users some orientation by using established navigation elements.

## Bottom Navigation

A bottom navigation is an icon-button-based navigation bar fixed at the bottom of a page. It offers a comfortable way of navigating on mobile touch devices since the distance to reach for is shorter. Disadvantageous is the permanent reduction of available viewport height for content. Also regarding desktop devices or devices with wider viewports in general the bottom navigation is less commonly used. Most bottom navs span the whole width of the viewport which is even worse on desktop devices. One could limit the bottom nav's width but that would result in a notch which is also controversial. Another reason might be that users with mouse device tend to focus screens differently.

By default the vertical scrollbar will span the whole viewport height. In order to limit the scrollbar height to the content viewport (without footer) the content has to be wrapped in a `display="fixed"` Box component with `height="calc(100 - footerHeight)` `and width="100%"`.

The proposed `<BottomNav/>` component is based on Material UI's `<BottomNavigation/>` and `<BottomNavigationAction/>` components. The `<BottomNav/>` component is a simple wrapper for `<BottomNavigation/>` component. By default it sets `showLabels` to true and comes with internal state control for the active navigation item to demonstrate/prototype the functionality. In order to process the clicked navigation requests properly the `value` and `onChange` propertys have to be used and some sort of state control has to be implemented in the parent component. But in contrast to the underlying material ui component the items are provided as array of BottomNavigationActionProps (Array of objects, each containing props for the underlying `<BottomNavigationAction/>` component).

TEST abcdefghijklmnopqrstuvwxyz
https://stackoverflow.com/ https://stackoverflow.com/
TEST2 abcdefghijklmnopqrstuvwxyz

TEST3 abcdefghijklmnopqrstuvwxyz
[SomLinkyLink](https://stackoverflow.com/) [SomLinkyLink](https://stackoverflow.com/) https://stackoverflow.com/
TEST4 abcdefghijklmnopqrstuvwxyz

TEST5 abcdefghijklmnopqrstuvwxyz
[SomLinkyLink](https://stackoverflow.com/) Test5a abcdefghijklmnopqrstuvwxyz  [SomLinkyLink](https://stackoverflow.com/) Test5a abcdefghijklmnopqrstuvwxyz https://stackoverflow.com/
TEST6 abcdefghijklmnopqrstuvwxyz

### Implementation

```javascript
export const App = () => {
  const footerHeight = 50;
  return (
    <React.Fragment>
      <Box position="fixed" height={`calc(100% - ${footerHeight}px)`} width="100%">
        some Content .....
      </Box>
      <Box position="fixed" height={footerHeight} bottom={0} left={0} width="100%" bgcolor="teal">
        <BottomNav
          navItems={[
            { label: "Home", icon: <Icon size={1} path={mdiHome} /> },
            { label: "Work", icon: <Icon size={1} path={mdiFactory} /> },
            { label: "Travel", icon: <Icon size={1} path={mdiAirplane} /> },
            { label: "Spare Time", icon: <Icon size={1} path={mdiGamepad} /> },
          ]}
        />
      </Box>
    </React.Fragment>
  );
};
```

### Props

| Name       | Type                    | Default | Description                                                                                                                                                                                                                                                        |
| ---------- | ----------------------- | ------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| navItems   | NavigationActionProps[] |         | The content of each component.                                                                                                                                                                                                                                     |
| classes    | object                  |         | [Override or extend the styles applied to the component. See CSS API below for more details.](https://next.material-ui.com/api/bottom-navigation/#css)                                                                                                             |
| component  | elementType             |         | The component used for the root node. Either a string to use a HTML element or a component.                                                                                                                                                                        |
| onChange   | func                    |         | Callback fired when the value changes.<br>Signature:<br>function(event: React.SyntheticEvent, value: any) => void<br>event: The event source of the callback. Warning: This is a generic event not a change event.<br>value: We default to the index of the child. |
| showLabels | bool                    | FALSE   | If true, all BottomNavigationActions will show their labels. By default, only the selected BottomNavigationAction will show its label.                                                                                                                             |
| sx         | object                  |         | [The system prop that allows defining system overrides as well as additional CSS styles. See the \`sx\` page for more details.](https://next.material-ui.com/system/the-sx-prop/)                                                                                  |
| value      | any                     |         | The value of the currently selected BottomNavigationAction.                                                                                                                                                                                                        |

### navItem Props

each navigation item in the navItem array supports the following props:

| Name      | Type            | Default | Description                                                                                                                                                                       |
| --------- | --------------- | ------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| children  | unsupportedProp |         | This prop isn't supported. Use the `component` prop if you need to change the children structure.                                                                                 |
| classes   | object          |         | Override or extend the styles applied to the component. See [CSS API](https://next.material-ui.com/api/bottom-navigation-action/#css) below for more details.                     |
| icon      | node            |         | The icon to display.                                                                                                                                                              |
| label     | node            |         | The label element.                                                                                                                                                                |
| showLabel | bool            | true    | If `true`, all BottomNav items will show its label. If `false` only the active item will show its label.                                                                          |
| sx        | object          |         | The system prop that allows defining system overrides as well as additional CSS styles. See the [\`sx\` page](https://next.material-ui.com/system/the-sx-prop/) for more details. |
| value     | any             |         | You can provide your own value. Otherwise, we fallback to the child position index.                                                                                               |

## App Bar

App bars are very flexible menu bars most oftenly placed on top of a website. App bars are widely used on many websites and apps as navigation menu. Almost all app bars tend to display a title and a "Menu" IconButton (the hamburger) to open additional navigation elements. Other elements like (Icon-)Buttons and Search Fields can be added and placed as desired.  
The proposed CAppBar component is therfore a simple container based on material ui's `<Paper/>` component coming with styles for elevation (shadow depth). The underlying HTML container is a semantic `<header/>` element with a default `position: "fixed"`, `width: "100%"` (always same position, span full width), and `bgcolor: "primary.main"`, `color: "primary.contrastText"` (use material ui theme colors). The Appbar can be sized can chosen freely and be sized and styled as desired.

### Implementation

```javascript
export const App = () => {
  const barHeight = 64;
  return (
    <React.Fragment>
      <Box position="fixed" height={`calc(100% - ${barHeight}px)`} top={barHeight} overflow="auto" width="100%">
        some Content
      </Box>

      <CAppBar backgroundColor="primary.main" color="primary.contrastText" height={barHeight}>
        {/** content can be composed and styled as needed  */}
        <Stack direction="row" p={1} alignItems="center">
          <IconButton size="large" edge="start" color="inherit" aria-label="menu" sx={{ mr: 2 }}>
            <Icon size={1} path={mdiMenu} />
          </IconButton>
          <Typography variant="h6" component="div" sx={{ flexGrow: 1 }}>
            Some title here
          </Typography>
          <Box>
            <IconButton size="large" edge="start" color="inherit" sx={{ mr: 2 }}>
              <Icon size={1} path={mdiAirplane} />
            </IconButton>
            <IconButton size="large" edge="start" color="inherit">
              <Icon size={1} path={mdiHome} />
            </IconButton>
          </Box>
        </Stack>
      </CAppBar>
    </React.Fragment>
  );
};
```

### Props

| Name            | Type                                 | Default                | Description                                                                                                                                                                       |
| --------------- | ------------------------------------ | ---------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| children        | node                                 |                        | The content of the component.                                                                                                                                                     |
| classes         | object                               |                        | Override or extend the styles applied to the component. See [CSS API](https://next.material-ui.com/api/paper/#css) below for more details.                                        |
| component       | elementType                          |                        | The component used for the root node. Either a string to use a HTML element or a component.                                                                                       |
| elevation       | integer                              | 1                      | Shadow depth, corresponds to `dp` in the spec. It accepts values between 0 and 24 inclusive.                                                                                      |
| square          | bool                                 | false                  | If `true`, rounded corners are disabled.                                                                                                                                          |
| sx              | object                               |                        | The system prop that allows defining system overrides as well as additional CSS styles. See the [\`sx\` page](https://next.material-ui.com/system/the-sx-prop/) for more details. |
| variant         | 'elevation' \| 'outlined'\| 'string' | 'elevation'            | the variant to use                                                                                                                                                                |
| position        | React.CSSProperties["position"]      | fixed                  | CSS position property of the appbar container                                                                                                                                     |
| backgroundColor | BoxProps["bgcolor"]                  | "primary.main"         | CSS backgroundColor property supporting some mui theme values                                                                                                                     |
| color           | BoxProps["color"]                    | "primary.contrastText" | CSS color property supporting some mui theme values                                                                                                                               |
| height          | BoxProps["height"]                   | "auto"                 | height shortcut, for layout purposes relevant to control height programmatically                                                                                                  |

## Drawer

Drawers are static side sheets or dynamic overlays. They are usually complementary to other navigation elements like app bars. Many websites use drawers for menu navigation. It is also very popular as table of content for mobile devices. The static variant - due to permanent reduction of available viewport for content - should be prefered for devices with medium to big screens (> tablet). Dynamic drawers can partly cover the screen starting from any viewport edge (left, right, top, bottom) or they can overlay the whole screen. The content of a drawer can be designed freely. Most drawers contain some sort of clickable list with navigation targets, often visually emphasized with icons.
Material UI's `<Drawer/>` resp. `<SwipableDrawer/>` component provides a quick way to implement a drawer. Since both are using a portal the components can be placed anywhere in any parent (layout) component (JSX element). The drawer are served with build-in animations, elevations (shadows) and comes with a backdrop, causing the screen to dim and adding a close-on-click-away behavior. If the drawer does not need to be swipable the default `<Swiper/>` component should be used to reduce the package size (swipable drawer has 2kB gzipped overload). The `<SwipableDrawer/>` component adds customizable touch gestures to open and close the drawer which are exclusively working on touch devices, which is disadvantageos. The open gestures - swiping from edge to center often collides with native? or browser-default behavior (history back, history forwand in browser) on mobile devices. As far as I know there is no good to solution to this issues in browsers. Or is there? But things look differently in a native environment - I haven't fully covered this yet but seems possible.
Therefore a custom `<CDrawer/>` is introduced. It will either use the `<Swiper/>` or `<SwipableDrawer/>` component depending on whether or not `useSwipeableDrawer` property is provided. Another difference is `disableSwipeToOpen` is not only dsiabled on IOS devices (material ui default) but on all devices since it is often not working as intended (collides with browser/native gestures). `open`, `onOpen`, `onClose` are required compomnent propertys.

### Implementation

```javascript
export const App = () => {
  const [DrawerOpen, setDrawerOpen] = React.useState(false);
  const openDrawer = (event: React.KeyboardEvent | React.MouseEvent) => {
    setDrawerOpen(true);
  };
  const closeDrawer = (event: React.KeyboardEvent | React.MouseEvent) => {
    setDrawerOpen(false);
  };

  return (
    <React.Fragment>
      <CDrawer open={DrawerOpen} onOpen={openDrawer} onClose={closeDrawer}>
        <List>
          {["Inbox", "Starred", "Send email", "Drafts"].map((text, index) => (
            <ListItem button key={text}>
              <ListItemIcon>{index % 2 === 0 ? <InboxIcon /> : <MailIcon />}</ListItemIcon>
              <ListItemText primary={text} />
            </ListItem>
          ))}
        </List>
      </CDrawer>
    </React.Fragment>
  );
};
```

### Props Drawer

| Name               | Type                                  | Default                                             | Description                                                                                                                                                                       |
| ------------------ | ------------------------------------- | --------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| anchor             | bottom', 'left', 'right', 'top'       | 'left'                                              | Side from which the drawer will appear.                                                                                                                                           |
| children           | node                                  |                                                     | The content of the component.                                                                                                                                                     |
| classes            | object                                |                                                     | [Override or extend the styles applied to the component. See CSS API below for more details.](https://next.material-ui.com/api/drawer/#css)                                       |
| elevation          | integer                               | 16                                                  | The elevation of the drawer.                                                                                                                                                      |
| hideBackdrop       | bool                                  | FALSE                                               | If true, the backdrop is not rendered.                                                                                                                                            |
| ModalProps         | object                                | {}                                                  | [Props applied to the Modal element.](https://next.material-ui.com/api/modal/)                                                                                                    |
| onClose            | func                                  |                                                     | Callback fired when the component requests to be closed.<br>Signature:<br>function(event: object) => void<br>event: The event source of the callback.                             |
| open               | bool                                  | FALSE                                               | If true, the component is shown.                                                                                                                                                  |
| PaperProps         | object                                | {}                                                  | [Props applied to the Paper element.](https://next.material-ui.com/api/paper/)                                                                                                    |
| SlideProps         | object                                |                                                     | [Props applied to the Slide element.](https://next.material-ui.com/api/slide/)                                                                                                    |
| sx                 | object                                |                                                     | [The system prop that allows defining system overrides as well as additional CSS styles. See the \`sx\` page for more details.](https://next.material-ui.com/system/the-sx-prop/) |
| transitionDuration | number, { appear?: number, enter?: number, exit?: number } | { enter: duration.enteringScreen, exit: duration.leavingScreen }| The duration for the transition, in milliseconds. You may specify a single timeout for all transitions, or individually with an object. |
| variant            | permanent', 'persistent', 'temporary' | 'temporary'                                         | The variant to use.                                                                                                                                                               |                                                                                                                                                           |

### Props SwipeableDrawer

| Name                      | Type       | Default                                             | Description                                                                                                                                                   |
| ------------------------- | ---------- | --------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| onClose<sup>\*</sup>      | func       |                                                     | Callback fired when the component requests to be closed.<br><br>Signature:<br>`function(event: object) => void`<br>*event:* The event source of the callback. |
| onOpen<sup>\*</sup>       | func       |                                                     | Callback fired when the component requests to be opened.<br><br>Signature:<br>`function(event: object) => void`<br>*event:* The event source of the callback. |
| open<sup>\*</sup>         | bool       | false                                               | If `true`, the component is shown.                                                                                                                            |
| children                  | node       |                                                     | The content of the component.                                                                                                                                 |
| disableBackdropTransition | bool       | false                                               | Disable the backdrop transition. This can improve the FPS on low-end devices.                                                                                 |
| disableDiscovery          | bool       | false                                               | If `true`, touching the screen near the edge of the drawer will not slide in the drawer a bit to promote accidental discovery of the swipe gesture.           |
| disableSwipeToOpen        | bool       | true                                                | If `true`, swipe to open is disabled. This is useful in browsers where swiping triggers navigation actions                                                    |
| hysteresis                | number     | 0.52                                                | Affects how far the drawer must be opened/closed to change its state. Specified as percent (0-1) of the width of the drawer                                   |
| minFlingVelocity          | number     | 450                                                 | Defines, from which (average) velocity on, the swipe is defined as complete although hysteresis isn't reached. Good threshold is between 250 - 1000 px/s      |
| SwipeAreaProps            | object     |                                                     | The element is used to intercept the touch events on the edge.                                                                                                |
| swipeAreaWidth            | number     | 20                                                  | The width of the left most (or right most) area in `px` that the drawer can be swiped open from.                                                              |
| transitionDuration        | number<br> |  { appear?: number, enter?: number, exit?: number } | { enter: duration.enteringScreen, exit: duration.leavingScreen }                                                                                              | The duration for the transition, in milliseconds. You may specify a single timeout for all transitions, or individually with an object. |

## Breadcrumbs

## Link

## Menu

## Stepper

## Tabs

## Speed dial

## Pagination

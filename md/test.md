# `<CTable />`
react wrapper component for Material UI's `<Table/>` component facilitating/specifying usage and extending functionality.

| Name        | Type           | Default  | Required  |
| ------------- |:-------------:| -----:| -----:|
| [classes](#classes) | { rows?: string;<br /> roweven?: string;<br /> rowodd?: string;<br /> head?: string;<br /> selected?: string;<br /> "@media(pointer: fine)"?: string;<br /> stickyHeader?: string;<br /> } | {} |  |
| [conditionalCellClass](#conditionalCellClass) | (icol: number,<br /> irow: number,<br /> colkey: string,<br /> colcontent: string) => string | ??? |  |
| [conditionalRowClass](#conditionalRowClass) | (irow: number) => string | ??? |  |
| [data](#data) | { [key: string]: string;<br /> }[] | ??? | ✔️ |
| [doColorHeadRow](#doColorHeadRow) | boolean | true |  |
| [doColorRows](#doColorRows) | boolean | true |  |
| [header](#header) | { id: string;<br /> numeric?: boolean;<br /> disablePadding?: boolean;<br /> label?: string;<br /> align?: Alignment;<br /> }[] | [] |  |
| [preview](#preview) | number | 0 |  |
| [size](#size) | ```TODO 🚧``` | ```TODO 🚧 ``` |  |
| [TableBodyProps](#TableBodyProps) | ```TODO 🚧``` | ```TODO 🚧 ``` |  |
| [TableCheckboxProps](#TableCheckboxProps) | ```TODO 🚧``` | ```TODO 🚧 ``` |  |
| [TableContainerProps](#TableContainerProps) | ```TODO 🚧``` | ```TODO 🚧 ``` |  |
| [TableHeadProps](#TableHeadProps) | ```TODO 🚧``` | ```TODO 🚧 ``` |  |
| [TablePaginationProps](#TablePaginationProps) | ```TODO 🚧``` | ```TODO 🚧 ``` |  |
| [TableProps](#TableProps) | ```TODO 🚧``` | ```TODO 🚧 ``` |  |
| [title](#title) | string | Title 1235813 |  |
| [ToolbarProps](#ToolbarProps) | ```TODO 🚧``` | ```TODO 🚧 ``` |  |
| [ToolbarTypoProps](#ToolbarTypoProps) | ```TODO 🚧``` | ```TODO 🚧 ``` |  |
| [useHeader](#useHeader) | boolean | true |  |
| [usePagination](#usePagination) | boolean | true |  |
| [useSelectableAllRows](#useSelectableAllRows) | boolean | true |  |
| [useSelectableRows](#useSelectableRows) | boolean | true |  |
| [useStickyHeader](#useStickyHeader) | boolean | true |  |
| [useToolbar](#useToolbar) | boolean | true |  |

### \(`classes`\) 
object containing custom classes (made with MUIs makeStyles() hook, only those hook classes working?)\
supported classes:
- rows: superseeds roweven and rowodd, [doColorRows](#doColorRows) must be true
- roweven: even rows (first row is 0), [doColorRows](#doColorRows) must be true
- rowodd: odd rows (first row is 0), [doColorRows](#doColorRows) must be true\
default class's background is "#bdbdbd" if MUI theme is light otherwise (dark) it's "#757575"
- head: header row, [doColorHeadRow](#doColorHeadRow) must be true and [useStickyHeader](#useStickyHeader) false\
default class's background is "#757575" if MUI theme is light otherwise (dark) it's "#bdbdbd"
- seleceted: selected rows, \
default class's background is determined by MUI theme: theme.palette.primary.main
- stickyHeader: class for sticky header if [useStickyHeader](#useStickyHeader) is true, (doColorHeadRow is not active) \
default class's background is theme.palette.background.default
- "@media(pointer: fine)": css-media-query for pointers(not touch devices) intended to apply custom mouse hover effect for previously provided classes (rows, roweven...), see code example below. \
  by default: mouse hover effect for roweven, rowodd, selected is applied. Their hover background color is "#757575" if MUI theme is light otherwise (dark) it's "#bdbdbd"

example\
JS:
```ts
const myclasses= makeStyles(theme => ({
head: {background: blue,},
"@media(pointer: fine)": {
    head: {"&:hover": {background: "orange",},},
}
}));
```
JSX:
```jsx
<CTable classes={myclasses}\>
```
### \(`conditionalCellClass`\) 
Method conditionalCellClass can be provided to highlight/modify certain specific cells by providing specific class.\
Method is called when rendering table. The following parameters are passed: (icol, irow, colkey, rowcontent).\
your method can perform some conditional checks based on parameters and can return a MUI class (if your condition is fulfilled).\
example:
```jsx
<CTable conditionalCellClass={(icol, irow, colkey, rowcontent) => {
   if (irow === 1 && icol === 0) return specialcellclass
}} />
```
### \(`conditionalRowClass`\) 
similar to conditionalCellClass but used to highlight/modify whole rows.
Method is called when rendering table. The following parameters are passed: (irow).\
your method can perform some conditional checks based on parameters and can return a MUI class (if your condition is fulfilled).\
example:
```jsx
<CTable conditionalRowClass={irow => {
if (irow === 0) return specialrowclass
}} />
```
### \(`data`\) 
data to be displayed shapes as Array of Objects. A dataset (row) is represented by one object's propertys.\
Data is filled by sequence! of object propertys (not their property key!). Empty cells must be provided by property containing empty string.\
But! Data's property keys must be same for 1 column to provide sorting functionality.\
example:
```ts
data=[{col1: 1, col2: 2, col3: 3}, {col1: 4, col2: 5, col3: 6},]
```
### \(`doColorHeadRow`\) 
determines whether header class (see [classes](#classes)) shall be applied to table header\
[useStickyHeader](#useStickyHeader) must be false.
### \(`doColorRows`\) 
determines whether or not to color the table rows
### \(`header`\) 
header row data of shape Array of Objects where one object represents one column's features/settings.\ 
header columns are filled by sequence! of objects within enclosing array.
- id: relevant for sorting functionality. When clicking/touching a column header all data whose property keys correspond to id is sorted.
- numeric: relevant for aligning columns. Columns with numeric=true are aligned on right side. Otherwise column is aligned on left side.
- disablePadding: allows you to disable padding for certain columns
- label: column header label to be applied.
### \(`preview`\) 
limits the amount of data (rows) displayed in the table (data is not modified/deleted, header row is not counted)
### \(`size`\) 
table size can be modified by setting MUI's table size property. See https://material-ui.com/api/table/ for MUI propertys.
@nospec MUI component propertys
### \(`TableBodyProps`\) 
table body is represented by MUI's TableBody component. TableBodyProps allows you to provide an object with MUI's TableBody Props which are directly forwareded by Rest/Spread? operator. See https://material-ui.com/api/table-body/ for MUI propertys.
@nospec MUI component propertys
### \(`TableCheckboxProps`\) 
row checkboxes are represented by MUI's Checkbox components.\ TableCheckboxProps allows you to provide an object for all Checkboxes of the table with MUI's Checkbox Props which are directly forwareded by Rest/Spread? operator. See https://material-ui.com/api/checkbox/ for MUI propertys.
@nospec MUI component propertys
### \(`TableContainerProps`\) 
table is wrapped in MUI's TableContainer component. TableContainerProps allows you to provide an object with MUI's TableContainer Props which are directly forwareded by Rest/Spread? operator. See https://material-ui.com/api/table-container/ for MUI propertys.
@nospec MUI component propertys
### \(`TableHeadProps`\) 
table head is represented by MUI's TableHead component.\ TableHeadProps allows you to provide an object with MUI's TableHead Props which are directly forwareded by Rest/Spread? operator. See https://material-ui.com/api/table-head/ for MUI propertys.
@nospec MUI component propertys
### \(`TablePaginationProps`\) 
table pagination is represented by MUI's TablePagination component. TablePaginationProps allows you to provide an object with MUI's TablePagination Props which are directly forwareded by Rest/Spread? operator. See https://material-ui.com/api/table-pagination/ for MUI propertys.
@nospec MUI component propertys
### \(`TableProps`\) 
object for external MUI Table Props\ 
table is represented by MUI's Table component. TableProps allows you to provide an object with MUI's Table Props which are directly forwareded by rest operator. See https://material-ui.com/api/table/ for MUI propertys.\
e.g.
```jsx
<CTable TableProps={{size: "small", padding: "none"}}/>
```
### \(`title`\) 
table title to display if [useToolbar](#useToolbar) is true
### \(`ToolbarProps`\) 
table toolbar is represented by MUI's Toolbar component.\ ToolbarProps allows you to provide an object with MUI's Toolbar Props which are directly forwareded by Rest/Spread? operator. See https://material-ui.com/api/toolbar/ for MUI propertys.
@nospec MUI component propertys
### \(`ToolbarTypoProps`\) 
table toolbar's title is represented by a MUI Typography component.\ ToolbarTypoProps allows you to provide an object with MUI's Typography Props which are directly forwareded by Rest/Spread? operator. See https://material-ui.com/api/typography/ for MUI propertys.
@nospec MUI component propertys
### \(`useHeader`\) 
determines whether or not to use the header row if property header is provided
### \(`usePagination`\) 
determines whether or not to use pagination
### \(`useSelectableAllRows`\) 
determines whether all rows can be selected by clicking/touching the header's checkbox.\\ 
[useSelectableRows](#useSelectableRows) must be true. Checkboxes can be customized by using [TableCheckboxProps](#TableCheckboxProps).
### \(`useSelectableRows`\) 
determines whether rows can be selected. If true an additional checkbox column is added on left side of table.\\ 
Checkboxes can be customized by using [TableCheckboxProps](#TableCheckboxProps).
### \(`useStickyHeader`\) 
determines whether or not header is sticky, if true doColorRows is not effective, header can only be customized with stickyHeader class or by MUI theme's default background (see [classes](#classes))
### \(`useToolbar`\) 
determines whether or not to use the toolbar, currently just containing title

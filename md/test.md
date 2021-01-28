# `<CTableDocu />`
react wrapper component for Material UI's `<Table/>` component facilitating/specifying usage and extending functionality.
| Name        | Type           | Default  |
| ------------- |:-------------:| -----:|
| classes | { rows?: string; roweven?: string; rowodd?: string; head?: string; selected?: string; "@media(pointer: fine)"?: string; stickyHeader?: string; } | {} | 
| conditionalCellClass | (icol: number, irow: number, colkey: string, colcontent: string) => string | ? | 
| conditionalRowClass | (irow: number) => string | ? | 
| data | { [key: string]: string; }[] | [] | 
| doColorHeadRow | boolean | true | 
| doColorRows | boolean | true | 
| header | { id: string; numeric?: boolean; disablePadding?: boolean; label?: string; align?: Alignment; }[] | [] | 
| preview | number | 0 | 
| size | Size | small | 
| TableBodyProps | CommonProps<TableBodyTypeMap<{}, "tbody">> & Pick<Pick<DetailedHTMLProps<HTMLAttributes<HTMLTableSectionElement>, HTMLTableSectionElement>, "title" | "slot" | "style" | ... 251 more ... | "onTransitionEndCapture"> & { ...; }, "title" | ... 252 more ... | "onTransitionEndCapture"> | {} | 
| TableCheckboxProps | CheckboxProps | {} | 
| TableContainerProps | CommonProps<TableContainerTypeMap<{}, "div">> & Pick<Pick<DetailedHTMLProps<HTMLAttributes<HTMLDivElement>, HTMLDivElement>, "title" | "slot" | "style" | "className" | ... 250 more ... | "onTransitionEndCapture"> & { ...; }, "title" | ... 252 more ... | "onTransitionEndCapture"> | {} | 
| TableHeadProps | CommonProps<TableHeadTypeMap<{}, "thead">> & Pick<Pick<DetailedHTMLProps<HTMLAttributes<HTMLTableSectionElement>, HTMLTableSectionElement>, "title" | "slot" | "style" | ... 251 more ... | "onTransitionEndCapture"> & { ...; }, "title" | ... 252 more ... | "onTransitionEndCapture"> | {} | 
| TablePaginationProps | (Pick<TableCellProps, "title" | "ref" | "abbr" | "slot" | "style" | "className" | "innerRef" | "defaultChecked" | "defaultValue" | "suppressContentEditableWarning" | "suppressHydrationWarning" | ... 257 more ... | "variant"> & { ...; } & CommonProps<...> & Pick<...>) | (Pick<...> & ... 2 more ... & Pick<...>) | ? | 
| TableProps | { padding?: Padding; size?: Size; stickyHeader?: boolean; } & CommonProps<TableTypeMap<{}, "table">> & Pick<Pick<DetailedHTMLProps<TableHTMLAttributes<HTMLTableElement>, HTMLTableElement>, "title" | ... 257 more ... | "width"> & { ...; }, "title" | ... 256 more ... | "width"> | {} | 
| title | string | Title 1235813 | 
| ToolbarProps | { disableGutters?: boolean; variant?: "regular" | "dense"; } & CommonProps<ToolbarTypeMap<{}, "div">> & Pick<Pick<DetailedHTMLProps<HTMLAttributes<HTMLDivElement>, HTMLDivElement>, "title" | ... 253 more ... | "onTransitionEndCapture"> & { ...; }, "title" | ... 252 more ... | "onTransitionEndCapture"> | {} | 
| ToolbarTypoProps | { align?: Alignment; children?: ReactNode; color?: "inherit" | "primary" | "secondary" | "initial" | "textPrimary" | "textSecondary" | "error"; display?: "inline" | "initial" | "block"; ... 4 more ...; variantMapping?: Partial<...>; } & CommonProps<...> & Pick<...> | {} | 
| useHeader | boolean | true | 
| usePagination | boolean | true | 
| useSelectableAllRows | boolean | true | 
| useSelectableRows | boolean | true | 
| useStickyHeader | boolean | true | 
| useToolbar | boolean | true | 

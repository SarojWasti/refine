---
id: create-button
title: Create
---

import createButton from '@site/static/img/guides-and-concepts/components/buttons/create/create.png';

`<CreateButton>` uses Ant Design's [`<Button>`](https://ant.design/components/button/) component. It uses the `create` method from [`useNavigation`](/api-reference/core/hooks/navigation/useNavigation.md) under the hood. It can be useful to redirect the app to the create page route of resource.

## Usage

```tsx
import {
    // highlight-next-line
    CreateButton,
    List,
    Table,
    useTable,
} from "@pankod/refine-antd";

export const PostList: React.FC = () => {
    const { tableProps } = useTable<IPost>();

    return (
        // highlight-next-line
        <List pageHeaderProps={{ extra: <CreateButton /> }}>
            <Table {...tableProps} rowKey="id">
                <Table.Column dataIndex="id" title="ID" />
                <Table.Column dataIndex="title" title="Title" />
            </Table>
        </List>
    );
};

interface IPost {
    id: number;
    title: string;
}
```

Will look like this:

<div class="img-container">
    <div class="window">
        <div class="control red"></div>
        <div class="control orange"></div>
        <div class="control green"></div>
    </div>
    <img src={createButton} alt="Default create button" />
</div>

## Properties

### `resourceNameOrRouteName`

It is used to redirect the app to the `/create` endpoint of the given resource name. By default, the app redirects to a URL with `/create` defined by the name property of resource object.

```tsx 
import { CreateButton } from "@pankod/refine-antd";

export const MyCreateComponent = () => {
    return <CreateButton resourceNameOrRouteName="posts" />;
};
```

Clicking the button will trigger the `create` method of [`useNavigation`](/api-reference/core/hooks/navigation/useNavigation.md) and then redirect to `/posts/create`.

### `hideText`

It is used to show and not show the text of the button. When `true`, only the button icon is visible.

```tsx 
import { CreateButton } from "@pankod/refine-antd";

export const MyCreateComponent = () => {
    return <CreateButton hideText />;
};
```

### `ignoreAccessControlProvider`

It is used to skip access control for the button so that it doesn't check for access control. This is relevant only when an [`accessControlProvider`](/api-reference/core/providers/accessControl-provider.md) is provided to [`<Refine/>`](/api-reference/core/components/refine-config.md)

```tsx 
import { CreateButton } from "@pankod/refine-antd";

export const MyListComponent = () => {
    return <CreateButton ignoreAccessControlProvider />;
};
```

## API Reference

### Properties

<PropsTable module="@pankod/refine-antd/CreateButton" />

:::tip External Props
It also accepts all props of Ant Design [Button](https://ant.design/components/button/#API).
:::

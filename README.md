# redux-boilerplate-snippets
[ speed coding :turtle: ]

Redux boilerplate snippets (aka [live templates](https://www.jetbrains.com/help/idea/2016.1/live-templates.html)) for JetBrains series editors

## Installation

1. Download [redux.xml](redux.xml) file and copy it to your JetBrains editor's templates folder:

    - Windows: `<your home directory>\.<product name><version number>\config\templates`
    - Linux: `~\.<product name><version number>\config\templates`
    - OS X: `~/Library/Preferences/<product name><version number>/templates`

     e.g. `~/Library/Preferences/WebStorm10/templates` on OS X for WebStorm 10

2. Restart your IDE.

3. To see all templates, go to `Preferences` -> `Live Templates` and expand the `redux` Template Group.


## Snippets

<!--DOC_START-->
### `action`

```js
export const $ACTION_NAME$ = "@@$DOMAIN$/$ACTION_NAME$";

export const $CAMEL_CASED_ACTION_NAME$ = ($PARAM$) => {
  return {
    type: $ACTION_NAME$,
    $PARAM$,
  };
};

case $ACTION_NAME$: {
    $CODE$
    return {
        ...state,
        $UPDATED_STATE$,
    }
}

```

### `fetch-action`

```js
export const FETCH_$DATA$ = {
    REQUEST: "@@$DOMAIN$/FETCH_$DATA$_REQUEST",
    SUCCESS: "@@$DOMAIN$/FETCH_$DATA$_SUCCESS",
    ERROR: "@@$DOMAIN$/FETCH_$DATA$_ERROR",
};

export const fetch$PASCAL_CASED_DATA$Request = ($PARAMS$) => {
  return {
    type: FETCH_$DATA$.REQUEST,
    $PARAMS$,
  };
};

export const fetch$PASCAL_CASED_DATA$Success = ($CAMEL_CASED_DATA$) => {
  return {
    type: FETCH_$DATA$.SUCCESS,
    $CAMEL_CASED_DATA$,
  };
};

export const fetch$PASCAL_CASED_DATA$Error = (error) => {
  return {
    type: FETCH_$DATA$.ERROR,
    error,
  };
};

case FETCH_$DATA$.SUCCESS: {
    return {
        ...state,
        $CAMEL_CASED_DATA$: action.$CAMEL_CASED_DATA$,
    }
}

function* fetch$PASCAL_CASED_DATA$({ $PARAMS$ }) {
  try {
    const $CAMEL_CASED_DATA$ = yield call(services.fetch$PASCAL_CASED_DATA$, $PARAMS$);
    yield put(fetch$PASCAL_CASED_DATA$Success($CAMEL_CASED_DATA$));
  } catch (e) {
    yield put(fetch$PASCAL_CASED_DATA$Error(e));
  }
}

export function fetch$PASCAL_CASED_DATA$Request($PARAMS$) {
  return request.get(SERVER_END_POINT.FETCH_$DATA$, {
    params: {
       $PARAMS$,
    }
  }
}
```

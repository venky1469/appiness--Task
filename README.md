// actions
function login (form) {
    return dispatch => doLogin(form)
      .then(() => dispatch({ type: 'LOGGED_IN' }))
      .catch(() => dispatch({ type: 'LOGIN_FAILED' }))
  }
  
  // reducer
  const initialState = {
    // some fields...,
    loggedIn: false,
    shouldRedirect: false,
    errorMessage: null
  }
  function application (state = initialState, action) {
    switch (action.type) {
      case 'LOGGED_IN':
        return Object.assign({}, state, { loggedIn: true, shouldRedirect: true })
      case 'LOGIN_FAILED':
        return Object.assign({}, state, { loggedIn: false, shouldRedirect: false, errorMessage: action.error.message })
    }
    return state
  }
  
 connect(state => {'stateapplication'})
  class Login extends 'React.Component'{
    componentWillUpdate () {
      const { store, router } = this.context
      const { application } = this.props
      if (application.shouldRedirect) {
        store.dispatch(applicationActions.resetSubmitState())
        router.transition(...)  
      }
    }
    onSubmit () {
      const actions = bindActionCreators(applicationActions, dispatch)
      actions.login({...})
    }
  
    render () {
      const { errorMessage } = this.props
      return (
        <div>
          {errorMessage ? <p>{errorMessage}</p> : null}
          <Form {...props} onSubmit={onSubmit}>
            {...}
          </Form>
        </div>
      )
    }
  }

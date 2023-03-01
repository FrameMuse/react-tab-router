# React Tab Router

## Motivation

Navigate between routes with in memory storage.
There is already `react-router` with `MemoryRouter` but it can't take deeply nested routes, so there can't be `BrowserRouter` and `MemoryRouter` both at the same time.
That's why I created this solution, it works similar to `MemoryRouter` but with no conflicts using `BrowserRouter`.
Probably, this will be deprected when `react-router` allows using nested routers.

## Usage

A real-world example, taken from one of my projects.

### Code

```tsx
// Just names of tabs for convenience. As this is supposed to be used in local context and there is no need to show what exactly pathname is, there may be added an enum to make it easier to find the correct tab. 
enum Tabs {
  Metamask, TrustWallet
}

function InstructionView() {
  return (
    <div className="instruction">
      <ViewTitle>Instruction</ViewTitle>
      <ViewContainer>
        <div className="instruction__guides">
          <TabRouter defaultPath={Tabs.Metamask}>
            <TabLinks>
              <TabLink to={Tabs.Metamask}>MetaMask</TabLink>
              <TabLink to={Tabs.TrustWallet}>TrustWallet</TabLink>
            </TabLinks>
            <br />

            <TabRoute path={Tabs.Metamask}>
              <MetaMaskInstruction />
            </TabRoute>
            <TabRoute path={Tabs.TrustWallet}>
              <TrustWalletInstruction />
            </TabRoute>
          </TabRouter>
        </div>
      </ViewContainer>
    </div>
  )
}
```

### Result

![image](https://user-images.githubusercontent.com/53980482/222292762-3eb525a2-011c-4e75-9170-6349500eee1d.png)
![image](https://user-images.githubusercontent.com/53980482/222292970-1c410e64-7c1d-477a-9285-fc2fe82d1a57.png)

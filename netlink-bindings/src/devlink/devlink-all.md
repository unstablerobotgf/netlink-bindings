
# Operation "get"

## Do (request)

```rust
PushOpGetDoRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  ;
```

```rust
let attrs = OpGetDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_reload_failed(); // u8
{ // Nested DevStats
  let attrs = attrs.get_dev_stats();
  { // Nested ReloadStats
    let attrs = attrs.get_reload_stats();
    { // Nested ReloadActionInfo

      // Attribute may repeat multiple times (treat it as array)
      for entry in attrs.get_reload_action_info() {

        // Associated type: "ReloadAction" (enum)
        entry.get_reload_action(); // u8
        { // Nested ReloadActionStats

          // Attribute may repeat multiple times (treat it as array)
          for entry in entry.get_reload_action_stats() {
            { // Nested ReloadStatsEntry

              // Attribute may repeat multiple times (treat it as array)
              for entry in entry.get_reload_stats_entry() {
                entry.get_reload_stats_limit(); // u8
                entry.get_reload_stats_value(); // u32
              }
            }
          }
        }
      }
    }
  }
  { // Nested RemoteReloadStats
    let attrs = attrs.get_remote_reload_stats();
    { // Nested ReloadActionInfo

      // Attribute may repeat multiple times (treat it as array)
      for entry in attrs.get_reload_action_info() {

        // Associated type: "ReloadAction" (enum)
        entry.get_reload_action(); // u8
        { // Nested ReloadActionStats

          // Attribute may repeat multiple times (treat it as array)
          for entry in entry.get_reload_action_stats() {
            { // Nested ReloadStatsEntry

              // Attribute may repeat multiple times (treat it as array)
              for entry in entry.get_reload_stats_entry() {
                entry.get_reload_stats_limit(); // u8
                entry.get_reload_stats_value(); // u32
              }
            }
          }
        }
      }
    }
  }
}
```

### Do (reply)

```rust
PushOpGetDoReply::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_reload_failed(val) // u8
  .nested_dev_stats()
    .nested_reload_stats()

      // Attribute may repeat multiple times (treat it as array)
      .nested_reload_action_info()

        // Associated type: "ReloadAction" (enum)
        .push_reload_action(val) // u8

        // Attribute may repeat multiple times (treat it as array)
        .nested_reload_action_stats()

          // Attribute may repeat multiple times (treat it as array)
          .nested_reload_stats_entry()
            .push_reload_stats_limit(val) // u8
            .push_reload_stats_value(val) // u32
          .end_nested()
        .end_nested()
      .end_nested()
    .end_nested()
    .nested_remote_reload_stats()

      // Attribute may repeat multiple times (treat it as array)
      .nested_reload_action_info()

        // Associated type: "ReloadAction" (enum)
        .push_reload_action(val) // u8

        // Attribute may repeat multiple times (treat it as array)
        .nested_reload_action_stats()

          // Attribute may repeat multiple times (treat it as array)
          .nested_reload_stats_entry()
            .push_reload_stats_limit(val) // u8
            .push_reload_stats_value(val) // u32
          .end_nested()
        .end_nested()
      .end_nested()
    .end_nested()
  .end_nested()
  ;
```

```rust
let attrs = OpGetDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_reload_failed(); // u8
{ // Nested DevStats
  let attrs = attrs.get_dev_stats();
  { // Nested ReloadStats
    let attrs = attrs.get_reload_stats();
    { // Nested ReloadActionInfo

      // Attribute may repeat multiple times (treat it as array)
      for entry in attrs.get_reload_action_info() {

        // Associated type: "ReloadAction" (enum)
        entry.get_reload_action(); // u8
        { // Nested ReloadActionStats

          // Attribute may repeat multiple times (treat it as array)
          for entry in entry.get_reload_action_stats() {
            { // Nested ReloadStatsEntry

              // Attribute may repeat multiple times (treat it as array)
              for entry in entry.get_reload_stats_entry() {
                entry.get_reload_stats_limit(); // u8
                entry.get_reload_stats_value(); // u32
              }
            }
          }
        }
      }
    }
  }
  { // Nested RemoteReloadStats
    let attrs = attrs.get_remote_reload_stats();
    { // Nested ReloadActionInfo

      // Attribute may repeat multiple times (treat it as array)
      for entry in attrs.get_reload_action_info() {

        // Associated type: "ReloadAction" (enum)
        entry.get_reload_action(); // u8
        { // Nested ReloadActionStats

          // Attribute may repeat multiple times (treat it as array)
          for entry in entry.get_reload_action_stats() {
            { // Nested ReloadStatsEntry

              // Attribute may repeat multiple times (treat it as array)
              for entry in entry.get_reload_stats_entry() {
                entry.get_reload_stats_limit(); // u8
                entry.get_reload_stats_value(); // u32
              }
            }
          }
        }
      }
    }
  }
}
```

## Low-level decoding

### Do (request)

```rust
let iter = OpGetDoRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
  }
}
```

### Do (reply)

```rust
let iter = OpGetDoReply::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    ReloadFailed(val) => {}, // u8
    DevStats(iter) => {
      for attr in iter {
        match attr {
          ReloadStats(iter) => {
            for attr in iter {
              match attr {

                // Attribute may repeat multiple times (treat it as array)
                ReloadActionInfo(iter) => {
                  for attr in iter {
                    match attr {

                      // Associated type: "ReloadAction" (enum)
                      ReloadAction(val) => {}, // u8

                      // Attribute may repeat multiple times (treat it as array)
                      ReloadActionStats(iter) => {
                        for attr in iter {
                          match attr {

                            // Attribute may repeat multiple times (treat it as array)
                            ReloadStatsEntry(iter) => {
                              for attr in iter {
                                match attr {
                                  ReloadStatsLimit(val) => {}, // u8
                                  ReloadStatsValue(val) => {}, // u32
                                }
                              }
                            },
                          }
                        }
                      },
                    }
                  }
                },
              }
            }
          },
          RemoteReloadStats(iter) => {
            for attr in iter {
              match attr {

                // Attribute may repeat multiple times (treat it as array)
                ReloadActionInfo(iter) => {
                  for attr in iter {
                    match attr {

                      // Associated type: "ReloadAction" (enum)
                      ReloadAction(val) => {}, // u8

                      // Attribute may repeat multiple times (treat it as array)
                      ReloadActionStats(iter) => {
                        for attr in iter {
                          match attr {

                            // Attribute may repeat multiple times (treat it as array)
                            ReloadStatsEntry(iter) => {
                              for attr in iter {
                                match attr {
                                  ReloadStatsLimit(val) => {}, // u8
                                  ReloadStatsValue(val) => {}, // u32
                                }
                              }
                            },
                          }
                        }
                      },
                    }
                  }
                },
              }
            }
          },
        }
      }
    },
  }
}
```

## Dump (request)

```rust
PushOpGetDumpRequest::new(&mut vec)
  ;
```

```rust
let attrs = OpGetDumpReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_reload_failed(); // u8
{ // Nested DevStats
  let attrs = attrs.get_dev_stats();
  { // Nested ReloadStats
    let attrs = attrs.get_reload_stats();
    { // Nested ReloadActionInfo

      // Attribute may repeat multiple times (treat it as array)
      for entry in attrs.get_reload_action_info() {

        // Associated type: "ReloadAction" (enum)
        entry.get_reload_action(); // u8
        { // Nested ReloadActionStats

          // Attribute may repeat multiple times (treat it as array)
          for entry in entry.get_reload_action_stats() {
            { // Nested ReloadStatsEntry

              // Attribute may repeat multiple times (treat it as array)
              for entry in entry.get_reload_stats_entry() {
                entry.get_reload_stats_limit(); // u8
                entry.get_reload_stats_value(); // u32
              }
            }
          }
        }
      }
    }
  }
  { // Nested RemoteReloadStats
    let attrs = attrs.get_remote_reload_stats();
    { // Nested ReloadActionInfo

      // Attribute may repeat multiple times (treat it as array)
      for entry in attrs.get_reload_action_info() {

        // Associated type: "ReloadAction" (enum)
        entry.get_reload_action(); // u8
        { // Nested ReloadActionStats

          // Attribute may repeat multiple times (treat it as array)
          for entry in entry.get_reload_action_stats() {
            { // Nested ReloadStatsEntry

              // Attribute may repeat multiple times (treat it as array)
              for entry in entry.get_reload_stats_entry() {
                entry.get_reload_stats_limit(); // u8
                entry.get_reload_stats_value(); // u32
              }
            }
          }
        }
      }
    }
  }
}
```

### Dump (reply)

```rust
PushOpGetDumpReply::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_reload_failed(val) // u8
  .nested_dev_stats()
    .nested_reload_stats()

      // Attribute may repeat multiple times (treat it as array)
      .nested_reload_action_info()

        // Associated type: "ReloadAction" (enum)
        .push_reload_action(val) // u8

        // Attribute may repeat multiple times (treat it as array)
        .nested_reload_action_stats()

          // Attribute may repeat multiple times (treat it as array)
          .nested_reload_stats_entry()
            .push_reload_stats_limit(val) // u8
            .push_reload_stats_value(val) // u32
          .end_nested()
        .end_nested()
      .end_nested()
    .end_nested()
    .nested_remote_reload_stats()

      // Attribute may repeat multiple times (treat it as array)
      .nested_reload_action_info()

        // Associated type: "ReloadAction" (enum)
        .push_reload_action(val) // u8

        // Attribute may repeat multiple times (treat it as array)
        .nested_reload_action_stats()

          // Attribute may repeat multiple times (treat it as array)
          .nested_reload_stats_entry()
            .push_reload_stats_limit(val) // u8
            .push_reload_stats_value(val) // u32
          .end_nested()
        .end_nested()
      .end_nested()
    .end_nested()
  .end_nested()
  ;
```

```rust
let attrs = OpGetDumpReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_reload_failed(); // u8
{ // Nested DevStats
  let attrs = attrs.get_dev_stats();
  { // Nested ReloadStats
    let attrs = attrs.get_reload_stats();
    { // Nested ReloadActionInfo

      // Attribute may repeat multiple times (treat it as array)
      for entry in attrs.get_reload_action_info() {

        // Associated type: "ReloadAction" (enum)
        entry.get_reload_action(); // u8
        { // Nested ReloadActionStats

          // Attribute may repeat multiple times (treat it as array)
          for entry in entry.get_reload_action_stats() {
            { // Nested ReloadStatsEntry

              // Attribute may repeat multiple times (treat it as array)
              for entry in entry.get_reload_stats_entry() {
                entry.get_reload_stats_limit(); // u8
                entry.get_reload_stats_value(); // u32
              }
            }
          }
        }
      }
    }
  }
  { // Nested RemoteReloadStats
    let attrs = attrs.get_remote_reload_stats();
    { // Nested ReloadActionInfo

      // Attribute may repeat multiple times (treat it as array)
      for entry in attrs.get_reload_action_info() {

        // Associated type: "ReloadAction" (enum)
        entry.get_reload_action(); // u8
        { // Nested ReloadActionStats

          // Attribute may repeat multiple times (treat it as array)
          for entry in entry.get_reload_action_stats() {
            { // Nested ReloadStatsEntry

              // Attribute may repeat multiple times (treat it as array)
              for entry in entry.get_reload_stats_entry() {
                entry.get_reload_stats_limit(); // u8
                entry.get_reload_stats_value(); // u32
              }
            }
          }
        }
      }
    }
  }
}
```

## Low-level decoding

### Dump (request)

```rust
let iter = OpGetDumpRequest::new(buf);
// No attributes
```

### Dump (reply)

```rust
let iter = OpGetDumpReply::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    ReloadFailed(val) => {}, // u8
    DevStats(iter) => {
      for attr in iter {
        match attr {
          ReloadStats(iter) => {
            for attr in iter {
              match attr {

                // Attribute may repeat multiple times (treat it as array)
                ReloadActionInfo(iter) => {
                  for attr in iter {
                    match attr {

                      // Associated type: "ReloadAction" (enum)
                      ReloadAction(val) => {}, // u8

                      // Attribute may repeat multiple times (treat it as array)
                      ReloadActionStats(iter) => {
                        for attr in iter {
                          match attr {

                            // Attribute may repeat multiple times (treat it as array)
                            ReloadStatsEntry(iter) => {
                              for attr in iter {
                                match attr {
                                  ReloadStatsLimit(val) => {}, // u8
                                  ReloadStatsValue(val) => {}, // u32
                                }
                              }
                            },
                          }
                        }
                      },
                    }
                  }
                },
              }
            }
          },
          RemoteReloadStats(iter) => {
            for attr in iter {
              match attr {

                // Attribute may repeat multiple times (treat it as array)
                ReloadActionInfo(iter) => {
                  for attr in iter {
                    match attr {

                      // Associated type: "ReloadAction" (enum)
                      ReloadAction(val) => {}, // u8

                      // Attribute may repeat multiple times (treat it as array)
                      ReloadActionStats(iter) => {
                        for attr in iter {
                          match attr {

                            // Attribute may repeat multiple times (treat it as array)
                            ReloadStatsEntry(iter) => {
                              for attr in iter {
                                match attr {
                                  ReloadStatsLimit(val) => {}, // u8
                                  ReloadStatsValue(val) => {}, // u32
                                }
                              }
                            },
                          }
                        }
                      },
                    }
                  }
                },
              }
            }
          },
        }
      }
    },
  }
}
```

# Operation "port-get"

## Do (request)

```rust
PushOpPortGetDoRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_port_index(val) // u32
  ;
```

```rust
let attrs = OpPortGetDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_port_index(); // u32
```

### Do (reply)

```rust
PushOpPortGetDoReply::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_port_index(val) // u32
  ;
```

```rust
let attrs = OpPortGetDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_port_index(); // u32
```

## Low-level decoding

### Do (request)

```rust
let iter = OpPortGetDoRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    PortIndex(val) => {}, // u32
  }
}
```

### Do (reply)

```rust
let iter = OpPortGetDoReply::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    PortIndex(val) => {}, // u32
  }
}
```

## Dump (request)

```rust
PushOpPortGetDumpRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  ;
```

```rust
let attrs = OpPortGetDumpReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_port_index(); // u32
```

### Dump (reply)

```rust
PushOpPortGetDumpReply::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_port_index(val) // u32
  ;
```

```rust
let attrs = OpPortGetDumpReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_port_index(); // u32
```

## Low-level decoding

### Dump (request)

```rust
let iter = OpPortGetDumpRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
  }
}
```

### Dump (reply)

```rust
let iter = OpPortGetDumpReply::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    PortIndex(val) => {}, // u32
  }
}
```

# Operation "port-set"

## Do (request)

```rust
PushOpPortSetDoRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_port_index(val) // u32

  // Associated type: "PortType" (enum)
  .push_port_type(val) // u16
  .nested_port_function()
    .push_hw_addr(val) // &[u8]

    // Associated type: "PortFnState" (enum)
    .push_state(val) // u8

    // Associated type: "PortFnOpstate" (enum)
    .push_opstate(val) // u8

    // Associated type: "PortFnAttrCap" (1 bit per enumeration)
    .push_caps(val) // PushBuiltinBitfield32
  .end_nested()
  ;
```

```rust
let attrs = OpPortSetDoReply::new(buf);

// No attributes
```

### Do (reply)

```rust
PushOpPortSetDoReply::new(&mut vec)
  ;
```

```rust
let attrs = OpPortSetDoReply::new(buf);

// No attributes
```

## Low-level decoding

### Do (request)

```rust
let iter = OpPortSetDoRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    PortIndex(val) => {}, // u32

    // Associated type: "PortType" (enum)
    PortType(val) => {}, // u16
    PortFunction(iter) => {
      for attr in iter {
        match attr {
          HwAddr(val) => {}, // &[u8]

          // Associated type: "PortFnState" (enum)
          State(val) => {}, // u8

          // Associated type: "PortFnOpstate" (enum)
          Opstate(val) => {}, // u8

          // Associated type: "PortFnAttrCap" (1 bit per enumeration)
          Caps(val) => {}, // PushBuiltinBitfield32
        }
      }
    },
  }
}
```

### Do (reply)

```rust
let iter = OpPortSetDoReply::new(buf);
// No attributes
```

# Operation "port-new"

## Do (request)

```rust
PushOpPortNewDoRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_port_index(val) // u32

  // Associated type: "PortFlavour" (enum)
  .push_port_flavour(val) // u16
  .push_port_pci_pf_number(val) // u16
  .push_port_pci_sf_number(val) // u32
  .push_port_controller_number(val) // u32
  ;
```

```rust
let attrs = OpPortNewDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_port_index(); // u32
```

### Do (reply)

```rust
PushOpPortNewDoReply::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_port_index(val) // u32
  ;
```

```rust
let attrs = OpPortNewDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_port_index(); // u32
```

## Low-level decoding

### Do (request)

```rust
let iter = OpPortNewDoRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    PortIndex(val) => {}, // u32

    // Associated type: "PortFlavour" (enum)
    PortFlavour(val) => {}, // u16
    PortPciPfNumber(val) => {}, // u16
    PortPciSfNumber(val) => {}, // u32
    PortControllerNumber(val) => {}, // u32
  }
}
```

### Do (reply)

```rust
let iter = OpPortNewDoReply::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    PortIndex(val) => {}, // u32
  }
}
```

# Operation "port-del"

## Do (request)

```rust
PushOpPortDelDoRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_port_index(val) // u32
  ;
```

```rust
let attrs = OpPortDelDoReply::new(buf);

// No attributes
```

### Do (reply)

```rust
PushOpPortDelDoReply::new(&mut vec)
  ;
```

```rust
let attrs = OpPortDelDoReply::new(buf);

// No attributes
```

## Low-level decoding

### Do (request)

```rust
let iter = OpPortDelDoRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    PortIndex(val) => {}, // u32
  }
}
```

### Do (reply)

```rust
let iter = OpPortDelDoReply::new(buf);
// No attributes
```

# Operation "port-split"

## Do (request)

```rust
PushOpPortSplitDoRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_port_index(val) // u32
  .push_port_split_count(val) // u32
  ;
```

```rust
let attrs = OpPortSplitDoReply::new(buf);

// No attributes
```

### Do (reply)

```rust
PushOpPortSplitDoReply::new(&mut vec)
  ;
```

```rust
let attrs = OpPortSplitDoReply::new(buf);

// No attributes
```

## Low-level decoding

### Do (request)

```rust
let iter = OpPortSplitDoRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    PortIndex(val) => {}, // u32
    PortSplitCount(val) => {}, // u32
  }
}
```

### Do (reply)

```rust
let iter = OpPortSplitDoReply::new(buf);
// No attributes
```

# Operation "port-unsplit"

## Do (request)

```rust
PushOpPortUnsplitDoRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_port_index(val) // u32
  ;
```

```rust
let attrs = OpPortUnsplitDoReply::new(buf);

// No attributes
```

### Do (reply)

```rust
PushOpPortUnsplitDoReply::new(&mut vec)
  ;
```

```rust
let attrs = OpPortUnsplitDoReply::new(buf);

// No attributes
```

## Low-level decoding

### Do (request)

```rust
let iter = OpPortUnsplitDoRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    PortIndex(val) => {}, // u32
  }
}
```

### Do (reply)

```rust
let iter = OpPortUnsplitDoReply::new(buf);
// No attributes
```

# Operation "sb-get"

## Do (request)

```rust
PushOpSbGetDoRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_sb_index(val) // u32
  ;
```

```rust
let attrs = OpSbGetDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_sb_index(); // u32
```

### Do (reply)

```rust
PushOpSbGetDoReply::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_sb_index(val) // u32
  ;
```

```rust
let attrs = OpSbGetDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_sb_index(); // u32
```

## Low-level decoding

### Do (request)

```rust
let iter = OpSbGetDoRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    SbIndex(val) => {}, // u32
  }
}
```

### Do (reply)

```rust
let iter = OpSbGetDoReply::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    SbIndex(val) => {}, // u32
  }
}
```

## Dump (request)

```rust
PushOpSbGetDumpRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  ;
```

```rust
let attrs = OpSbGetDumpReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_sb_index(); // u32
```

### Dump (reply)

```rust
PushOpSbGetDumpReply::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_sb_index(val) // u32
  ;
```

```rust
let attrs = OpSbGetDumpReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_sb_index(); // u32
```

## Low-level decoding

### Dump (request)

```rust
let iter = OpSbGetDumpRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
  }
}
```

### Dump (reply)

```rust
let iter = OpSbGetDumpReply::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    SbIndex(val) => {}, // u32
  }
}
```

# Operation "sb-pool-get"

## Do (request)

```rust
PushOpSbPoolGetDoRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_sb_index(val) // u32
  .push_sb_pool_index(val) // u16
  ;
```

```rust
let attrs = OpSbPoolGetDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_sb_index(); // u32
attrs.get_sb_pool_index(); // u16
```

### Do (reply)

```rust
PushOpSbPoolGetDoReply::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_sb_index(val) // u32
  .push_sb_pool_index(val) // u16
  ;
```

```rust
let attrs = OpSbPoolGetDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_sb_index(); // u32
attrs.get_sb_pool_index(); // u16
```

## Low-level decoding

### Do (request)

```rust
let iter = OpSbPoolGetDoRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    SbIndex(val) => {}, // u32
    SbPoolIndex(val) => {}, // u16
  }
}
```

### Do (reply)

```rust
let iter = OpSbPoolGetDoReply::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    SbIndex(val) => {}, // u32
    SbPoolIndex(val) => {}, // u16
  }
}
```

## Dump (request)

```rust
PushOpSbPoolGetDumpRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  ;
```

```rust
let attrs = OpSbPoolGetDumpReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_sb_index(); // u32
attrs.get_sb_pool_index(); // u16
```

### Dump (reply)

```rust
PushOpSbPoolGetDumpReply::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_sb_index(val) // u32
  .push_sb_pool_index(val) // u16
  ;
```

```rust
let attrs = OpSbPoolGetDumpReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_sb_index(); // u32
attrs.get_sb_pool_index(); // u16
```

## Low-level decoding

### Dump (request)

```rust
let iter = OpSbPoolGetDumpRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
  }
}
```

### Dump (reply)

```rust
let iter = OpSbPoolGetDumpReply::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    SbIndex(val) => {}, // u32
    SbPoolIndex(val) => {}, // u16
  }
}
```

# Operation "sb-pool-set"

## Do (request)

```rust
PushOpSbPoolSetDoRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_sb_index(val) // u32
  .push_sb_pool_index(val) // u16

  // Associated type: "SbThresholdType" (enum)
  .push_sb_pool_threshold_type(val) // u8
  .push_sb_pool_size(val) // u32
  ;
```

```rust
let attrs = OpSbPoolSetDoReply::new(buf);

// No attributes
```

### Do (reply)

```rust
PushOpSbPoolSetDoReply::new(&mut vec)
  ;
```

```rust
let attrs = OpSbPoolSetDoReply::new(buf);

// No attributes
```

## Low-level decoding

### Do (request)

```rust
let iter = OpSbPoolSetDoRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    SbIndex(val) => {}, // u32
    SbPoolIndex(val) => {}, // u16

    // Associated type: "SbThresholdType" (enum)
    SbPoolThresholdType(val) => {}, // u8
    SbPoolSize(val) => {}, // u32
  }
}
```

### Do (reply)

```rust
let iter = OpSbPoolSetDoReply::new(buf);
// No attributes
```

# Operation "sb-port-pool-get"

## Do (request)

```rust
PushOpSbPortPoolGetDoRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_port_index(val) // u32
  .push_sb_index(val) // u32
  .push_sb_pool_index(val) // u16
  ;
```

```rust
let attrs = OpSbPortPoolGetDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_port_index(); // u32
attrs.get_sb_index(); // u32
attrs.get_sb_pool_index(); // u16
```

### Do (reply)

```rust
PushOpSbPortPoolGetDoReply::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_port_index(val) // u32
  .push_sb_index(val) // u32
  .push_sb_pool_index(val) // u16
  ;
```

```rust
let attrs = OpSbPortPoolGetDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_port_index(); // u32
attrs.get_sb_index(); // u32
attrs.get_sb_pool_index(); // u16
```

## Low-level decoding

### Do (request)

```rust
let iter = OpSbPortPoolGetDoRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    PortIndex(val) => {}, // u32
    SbIndex(val) => {}, // u32
    SbPoolIndex(val) => {}, // u16
  }
}
```

### Do (reply)

```rust
let iter = OpSbPortPoolGetDoReply::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    PortIndex(val) => {}, // u32
    SbIndex(val) => {}, // u32
    SbPoolIndex(val) => {}, // u16
  }
}
```

## Dump (request)

```rust
PushOpSbPortPoolGetDumpRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  ;
```

```rust
let attrs = OpSbPortPoolGetDumpReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_port_index(); // u32
attrs.get_sb_index(); // u32
attrs.get_sb_pool_index(); // u16
```

### Dump (reply)

```rust
PushOpSbPortPoolGetDumpReply::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_port_index(val) // u32
  .push_sb_index(val) // u32
  .push_sb_pool_index(val) // u16
  ;
```

```rust
let attrs = OpSbPortPoolGetDumpReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_port_index(); // u32
attrs.get_sb_index(); // u32
attrs.get_sb_pool_index(); // u16
```

## Low-level decoding

### Dump (request)

```rust
let iter = OpSbPortPoolGetDumpRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
  }
}
```

### Dump (reply)

```rust
let iter = OpSbPortPoolGetDumpReply::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    PortIndex(val) => {}, // u32
    SbIndex(val) => {}, // u32
    SbPoolIndex(val) => {}, // u16
  }
}
```

# Operation "sb-port-pool-set"

## Do (request)

```rust
PushOpSbPortPoolSetDoRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_port_index(val) // u32
  .push_sb_index(val) // u32
  .push_sb_pool_index(val) // u16
  .push_sb_threshold(val) // u32
  ;
```

```rust
let attrs = OpSbPortPoolSetDoReply::new(buf);

// No attributes
```

### Do (reply)

```rust
PushOpSbPortPoolSetDoReply::new(&mut vec)
  ;
```

```rust
let attrs = OpSbPortPoolSetDoReply::new(buf);

// No attributes
```

## Low-level decoding

### Do (request)

```rust
let iter = OpSbPortPoolSetDoRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    PortIndex(val) => {}, // u32
    SbIndex(val) => {}, // u32
    SbPoolIndex(val) => {}, // u16
    SbThreshold(val) => {}, // u32
  }
}
```

### Do (reply)

```rust
let iter = OpSbPortPoolSetDoReply::new(buf);
// No attributes
```

# Operation "sb-tc-pool-bind-get"

## Do (request)

```rust
PushOpSbTcPoolBindGetDoRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_port_index(val) // u32
  .push_sb_index(val) // u32

  // Associated type: "SbPoolType" (enum)
  .push_sb_pool_type(val) // u8
  .push_sb_tc_index(val) // u16
  ;
```

```rust
let attrs = OpSbTcPoolBindGetDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_port_index(); // u32
attrs.get_sb_index(); // u32

// Associated type: "SbPoolType" (enum)
attrs.get_sb_pool_type(); // u8
attrs.get_sb_tc_index(); // u16
```

### Do (reply)

```rust
PushOpSbTcPoolBindGetDoReply::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_port_index(val) // u32
  .push_sb_index(val) // u32

  // Associated type: "SbPoolType" (enum)
  .push_sb_pool_type(val) // u8
  .push_sb_tc_index(val) // u16
  ;
```

```rust
let attrs = OpSbTcPoolBindGetDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_port_index(); // u32
attrs.get_sb_index(); // u32

// Associated type: "SbPoolType" (enum)
attrs.get_sb_pool_type(); // u8
attrs.get_sb_tc_index(); // u16
```

## Low-level decoding

### Do (request)

```rust
let iter = OpSbTcPoolBindGetDoRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    PortIndex(val) => {}, // u32
    SbIndex(val) => {}, // u32

    // Associated type: "SbPoolType" (enum)
    SbPoolType(val) => {}, // u8
    SbTcIndex(val) => {}, // u16
  }
}
```

### Do (reply)

```rust
let iter = OpSbTcPoolBindGetDoReply::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    PortIndex(val) => {}, // u32
    SbIndex(val) => {}, // u32

    // Associated type: "SbPoolType" (enum)
    SbPoolType(val) => {}, // u8
    SbTcIndex(val) => {}, // u16
  }
}
```

## Dump (request)

```rust
PushOpSbTcPoolBindGetDumpRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  ;
```

```rust
let attrs = OpSbTcPoolBindGetDumpReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_port_index(); // u32
attrs.get_sb_index(); // u32

// Associated type: "SbPoolType" (enum)
attrs.get_sb_pool_type(); // u8
attrs.get_sb_tc_index(); // u16
```

### Dump (reply)

```rust
PushOpSbTcPoolBindGetDumpReply::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_port_index(val) // u32
  .push_sb_index(val) // u32

  // Associated type: "SbPoolType" (enum)
  .push_sb_pool_type(val) // u8
  .push_sb_tc_index(val) // u16
  ;
```

```rust
let attrs = OpSbTcPoolBindGetDumpReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_port_index(); // u32
attrs.get_sb_index(); // u32

// Associated type: "SbPoolType" (enum)
attrs.get_sb_pool_type(); // u8
attrs.get_sb_tc_index(); // u16
```

## Low-level decoding

### Dump (request)

```rust
let iter = OpSbTcPoolBindGetDumpRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
  }
}
```

### Dump (reply)

```rust
let iter = OpSbTcPoolBindGetDumpReply::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    PortIndex(val) => {}, // u32
    SbIndex(val) => {}, // u32

    // Associated type: "SbPoolType" (enum)
    SbPoolType(val) => {}, // u8
    SbTcIndex(val) => {}, // u16
  }
}
```

# Operation "sb-tc-pool-bind-set"

## Do (request)

```rust
PushOpSbTcPoolBindSetDoRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_port_index(val) // u32
  .push_sb_index(val) // u32
  .push_sb_pool_index(val) // u16

  // Associated type: "SbPoolType" (enum)
  .push_sb_pool_type(val) // u8
  .push_sb_tc_index(val) // u16
  .push_sb_threshold(val) // u32
  ;
```

```rust
let attrs = OpSbTcPoolBindSetDoReply::new(buf);

// No attributes
```

### Do (reply)

```rust
PushOpSbTcPoolBindSetDoReply::new(&mut vec)
  ;
```

```rust
let attrs = OpSbTcPoolBindSetDoReply::new(buf);

// No attributes
```

## Low-level decoding

### Do (request)

```rust
let iter = OpSbTcPoolBindSetDoRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    PortIndex(val) => {}, // u32
    SbIndex(val) => {}, // u32
    SbPoolIndex(val) => {}, // u16

    // Associated type: "SbPoolType" (enum)
    SbPoolType(val) => {}, // u8
    SbTcIndex(val) => {}, // u16
    SbThreshold(val) => {}, // u32
  }
}
```

### Do (reply)

```rust
let iter = OpSbTcPoolBindSetDoReply::new(buf);
// No attributes
```

# Operation "sb-occ-snapshot"

## Do (request)

```rust
PushOpSbOccSnapshotDoRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_sb_index(val) // u32
  ;
```

```rust
let attrs = OpSbOccSnapshotDoReply::new(buf);

// No attributes
```

### Do (reply)

```rust
PushOpSbOccSnapshotDoReply::new(&mut vec)
  ;
```

```rust
let attrs = OpSbOccSnapshotDoReply::new(buf);

// No attributes
```

## Low-level decoding

### Do (request)

```rust
let iter = OpSbOccSnapshotDoRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    SbIndex(val) => {}, // u32
  }
}
```

### Do (reply)

```rust
let iter = OpSbOccSnapshotDoReply::new(buf);
// No attributes
```

# Operation "sb-occ-max-clear"

## Do (request)

```rust
PushOpSbOccMaxClearDoRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_sb_index(val) // u32
  ;
```

```rust
let attrs = OpSbOccMaxClearDoReply::new(buf);

// No attributes
```

### Do (reply)

```rust
PushOpSbOccMaxClearDoReply::new(&mut vec)
  ;
```

```rust
let attrs = OpSbOccMaxClearDoReply::new(buf);

// No attributes
```

## Low-level decoding

### Do (request)

```rust
let iter = OpSbOccMaxClearDoRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    SbIndex(val) => {}, // u32
  }
}
```

### Do (reply)

```rust
let iter = OpSbOccMaxClearDoReply::new(buf);
// No attributes
```

# Operation "eswitch-get"

## Do (request)

```rust
PushOpEswitchGetDoRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  ;
```

```rust
let attrs = OpEswitchGetDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr

// Associated type: "EswitchMode" (enum)
attrs.get_eswitch_mode(); // u16

// Associated type: "EswitchInlineMode" (enum)
attrs.get_eswitch_inline_mode(); // u8

// Associated type: "EswitchEncapMode" (enum)
attrs.get_eswitch_encap_mode(); // u8
```

### Do (reply)

```rust
PushOpEswitchGetDoReply::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]

  // Associated type: "EswitchMode" (enum)
  .push_eswitch_mode(val) // u16

  // Associated type: "EswitchInlineMode" (enum)
  .push_eswitch_inline_mode(val) // u8

  // Associated type: "EswitchEncapMode" (enum)
  .push_eswitch_encap_mode(val) // u8
  ;
```

```rust
let attrs = OpEswitchGetDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr

// Associated type: "EswitchMode" (enum)
attrs.get_eswitch_mode(); // u16

// Associated type: "EswitchInlineMode" (enum)
attrs.get_eswitch_inline_mode(); // u8

// Associated type: "EswitchEncapMode" (enum)
attrs.get_eswitch_encap_mode(); // u8
```

## Low-level decoding

### Do (request)

```rust
let iter = OpEswitchGetDoRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
  }
}
```

### Do (reply)

```rust
let iter = OpEswitchGetDoReply::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr

    // Associated type: "EswitchMode" (enum)
    EswitchMode(val) => {}, // u16

    // Associated type: "EswitchInlineMode" (enum)
    EswitchInlineMode(val) => {}, // u8

    // Associated type: "EswitchEncapMode" (enum)
    EswitchEncapMode(val) => {}, // u8
  }
}
```

# Operation "eswitch-set"

## Do (request)

```rust
PushOpEswitchSetDoRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]

  // Associated type: "EswitchMode" (enum)
  .push_eswitch_mode(val) // u16

  // Associated type: "EswitchInlineMode" (enum)
  .push_eswitch_inline_mode(val) // u8

  // Associated type: "EswitchEncapMode" (enum)
  .push_eswitch_encap_mode(val) // u8
  ;
```

```rust
let attrs = OpEswitchSetDoReply::new(buf);

// No attributes
```

### Do (reply)

```rust
PushOpEswitchSetDoReply::new(&mut vec)
  ;
```

```rust
let attrs = OpEswitchSetDoReply::new(buf);

// No attributes
```

## Low-level decoding

### Do (request)

```rust
let iter = OpEswitchSetDoRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr

    // Associated type: "EswitchMode" (enum)
    EswitchMode(val) => {}, // u16

    // Associated type: "EswitchInlineMode" (enum)
    EswitchInlineMode(val) => {}, // u8

    // Associated type: "EswitchEncapMode" (enum)
    EswitchEncapMode(val) => {}, // u8
  }
}
```

### Do (reply)

```rust
let iter = OpEswitchSetDoReply::new(buf);
// No attributes
```

# Operation "dpipe-table-get"

## Do (request)

```rust
PushOpDpipeTableGetDoRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_dpipe_table_name(val) // &CStr
  .push_dpipe_table_name_bytes(val) // &[u8]
  ;
```

```rust
let attrs = OpDpipeTableGetDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
{ // Nested DpipeTables
  let attrs = attrs.get_dpipe_tables();
  { // Nested DpipeTable

    // Attribute may repeat multiple times (treat it as array)
    for entry in attrs.get_dpipe_table() {
      entry.get_dpipe_table_name(); // &CStr
      entry.get_dpipe_table_size(); // u64
      entry.get_dpipe_table_name(); // &CStr
      entry.get_dpipe_table_size(); // u64
      { // Nested DpipeTableMatches
        let attrs = entry.get_dpipe_table_matches();
        { // Nested DpipeMatch

          // Attribute may repeat multiple times (treat it as array)
          for entry in attrs.get_dpipe_match() {

            // Associated type: "DpipeMatchType" (enum)
            entry.get_dpipe_match_type(); // u32

            // Associated type: "DpipeHeaderId" (enum)
            entry.get_dpipe_header_id(); // u32
            entry.get_dpipe_header_global(); // u8
            entry.get_dpipe_header_index(); // u32
            entry.get_dpipe_field_id(); // u32
          }
        }
      }
      { // Nested DpipeTableActions
        let attrs = entry.get_dpipe_table_actions();
        { // Nested DpipeAction

          // Attribute may repeat multiple times (treat it as array)
          for entry in attrs.get_dpipe_action() {

            // Associated type: "DpipeActionType" (enum)
            entry.get_dpipe_action_type(); // u32

            // Associated type: "DpipeHeaderId" (enum)
            entry.get_dpipe_header_id(); // u32
            entry.get_dpipe_header_global(); // u8
            entry.get_dpipe_header_index(); // u32
            entry.get_dpipe_field_id(); // u32
          }
        }
      }
      entry.get_dpipe_table_counters_enabled(); // u8
      entry.get_dpipe_table_resource_id(); // u64
      entry.get_dpipe_table_resource_units(); // u64
    }
  }
}
```

### Do (reply)

```rust
PushOpDpipeTableGetDoReply::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .nested_dpipe_tables()

    // Attribute may repeat multiple times (treat it as array)
    .nested_dpipe_table()
      .push_dpipe_table_name(val) // &CStr
      .push_dpipe_table_name_bytes(val) // &[u8]
      .push_dpipe_table_size(val) // u64
      .push_dpipe_table_name(val) // &CStr
      .push_dpipe_table_name_bytes(val) // &[u8]
      .push_dpipe_table_size(val) // u64
      .nested_dpipe_table_matches()

        // Attribute may repeat multiple times (treat it as array)
        .nested_dpipe_match()

          // Associated type: "DpipeMatchType" (enum)
          .push_dpipe_match_type(val) // u32

          // Associated type: "DpipeHeaderId" (enum)
          .push_dpipe_header_id(val) // u32
          .push_dpipe_header_global(val) // u8
          .push_dpipe_header_index(val) // u32
          .push_dpipe_field_id(val) // u32
        .end_nested()
      .end_nested()
      .nested_dpipe_table_actions()

        // Attribute may repeat multiple times (treat it as array)
        .nested_dpipe_action()

          // Associated type: "DpipeActionType" (enum)
          .push_dpipe_action_type(val) // u32

          // Associated type: "DpipeHeaderId" (enum)
          .push_dpipe_header_id(val) // u32
          .push_dpipe_header_global(val) // u8
          .push_dpipe_header_index(val) // u32
          .push_dpipe_field_id(val) // u32
        .end_nested()
      .end_nested()
      .push_dpipe_table_counters_enabled(val) // u8
      .push_dpipe_table_resource_id(val) // u64
      .push_dpipe_table_resource_units(val) // u64
    .end_nested()
  .end_nested()
  ;
```

```rust
let attrs = OpDpipeTableGetDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
{ // Nested DpipeTables
  let attrs = attrs.get_dpipe_tables();
  { // Nested DpipeTable

    // Attribute may repeat multiple times (treat it as array)
    for entry in attrs.get_dpipe_table() {
      entry.get_dpipe_table_name(); // &CStr
      entry.get_dpipe_table_size(); // u64
      entry.get_dpipe_table_name(); // &CStr
      entry.get_dpipe_table_size(); // u64
      { // Nested DpipeTableMatches
        let attrs = entry.get_dpipe_table_matches();
        { // Nested DpipeMatch

          // Attribute may repeat multiple times (treat it as array)
          for entry in attrs.get_dpipe_match() {

            // Associated type: "DpipeMatchType" (enum)
            entry.get_dpipe_match_type(); // u32

            // Associated type: "DpipeHeaderId" (enum)
            entry.get_dpipe_header_id(); // u32
            entry.get_dpipe_header_global(); // u8
            entry.get_dpipe_header_index(); // u32
            entry.get_dpipe_field_id(); // u32
          }
        }
      }
      { // Nested DpipeTableActions
        let attrs = entry.get_dpipe_table_actions();
        { // Nested DpipeAction

          // Attribute may repeat multiple times (treat it as array)
          for entry in attrs.get_dpipe_action() {

            // Associated type: "DpipeActionType" (enum)
            entry.get_dpipe_action_type(); // u32

            // Associated type: "DpipeHeaderId" (enum)
            entry.get_dpipe_header_id(); // u32
            entry.get_dpipe_header_global(); // u8
            entry.get_dpipe_header_index(); // u32
            entry.get_dpipe_field_id(); // u32
          }
        }
      }
      entry.get_dpipe_table_counters_enabled(); // u8
      entry.get_dpipe_table_resource_id(); // u64
      entry.get_dpipe_table_resource_units(); // u64
    }
  }
}
```

## Low-level decoding

### Do (request)

```rust
let iter = OpDpipeTableGetDoRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    DpipeTableName(val) => {}, // &CStr
  }
}
```

### Do (reply)

```rust
let iter = OpDpipeTableGetDoReply::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    DpipeTables(iter) => {
      for attr in iter {
        match attr {

          // Attribute may repeat multiple times (treat it as array)
          DpipeTable(iter) => {
            for attr in iter {
              match attr {
                DpipeTableName(val) => {}, // &CStr
                DpipeTableSize(val) => {}, // u64
                DpipeTableName(val) => {}, // &CStr
                DpipeTableSize(val) => {}, // u64
                DpipeTableMatches(iter) => {
                  for attr in iter {
                    match attr {

                      // Attribute may repeat multiple times (treat it as array)
                      DpipeMatch(iter) => {
                        for attr in iter {
                          match attr {

                            // Associated type: "DpipeMatchType" (enum)
                            DpipeMatchType(val) => {}, // u32

                            // Associated type: "DpipeHeaderId" (enum)
                            DpipeHeaderId(val) => {}, // u32
                            DpipeHeaderGlobal(val) => {}, // u8
                            DpipeHeaderIndex(val) => {}, // u32
                            DpipeFieldId(val) => {}, // u32
                          }
                        }
                      },
                    }
                  }
                },
                DpipeTableActions(iter) => {
                  for attr in iter {
                    match attr {

                      // Attribute may repeat multiple times (treat it as array)
                      DpipeAction(iter) => {
                        for attr in iter {
                          match attr {

                            // Associated type: "DpipeActionType" (enum)
                            DpipeActionType(val) => {}, // u32

                            // Associated type: "DpipeHeaderId" (enum)
                            DpipeHeaderId(val) => {}, // u32
                            DpipeHeaderGlobal(val) => {}, // u8
                            DpipeHeaderIndex(val) => {}, // u32
                            DpipeFieldId(val) => {}, // u32
                          }
                        }
                      },
                    }
                  }
                },
                DpipeTableCountersEnabled(val) => {}, // u8
                DpipeTableResourceId(val) => {}, // u64
                DpipeTableResourceUnits(val) => {}, // u64
              }
            }
          },
        }
      }
    },
  }
}
```

# Operation "dpipe-entries-get"

## Do (request)

```rust
PushOpDpipeEntriesGetDoRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_dpipe_table_name(val) // &CStr
  .push_dpipe_table_name_bytes(val) // &[u8]
  ;
```

```rust
let attrs = OpDpipeEntriesGetDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
{ // Nested DpipeEntries
  let attrs = attrs.get_dpipe_entries();
  { // Nested DpipeEntry

    // Attribute may repeat multiple times (treat it as array)
    for entry in attrs.get_dpipe_entry() {
      entry.get_dpipe_entry_index(); // u64
      { // Nested DpipeEntryMatchValues
        let attrs = entry.get_dpipe_entry_match_values();
        { // Nested DpipeMatchValue

          // Attribute may repeat multiple times (treat it as array)
          for entry in attrs.get_dpipe_match_value() {
            { // Nested DpipeMatch

              // Attribute may repeat multiple times (treat it as array)
              for entry in entry.get_dpipe_match() {

                // Associated type: "DpipeMatchType" (enum)
                entry.get_dpipe_match_type(); // u32

                // Associated type: "DpipeHeaderId" (enum)
                entry.get_dpipe_header_id(); // u32
                entry.get_dpipe_header_global(); // u8
                entry.get_dpipe_header_index(); // u32
                entry.get_dpipe_field_id(); // u32
              }
            }
            entry.get_dpipe_value(); // &[u8]
            entry.get_dpipe_value_mask(); // &[u8]
            entry.get_dpipe_value_mapping(); // u32
          }
        }
      }
      { // Nested DpipeEntryActionValues
        let attrs = entry.get_dpipe_entry_action_values();
        { // Nested DpipeActionValue

          // Attribute may repeat multiple times (treat it as array)
          for entry in attrs.get_dpipe_action_value() {
            { // Nested DpipeAction

              // Attribute may repeat multiple times (treat it as array)
              for entry in entry.get_dpipe_action() {

                // Associated type: "DpipeActionType" (enum)
                entry.get_dpipe_action_type(); // u32

                // Associated type: "DpipeHeaderId" (enum)
                entry.get_dpipe_header_id(); // u32
                entry.get_dpipe_header_global(); // u8
                entry.get_dpipe_header_index(); // u32
                entry.get_dpipe_field_id(); // u32
              }
            }
            entry.get_dpipe_value(); // &[u8]
            entry.get_dpipe_value_mask(); // &[u8]
            entry.get_dpipe_value_mapping(); // u32
          }
        }
      }
      entry.get_dpipe_entry_counter(); // u64
    }
  }
}
```

### Do (reply)

```rust
PushOpDpipeEntriesGetDoReply::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .nested_dpipe_entries()

    // Attribute may repeat multiple times (treat it as array)
    .nested_dpipe_entry()
      .push_dpipe_entry_index(val) // u64
      .nested_dpipe_entry_match_values()

        // Attribute may repeat multiple times (treat it as array)
        .nested_dpipe_match_value()

          // Attribute may repeat multiple times (treat it as array)
          .nested_dpipe_match()

            // Associated type: "DpipeMatchType" (enum)
            .push_dpipe_match_type(val) // u32

            // Associated type: "DpipeHeaderId" (enum)
            .push_dpipe_header_id(val) // u32
            .push_dpipe_header_global(val) // u8
            .push_dpipe_header_index(val) // u32
            .push_dpipe_field_id(val) // u32
          .end_nested()
          .push_dpipe_value(val) // &[u8]
          .push_dpipe_value_mask(val) // &[u8]
          .push_dpipe_value_mapping(val) // u32
        .end_nested()
      .end_nested()
      .nested_dpipe_entry_action_values()

        // Attribute may repeat multiple times (treat it as array)
        .nested_dpipe_action_value()

          // Attribute may repeat multiple times (treat it as array)
          .nested_dpipe_action()

            // Associated type: "DpipeActionType" (enum)
            .push_dpipe_action_type(val) // u32

            // Associated type: "DpipeHeaderId" (enum)
            .push_dpipe_header_id(val) // u32
            .push_dpipe_header_global(val) // u8
            .push_dpipe_header_index(val) // u32
            .push_dpipe_field_id(val) // u32
          .end_nested()
          .push_dpipe_value(val) // &[u8]
          .push_dpipe_value_mask(val) // &[u8]
          .push_dpipe_value_mapping(val) // u32
        .end_nested()
      .end_nested()
      .push_dpipe_entry_counter(val) // u64
    .end_nested()
  .end_nested()
  ;
```

```rust
let attrs = OpDpipeEntriesGetDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
{ // Nested DpipeEntries
  let attrs = attrs.get_dpipe_entries();
  { // Nested DpipeEntry

    // Attribute may repeat multiple times (treat it as array)
    for entry in attrs.get_dpipe_entry() {
      entry.get_dpipe_entry_index(); // u64
      { // Nested DpipeEntryMatchValues
        let attrs = entry.get_dpipe_entry_match_values();
        { // Nested DpipeMatchValue

          // Attribute may repeat multiple times (treat it as array)
          for entry in attrs.get_dpipe_match_value() {
            { // Nested DpipeMatch

              // Attribute may repeat multiple times (treat it as array)
              for entry in entry.get_dpipe_match() {

                // Associated type: "DpipeMatchType" (enum)
                entry.get_dpipe_match_type(); // u32

                // Associated type: "DpipeHeaderId" (enum)
                entry.get_dpipe_header_id(); // u32
                entry.get_dpipe_header_global(); // u8
                entry.get_dpipe_header_index(); // u32
                entry.get_dpipe_field_id(); // u32
              }
            }
            entry.get_dpipe_value(); // &[u8]
            entry.get_dpipe_value_mask(); // &[u8]
            entry.get_dpipe_value_mapping(); // u32
          }
        }
      }
      { // Nested DpipeEntryActionValues
        let attrs = entry.get_dpipe_entry_action_values();
        { // Nested DpipeActionValue

          // Attribute may repeat multiple times (treat it as array)
          for entry in attrs.get_dpipe_action_value() {
            { // Nested DpipeAction

              // Attribute may repeat multiple times (treat it as array)
              for entry in entry.get_dpipe_action() {

                // Associated type: "DpipeActionType" (enum)
                entry.get_dpipe_action_type(); // u32

                // Associated type: "DpipeHeaderId" (enum)
                entry.get_dpipe_header_id(); // u32
                entry.get_dpipe_header_global(); // u8
                entry.get_dpipe_header_index(); // u32
                entry.get_dpipe_field_id(); // u32
              }
            }
            entry.get_dpipe_value(); // &[u8]
            entry.get_dpipe_value_mask(); // &[u8]
            entry.get_dpipe_value_mapping(); // u32
          }
        }
      }
      entry.get_dpipe_entry_counter(); // u64
    }
  }
}
```

## Low-level decoding

### Do (request)

```rust
let iter = OpDpipeEntriesGetDoRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    DpipeTableName(val) => {}, // &CStr
  }
}
```

### Do (reply)

```rust
let iter = OpDpipeEntriesGetDoReply::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    DpipeEntries(iter) => {
      for attr in iter {
        match attr {

          // Attribute may repeat multiple times (treat it as array)
          DpipeEntry(iter) => {
            for attr in iter {
              match attr {
                DpipeEntryIndex(val) => {}, // u64
                DpipeEntryMatchValues(iter) => {
                  for attr in iter {
                    match attr {

                      // Attribute may repeat multiple times (treat it as array)
                      DpipeMatchValue(iter) => {
                        for attr in iter {
                          match attr {

                            // Attribute may repeat multiple times (treat it as array)
                            DpipeMatch(iter) => {
                              for attr in iter {
                                match attr {

                                  // Associated type: "DpipeMatchType" (enum)
                                  DpipeMatchType(val) => {}, // u32

                                  // Associated type: "DpipeHeaderId" (enum)
                                  DpipeHeaderId(val) => {}, // u32
                                  DpipeHeaderGlobal(val) => {}, // u8
                                  DpipeHeaderIndex(val) => {}, // u32
                                  DpipeFieldId(val) => {}, // u32
                                }
                              }
                            },
                            DpipeValue(val) => {}, // &[u8]
                            DpipeValueMask(val) => {}, // &[u8]
                            DpipeValueMapping(val) => {}, // u32
                          }
                        }
                      },
                    }
                  }
                },
                DpipeEntryActionValues(iter) => {
                  for attr in iter {
                    match attr {

                      // Attribute may repeat multiple times (treat it as array)
                      DpipeActionValue(iter) => {
                        for attr in iter {
                          match attr {

                            // Attribute may repeat multiple times (treat it as array)
                            DpipeAction(iter) => {
                              for attr in iter {
                                match attr {

                                  // Associated type: "DpipeActionType" (enum)
                                  DpipeActionType(val) => {}, // u32

                                  // Associated type: "DpipeHeaderId" (enum)
                                  DpipeHeaderId(val) => {}, // u32
                                  DpipeHeaderGlobal(val) => {}, // u8
                                  DpipeHeaderIndex(val) => {}, // u32
                                  DpipeFieldId(val) => {}, // u32
                                }
                              }
                            },
                            DpipeValue(val) => {}, // &[u8]
                            DpipeValueMask(val) => {}, // &[u8]
                            DpipeValueMapping(val) => {}, // u32
                          }
                        }
                      },
                    }
                  }
                },
                DpipeEntryCounter(val) => {}, // u64
              }
            }
          },
        }
      }
    },
  }
}
```

# Operation "dpipe-headers-get"

## Do (request)

```rust
PushOpDpipeHeadersGetDoRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  ;
```

```rust
let attrs = OpDpipeHeadersGetDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
{ // Nested DpipeHeaders
  let attrs = attrs.get_dpipe_headers();
  { // Nested DpipeHeader

    // Attribute may repeat multiple times (treat it as array)
    for entry in attrs.get_dpipe_header() {
      entry.get_dpipe_header_name(); // &CStr

      // Associated type: "DpipeHeaderId" (enum)
      entry.get_dpipe_header_id(); // u32
      entry.get_dpipe_header_global(); // u8
      { // Nested DpipeHeaderFields
        let attrs = entry.get_dpipe_header_fields();
        { // Nested DpipeField

          // Attribute may repeat multiple times (treat it as array)
          for entry in attrs.get_dpipe_field() {
            entry.get_dpipe_field_name(); // &CStr
            entry.get_dpipe_field_id(); // u32
            entry.get_dpipe_field_bitwidth(); // u32

            // Associated type: "DpipeFieldMappingType" (enum)
            entry.get_dpipe_field_mapping_type(); // u32
          }
        }
      }
    }
  }
}
```

### Do (reply)

```rust
PushOpDpipeHeadersGetDoReply::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .nested_dpipe_headers()

    // Attribute may repeat multiple times (treat it as array)
    .nested_dpipe_header()
      .push_dpipe_header_name(val) // &CStr
      .push_dpipe_header_name_bytes(val) // &[u8]

      // Associated type: "DpipeHeaderId" (enum)
      .push_dpipe_header_id(val) // u32
      .push_dpipe_header_global(val) // u8
      .nested_dpipe_header_fields()

        // Attribute may repeat multiple times (treat it as array)
        .nested_dpipe_field()
          .push_dpipe_field_name(val) // &CStr
          .push_dpipe_field_name_bytes(val) // &[u8]
          .push_dpipe_field_id(val) // u32
          .push_dpipe_field_bitwidth(val) // u32

          // Associated type: "DpipeFieldMappingType" (enum)
          .push_dpipe_field_mapping_type(val) // u32
        .end_nested()
      .end_nested()
    .end_nested()
  .end_nested()
  ;
```

```rust
let attrs = OpDpipeHeadersGetDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
{ // Nested DpipeHeaders
  let attrs = attrs.get_dpipe_headers();
  { // Nested DpipeHeader

    // Attribute may repeat multiple times (treat it as array)
    for entry in attrs.get_dpipe_header() {
      entry.get_dpipe_header_name(); // &CStr

      // Associated type: "DpipeHeaderId" (enum)
      entry.get_dpipe_header_id(); // u32
      entry.get_dpipe_header_global(); // u8
      { // Nested DpipeHeaderFields
        let attrs = entry.get_dpipe_header_fields();
        { // Nested DpipeField

          // Attribute may repeat multiple times (treat it as array)
          for entry in attrs.get_dpipe_field() {
            entry.get_dpipe_field_name(); // &CStr
            entry.get_dpipe_field_id(); // u32
            entry.get_dpipe_field_bitwidth(); // u32

            // Associated type: "DpipeFieldMappingType" (enum)
            entry.get_dpipe_field_mapping_type(); // u32
          }
        }
      }
    }
  }
}
```

## Low-level decoding

### Do (request)

```rust
let iter = OpDpipeHeadersGetDoRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
  }
}
```

### Do (reply)

```rust
let iter = OpDpipeHeadersGetDoReply::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    DpipeHeaders(iter) => {
      for attr in iter {
        match attr {

          // Attribute may repeat multiple times (treat it as array)
          DpipeHeader(iter) => {
            for attr in iter {
              match attr {
                DpipeHeaderName(val) => {}, // &CStr

                // Associated type: "DpipeHeaderId" (enum)
                DpipeHeaderId(val) => {}, // u32
                DpipeHeaderGlobal(val) => {}, // u8
                DpipeHeaderFields(iter) => {
                  for attr in iter {
                    match attr {

                      // Attribute may repeat multiple times (treat it as array)
                      DpipeField(iter) => {
                        for attr in iter {
                          match attr {
                            DpipeFieldName(val) => {}, // &CStr
                            DpipeFieldId(val) => {}, // u32
                            DpipeFieldBitwidth(val) => {}, // u32

                            // Associated type: "DpipeFieldMappingType" (enum)
                            DpipeFieldMappingType(val) => {}, // u32
                          }
                        }
                      },
                    }
                  }
                },
              }
            }
          },
        }
      }
    },
  }
}
```

# Operation "dpipe-table-counters-set"

## Do (request)

```rust
PushOpDpipeTableCountersSetDoRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_dpipe_table_name(val) // &CStr
  .push_dpipe_table_name_bytes(val) // &[u8]
  .push_dpipe_table_counters_enabled(val) // u8
  ;
```

```rust
let attrs = OpDpipeTableCountersSetDoReply::new(buf);

// No attributes
```

### Do (reply)

```rust
PushOpDpipeTableCountersSetDoReply::new(&mut vec)
  ;
```

```rust
let attrs = OpDpipeTableCountersSetDoReply::new(buf);

// No attributes
```

## Low-level decoding

### Do (request)

```rust
let iter = OpDpipeTableCountersSetDoRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    DpipeTableName(val) => {}, // &CStr
    DpipeTableCountersEnabled(val) => {}, // u8
  }
}
```

### Do (reply)

```rust
let iter = OpDpipeTableCountersSetDoReply::new(buf);
// No attributes
```

# Operation "resource-set"

## Do (request)

```rust
PushOpResourceSetDoRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_resource_id(val) // u64
  .push_resource_size(val) // u64
  ;
```

```rust
let attrs = OpResourceSetDoReply::new(buf);

// No attributes
```

### Do (reply)

```rust
PushOpResourceSetDoReply::new(&mut vec)
  ;
```

```rust
let attrs = OpResourceSetDoReply::new(buf);

// No attributes
```

## Low-level decoding

### Do (request)

```rust
let iter = OpResourceSetDoRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    ResourceId(val) => {}, // u64
    ResourceSize(val) => {}, // u64
  }
}
```

### Do (reply)

```rust
let iter = OpResourceSetDoReply::new(buf);
// No attributes
```

# Operation "resource-dump"

## Do (request)

```rust
PushOpResourceDumpDoRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  ;
```

```rust
let attrs = OpResourceDumpDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
{ // Nested ResourceList
  let attrs = attrs.get_resource_list();
  { // Nested Resource

    // Attribute may repeat multiple times (treat it as array)
    for entry in attrs.get_resource() {
      entry.get_resource_name(); // &CStr
      entry.get_resource_id(); // u64
      entry.get_resource_size(); // u64
      entry.get_resource_size_new(); // u64
      entry.get_resource_size_valid(); // u8
      entry.get_resource_size_min(); // u64
      entry.get_resource_size_max(); // u64
      entry.get_resource_size_gran(); // u64

      // Associated type: "ResourceUnit" (enum)
      entry.get_resource_unit(); // u8
      entry.get_resource_occ(); // u64
    }
  }
}
```

### Do (reply)

```rust
PushOpResourceDumpDoReply::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .nested_resource_list()

    // Attribute may repeat multiple times (treat it as array)
    .nested_resource()
      .push_resource_name(val) // &CStr
      .push_resource_name_bytes(val) // &[u8]
      .push_resource_id(val) // u64
      .push_resource_size(val) // u64
      .push_resource_size_new(val) // u64
      .push_resource_size_valid(val) // u8
      .push_resource_size_min(val) // u64
      .push_resource_size_max(val) // u64
      .push_resource_size_gran(val) // u64

      // Associated type: "ResourceUnit" (enum)
      .push_resource_unit(val) // u8
      .push_resource_occ(val) // u64
    .end_nested()
  .end_nested()
  ;
```

```rust
let attrs = OpResourceDumpDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
{ // Nested ResourceList
  let attrs = attrs.get_resource_list();
  { // Nested Resource

    // Attribute may repeat multiple times (treat it as array)
    for entry in attrs.get_resource() {
      entry.get_resource_name(); // &CStr
      entry.get_resource_id(); // u64
      entry.get_resource_size(); // u64
      entry.get_resource_size_new(); // u64
      entry.get_resource_size_valid(); // u8
      entry.get_resource_size_min(); // u64
      entry.get_resource_size_max(); // u64
      entry.get_resource_size_gran(); // u64

      // Associated type: "ResourceUnit" (enum)
      entry.get_resource_unit(); // u8
      entry.get_resource_occ(); // u64
    }
  }
}
```

## Low-level decoding

### Do (request)

```rust
let iter = OpResourceDumpDoRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
  }
}
```

### Do (reply)

```rust
let iter = OpResourceDumpDoReply::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    ResourceList(iter) => {
      for attr in iter {
        match attr {

          // Attribute may repeat multiple times (treat it as array)
          Resource(iter) => {
            for attr in iter {
              match attr {
                ResourceName(val) => {}, // &CStr
                ResourceId(val) => {}, // u64
                ResourceSize(val) => {}, // u64
                ResourceSizeNew(val) => {}, // u64
                ResourceSizeValid(val) => {}, // u8
                ResourceSizeMin(val) => {}, // u64
                ResourceSizeMax(val) => {}, // u64
                ResourceSizeGran(val) => {}, // u64

                // Associated type: "ResourceUnit" (enum)
                ResourceUnit(val) => {}, // u8
                ResourceOcc(val) => {}, // u64
              }
            }
          },
        }
      }
    },
  }
}
```

# Operation "reload"

## Do (request)

```rust
PushOpReloadDoRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]

  // Associated type: "ReloadAction" (enum)
  .push_reload_action(val) // u8

  // Associated type: "ReloadAction" (1 bit per enumeration)
  .push_reload_limits(val) // PushBuiltinBitfield32
  .push_netns_pid(val) // u32
  .push_netns_fd(val) // u32
  .push_netns_id(val) // u32
  ;
```

```rust
let attrs = OpReloadDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr

// Associated type: "ReloadAction" (1 bit per enumeration)
attrs.get_reload_actions_performed(); // PushBuiltinBitfield32
```

### Do (reply)

```rust
PushOpReloadDoReply::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]

  // Associated type: "ReloadAction" (1 bit per enumeration)
  .push_reload_actions_performed(val) // PushBuiltinBitfield32
  ;
```

```rust
let attrs = OpReloadDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr

// Associated type: "ReloadAction" (1 bit per enumeration)
attrs.get_reload_actions_performed(); // PushBuiltinBitfield32
```

## Low-level decoding

### Do (request)

```rust
let iter = OpReloadDoRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr

    // Associated type: "ReloadAction" (enum)
    ReloadAction(val) => {}, // u8

    // Associated type: "ReloadAction" (1 bit per enumeration)
    ReloadLimits(val) => {}, // PushBuiltinBitfield32
    NetnsPid(val) => {}, // u32
    NetnsFd(val) => {}, // u32
    NetnsId(val) => {}, // u32
  }
}
```

### Do (reply)

```rust
let iter = OpReloadDoReply::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr

    // Associated type: "ReloadAction" (1 bit per enumeration)
    ReloadActionsPerformed(val) => {}, // PushBuiltinBitfield32
  }
}
```

# Operation "param-get"

## Do (request)

```rust
PushOpParamGetDoRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_param_name(val) // &CStr
  .push_param_name_bytes(val) // &[u8]
  ;
```

```rust
let attrs = OpParamGetDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_param_name(); // &CStr
```

### Do (reply)

```rust
PushOpParamGetDoReply::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_param_name(val) // &CStr
  .push_param_name_bytes(val) // &[u8]
  ;
```

```rust
let attrs = OpParamGetDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_param_name(); // &CStr
```

## Low-level decoding

### Do (request)

```rust
let iter = OpParamGetDoRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    ParamName(val) => {}, // &CStr
  }
}
```

### Do (reply)

```rust
let iter = OpParamGetDoReply::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    ParamName(val) => {}, // &CStr
  }
}
```

## Dump (request)

```rust
PushOpParamGetDumpRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  ;
```

```rust
let attrs = OpParamGetDumpReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_param_name(); // &CStr
```

### Dump (reply)

```rust
PushOpParamGetDumpReply::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_param_name(val) // &CStr
  .push_param_name_bytes(val) // &[u8]
  ;
```

```rust
let attrs = OpParamGetDumpReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_param_name(); // &CStr
```

## Low-level decoding

### Dump (request)

```rust
let iter = OpParamGetDumpRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
  }
}
```

### Dump (reply)

```rust
let iter = OpParamGetDumpReply::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    ParamName(val) => {}, // &CStr
  }
}
```

# Operation "param-set"

## Do (request)

```rust
PushOpParamSetDoRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_param_name(val) // &CStr
  .push_param_name_bytes(val) // &[u8]

  // Associated type: "VarAttrType" (enum)
  .push_param_type(val) // u8

  // Associated type: "ParamCmode" (enum)
  .push_param_value_cmode(val) // u8
  ;
```

```rust
let attrs = OpParamSetDoReply::new(buf);

// No attributes
```

### Do (reply)

```rust
PushOpParamSetDoReply::new(&mut vec)
  ;
```

```rust
let attrs = OpParamSetDoReply::new(buf);

// No attributes
```

## Low-level decoding

### Do (request)

```rust
let iter = OpParamSetDoRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    ParamName(val) => {}, // &CStr

    // Associated type: "VarAttrType" (enum)
    ParamType(val) => {}, // u8

    // Associated type: "ParamCmode" (enum)
    ParamValueCmode(val) => {}, // u8
  }
}
```

### Do (reply)

```rust
let iter = OpParamSetDoReply::new(buf);
// No attributes
```

# Operation "region-get"

## Do (request)

```rust
PushOpRegionGetDoRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_port_index(val) // u32
  .push_region_name(val) // &CStr
  .push_region_name_bytes(val) // &[u8]
  ;
```

```rust
let attrs = OpRegionGetDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_port_index(); // u32
attrs.get_region_name(); // &CStr
```

### Do (reply)

```rust
PushOpRegionGetDoReply::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_port_index(val) // u32
  .push_region_name(val) // &CStr
  .push_region_name_bytes(val) // &[u8]
  ;
```

```rust
let attrs = OpRegionGetDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_port_index(); // u32
attrs.get_region_name(); // &CStr
```

## Low-level decoding

### Do (request)

```rust
let iter = OpRegionGetDoRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    PortIndex(val) => {}, // u32
    RegionName(val) => {}, // &CStr
  }
}
```

### Do (reply)

```rust
let iter = OpRegionGetDoReply::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    PortIndex(val) => {}, // u32
    RegionName(val) => {}, // &CStr
  }
}
```

## Dump (request)

```rust
PushOpRegionGetDumpRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  ;
```

```rust
let attrs = OpRegionGetDumpReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_port_index(); // u32
attrs.get_region_name(); // &CStr
```

### Dump (reply)

```rust
PushOpRegionGetDumpReply::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_port_index(val) // u32
  .push_region_name(val) // &CStr
  .push_region_name_bytes(val) // &[u8]
  ;
```

```rust
let attrs = OpRegionGetDumpReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_port_index(); // u32
attrs.get_region_name(); // &CStr
```

## Low-level decoding

### Dump (request)

```rust
let iter = OpRegionGetDumpRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
  }
}
```

### Dump (reply)

```rust
let iter = OpRegionGetDumpReply::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    PortIndex(val) => {}, // u32
    RegionName(val) => {}, // &CStr
  }
}
```

# Operation "region-new"

## Do (request)

```rust
PushOpRegionNewDoRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_port_index(val) // u32
  .push_region_name(val) // &CStr
  .push_region_name_bytes(val) // &[u8]
  .push_region_snapshot_id(val) // u32
  ;
```

```rust
let attrs = OpRegionNewDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_port_index(); // u32
attrs.get_region_name(); // &CStr
attrs.get_region_snapshot_id(); // u32
```

### Do (reply)

```rust
PushOpRegionNewDoReply::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_port_index(val) // u32
  .push_region_name(val) // &CStr
  .push_region_name_bytes(val) // &[u8]
  .push_region_snapshot_id(val) // u32
  ;
```

```rust
let attrs = OpRegionNewDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_port_index(); // u32
attrs.get_region_name(); // &CStr
attrs.get_region_snapshot_id(); // u32
```

## Low-level decoding

### Do (request)

```rust
let iter = OpRegionNewDoRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    PortIndex(val) => {}, // u32
    RegionName(val) => {}, // &CStr
    RegionSnapshotId(val) => {}, // u32
  }
}
```

### Do (reply)

```rust
let iter = OpRegionNewDoReply::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    PortIndex(val) => {}, // u32
    RegionName(val) => {}, // &CStr
    RegionSnapshotId(val) => {}, // u32
  }
}
```

# Operation "region-del"

## Do (request)

```rust
PushOpRegionDelDoRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_port_index(val) // u32
  .push_region_name(val) // &CStr
  .push_region_name_bytes(val) // &[u8]
  .push_region_snapshot_id(val) // u32
  ;
```

```rust
let attrs = OpRegionDelDoReply::new(buf);

// No attributes
```

### Do (reply)

```rust
PushOpRegionDelDoReply::new(&mut vec)
  ;
```

```rust
let attrs = OpRegionDelDoReply::new(buf);

// No attributes
```

## Low-level decoding

### Do (request)

```rust
let iter = OpRegionDelDoRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    PortIndex(val) => {}, // u32
    RegionName(val) => {}, // &CStr
    RegionSnapshotId(val) => {}, // u32
  }
}
```

### Do (reply)

```rust
let iter = OpRegionDelDoReply::new(buf);
// No attributes
```

# Operation "region-read"

## Dump (request)

```rust
PushOpRegionReadDumpRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_port_index(val) // u32
  .push_region_name(val) // &CStr
  .push_region_name_bytes(val) // &[u8]
  .push_region_snapshot_id(val) // u32
  .push_region_direct(val) // ()
  .push_region_chunk_addr(val) // u64
  .push_region_chunk_len(val) // u64
  ;
```

```rust
let attrs = OpRegionReadDumpReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_port_index(); // u32
attrs.get_region_name(); // &CStr
```

### Dump (reply)

```rust
PushOpRegionReadDumpReply::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_port_index(val) // u32
  .push_region_name(val) // &CStr
  .push_region_name_bytes(val) // &[u8]
  ;
```

```rust
let attrs = OpRegionReadDumpReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_port_index(); // u32
attrs.get_region_name(); // &CStr
```

## Low-level decoding

### Dump (request)

```rust
let iter = OpRegionReadDumpRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    PortIndex(val) => {}, // u32
    RegionName(val) => {}, // &CStr
    RegionSnapshotId(val) => {}, // u32
    RegionDirect(val) => {}, // ()
    RegionChunkAddr(val) => {}, // u64
    RegionChunkLen(val) => {}, // u64
  }
}
```

### Dump (reply)

```rust
let iter = OpRegionReadDumpReply::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    PortIndex(val) => {}, // u32
    RegionName(val) => {}, // &CStr
  }
}
```

# Operation "port-param-get"

## Do (request)

```rust
PushOpPortParamGetDoRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_port_index(val) // u32
  ;
```

```rust
let attrs = OpPortParamGetDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_port_index(); // u32
```

### Do (reply)

```rust
PushOpPortParamGetDoReply::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_port_index(val) // u32
  ;
```

```rust
let attrs = OpPortParamGetDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_port_index(); // u32
```

## Low-level decoding

### Do (request)

```rust
let iter = OpPortParamGetDoRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    PortIndex(val) => {}, // u32
  }
}
```

### Do (reply)

```rust
let iter = OpPortParamGetDoReply::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    PortIndex(val) => {}, // u32
  }
}
```

## Dump (request)

```rust
PushOpPortParamGetDumpRequest::new(&mut vec)
  ;
```

```rust
let attrs = OpPortParamGetDumpReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_port_index(); // u32
```

### Dump (reply)

```rust
PushOpPortParamGetDumpReply::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_port_index(val) // u32
  ;
```

```rust
let attrs = OpPortParamGetDumpReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_port_index(); // u32
```

## Low-level decoding

### Dump (request)

```rust
let iter = OpPortParamGetDumpRequest::new(buf);
// No attributes
```

### Dump (reply)

```rust
let iter = OpPortParamGetDumpReply::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    PortIndex(val) => {}, // u32
  }
}
```

# Operation "port-param-set"

## Do (request)

```rust
PushOpPortParamSetDoRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_port_index(val) // u32
  ;
```

```rust
let attrs = OpPortParamSetDoReply::new(buf);

// No attributes
```

### Do (reply)

```rust
PushOpPortParamSetDoReply::new(&mut vec)
  ;
```

```rust
let attrs = OpPortParamSetDoReply::new(buf);

// No attributes
```

## Low-level decoding

### Do (request)

```rust
let iter = OpPortParamSetDoRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    PortIndex(val) => {}, // u32
  }
}
```

### Do (reply)

```rust
let iter = OpPortParamSetDoReply::new(buf);
// No attributes
```

# Operation "info-get"

## Do (request)

```rust
PushOpInfoGetDoRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  ;
```

```rust
let attrs = OpInfoGetDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_info_driver_name(); // &CStr
attrs.get_info_serial_number(); // &CStr
{ // Nested InfoVersionFixed

  // Attribute may repeat multiple times (treat it as array)
  for entry in attrs.get_info_version_fixed() {
    entry.get_info_version_name(); // &CStr
    entry.get_info_version_value(); // &CStr
  }
}
{ // Nested InfoVersionRunning

  // Attribute may repeat multiple times (treat it as array)
  for entry in attrs.get_info_version_running() {
    entry.get_info_version_name(); // &CStr
    entry.get_info_version_value(); // &CStr
  }
}
{ // Nested InfoVersionStored

  // Attribute may repeat multiple times (treat it as array)
  for entry in attrs.get_info_version_stored() {
    entry.get_info_version_name(); // &CStr
    entry.get_info_version_value(); // &CStr
  }
}
attrs.get_info_board_serial_number(); // &CStr
```

### Do (reply)

```rust
PushOpInfoGetDoReply::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_info_driver_name(val) // &CStr
  .push_info_driver_name_bytes(val) // &[u8]
  .push_info_serial_number(val) // &CStr
  .push_info_serial_number_bytes(val) // &[u8]

  // Attribute may repeat multiple times (treat it as array)
  .nested_info_version_fixed()
    .push_info_version_name(val) // &CStr
    .push_info_version_name_bytes(val) // &[u8]
    .push_info_version_value(val) // &CStr
    .push_info_version_value_bytes(val) // &[u8]
  .end_nested()

  // Attribute may repeat multiple times (treat it as array)
  .nested_info_version_running()
    .push_info_version_name(val) // &CStr
    .push_info_version_name_bytes(val) // &[u8]
    .push_info_version_value(val) // &CStr
    .push_info_version_value_bytes(val) // &[u8]
  .end_nested()

  // Attribute may repeat multiple times (treat it as array)
  .nested_info_version_stored()
    .push_info_version_name(val) // &CStr
    .push_info_version_name_bytes(val) // &[u8]
    .push_info_version_value(val) // &CStr
    .push_info_version_value_bytes(val) // &[u8]
  .end_nested()
  .push_info_board_serial_number(val) // &CStr
  .push_info_board_serial_number_bytes(val) // &[u8]
  ;
```

```rust
let attrs = OpInfoGetDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_info_driver_name(); // &CStr
attrs.get_info_serial_number(); // &CStr
{ // Nested InfoVersionFixed

  // Attribute may repeat multiple times (treat it as array)
  for entry in attrs.get_info_version_fixed() {
    entry.get_info_version_name(); // &CStr
    entry.get_info_version_value(); // &CStr
  }
}
{ // Nested InfoVersionRunning

  // Attribute may repeat multiple times (treat it as array)
  for entry in attrs.get_info_version_running() {
    entry.get_info_version_name(); // &CStr
    entry.get_info_version_value(); // &CStr
  }
}
{ // Nested InfoVersionStored

  // Attribute may repeat multiple times (treat it as array)
  for entry in attrs.get_info_version_stored() {
    entry.get_info_version_name(); // &CStr
    entry.get_info_version_value(); // &CStr
  }
}
attrs.get_info_board_serial_number(); // &CStr
```

## Low-level decoding

### Do (request)

```rust
let iter = OpInfoGetDoRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
  }
}
```

### Do (reply)

```rust
let iter = OpInfoGetDoReply::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    InfoDriverName(val) => {}, // &CStr
    InfoSerialNumber(val) => {}, // &CStr

    // Attribute may repeat multiple times (treat it as array)
    InfoVersionFixed(iter) => {
      for attr in iter {
        match attr {
          InfoVersionName(val) => {}, // &CStr
          InfoVersionValue(val) => {}, // &CStr
        }
      }
    },

    // Attribute may repeat multiple times (treat it as array)
    InfoVersionRunning(iter) => {
      for attr in iter {
        match attr {
          InfoVersionName(val) => {}, // &CStr
          InfoVersionValue(val) => {}, // &CStr
        }
      }
    },

    // Attribute may repeat multiple times (treat it as array)
    InfoVersionStored(iter) => {
      for attr in iter {
        match attr {
          InfoVersionName(val) => {}, // &CStr
          InfoVersionValue(val) => {}, // &CStr
        }
      }
    },
    InfoBoardSerialNumber(val) => {}, // &CStr
  }
}
```

## Dump (request)

```rust
PushOpInfoGetDumpRequest::new(&mut vec)
  ;
```

```rust
let attrs = OpInfoGetDumpReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_info_driver_name(); // &CStr
attrs.get_info_serial_number(); // &CStr
{ // Nested InfoVersionFixed

  // Attribute may repeat multiple times (treat it as array)
  for entry in attrs.get_info_version_fixed() {
    entry.get_info_version_name(); // &CStr
    entry.get_info_version_value(); // &CStr
  }
}
{ // Nested InfoVersionRunning

  // Attribute may repeat multiple times (treat it as array)
  for entry in attrs.get_info_version_running() {
    entry.get_info_version_name(); // &CStr
    entry.get_info_version_value(); // &CStr
  }
}
{ // Nested InfoVersionStored

  // Attribute may repeat multiple times (treat it as array)
  for entry in attrs.get_info_version_stored() {
    entry.get_info_version_name(); // &CStr
    entry.get_info_version_value(); // &CStr
  }
}
attrs.get_info_board_serial_number(); // &CStr
```

### Dump (reply)

```rust
PushOpInfoGetDumpReply::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_info_driver_name(val) // &CStr
  .push_info_driver_name_bytes(val) // &[u8]
  .push_info_serial_number(val) // &CStr
  .push_info_serial_number_bytes(val) // &[u8]

  // Attribute may repeat multiple times (treat it as array)
  .nested_info_version_fixed()
    .push_info_version_name(val) // &CStr
    .push_info_version_name_bytes(val) // &[u8]
    .push_info_version_value(val) // &CStr
    .push_info_version_value_bytes(val) // &[u8]
  .end_nested()

  // Attribute may repeat multiple times (treat it as array)
  .nested_info_version_running()
    .push_info_version_name(val) // &CStr
    .push_info_version_name_bytes(val) // &[u8]
    .push_info_version_value(val) // &CStr
    .push_info_version_value_bytes(val) // &[u8]
  .end_nested()

  // Attribute may repeat multiple times (treat it as array)
  .nested_info_version_stored()
    .push_info_version_name(val) // &CStr
    .push_info_version_name_bytes(val) // &[u8]
    .push_info_version_value(val) // &CStr
    .push_info_version_value_bytes(val) // &[u8]
  .end_nested()
  .push_info_board_serial_number(val) // &CStr
  .push_info_board_serial_number_bytes(val) // &[u8]
  ;
```

```rust
let attrs = OpInfoGetDumpReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_info_driver_name(); // &CStr
attrs.get_info_serial_number(); // &CStr
{ // Nested InfoVersionFixed

  // Attribute may repeat multiple times (treat it as array)
  for entry in attrs.get_info_version_fixed() {
    entry.get_info_version_name(); // &CStr
    entry.get_info_version_value(); // &CStr
  }
}
{ // Nested InfoVersionRunning

  // Attribute may repeat multiple times (treat it as array)
  for entry in attrs.get_info_version_running() {
    entry.get_info_version_name(); // &CStr
    entry.get_info_version_value(); // &CStr
  }
}
{ // Nested InfoVersionStored

  // Attribute may repeat multiple times (treat it as array)
  for entry in attrs.get_info_version_stored() {
    entry.get_info_version_name(); // &CStr
    entry.get_info_version_value(); // &CStr
  }
}
attrs.get_info_board_serial_number(); // &CStr
```

## Low-level decoding

### Dump (request)

```rust
let iter = OpInfoGetDumpRequest::new(buf);
// No attributes
```

### Dump (reply)

```rust
let iter = OpInfoGetDumpReply::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    InfoDriverName(val) => {}, // &CStr
    InfoSerialNumber(val) => {}, // &CStr

    // Attribute may repeat multiple times (treat it as array)
    InfoVersionFixed(iter) => {
      for attr in iter {
        match attr {
          InfoVersionName(val) => {}, // &CStr
          InfoVersionValue(val) => {}, // &CStr
        }
      }
    },

    // Attribute may repeat multiple times (treat it as array)
    InfoVersionRunning(iter) => {
      for attr in iter {
        match attr {
          InfoVersionName(val) => {}, // &CStr
          InfoVersionValue(val) => {}, // &CStr
        }
      }
    },

    // Attribute may repeat multiple times (treat it as array)
    InfoVersionStored(iter) => {
      for attr in iter {
        match attr {
          InfoVersionName(val) => {}, // &CStr
          InfoVersionValue(val) => {}, // &CStr
        }
      }
    },
    InfoBoardSerialNumber(val) => {}, // &CStr
  }
}
```

# Operation "health-reporter-get"

## Do (request)

```rust
PushOpHealthReporterGetDoRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_port_index(val) // u32
  .push_health_reporter_name(val) // &CStr
  .push_health_reporter_name_bytes(val) // &[u8]
  ;
```

```rust
let attrs = OpHealthReporterGetDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_port_index(); // u32
attrs.get_health_reporter_name(); // &CStr
```

### Do (reply)

```rust
PushOpHealthReporterGetDoReply::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_port_index(val) // u32
  .push_health_reporter_name(val) // &CStr
  .push_health_reporter_name_bytes(val) // &[u8]
  ;
```

```rust
let attrs = OpHealthReporterGetDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_port_index(); // u32
attrs.get_health_reporter_name(); // &CStr
```

## Low-level decoding

### Do (request)

```rust
let iter = OpHealthReporterGetDoRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    PortIndex(val) => {}, // u32
    HealthReporterName(val) => {}, // &CStr
  }
}
```

### Do (reply)

```rust
let iter = OpHealthReporterGetDoReply::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    PortIndex(val) => {}, // u32
    HealthReporterName(val) => {}, // &CStr
  }
}
```

## Dump (request)

```rust
PushOpHealthReporterGetDumpRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_port_index(val) // u32
  ;
```

```rust
let attrs = OpHealthReporterGetDumpReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_port_index(); // u32
attrs.get_health_reporter_name(); // &CStr
```

### Dump (reply)

```rust
PushOpHealthReporterGetDumpReply::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_port_index(val) // u32
  .push_health_reporter_name(val) // &CStr
  .push_health_reporter_name_bytes(val) // &[u8]
  ;
```

```rust
let attrs = OpHealthReporterGetDumpReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_port_index(); // u32
attrs.get_health_reporter_name(); // &CStr
```

## Low-level decoding

### Dump (request)

```rust
let iter = OpHealthReporterGetDumpRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    PortIndex(val) => {}, // u32
  }
}
```

### Dump (reply)

```rust
let iter = OpHealthReporterGetDumpReply::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    PortIndex(val) => {}, // u32
    HealthReporterName(val) => {}, // &CStr
  }
}
```

# Operation "health-reporter-set"

## Do (request)

```rust
PushOpHealthReporterSetDoRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_port_index(val) // u32
  .push_health_reporter_name(val) // &CStr
  .push_health_reporter_name_bytes(val) // &[u8]
  .push_health_reporter_graceful_period(val) // u64
  .push_health_reporter_auto_recover(val) // u8
  .push_health_reporter_auto_dump(val) // u8

  // Time (in msec) for recoveries before starting the grace period.
  .push_health_reporter_burst_period(val) // u64
  ;
```

```rust
let attrs = OpHealthReporterSetDoReply::new(buf);

// No attributes
```

### Do (reply)

```rust
PushOpHealthReporterSetDoReply::new(&mut vec)
  ;
```

```rust
let attrs = OpHealthReporterSetDoReply::new(buf);

// No attributes
```

## Low-level decoding

### Do (request)

```rust
let iter = OpHealthReporterSetDoRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    PortIndex(val) => {}, // u32
    HealthReporterName(val) => {}, // &CStr
    HealthReporterGracefulPeriod(val) => {}, // u64
    HealthReporterAutoRecover(val) => {}, // u8
    HealthReporterAutoDump(val) => {}, // u8

    // Time (in msec) for recoveries before starting the grace period.
    HealthReporterBurstPeriod(val) => {}, // u64
  }
}
```

### Do (reply)

```rust
let iter = OpHealthReporterSetDoReply::new(buf);
// No attributes
```

# Operation "health-reporter-recover"

## Do (request)

```rust
PushOpHealthReporterRecoverDoRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_port_index(val) // u32
  .push_health_reporter_name(val) // &CStr
  .push_health_reporter_name_bytes(val) // &[u8]
  ;
```

```rust
let attrs = OpHealthReporterRecoverDoReply::new(buf);

// No attributes
```

### Do (reply)

```rust
PushOpHealthReporterRecoverDoReply::new(&mut vec)
  ;
```

```rust
let attrs = OpHealthReporterRecoverDoReply::new(buf);

// No attributes
```

## Low-level decoding

### Do (request)

```rust
let iter = OpHealthReporterRecoverDoRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    PortIndex(val) => {}, // u32
    HealthReporterName(val) => {}, // &CStr
  }
}
```

### Do (reply)

```rust
let iter = OpHealthReporterRecoverDoReply::new(buf);
// No attributes
```

# Operation "health-reporter-diagnose"

## Do (request)

```rust
PushOpHealthReporterDiagnoseDoRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_port_index(val) // u32
  .push_health_reporter_name(val) // &CStr
  .push_health_reporter_name_bytes(val) // &[u8]
  ;
```

```rust
let attrs = OpHealthReporterDiagnoseDoReply::new(buf);

// No attributes
```

### Do (reply)

```rust
PushOpHealthReporterDiagnoseDoReply::new(&mut vec)
  ;
```

```rust
let attrs = OpHealthReporterDiagnoseDoReply::new(buf);

// No attributes
```

## Low-level decoding

### Do (request)

```rust
let iter = OpHealthReporterDiagnoseDoRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    PortIndex(val) => {}, // u32
    HealthReporterName(val) => {}, // &CStr
  }
}
```

### Do (reply)

```rust
let iter = OpHealthReporterDiagnoseDoReply::new(buf);
// No attributes
```

# Operation "health-reporter-dump-get"

## Dump (request)

```rust
PushOpHealthReporterDumpGetDumpRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_port_index(val) // u32
  .push_health_reporter_name(val) // &CStr
  .push_health_reporter_name_bytes(val) // &[u8]
  ;
```

```rust
let attrs = OpHealthReporterDumpGetDumpReply::new(buf);

{ // Nested Fmsg
  let attrs = attrs.get_fmsg();
  attrs.get_fmsg_obj_nest_start(); // ()
  attrs.get_fmsg_pair_nest_start(); // ()
  attrs.get_fmsg_arr_nest_start(); // ()
  attrs.get_fmsg_nest_end(); // ()
  attrs.get_fmsg_obj_name(); // &CStr
}
```

### Dump (reply)

```rust
PushOpHealthReporterDumpGetDumpReply::new(&mut vec)
  .nested_fmsg()
    .push_fmsg_obj_nest_start(val) // ()
    .push_fmsg_pair_nest_start(val) // ()
    .push_fmsg_arr_nest_start(val) // ()
    .push_fmsg_nest_end(val) // ()
    .push_fmsg_obj_name(val) // &CStr
    .push_fmsg_obj_name_bytes(val) // &[u8]
  .end_nested()
  ;
```

```rust
let attrs = OpHealthReporterDumpGetDumpReply::new(buf);

{ // Nested Fmsg
  let attrs = attrs.get_fmsg();
  attrs.get_fmsg_obj_nest_start(); // ()
  attrs.get_fmsg_pair_nest_start(); // ()
  attrs.get_fmsg_arr_nest_start(); // ()
  attrs.get_fmsg_nest_end(); // ()
  attrs.get_fmsg_obj_name(); // &CStr
}
```

## Low-level decoding

### Dump (request)

```rust
let iter = OpHealthReporterDumpGetDumpRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    PortIndex(val) => {}, // u32
    HealthReporterName(val) => {}, // &CStr
  }
}
```

### Dump (reply)

```rust
let iter = OpHealthReporterDumpGetDumpReply::new(buf);
for attr in iter {
  match attr {
    Fmsg(iter) => {
      for attr in iter {
        match attr {
          FmsgObjNestStart(val) => {}, // ()
          FmsgPairNestStart(val) => {}, // ()
          FmsgArrNestStart(val) => {}, // ()
          FmsgNestEnd(val) => {}, // ()
          FmsgObjName(val) => {}, // &CStr
        }
      }
    },
  }
}
```

# Operation "health-reporter-dump-clear"

## Do (request)

```rust
PushOpHealthReporterDumpClearDoRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_port_index(val) // u32
  .push_health_reporter_name(val) // &CStr
  .push_health_reporter_name_bytes(val) // &[u8]
  ;
```

```rust
let attrs = OpHealthReporterDumpClearDoReply::new(buf);

// No attributes
```

### Do (reply)

```rust
PushOpHealthReporterDumpClearDoReply::new(&mut vec)
  ;
```

```rust
let attrs = OpHealthReporterDumpClearDoReply::new(buf);

// No attributes
```

## Low-level decoding

### Do (request)

```rust
let iter = OpHealthReporterDumpClearDoRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    PortIndex(val) => {}, // u32
    HealthReporterName(val) => {}, // &CStr
  }
}
```

### Do (reply)

```rust
let iter = OpHealthReporterDumpClearDoReply::new(buf);
// No attributes
```

# Operation "flash-update"

## Do (request)

```rust
PushOpFlashUpdateDoRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_flash_update_file_name(val) // &CStr
  .push_flash_update_file_name_bytes(val) // &[u8]
  .push_flash_update_component(val) // &CStr
  .push_flash_update_component_bytes(val) // &[u8]

  // Associated type: "FlashOverwrite" (1 bit per enumeration)
  .push_flash_update_overwrite_mask(val) // PushBuiltinBitfield32
  ;
```

```rust
let attrs = OpFlashUpdateDoReply::new(buf);

// No attributes
```

### Do (reply)

```rust
PushOpFlashUpdateDoReply::new(&mut vec)
  ;
```

```rust
let attrs = OpFlashUpdateDoReply::new(buf);

// No attributes
```

## Low-level decoding

### Do (request)

```rust
let iter = OpFlashUpdateDoRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    FlashUpdateFileName(val) => {}, // &CStr
    FlashUpdateComponent(val) => {}, // &CStr

    // Associated type: "FlashOverwrite" (1 bit per enumeration)
    FlashUpdateOverwriteMask(val) => {}, // PushBuiltinBitfield32
  }
}
```

### Do (reply)

```rust
let iter = OpFlashUpdateDoReply::new(buf);
// No attributes
```

# Operation "trap-get"

## Do (request)

```rust
PushOpTrapGetDoRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_trap_name(val) // &CStr
  .push_trap_name_bytes(val) // &[u8]
  ;
```

```rust
let attrs = OpTrapGetDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_trap_name(); // &CStr
```

### Do (reply)

```rust
PushOpTrapGetDoReply::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_trap_name(val) // &CStr
  .push_trap_name_bytes(val) // &[u8]
  ;
```

```rust
let attrs = OpTrapGetDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_trap_name(); // &CStr
```

## Low-level decoding

### Do (request)

```rust
let iter = OpTrapGetDoRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    TrapName(val) => {}, // &CStr
  }
}
```

### Do (reply)

```rust
let iter = OpTrapGetDoReply::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    TrapName(val) => {}, // &CStr
  }
}
```

## Dump (request)

```rust
PushOpTrapGetDumpRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  ;
```

```rust
let attrs = OpTrapGetDumpReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_trap_name(); // &CStr
```

### Dump (reply)

```rust
PushOpTrapGetDumpReply::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_trap_name(val) // &CStr
  .push_trap_name_bytes(val) // &[u8]
  ;
```

```rust
let attrs = OpTrapGetDumpReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_trap_name(); // &CStr
```

## Low-level decoding

### Dump (request)

```rust
let iter = OpTrapGetDumpRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
  }
}
```

### Dump (reply)

```rust
let iter = OpTrapGetDumpReply::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    TrapName(val) => {}, // &CStr
  }
}
```

# Operation "trap-set"

## Do (request)

```rust
PushOpTrapSetDoRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_trap_name(val) // &CStr
  .push_trap_name_bytes(val) // &[u8]

  // Associated type: "TrapAction" (enum)
  .push_trap_action(val) // u8
  ;
```

```rust
let attrs = OpTrapSetDoReply::new(buf);

// No attributes
```

### Do (reply)

```rust
PushOpTrapSetDoReply::new(&mut vec)
  ;
```

```rust
let attrs = OpTrapSetDoReply::new(buf);

// No attributes
```

## Low-level decoding

### Do (request)

```rust
let iter = OpTrapSetDoRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    TrapName(val) => {}, // &CStr

    // Associated type: "TrapAction" (enum)
    TrapAction(val) => {}, // u8
  }
}
```

### Do (reply)

```rust
let iter = OpTrapSetDoReply::new(buf);
// No attributes
```

# Operation "trap-group-get"

## Do (request)

```rust
PushOpTrapGroupGetDoRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_trap_group_name(val) // &CStr
  .push_trap_group_name_bytes(val) // &[u8]
  ;
```

```rust
let attrs = OpTrapGroupGetDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_trap_group_name(); // &CStr
```

### Do (reply)

```rust
PushOpTrapGroupGetDoReply::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_trap_group_name(val) // &CStr
  .push_trap_group_name_bytes(val) // &[u8]
  ;
```

```rust
let attrs = OpTrapGroupGetDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_trap_group_name(); // &CStr
```

## Low-level decoding

### Do (request)

```rust
let iter = OpTrapGroupGetDoRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    TrapGroupName(val) => {}, // &CStr
  }
}
```

### Do (reply)

```rust
let iter = OpTrapGroupGetDoReply::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    TrapGroupName(val) => {}, // &CStr
  }
}
```

## Dump (request)

```rust
PushOpTrapGroupGetDumpRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  ;
```

```rust
let attrs = OpTrapGroupGetDumpReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_trap_group_name(); // &CStr
```

### Dump (reply)

```rust
PushOpTrapGroupGetDumpReply::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_trap_group_name(val) // &CStr
  .push_trap_group_name_bytes(val) // &[u8]
  ;
```

```rust
let attrs = OpTrapGroupGetDumpReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_trap_group_name(); // &CStr
```

## Low-level decoding

### Dump (request)

```rust
let iter = OpTrapGroupGetDumpRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
  }
}
```

### Dump (reply)

```rust
let iter = OpTrapGroupGetDumpReply::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    TrapGroupName(val) => {}, // &CStr
  }
}
```

# Operation "trap-group-set"

## Do (request)

```rust
PushOpTrapGroupSetDoRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_trap_group_name(val) // &CStr
  .push_trap_group_name_bytes(val) // &[u8]

  // Associated type: "TrapAction" (enum)
  .push_trap_action(val) // u8
  .push_trap_policer_id(val) // u32
  ;
```

```rust
let attrs = OpTrapGroupSetDoReply::new(buf);

// No attributes
```

### Do (reply)

```rust
PushOpTrapGroupSetDoReply::new(&mut vec)
  ;
```

```rust
let attrs = OpTrapGroupSetDoReply::new(buf);

// No attributes
```

## Low-level decoding

### Do (request)

```rust
let iter = OpTrapGroupSetDoRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    TrapGroupName(val) => {}, // &CStr

    // Associated type: "TrapAction" (enum)
    TrapAction(val) => {}, // u8
    TrapPolicerId(val) => {}, // u32
  }
}
```

### Do (reply)

```rust
let iter = OpTrapGroupSetDoReply::new(buf);
// No attributes
```

# Operation "trap-policer-get"

## Do (request)

```rust
PushOpTrapPolicerGetDoRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_trap_policer_id(val) // u32
  ;
```

```rust
let attrs = OpTrapPolicerGetDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_trap_policer_id(); // u32
```

### Do (reply)

```rust
PushOpTrapPolicerGetDoReply::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_trap_policer_id(val) // u32
  ;
```

```rust
let attrs = OpTrapPolicerGetDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_trap_policer_id(); // u32
```

## Low-level decoding

### Do (request)

```rust
let iter = OpTrapPolicerGetDoRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    TrapPolicerId(val) => {}, // u32
  }
}
```

### Do (reply)

```rust
let iter = OpTrapPolicerGetDoReply::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    TrapPolicerId(val) => {}, // u32
  }
}
```

## Dump (request)

```rust
PushOpTrapPolicerGetDumpRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  ;
```

```rust
let attrs = OpTrapPolicerGetDumpReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_trap_policer_id(); // u32
```

### Dump (reply)

```rust
PushOpTrapPolicerGetDumpReply::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_trap_policer_id(val) // u32
  ;
```

```rust
let attrs = OpTrapPolicerGetDumpReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_trap_policer_id(); // u32
```

## Low-level decoding

### Dump (request)

```rust
let iter = OpTrapPolicerGetDumpRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
  }
}
```

### Dump (reply)

```rust
let iter = OpTrapPolicerGetDumpReply::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    TrapPolicerId(val) => {}, // u32
  }
}
```

# Operation "trap-policer-set"

## Do (request)

```rust
PushOpTrapPolicerSetDoRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_trap_policer_id(val) // u32
  .push_trap_policer_rate(val) // u64
  .push_trap_policer_burst(val) // u64
  ;
```

```rust
let attrs = OpTrapPolicerSetDoReply::new(buf);

// No attributes
```

### Do (reply)

```rust
PushOpTrapPolicerSetDoReply::new(&mut vec)
  ;
```

```rust
let attrs = OpTrapPolicerSetDoReply::new(buf);

// No attributes
```

## Low-level decoding

### Do (request)

```rust
let iter = OpTrapPolicerSetDoRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    TrapPolicerId(val) => {}, // u32
    TrapPolicerRate(val) => {}, // u64
    TrapPolicerBurst(val) => {}, // u64
  }
}
```

### Do (reply)

```rust
let iter = OpTrapPolicerSetDoReply::new(buf);
// No attributes
```

# Operation "health-reporter-test"

## Do (request)

```rust
PushOpHealthReporterTestDoRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_port_index(val) // u32
  .push_health_reporter_name(val) // &CStr
  .push_health_reporter_name_bytes(val) // &[u8]
  ;
```

```rust
let attrs = OpHealthReporterTestDoReply::new(buf);

// No attributes
```

### Do (reply)

```rust
PushOpHealthReporterTestDoReply::new(&mut vec)
  ;
```

```rust
let attrs = OpHealthReporterTestDoReply::new(buf);

// No attributes
```

## Low-level decoding

### Do (request)

```rust
let iter = OpHealthReporterTestDoRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    PortIndex(val) => {}, // u32
    HealthReporterName(val) => {}, // &CStr
  }
}
```

### Do (reply)

```rust
let iter = OpHealthReporterTestDoReply::new(buf);
// No attributes
```

# Operation "rate-get"

## Do (request)

```rust
PushOpRateGetDoRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_port_index(val) // u32
  .push_rate_node_name(val) // &CStr
  .push_rate_node_name_bytes(val) // &[u8]
  ;
```

```rust
let attrs = OpRateGetDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_port_index(); // u32
attrs.get_rate_node_name(); // &CStr
```

### Do (reply)

```rust
PushOpRateGetDoReply::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_port_index(val) // u32
  .push_rate_node_name(val) // &CStr
  .push_rate_node_name_bytes(val) // &[u8]
  ;
```

```rust
let attrs = OpRateGetDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_port_index(); // u32
attrs.get_rate_node_name(); // &CStr
```

## Low-level decoding

### Do (request)

```rust
let iter = OpRateGetDoRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    PortIndex(val) => {}, // u32
    RateNodeName(val) => {}, // &CStr
  }
}
```

### Do (reply)

```rust
let iter = OpRateGetDoReply::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    PortIndex(val) => {}, // u32
    RateNodeName(val) => {}, // &CStr
  }
}
```

## Dump (request)

```rust
PushOpRateGetDumpRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  ;
```

```rust
let attrs = OpRateGetDumpReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_port_index(); // u32
attrs.get_rate_node_name(); // &CStr
```

### Dump (reply)

```rust
PushOpRateGetDumpReply::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_port_index(val) // u32
  .push_rate_node_name(val) // &CStr
  .push_rate_node_name_bytes(val) // &[u8]
  ;
```

```rust
let attrs = OpRateGetDumpReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_port_index(); // u32
attrs.get_rate_node_name(); // &CStr
```

## Low-level decoding

### Dump (request)

```rust
let iter = OpRateGetDumpRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
  }
}
```

### Dump (reply)

```rust
let iter = OpRateGetDumpReply::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    PortIndex(val) => {}, // u32
    RateNodeName(val) => {}, // &CStr
  }
}
```

# Operation "rate-set"

## Do (request)

```rust
PushOpRateSetDoRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_rate_node_name(val) // &CStr
  .push_rate_node_name_bytes(val) // &[u8]
  .push_rate_tx_share(val) // u64
  .push_rate_tx_max(val) // u64
  .push_rate_tx_priority(val) // u32
  .push_rate_tx_weight(val) // u32
  .push_rate_parent_node_name(val) // &CStr
  .push_rate_parent_node_name_bytes(val) // &[u8]

  // Attribute may repeat multiple times (treat it as array)
  .nested_rate_tc_bws()
    .push_index(val) // u8

    // Specifies the bandwidth share assigned to the Traffic Class.
    // The bandwidth for the traffic class is determined
    // in proportion to the sum of the shares of all configured classes.
    .push_bw(val) // u32
  .end_nested()
  ;
```

```rust
let attrs = OpRateSetDoReply::new(buf);

// No attributes
```

### Do (reply)

```rust
PushOpRateSetDoReply::new(&mut vec)
  ;
```

```rust
let attrs = OpRateSetDoReply::new(buf);

// No attributes
```

## Low-level decoding

### Do (request)

```rust
let iter = OpRateSetDoRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    RateNodeName(val) => {}, // &CStr
    RateTxShare(val) => {}, // u64
    RateTxMax(val) => {}, // u64
    RateTxPriority(val) => {}, // u32
    RateTxWeight(val) => {}, // u32
    RateParentNodeName(val) => {}, // &CStr

    // Attribute may repeat multiple times (treat it as array)
    RateTcBws(iter) => {
      for attr in iter {
        match attr {
          Index(val) => {}, // u8

          // Specifies the bandwidth share assigned to the Traffic Class.
          // The bandwidth for the traffic class is determined
          // in proportion to the sum of the shares of all configured classes.
          Bw(val) => {}, // u32
        }
      }
    },
  }
}
```

### Do (reply)

```rust
let iter = OpRateSetDoReply::new(buf);
// No attributes
```

# Operation "rate-new"

## Do (request)

```rust
PushOpRateNewDoRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_rate_node_name(val) // &CStr
  .push_rate_node_name_bytes(val) // &[u8]
  .push_rate_tx_share(val) // u64
  .push_rate_tx_max(val) // u64
  .push_rate_tx_priority(val) // u32
  .push_rate_tx_weight(val) // u32
  .push_rate_parent_node_name(val) // &CStr
  .push_rate_parent_node_name_bytes(val) // &[u8]

  // Attribute may repeat multiple times (treat it as array)
  .nested_rate_tc_bws()
    .push_index(val) // u8

    // Specifies the bandwidth share assigned to the Traffic Class.
    // The bandwidth for the traffic class is determined
    // in proportion to the sum of the shares of all configured classes.
    .push_bw(val) // u32
  .end_nested()
  ;
```

```rust
let attrs = OpRateNewDoReply::new(buf);

// No attributes
```

### Do (reply)

```rust
PushOpRateNewDoReply::new(&mut vec)
  ;
```

```rust
let attrs = OpRateNewDoReply::new(buf);

// No attributes
```

## Low-level decoding

### Do (request)

```rust
let iter = OpRateNewDoRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    RateNodeName(val) => {}, // &CStr
    RateTxShare(val) => {}, // u64
    RateTxMax(val) => {}, // u64
    RateTxPriority(val) => {}, // u32
    RateTxWeight(val) => {}, // u32
    RateParentNodeName(val) => {}, // &CStr

    // Attribute may repeat multiple times (treat it as array)
    RateTcBws(iter) => {
      for attr in iter {
        match attr {
          Index(val) => {}, // u8

          // Specifies the bandwidth share assigned to the Traffic Class.
          // The bandwidth for the traffic class is determined
          // in proportion to the sum of the shares of all configured classes.
          Bw(val) => {}, // u32
        }
      }
    },
  }
}
```

### Do (reply)

```rust
let iter = OpRateNewDoReply::new(buf);
// No attributes
```

# Operation "rate-del"

## Do (request)

```rust
PushOpRateDelDoRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_rate_node_name(val) // &CStr
  .push_rate_node_name_bytes(val) // &[u8]
  ;
```

```rust
let attrs = OpRateDelDoReply::new(buf);

// No attributes
```

### Do (reply)

```rust
PushOpRateDelDoReply::new(&mut vec)
  ;
```

```rust
let attrs = OpRateDelDoReply::new(buf);

// No attributes
```

## Low-level decoding

### Do (request)

```rust
let iter = OpRateDelDoRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    RateNodeName(val) => {}, // &CStr
  }
}
```

### Do (reply)

```rust
let iter = OpRateDelDoReply::new(buf);
// No attributes
```

# Operation "linecard-get"

## Do (request)

```rust
PushOpLinecardGetDoRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_linecard_index(val) // u32
  ;
```

```rust
let attrs = OpLinecardGetDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_linecard_index(); // u32
```

### Do (reply)

```rust
PushOpLinecardGetDoReply::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_linecard_index(val) // u32
  ;
```

```rust
let attrs = OpLinecardGetDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_linecard_index(); // u32
```

## Low-level decoding

### Do (request)

```rust
let iter = OpLinecardGetDoRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    LinecardIndex(val) => {}, // u32
  }
}
```

### Do (reply)

```rust
let iter = OpLinecardGetDoReply::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    LinecardIndex(val) => {}, // u32
  }
}
```

## Dump (request)

```rust
PushOpLinecardGetDumpRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  ;
```

```rust
let attrs = OpLinecardGetDumpReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_linecard_index(); // u32
```

### Dump (reply)

```rust
PushOpLinecardGetDumpReply::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_linecard_index(val) // u32
  ;
```

```rust
let attrs = OpLinecardGetDumpReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_linecard_index(); // u32
```

## Low-level decoding

### Dump (request)

```rust
let iter = OpLinecardGetDumpRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
  }
}
```

### Dump (reply)

```rust
let iter = OpLinecardGetDumpReply::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    LinecardIndex(val) => {}, // u32
  }
}
```

# Operation "linecard-set"

## Do (request)

```rust
PushOpLinecardSetDoRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_linecard_index(val) // u32
  .push_linecard_type(val) // &CStr
  .push_linecard_type_bytes(val) // &[u8]
  ;
```

```rust
let attrs = OpLinecardSetDoReply::new(buf);

// No attributes
```

### Do (reply)

```rust
PushOpLinecardSetDoReply::new(&mut vec)
  ;
```

```rust
let attrs = OpLinecardSetDoReply::new(buf);

// No attributes
```

## Low-level decoding

### Do (request)

```rust
let iter = OpLinecardSetDoRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    LinecardIndex(val) => {}, // u32
    LinecardType(val) => {}, // &CStr
  }
}
```

### Do (reply)

```rust
let iter = OpLinecardSetDoReply::new(buf);
// No attributes
```

# Operation "selftests-get"

## Do (request)

```rust
PushOpSelftestsGetDoRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  ;
```

```rust
let attrs = OpSelftestsGetDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
```

### Do (reply)

```rust
PushOpSelftestsGetDoReply::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  ;
```

```rust
let attrs = OpSelftestsGetDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
```

## Low-level decoding

### Do (request)

```rust
let iter = OpSelftestsGetDoRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
  }
}
```

### Do (reply)

```rust
let iter = OpSelftestsGetDoReply::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
  }
}
```

## Dump (request)

```rust
PushOpSelftestsGetDumpRequest::new(&mut vec)
  ;
```

```rust
let attrs = OpSelftestsGetDumpReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
```

### Dump (reply)

```rust
PushOpSelftestsGetDumpReply::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  ;
```

```rust
let attrs = OpSelftestsGetDumpReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
```

## Low-level decoding

### Dump (request)

```rust
let iter = OpSelftestsGetDumpRequest::new(buf);
// No attributes
```

### Dump (reply)

```rust
let iter = OpSelftestsGetDumpReply::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
  }
}
```

# Operation "selftests-run"

## Do (request)

```rust
PushOpSelftestsRunDoRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .nested_selftests()
    .push_flash(val) // ()
  .end_nested()
  ;
```

```rust
let attrs = OpSelftestsRunDoReply::new(buf);

// No attributes
```

### Do (reply)

```rust
PushOpSelftestsRunDoReply::new(&mut vec)
  ;
```

```rust
let attrs = OpSelftestsRunDoReply::new(buf);

// No attributes
```

## Low-level decoding

### Do (request)

```rust
let iter = OpSelftestsRunDoRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    Selftests(iter) => {
      for attr in iter {
        match attr {
          Flash(val) => {}, // ()
        }
      }
    },
  }
}
```

### Do (reply)

```rust
let iter = OpSelftestsRunDoReply::new(buf);
// No attributes
```

# Operation "notify-filter-set"

## Do (request)

```rust
PushOpNotifyFilterSetDoRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  .push_port_index(val) // u32
  ;
```

```rust
let attrs = OpNotifyFilterSetDoReply::new(buf);

// No attributes
```

### Do (reply)

```rust
PushOpNotifyFilterSetDoReply::new(&mut vec)
  ;
```

```rust
let attrs = OpNotifyFilterSetDoReply::new(buf);

// No attributes
```

## Low-level decoding

### Do (request)

```rust
let iter = OpNotifyFilterSetDoRequest::new(buf);
for attr in iter {
  match attr {
    BusName(val) => {}, // &CStr
    DevName(val) => {}, // &CStr
    PortIndex(val) => {}, // u32
  }
}
```

### Do (reply)

```rust
let iter = OpNotifyFilterSetDoReply::new(buf);
// No attributes
```

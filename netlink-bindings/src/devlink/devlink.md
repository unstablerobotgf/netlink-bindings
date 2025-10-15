
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

### Do (reply)

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

## Dump (request)

```rust
PushOpGetDumpRequest::new(&mut vec)
  ;
```

### Dump (reply)

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

### Do (reply)

```rust
let attrs = OpPortGetDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_port_index(); // u32
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

### Dump (reply)

```rust
let attrs = OpPortGetDumpReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_port_index(); // u32
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

### Do (reply)

```rust
let attrs = OpPortSetDoReply::new(buf);

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

### Do (reply)

```rust
let attrs = OpPortNewDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_port_index(); // u32
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

### Do (reply)

```rust
let attrs = OpPortDelDoReply::new(buf);

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

### Do (reply)

```rust
let attrs = OpPortSplitDoReply::new(buf);

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

### Do (reply)

```rust
let attrs = OpPortUnsplitDoReply::new(buf);

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

### Do (reply)

```rust
let attrs = OpSbGetDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_sb_index(); // u32
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

### Dump (reply)

```rust
let attrs = OpSbGetDumpReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_sb_index(); // u32
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

### Do (reply)

```rust
let attrs = OpSbPoolGetDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_sb_index(); // u32
attrs.get_sb_pool_index(); // u16
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

### Dump (reply)

```rust
let attrs = OpSbPoolGetDumpReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_sb_index(); // u32
attrs.get_sb_pool_index(); // u16
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

### Do (reply)

```rust
let attrs = OpSbPoolSetDoReply::new(buf);

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

### Do (reply)

```rust
let attrs = OpSbPortPoolGetDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_port_index(); // u32
attrs.get_sb_index(); // u32
attrs.get_sb_pool_index(); // u16
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

### Dump (reply)

```rust
let attrs = OpSbPortPoolGetDumpReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_port_index(); // u32
attrs.get_sb_index(); // u32
attrs.get_sb_pool_index(); // u16
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

### Do (reply)

```rust
let attrs = OpSbPortPoolSetDoReply::new(buf);

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

### Do (reply)

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

## Dump (request)

```rust
PushOpSbTcPoolBindGetDumpRequest::new(&mut vec)
  .push_bus_name(val) // &CStr
  .push_bus_name_bytes(val) // &[u8]
  .push_dev_name(val) // &CStr
  .push_dev_name_bytes(val) // &[u8]
  ;
```

### Dump (reply)

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

### Do (reply)

```rust
let attrs = OpSbTcPoolBindSetDoReply::new(buf);

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

### Do (reply)

```rust
let attrs = OpSbOccSnapshotDoReply::new(buf);

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

### Do (reply)

```rust
let attrs = OpSbOccMaxClearDoReply::new(buf);

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

### Do (reply)

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

### Do (reply)

```rust
let attrs = OpEswitchSetDoReply::new(buf);

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

### Do (reply)

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

### Do (reply)

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

### Do (reply)

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

### Do (reply)

```rust
let attrs = OpDpipeTableCountersSetDoReply::new(buf);

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

### Do (reply)

```rust
let attrs = OpResourceSetDoReply::new(buf);

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

### Do (reply)

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

### Do (reply)

```rust
let attrs = OpReloadDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr

// Associated type: "ReloadAction" (1 bit per enumeration)
attrs.get_reload_actions_performed(); // PushBuiltinBitfield32
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

### Do (reply)

```rust
let attrs = OpParamGetDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_param_name(); // &CStr
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

### Dump (reply)

```rust
let attrs = OpParamGetDumpReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_param_name(); // &CStr
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

### Do (reply)

```rust
let attrs = OpParamSetDoReply::new(buf);

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

### Do (reply)

```rust
let attrs = OpRegionGetDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_port_index(); // u32
attrs.get_region_name(); // &CStr
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

### Dump (reply)

```rust
let attrs = OpRegionGetDumpReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_port_index(); // u32
attrs.get_region_name(); // &CStr
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

### Do (reply)

```rust
let attrs = OpRegionNewDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_port_index(); // u32
attrs.get_region_name(); // &CStr
attrs.get_region_snapshot_id(); // u32
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

### Do (reply)

```rust
let attrs = OpRegionDelDoReply::new(buf);

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

### Dump (reply)

```rust
let attrs = OpRegionReadDumpReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_port_index(); // u32
attrs.get_region_name(); // &CStr
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

### Do (reply)

```rust
let attrs = OpPortParamGetDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_port_index(); // u32
```

## Dump (request)

```rust
PushOpPortParamGetDumpRequest::new(&mut vec)
  ;
```

### Dump (reply)

```rust
let attrs = OpPortParamGetDumpReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_port_index(); // u32
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

### Do (reply)

```rust
let attrs = OpPortParamSetDoReply::new(buf);

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

### Do (reply)

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

## Dump (request)

```rust
PushOpInfoGetDumpRequest::new(&mut vec)
  ;
```

### Dump (reply)

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

### Do (reply)

```rust
let attrs = OpHealthReporterGetDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_port_index(); // u32
attrs.get_health_reporter_name(); // &CStr
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

### Dump (reply)

```rust
let attrs = OpHealthReporterGetDumpReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_port_index(); // u32
attrs.get_health_reporter_name(); // &CStr
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

### Do (reply)

```rust
let attrs = OpHealthReporterSetDoReply::new(buf);

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

### Do (reply)

```rust
let attrs = OpHealthReporterRecoverDoReply::new(buf);

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

### Do (reply)

```rust
let attrs = OpHealthReporterDiagnoseDoReply::new(buf);

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

### Dump (reply)

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

### Do (reply)

```rust
let attrs = OpHealthReporterDumpClearDoReply::new(buf);

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

### Do (reply)

```rust
let attrs = OpFlashUpdateDoReply::new(buf);

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

### Do (reply)

```rust
let attrs = OpTrapGetDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_trap_name(); // &CStr
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

### Dump (reply)

```rust
let attrs = OpTrapGetDumpReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_trap_name(); // &CStr
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

### Do (reply)

```rust
let attrs = OpTrapSetDoReply::new(buf);

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

### Do (reply)

```rust
let attrs = OpTrapGroupGetDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_trap_group_name(); // &CStr
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

### Dump (reply)

```rust
let attrs = OpTrapGroupGetDumpReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_trap_group_name(); // &CStr
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

### Do (reply)

```rust
let attrs = OpTrapGroupSetDoReply::new(buf);

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

### Do (reply)

```rust
let attrs = OpTrapPolicerGetDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_trap_policer_id(); // u32
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

### Dump (reply)

```rust
let attrs = OpTrapPolicerGetDumpReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_trap_policer_id(); // u32
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

### Do (reply)

```rust
let attrs = OpTrapPolicerSetDoReply::new(buf);

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

### Do (reply)

```rust
let attrs = OpHealthReporterTestDoReply::new(buf);

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

### Do (reply)

```rust
let attrs = OpRateGetDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_port_index(); // u32
attrs.get_rate_node_name(); // &CStr
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

### Dump (reply)

```rust
let attrs = OpRateGetDumpReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_port_index(); // u32
attrs.get_rate_node_name(); // &CStr
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

### Do (reply)

```rust
let attrs = OpRateSetDoReply::new(buf);

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

### Do (reply)

```rust
let attrs = OpRateNewDoReply::new(buf);

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

### Do (reply)

```rust
let attrs = OpRateDelDoReply::new(buf);

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

### Do (reply)

```rust
let attrs = OpLinecardGetDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_linecard_index(); // u32
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

### Dump (reply)

```rust
let attrs = OpLinecardGetDumpReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
attrs.get_linecard_index(); // u32
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

### Do (reply)

```rust
let attrs = OpLinecardSetDoReply::new(buf);

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

### Do (reply)

```rust
let attrs = OpSelftestsGetDoReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
```

## Dump (request)

```rust
PushOpSelftestsGetDumpRequest::new(&mut vec)
  ;
```

### Dump (reply)

```rust
let attrs = OpSelftestsGetDumpReply::new(buf);

attrs.get_bus_name(); // &CStr
attrs.get_dev_name(); // &CStr
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

### Do (reply)

```rust
let attrs = OpSelftestsRunDoReply::new(buf);

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

### Do (reply)

```rust
let attrs = OpNotifyFilterSetDoReply::new(buf);

// No attributes
```

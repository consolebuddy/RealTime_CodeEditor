### About

We've developed a Realtime Code Editor that supports collaborative coding, allowing multiple users to work together on the same code. The editor includes syntax highlighting capabilities.

Tech Used:  React.js, Node.js, Express.js, CodeMirror, Socket.io, Websockets, CSS, HTML, Javascript

graph TD
  subgraph Seeds (raw CSVs loaded by `dbt seed`)
    FB[src_ads_creative_facebook_all_data]
    TT[src_ads_tiktok_ads_all_data]
    TW[src_promoted_tweets_twitter_all_data]
    BG[src_ads_bing_all_data]
  end

  subgraph dbt Staging (rename, types, units)
    STG_FB[stg_facebook]
    STG_TT[stg_tiktok]
    STG_TW[stg_twitter]
    STG_BG[stg_bing]
  end

  subgraph dbt Marts (MCDM)
    FACT[ads_basic_performance]
  end

  subgraph BI
    DASH[Looker Studio: Ads Performance]
  end

  FB --> STG_FB
  TT --> STG_TT
  TW --> STG_TW
  BG --> STG_BG

  STG_FB --> FACT
  STG_TT --> FACT
  STG_TW --> FACT
  STG_BG --> FACT

  FACT --> DASH

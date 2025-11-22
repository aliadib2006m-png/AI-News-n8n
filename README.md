ass = 'very_high_risk';\n      tradingCondition = 'high_risk';\n    } else if (forecastActualRatio > 0.25) {\n      anomalyClass = 'high_risk';\n      tradingCondition = 'risky';\n    } else if (forecastActualRatio > 0.1) {\n      anomalyClass = 'medium_risk';\n    } else {\n      anomalyClass = 'low_risk';\n    }\n  }\n\n  return {\n    title: j.title || null,\n    country: j.country || null,\n    currency: j.currency || null,\n    date_time: j.date || j.date_time || null,\n    impact: j.impact || null,\n\n    previous: prev,\n    forecast: fcst,\n    actual: act,\n\n    prev_forecast_change_ratio: prevForecastRatio,\n    forecast_actual_diff_ratio: forecastActualRatio,\n\n    forecast_reliability: forecastReliability,  // very_stable / stable / volatile / very_volatile / unknown\n    trading_condition: tradingCondition,        // good_opportunity / risky / high_risk / unknown\n    anomaly_class: anomalyClass                 // low_risk / medium_risk / high_risk / very_high_risk / unknown\n  };\n});\n\n// اگر امروز هیچ خبر High Impact نداشتیم\nif (events.length === 0) {\n  return [\n    {\n      json: {\n        has_high_impact_news_today: false,\n        message: 'No high-impact news today.',\n        news: []\n      }\n    }\n  ];\n}\n\n// اگر خبر داریم\nreturn [\n  {\n    json: {\n      has_high_impact_news_today: true,\n      news: events\n    }\n  }\n];"
      },
      "type": "n8n-nodes-base.code",
      "typeVersion": 2,
      "position": [
        512,
        208
      ],
      "id": "40f2215f-bb32-4fee-b5e5-d00f0f9357b4",
      "name": "Prepare News"
    }
  ],
  "pinData": {},
  "connections": {
    "Schedule Trigger": {
      "main": [
        [
          {
            "node": "Get FF Calendar",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "Get FF Calendar": {
      "main": [
        [
          {
            "node": "Filter High Impact",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "Filter High Impact": {
      "main": [
        [
          {
            "node": "Prepare News",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "Message a model": {
      "main": [
        [
          {
            "node": "Send a message",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "Prepare News": {
      "main": [
        [
          {
            "node": "Message a model",
            "type": "main",
            "index": 0
          }
        ]
      ]
    }
  },
  "active": false,
  "settings": {
    "executionOrder": "v1"
  },
  "versionId": "b94f065d-f4aa-471f-96d5-27b6afa2da51",
  "meta": {
    "templateCredsSetupCompleted": true,
    "instanceId": "d294b4b29df618dbbbdb17e17062ea032538c8fa577c4b7cfe0a276df332872f"
  },
  "id": "mTJXPFqxHxL8bBc1",
  "tags": [
    {
      "createdAt": "2025-11-13T09:26:54.897Z",
      "updatedAt": "2025-11-13T09:26:54.897Z",
      "id": "YDfejNgiUvgyNWe2",
      "name": "AI News"
    }
  ]
}

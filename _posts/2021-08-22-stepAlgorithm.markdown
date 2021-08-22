---
layout: post
title:  "한글 Post Test"
date:   2021-08-22 19:03:36
categories: SWIFT iOS
---
한글 폰트와 포스트 방식 테스트중입니다
알고리즘 공부와 개발 진행 상황에 대해 포스트 해보려고합니다.

Notion과 github.io 둘중 한가지가 될것 같습니다.

```Exemple1
Swift
스텝 알고리즘 
1 Step = 1 Point, 하루 최대 1만P 가능, 1,3,5회에 보너스 1만P
func solution3(_ stepCounts: [Int]) -> Int {
    
    let maxCount = (stepCounts.filter { $0 > 10000 }).count // 일일 1만보 초과 수
    let normalPoint = (stepCounts.filter { $0 < 10000 }).reduce(0) { $0 + $1 } // 1만보 미만 포인트 합
    let walkPoint = (maxCount * 10000) + normalPoint // (상한포인트 * 도달수) + 만보 미만 포인트 합
    
    var totalPoint: Int // 보너스 포인트 + 순수 획득 포인트

    // 보너스 포인트 부여
    if maxCount <= 5 && maxCount % 2 == 1 {
       totalPoint = walkPoint + (((maxCount / 2) + (maxCount % 2)) * 10000 )
    } else {
        totalPoint = walkPoint + 30000
    }
    return totalPoint
}
```


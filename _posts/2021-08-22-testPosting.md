---
layout: post
title:  "한글 Post Test"
date:   2021-08-23 23:15:23
categories: SWIFT iOS
---
2차 테스트

```Exemple2
Swift
다익스트라 
모든 노드가 서로 연결된 (닫힌구조) 다중망 다익스트라

// 배열구현 N개의 마을, 양방향도로(:2차원 배열 1번 마을에서 2번마을, 4번마을 식으로 가기 때문에), 거리 k
func solution(_ N:Int, _ road: [[Int]], _ k:Int) -> Int { //거리가 k이하인 마을 '개수' 니 ㅑㅜㅅ로 반환
    // 1차원 배열 초기화.첫번째 마을로부터 최단거리를 갱신할 배열. 최대값으로 초기화
    var distanceFrom1stNode = [Int](repeating: Int.max, count: N + 1)
    // 2차원 배열, 그래프화
    // 해당 배열의 값이 0인경우 경로가 존재하지 않는 것
    var graph = [[Int]](repeating: [Int](repeating: 0, count: N + 1), count: N + 1)

    for data in road {
        let from = data[0]
        let to =  data[1]
        let cost = data[2]

        //자기 자신 거리 제외
        if graph[from][to] == 0 {
            graph[from][to] = cost
            graph[to][from] = cost
        } else {
            // 닫힌구조이므로 한 마을에서 다른마을까지의 가는 방법은 여러가지
            // 최단거리만을 판단하면 되기 때문에 소요시간이 가장 짧은 값으로 갱신함

            if cost < graph[from][to] {
                graph[from][to] = cost
                graph[to][from] = cost

            }
        }
    }

    // 배열 완료

    // 다익스트라 함수
    func dijkstra(start: Int) {
        var queue = [(Int, Int)]()
        //시작점 거리 초기화 0

        distanceFrom1stNode[start] = 0

        queue.append((1, distanceFrom1stNode[1]))

        while !queue.isEmpty {
            let current = queue.first!.0
            let cost = queue.first!.1
            queue.removeFirst()

            for next in 1...N {
                // 경로가 있고, 더 짧은 코트스 일 경우 배열을 갱신
                if graph[current][cost] != 0 && cost + graph[current][next] < distanceFrom1stNode[next] {
                    distanceFrom1stNode[next] = cost + graph[current][next]
                    queue.append((next, distanceFrom1stNode[next]))
                }
            }
        }
    }

    dijkstra(start: 1)

    return distanceFrom1stNode.filter{$0 <= k}.count
}

var v = [[Int]](repeating: Array(repeating: 2, count: 2), count: 2)

v[[1][0]]

func solution(_ v:[[Int]]) -> [Int] {

    var x: Int
    var y: Int

    if v[0][0] == v[0][2] {
        x = v[1][0]
    } else if v[1][0]==v[2][0]{
        x = v[0][0]
    } else {
        x = v[2][0]
    }

    if v[0][1] == v[1][1] {
        y = v[2][1]
    } else if v[1][1] == v[2][1] {
        y = v[0][1]
    } else {
        y = v[1][1]
    }

    var ans = [Int]()
    return ans([[x, y]])
}
```


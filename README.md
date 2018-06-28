LineStructures
===


## Description
Unityで線分・直線・半直線を扱うための構造体を提供するライブラリです。

現状は2Dのみ対応しています。  

## Usage
線分の構造体は`LineSegment`、直線の構造体は`StraightLine`、半直線の構造体は`HalfStraightLine`という構造体名で提供されています。

サンプルコード
```` csharp
void Start()
{
    // 原点から(10, 10)までの線分.
    var segment = new LineSegment(Vector2.zero, Vector2.one * 10f);

    // (0, -10)を通り、(0, 1)の方向ベクトルを持つ直線.
    var straight = new StraightLine(new Vector2(0f, -10f), Vector2.up);

    // (-10, 0)を始点に、(1, 0)方向に伸びる半直線.
    var half = new HalfStraightLine(new Vector2(-10f, 0f), Vector2.right);

    // (0, 10)から線分までの最短距離 -> 7.071068
    Debug.Log(Lines.GetDistance(segment, new Vector2(0f, 10f)));
    // 直線と半直線が交差しているか判定 -> true
    Debug.Log(Lines.IsCrossing(straight, half));
    // 直線と半直線の交点座標 -> (0, 0)
    Debug.Log(Lines.GetIntersection(straight, half));
}
````
より詳しい使い方は[Examples](Assets/LineStructures/Examples/)を参照してください。

## Behaviour
- 3つの構造体は`ILine`というインターフェースを実装しています。
- `Lines`クラスによって、ある点からの距離や、交差判定、交点座標などを取得することができます。
    - 交点座標計算においては、交差しているかのチェックは行っていません。交差している前提で計算を行っています。
- 各構造体は`DrawGizmos`メソッドによって、現状の設定をGizmosで表示させることができます。

## Screenshots
![screen shot](./Docs/Screenshot.png)

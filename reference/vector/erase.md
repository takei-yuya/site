# erase
* vector[meta header]
* std[meta namespace]
* vector[meta class]
* function[meta id-type]

```cpp
iterator erase(iterator position);       // (1) C++03
iterator erase(const_iterator position); // (2) C++11

iterator erase(iterator first, iterator last);             // (2) C++03
iterator erase(const_iterator first, const_iterator last); // (2) C++11
```

## 概要
指定した要素を削除する。


## 要件
- `T`はMoveAssignableでなければならない。


## 効果
- (1) : `position`が指す要素が削除される。
- (2) : `[first, last)`で示される範囲の要素が削除される。

削除された要素またはそれ以降の要素を指すイテレータや参照は無効になる。


## 戻り値
削除された要素の次の要素を指すイテレータを返す。そのような要素が存在しない場合は、[`end()`](end.md)を返す。さらに、削除された要素以降の要素の数と同じ回数の`T`のムーブ代入演算子が呼ばれる。


## 計算量
削除される要素の数と同じ回数の`T`のデストラクタが実行される。


## 備考
コピーコンストラクタ、ムーブコンストラクタ、代入演算子、ムーブ代入演算子が例外を投げる場合を除いて、この関数は例外を投げない。

## 例
```cpp
#include <iostream>
#include <vector>

int main ()
{
  unsigned int i;
  std::vector<unsigned int> myvector;

  // set some values (from 1 to 10)
  for (i=1; i<=10; i++) myvector.push_back(i);
  
  // erase the 6th element
  myvector.erase(myvector.begin()+5);

  // erase the first 3 elements:
  myvector.erase(myvector.begin(),myvector.begin()+3);

  std::cout << "myvector contains:";
  for (i=0; i<myvector.size(); i++)
    std::cout << " " << myvector[i];
  std::cout << std::endl;

  return 0;
}
```

### 出力
```
myvector contains: 4 5 7 8 9 10 
```


## 参照
- [N2350 Container insert/erase and iterator constness (Revision 1)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2350.pdf)


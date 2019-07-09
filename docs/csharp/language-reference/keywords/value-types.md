---
title: Değer türleri - C# başvurusu
ms.custom: seodec18
ms.date: 11/26/2018
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
ms.openlocfilehash: fd865f2a9c4a6d2c17f79a21866103a2db982e5f
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661584"
---
# <a name="value-types-c-reference"></a>Değer türleri (C# Başvurusu)

Değer türlerinin iki tür vardır:

- [Yapılar](struct.md)

- [Sabit Listeleri](enum.md)

## <a name="main-features-of-value-types"></a>Değer türleri'larının temel özellikleri

Bir değer türünde bir değişken türünde bir değer içerir. Örneğin, bir değişken `int` türü, değer içerebilir `42`. Bu, bir başvuru türü olarak da bilinen bir nesne örneği içeren bir başvuru türünün bir değişkeni farklıdır. Bu değer, bir değişkene bir değer türü yeni bir değer atadığınızda, kopyalanır. Başvuru türünde bir değişken için yeni bir değer atadığınızda, başvuru kopyalanır, nesnenin kendisini değil.

Tüm değer türleri örtülü olarak türetilmiş <xref:System.ValueType?displayProperty=nameWithType>.

Farklı başvuru türleri ile yeni bir tür bir değer türünden türetilemez. Ancak, başvuru türleri, ister yapılar, arabirimler uygulayabilirsiniz.

Değer türü değişkenler olamaz `null` varsayılan olarak. Ancak, karşılık gelen değişkenleri [boş değer atanabilir türler](../../../csharp/programming-guide/nullable-types/index.md) olabilir `null`.

Varsayılan değer türü başlatan örtük parametresiz bir oluşturucu her değer türünde. Değer türleri varsayılan değerler hakkında daha fazla bilgi için bkz. [varsayılan değerler tablosu](default-values-table.md).

## <a name="simple-types"></a>Basit türler

*Basit türler* bir dizi önceden tanımlanmış bir yapı türü tarafından sağlanan C# ve aşağıdaki türleri oluşturan:

- [Tam sayı türleri](../builtin-types/integral-numeric-types.md): tamsayı sayısal türleri ve [char](char.md) türü
- [Kayan nokta türleri](../builtin-types/floating-point-numeric-types.md)
- [bool](bool.md)

Basit türler anahtar sözcükleri tanımlanır, ancak bu anahtar sözcükler yalnızca önceden tanımlanmış bir yapı türleri için diğer adlar <xref:System> ad alanı. Örneğin, [int](../builtin-types/integral-numeric-types.md) bir diğer adıdır <xref:System.Int32?displayProperty=nameWithType>. Diğer adlar tam bir listesi için bkz. [yerleşik türler tablosu](built-in-types-table.md).

Basit türler, bazı ek işlemler izin vermek, diğer yapı türlerden farklılık gösterir:

- Basit türler, değişmez değerleri kullanılarak başlatılabilir. Örneğin, `'A'` bir sabit değer türü olan `char` ve `2001` bir sabit değer türü olan `int`.

- Sabitler ile basit türler bildirebilirsiniz [const](const.md) anahtar sözcüğü. Diğer yapı tür sabitleri mümkün değildir.

- Sabit ifadeler, işlenenleri tüm basit tür sabit değerlerdir, derleme zamanında değerlendirilir.

Daha fazla bilgi için [basit türler](~/_csharplang/spec/types.md#simple-types) bölümünü [ C# dil belirtimi](../language-specification/index.md).

## <a name="initializing-value-types"></a>Değer türleri başlatma

C# dilinde yerel değişkenler, kullanılmadan önce başlatılmalıdır. Örneğin, aşağıdaki örnekte olduğu gibi başlatma olmadan yerel bir değişken bildirmeniz:

```csharp
int myInt;
```

Bunu başlatılmadan önce kullanamazsınız. Aşağıdaki deyimi kullanarak başlatabilirsiniz:

```csharp
myInt = new int();  // Invoke parameterless constructor for int type.
```

Bu ifade, aşağıdaki deyime eşdeğerdir:

```csharp
myInt = 0;         // Assign an initial value, 0 in this example.
```

Elbette, bildirim ve başlatma aşağıdaki örneklerde gösterildiği gibi aynı deyimde olabilir:

```csharp
int myInt = new int();
```

– veya –

```csharp
int myInt = 0;
```

Kullanarak [yeni](../operators/new-operator.md) işleci belirli türün parametresiz oluşturucu çağırır ve varsayılan değer değişkenine atar. Önceki örnekte, parametresiz bir oluşturucu değer atanmış `0` için `myInt`. Varsayılan Oluşturucu çağırarak atanan değerler hakkında daha fazla bilgi için bkz: [varsayılan değerler tablosu](default-values-table.md).

Kullanıcı tanımlı türler ile kullanın [yeni](../operators/new-operator.md) parametresiz bir oluşturucu çağırmak için. Örneğin, aşağıdaki deyim, parametresiz oluşturucu çağırır `Point` yapısı:

```csharp
var p = new Point(); // Invoke parameterless constructor for the struct.
```

Bu çağrıdan sonra kesinlikle atanacak yapı olarak kabul edilir; diğer bir deyişle, tüm üyeleri varsayılan değerlerine başlatılır.

Hakkında daha fazla bilgi için `new` işleci bkz [yeni](../operators/new-operator.md).

Sayısal türlerin çıktı biçimlendirme hakkında daha fazla bilgi için bkz: [sayısal sonuçlar tablosunu biçimlendirme](formatting-numeric-results-table.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [Türler](types.md)
- [Başvuru Türleri](reference-types.md)
- [Boş değer atanabilir türler](../../programming-guide/nullable-types/index.md)

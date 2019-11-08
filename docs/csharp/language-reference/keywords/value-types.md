---
title: Değer türleri- C# başvuru
ms.custom: seodec18
ms.date: 11/26/2018
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
ms.openlocfilehash: 8703532ff8551e8bd42128eb9e8cdcf2afd9dad8
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739669"
---
# <a name="value-types-c-reference"></a>Değer türleri (C# başvuru)

İki tür değer türü vardır:

- [Yapılar](struct.md)

- [Sabit Listeleri](enum.md)

## <a name="main-features-of-value-types"></a>Değer türlerinin ana özellikleri

Değer türünde bir değişken, türün bir değerini içerir. Örneğin, `int` türünün bir değişkeni `42`değerini içerebilir. Bu, bir nesne olarak da bilinen tür örneğine başvuru içeren bir başvuru türü değişkeninden farklıdır. Değer türünde bir değişkene yeni bir değer atadığınızda, bu değer kopyalanır. Başvuru türündeki bir değişkene yeni bir değer atadığınızda, başvuru nesnenin kendisi değil, kopyalanır.

Tüm değer türleri örtük olarak <xref:System.ValueType?displayProperty=nameWithType>türetilir.

Başvuru türlerinden farklı olarak, bir değer türünden yeni bir tür türemezsiniz. Ancak, başvuru türleri gibi yapılar, arabirimler uygulayabilir.

Değer türü değişkenleri varsayılan olarak `null` olamaz. Ancak, karşılık gelen [null yapılabilir değer türlerinin](../builtin-types/nullable-value-types.md) değişkenleri `null`olabilir.

Her değer türünün, bu türün varsayılan değerini Başlatan örtük parametresiz bir Oluşturucusu vardır. Değer türlerinin varsayılan değerleri hakkında daha fazla bilgi için bkz. [varsayılan değerler tablosu](default-values-table.md).

## <a name="simple-types"></a>Basit türler

*Basit türler* tarafından C# sunulan önceden tanımlanmış bir yapı türleri kümesidir ve aşağıdaki türleri içerir:

- [Integral türleri](../builtin-types/integral-numeric-types.md): tamsayı sayısal türleri ve [char](char.md) türü
- [Kayan nokta türleri](../builtin-types/floating-point-numeric-types.md)
- [bool](bool.md)

Basit türler anahtar sözcükler aracılığıyla tanımlanır, ancak bu anahtar sözcükler yalnızca <xref:System> ad alanındaki önceden tanımlanmış yapı türleri için diğer adlardır. Örneğin, [int](../builtin-types/integral-numeric-types.md) bir <xref:System.Int32?displayProperty=nameWithType>diğer adıdır. Diğer adların tam listesi için bkz. [Yerleşik türler tablosu](built-in-types-table.md).

Basit türler, bazı ek işlemlere izin veren diğer yapı türlerinden farklıdır:

- Basit türler, değişmez değerler kullanılarak başlatılabilir. Örneğin, `'A'` türü `char` bir değişmez değerdir ve `2001` `int`türü bir değişmez değerdir.

- [Const](const.md) anahtar sözcüğüyle basit türlerin sabitlerini bildirebilirsiniz. Diğer yapı türlerinin sabitlerinin olması mümkün değildir.

- İşlenenleri hepsi basit tür sabitleri olan sabit ifadeler, derleme zamanında değerlendirilir.

Daha fazla bilgi için, [ C# dil belirtiminin](/dotnet/csharp/language-reference/language-specification/introduction) [basit türler](~/_csharplang/spec/types.md#simple-types) bölümüne bakın.

## <a name="initializing-value-types"></a>Değer türlerini başlatma

Yerel değişkenlerin kullanılmadan C# önce başlatılması gerekir. Örneğin, aşağıdaki örnekte olduğu gibi, başlatma olmadan yerel bir değişken bildirebilirsiniz:

```csharp
int myInt;
```

Bunu, başlamadan önce kullanamazsınız. Aşağıdaki ifadeyi kullanarak başlatabilirsiniz:

```csharp
myInt = new int();  // Invoke parameterless constructor for int type.
```

Bu ifade aşağıdaki ifadeye eşdeğerdir:

```csharp
myInt = 0;         // Assign an initial value, 0 in this example.
```

Tabii ki, bildirimi ve başlatmayı aşağıdaki örneklerle aynı bildirimde bulabilirsiniz:

```csharp
int myInt = new int();
```

veya

```csharp
int myInt = 0;
```

[New](../operators/new-operator.md) işlecini kullanmak, belirli türde parametresiz oluşturucuyu çağırır ve varsayılan değeri değişkenine atar. Önceki örnekte, parametresiz Oluşturucu değeri `myInt``0` atanır. Parametresiz oluşturucular çağırarak atanan değerler hakkında daha fazla bilgi için bkz. [varsayılan değerler tablosu](default-values-table.md).

Kullanıcı tanımlı türlerle, parametresiz oluşturucuyu çağırmak için [Yeni](../operators/new-operator.md) ' yi kullanın. Örneğin, aşağıdaki ifade `Point` yapısının parametresiz oluşturucusunu çağırır:

```csharp
var p = new Point(); // Invoke parameterless constructor for the struct.
```

Bu çağrıdan sonra yapının kesin olarak atanması kabul edilir; diğer bir deyişle, tüm üyeleri varsayılan değerlerine başlatılır.

`new` işleci hakkında daha fazla bilgi için, bkz. [Yeni](../operators/new-operator.md).

Sayısal türlerin çıkışını biçimlendirme hakkında daha fazla bilgi için bkz. [sayısal sonuçlar tablosunu biçimlendirme](formatting-numeric-results-table.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
- [C# anahtar sözcükleri](index.md)
- [Başvuru türleri](reference-types.md)
- [Null yapılabilir değer türleri](../builtin-types/nullable-value-types.md)

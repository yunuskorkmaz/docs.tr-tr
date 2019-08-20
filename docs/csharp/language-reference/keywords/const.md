---
title: const anahtar sözcüğü C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- const_CSharpKeyword
- const
helpviewer_keywords:
- const keyword [C#]
ms.assetid: 79eb447c-117b-4418-933f-97c50aa472db
ms.openlocfilehash: 2a2e4bb45d21708ea3971d2f5b784280b9d13d0d
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69605891"
---
# <a name="const-c-reference"></a>const (C# Başvurusu)

Sabit bir alan `const` veya sabit bir yerel değer bildirmek için anahtar sözcüğünü kullanırsınız. Sabit alanlar ve Yereller değişken değildir ve değiştirilemeyebilir. Sabitler sayı, Boole değeri, dize veya null başvuru olabilir. İstediğiniz zaman değiştirilmesini düşündüğünüz bilgileri temsil etmek için bir sabit oluşturmayın. Örneğin, bir hizmetin fiyatını, ürün sürüm numarasını veya şirketin marka adını depolamak için sabit bir alan kullanmayın. Bu değerler zaman içinde değişebilir ve derleyiciler yaydığı için, kitaplıklarınız ile derlenen diğer kodun değişiklikleri görmek için yeniden derlenmesi gerekir. Ayrıca bkz. [ReadOnly](./readonly.md) anahtar sözcüğü. Örneğin:

```csharp
const int X = 0;
public const double GravitationalConstant = 6.673e-11;
private const string ProductName = "Visual C#";
```

## <a name="remarks"></a>Açıklamalar

Sabit bir bildirimin türü, bildirimin sunmakta olduğu üyelerin türünü belirtir. Sabit bir yerel veya sabit alanın başlatıcısı, hedef türe örtük olarak dönüştürülemeyen bir sabit ifade olmalıdır.

Sabit bir ifade, derleme zamanında tam olarak değerlendirilebilen bir ifadedir. Bu nedenle, başvuru türlerinin sabitlerinin `string` tek olası değerleri ve null bir başvurudur.

Sabit bildirimi, şöyle birçok sabit bildirebilir:

```csharp
public const double X = 1.0, Y = 2.0, Z = 3.0;
```

Sabit `static` bildiriminde değiştiriciye izin verilmez.

Bir sabit, aşağıdaki gibi bir sabit ifadeye katılabilir:

```csharp
public const int C1 = 5;
public const int C2 = C1 + 100;
```

> [!NOTE]
> [ReadOnly](./readonly.md) anahtar sözcüğü `const` anahtar sözcükten farklıdır. Bir `const` alan yalnızca alanın bildiriminde başlatılabilir. Bir `readonly` alan, bildirimde ya da bir Oluşturucu içinde başlatılabilir. Bu nedenle `readonly` , alan, kullanılan oluşturucuya bağlı olarak farklı değerlere sahip olabilir. Ayrıca, `const` alan bir derleme zamanı sabiti `readonly` olsa da, bu satırda olduğu gibi çalışma zamanı sabitleri için kullanılabilir:`public static readonly uint l1 = (uint)DateTime.Now.Ticks;`

## <a name="example"></a>Örnek

[!code-csharp[csrefKeywordsModifiers#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#5)]

## <a name="example"></a>Örnek

Bu örnek, sabitlerin yerel değişkenler olarak nasıl kullanılacağını gösterir.

[!code-csharp[csrefKeywordsModifiers#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#6)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](./index.md)
- [Değiştiriciler](./modifiers.md)
- [readonly](./readonly.md)

---
title: const anahtar kelime - C# Referans
ms.date: 07/20/2015
f1_keywords:
- const_CSharpKeyword
- const
helpviewer_keywords:
- const keyword [C#]
ms.assetid: 79eb447c-117b-4418-933f-97c50aa472db
ms.openlocfilehash: 812aeb331b6dd333075d19076a896246ecc5b374
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713673"
---
# <a name="const-c-reference"></a>const (C# Başvurusu)

Anahtar kelimeyi `const` sabit bir alanı veya sabit yerel i Sabit alanlar ve yerel alanlar değişken değildir ve değiştirilmeyebilir. Sabitler sayılar, Boolean değerleri, dizeleri veya null başvuru olabilir. İstediğinuz zaman değiştirmeyi beklediğiniz bilgileri temsil etmek için sabit oluşturmayın. Örneğin, bir hizmetin fiyatını, ürün sürüm numarasını veya bir şirketin marka adını depolamak için sabit bir alan kullanmayın. Bu değerler zaman içinde değişebilir ve derleyiciler sabitleri yaydığından, kitaplıklarınızla derlenen diğer kodların değişiklikleri görmek için yeniden derlenmiş olması gerekir. Ayrıca yalnızca [okunan](./readonly.md) anahtar kelimeye de bakın. Örnek:

```csharp
const int X = 0;
public const double GravitationalConstant = 6.673e-11;
private const string ProductName = "Visual C#";
```

## <a name="remarks"></a>Açıklamalar

Sabit bir bildirimin türü, bildirimin tanıttığü üyelerin türünü belirtir. Sabit bir yerel veya sabit alanın baş harflerini, dolaylı olarak hedef türüne dönüştürülebilecek sabit bir ifade olmalıdır.

Sabit bir ifade, derleme zamanında tam olarak değerlendirilebilen bir ifadedir. Bu nedenle, başvuru türlerinin sabitleri `string` için tek olası değerler ve null başvuru vardır.

Sabit bildirim, aşağıdakiler gibi birden çok sabit bildirebilir:

```csharp
public const double X = 1.0, Y = 2.0, Z = 3.0;
```

`static` Değiştirici nin sürekli bir bildirimde yer almasına izin verilmez.

Bir sabit aşağıdaki gibi, sabit bir ifade katılabilir:

```csharp
public const int C1 = 5;
public const int C2 = C1 + 100;
```

> [!NOTE]
> [Yalnızca okunan](./readonly.md) anahtar `const` kelime, anahtar kelimeden farklıdır. Bir `const` alan yalnızca alanın bildiriminde başlatılabilir. Bir `readonly` alan, bildirimde veya bir oluşturucuda başharflere alınabilir. Bu `readonly` nedenle, alanların kullanılan oluşturucuya bağlı olarak farklı değerlere sahip olabilir. Ayrıca, bir `const` alan derleme zamanı sabiti `readonly` olmasına rağmen, alan bu satırda olduğu gibi çalışma zamanı sabitleri için kullanılabilir:`public static readonly uint l1 = (uint)DateTime.Now.Ticks;`

## <a name="example"></a>Örnek

[!code-csharp[csrefKeywordsModifiers#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#5)]

## <a name="example"></a>Örnek

Bu örnek, sabitlerin yerel değişkenler olarak nasıl kullanılacağını göstermektedir.

[!code-csharp[csrefKeywordsModifiers#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#6)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Kelimeler](./index.md)
- [Değiştiriciler](index.md)
- [Readonly](./readonly.md)

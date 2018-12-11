---
title: const anahtar sözcüğü - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- const_CSharpKeyword
- const
helpviewer_keywords:
- const keyword [C#]
ms.assetid: 79eb447c-117b-4418-933f-97c50aa472db
ms.openlocfilehash: 63fb86ed24dd4e30d3783d70e3249b9f8e5e20bd
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53245528"
---
# <a name="const-c-reference"></a>const (C# Başvurusu)

Kullandığınız `const` bir sabit alanı ya da sabit yerel bildirmek için anahtar sözcüğü. Sabit alanlar ve yerel değişkenleri değildir ve değiştirilemeyebilir. Sabitler, sayı, Boole değerleri, dize veya null başvuru olabilir. Dilediğiniz zaman değiştirin beklediğiniz bilgileri temsil eden bir sabit oluşturmayın. Örneğin, sabit bir alan bir hizmeti, bir ürün sürüm numarası veya bir şirketin marka adı fiyatı depolamak için kullanmayın. Bu değerler, zaman içinde değişebilir ve derleyiciler sabitleri yayıldığından Kitaplıklarınızı ile derlenmiş olan diğer kod değişiklikleri görmek için yeniden derlenmesi gerekir. Ayrıca bkz: [salt okunur](../../../csharp/language-reference/keywords/readonly.md) anahtar sözcüğü. Örneğin:

```csharp
const int x = 0;
public const double gravitationalConstant = 6.673e-11;
private const string productName = "Visual C#";
```

## <a name="remarks"></a>Açıklamalar

Sabit bildirimi türü bildirimin gösterdiği üyelerin türünü belirtir. Başlatıcı bir sabit yerel öğesi veya sabit alanının hedef türe örtük olarak dönüştürülebilir bir sabit ifade olmalıdır.

Sabit bir ifade derleme zamanında tam olarak değerlendirilebilecek bir ifadedir. Başvuru türü sabitleri için bu nedenle, tek olası değerler `string` ve null bir başvuru.

Sabit bildiriminde aşağıdaki gibi birden fazla sabit bildirilebilir:

```csharp
public const double x = 1.0, y = 2.0, z = 3.0;
```

`static` Değiştiricisi Sabit bildiriminde izin verilmez.

Bir sabit sabit bir ifadede gibi katılabilir:

```csharp
public const int c1 = 5;
public const int c2 = c1 + 100;
```

> [!NOTE]
> [Salt okunur](../../../csharp/language-reference/keywords/readonly.md) anahtar sözcüğünden farklıdır `const` anahtar sözcüğü. A `const` alanı alanın bildiriminde yalnızca başlatılabilir. A `readonly` alanı bildirimde veya oluşturucuda başlatılabilir. Bu nedenle, `readonly` alanları kullanılan oluşturucuya bağlı olarak farklı değerlere sahip olabilir. Ayrıca, ancak bir `const` alandır bir derleme zamanı sabiti `readonly` alan, bu satırda olduğu gibi çalışma zamanı sabitleri için kullanılabilir: `public static readonly uint l1 = (uint)DateTime.Now.Ticks;`

## <a name="example"></a>Örnek

[!code-csharp[csrefKeywordsModifiers#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#5)]

## <a name="example"></a>Örnek

Bu örnek, sabitlerin yerel değişkenler olarak kullanmayı gösterir.

[!code-csharp[csrefKeywordsModifiers#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#6)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
- [Değiştiriciler](../../../csharp/language-reference/keywords/modifiers.md)  
- [readonly](../../../csharp/language-reference/keywords/readonly.md)

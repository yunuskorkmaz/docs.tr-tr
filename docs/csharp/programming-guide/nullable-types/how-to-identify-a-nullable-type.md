---
title: 'Nasıl yapılır: boş değer atanabilir bir tür (C# programlama Kılavuzu) belirleme'
description: Boş değer atanabilir bir tür bir türdür örneği boş değer atanabilir bir tür olup olmadığını belirlemek hakkında bilgi edinin
ms.date: 09/24/2018
helpviewer_keywords:
- nullable types [C#], identifying
ms.assetid: d4b67ee2-66e8-40c1-ae9d-545d32c71387
ms.openlocfilehash: f9957568d3c68f60cc9286718be9f5a496f876e6
ms.sourcegitcommit: 700b9003ea6bdd83a53458bbc436c9b5778344f1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2018
ms.locfileid: "48261348"
---
# <a name="how-to-identify-a-nullable-type-c-programming-guide"></a>Nasıl yapılır: boş değer atanabilir bir tür (C# programlama Kılavuzu) belirleme

Aşağıdaki örnek nasıl belirleneceğini göstermektedir olup olmadığını bir <xref:System.Type?displayProperty=nameWithType> örneğini gösteren bir kapalı genel boş değer atanabilir tür diğer bir deyişle, <xref:System.Nullable%601?displayProperty=nameWithType> belirtilen türü parametre türüyle `T`:

[!code-csharp-interactive[whether Type is nullable](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#1)]

Örnekte gösterildiği gibi kullandığınız [typeof](../../language-reference/keywords/typeof.md) oluşturmak için işleç bir <xref:System.Type?displayProperty=nameWithType> nesne.  
  
Belirlemek istiyorsanız bir örnek olup boş değer atanabilir bir tür, kullanmayın <xref:System.Object.GetType%2A?displayProperty=nameWithType> almak için yöntemi bir <xref:System.Type> önceki kod ile test edilecek örneği. Çağırdığınızda <xref:System.Object.GetType%2A?displayProperty=nameWithType> yöntemi null yapılabilir bir tür örneği üzerinde örneğidir [Kutulu](using-nullable-types.md#boxing-and-unboxing) için <xref:System.Object>. Bir null olmayan boş değer atanabilir bir tür örneğinin kutulama temel türünde bir değer olarak kutulama için eşdeğer olarak <xref:System.Object.GetType%2A> döndürür bir <xref:System.Type> boş değer atanabilir bir tür temel alınan türünü temsil eden nesne:

[!code-csharp-interactive[GetType example](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#2)]

Kullanmayın [olduğu](../../language-reference/keywords/is.md) örneği boş değer atanabilir bir tür olup olmadığını belirlemek için işleci. Aşağıdaki örnekte gösterildiği gibi boş değer atanabilir bir tür ve kullanarak, temelindeki türe örnekleri türlerini ayırt edemez `is` işleci:

[!code-csharp-interactive[is operator example](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#3)]

Aşağıdaki örnekte gösterilen kod örneği boş değer atanabilir bir tür olup olmadığını belirlemek için kullanabilirsiniz:

[!code-csharp-interactive[whether an instance is of a nullable type](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#4)]
  
## <a name="see-also"></a>Ayrıca bkz.

- [Boş değer atanabilir türler](index.md)  
- [Boş değer atanabilir türleri kullanma](using-nullable-types.md)  
- <xref:System.Nullable.GetUnderlyingType%2A>  

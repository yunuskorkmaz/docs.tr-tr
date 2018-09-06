---
title: New kısıtlaması (C# Başvurusu)
ms.date: 07/20/2015
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
ms.openlocfilehash: 9948fc65030a4636c5d23db4ef8c3a584018d2f5
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43738608"
---
# <a name="new-constraint-c-reference"></a>New kısıtlaması (C# Başvurusu)

`new` Kısıtlaması belirtir bir genel sınıf bildiriminde herhangi bir tür bağımsız değişkeni genel bir parametresiz oluşturucusu olmalıdır. New'kısıtlamasının kullanılabilmesi için türü soyut olamaz.

## <a name="example"></a>Örnek

Uygulama `new` öğesini aşağıdaki örnekte gösterildiği gibi genel bir sınıf türünün yeni örneğini oluşturduğunda, bir tür parametresi kısıtlaması:

[!code-csharp[csrefKeywordsOperator#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#5)]

## <a name="example"></a>Örnek

Kullanırken `new()` kısıtlama diğer kısıtlamalarla en son belirtilmelidir:

[!code-csharp[csrefKeywordsOperator#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#6)]

Daha fazla bilgi için [tür parametrelerindeki kısıtlamalar](../../programming-guide/generics/constraints-on-type-parameters.md).

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic>
- [C# başvurusu](../../language-reference/index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [İşleç Anahtar Sözcükleri](operator-keywords.md)
- [Genel Türler](../../programming-guide/generics/index.md)
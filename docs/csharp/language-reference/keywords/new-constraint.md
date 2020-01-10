---
title: Yeni kısıtlama- C# başvuru
ms.date: 07/20/2015
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
ms.openlocfilehash: cd67aeb82d736b8941b0637494089723e7815505
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713349"
---
# <a name="new-constraint-c-reference"></a>Yeni kısıtlama (C# başvuru)

`new` kısıtlaması, genel sınıf bildirimindeki bir tür bağımsız değişkeninin Ortak parametresiz bir oluşturucuya sahip olması gerektiğini belirtir. `new` kısıtlamasını kullanmak için tür soyut olamaz.

Aşağıdaki örnekte gösterildiği gibi, genel bir sınıf türün yeni örneklerini oluşturduğunda, `new` kısıtlamasını bir tür parametresine uygulayın:

[!code-csharp[csrefKeywordsOperator#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#5)]

`new()` kısıtlamasını diğer kısıtlamalarla birlikte kullandığınızda, en son belirtilmelidir:

[!code-csharp[csrefKeywordsOperator#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#6)]

Daha fazla bilgi için bkz. [tür parametrelerindeki kısıtlamalar](../../programming-guide/generics/constraints-on-type-parameters.md).

Ayrıca, [bir türün örneğini](../operators/new-operator.md) veya bir [üye bildirimi değiştiricisini](new-modifier.md)oluşturmak için `new` anahtar sözcüğünü kullanabilirsiniz.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [tür parametresi kısıtlamaları](~/_csharplang/spec/classes.md#type-parameter-constraints) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../../language-reference/index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [Genel Türler](../../programming-guide/generics/index.md)

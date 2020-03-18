---
title: yeni kısıtlama - C# Referans
ms.date: 07/20/2015
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
ms.openlocfilehash: cd67aeb82d736b8941b0637494089723e7815505
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713349"
---
# <a name="new-constraint-c-reference"></a>yeni kısıtlama (C# Reference)

Kısıtlama, `new` genel bir sınıf bildirimindeki bir tür bağımsız değişkeninin ortak parametresiz bir oluşturucuya sahip olması gerektiğini belirtir. Kısıtlamayı `new` kullanmak için, tür soyut olamaz.

Genel `new` bir sınıf aşağıdaki örnekte gösterildiği gibi, tür yeni örnekler oluşturduğunda bir tür parametresine kısıtlama uygulayın:

[!code-csharp[csrefKeywordsOperator#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#5)]

Kısıtlamayı `new()` diğer kısıtlamalarla kullandığınızda, en son belirtilmelidir:

[!code-csharp[csrefKeywordsOperator#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#6)]

Daha fazla bilgi [için, Tür Parametreleri üzerindeki Kısıtlamalar'a](../../programming-guide/generics/constraints-on-type-parameters.md)bakın.

Anahtar kelimeyi, `new` bir [tür örneği oluşturmak](../operators/new-operator.md) veya [üye bildirimi değiştiricisi](new-modifier.md)olarak da kullanabilirsiniz.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Tür parametre kısıtlamaları](~/_csharplang/spec/classes.md#type-parameter-constraints) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../../language-reference/index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Kelimeler](index.md)
- [Genel Türler](../../programming-guide/generics/index.md)

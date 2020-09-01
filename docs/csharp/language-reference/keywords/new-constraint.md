---
description: New kısıtlaması-C# başvurusu
title: New kısıtlaması-C# başvurusu
ms.date: 07/20/2015
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
ms.openlocfilehash: f7b097729fe973aba7b85c48e1b1033aade83080
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139456"
---
# <a name="new-constraint-c-reference"></a>New kısıtlaması (C# Başvurusu)

`new`Kısıtlama, genel sınıf bildirimindeki bir tür bağımsız değişkeninin Ortak parametresiz bir oluşturucuya sahip olması gerektiğini belirtir. Kısıtlamayı kullanmak için `new` tür soyut olamaz.

`new`Aşağıdaki örnekte gösterildiği gibi, genel bir sınıf türün yeni örneklerini oluşturduğunda, kısıtlamayı bir tür parametresine uygulayın:

[!code-csharp[csrefKeywordsOperator#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#5)]

`new()`Kısıtlamayı diğer kısıtlamalarla birlikte kullandığınızda, en son belirtilmelidir:

[!code-csharp[csrefKeywordsOperator#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#6)]

Daha fazla bilgi için bkz. [tür parametrelerindeki kısıtlamalar](../../programming-guide/generics/constraints-on-type-parameters.md).

`new`Anahtar sözcüğünü, [bir tür örneği](../operators/new-operator.md) veya bir [üye bildirimi değiştiricisi](new-modifier.md)olarak oluşturmak için de kullanabilirsiniz.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [tür parametresi kısıtlamaları](~/_csharplang/spec/classes.md#type-parameter-constraints) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# anahtar sözcükleri](index.md)
- [Genel Türler](../../programming-guide/generics/index.md)

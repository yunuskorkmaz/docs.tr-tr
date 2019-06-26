---
title: New kısıtlaması - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
ms.openlocfilehash: 7c788be52010cdfadbd3c03f9e570815d25bdbef
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67401488"
---
# <a name="new-constraint-c-reference"></a>New kısıtlaması (C# Başvurusu)

`new` Kısıtlaması belirtir bir genel sınıf bildiriminde tür bağımsız değişkeni genel bir parametresiz oluşturucusu olmalıdır. Kullanılacak `new` kısıtlaması, türü olamaz abstract.

Uygulama `new` öğesini aşağıdaki örnekte gösterildiği gibi genel bir sınıf türünün yeni örneğini oluşturduğunda, bir tür parametresi kısıtlaması:

[!code-csharp[csrefKeywordsOperator#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#5)]

Kullanırken `new()` kısıtlama diğer kısıtlamalarla en son belirtilmelidir:

[!code-csharp[csrefKeywordsOperator#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#6)]

Daha fazla bilgi için [tür parametrelerindeki kısıtlamalar](../../programming-guide/generics/constraints-on-type-parameters.md).

De kullanabilirsiniz `new` anahtar [bir türün bir örneğini oluşturma](../operators/new-operator.md) veya farklı bir [üye bildirim değiştirici](new-modifier.md).

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [tür parametresi kısıtlamaları](~/_csharplang/spec/classes.md#type-parameter-constraints) bölümünü [ C# dil belirtimi](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../../language-reference/index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [Genel Türler](../../programming-guide/generics/index.md)

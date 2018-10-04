---
title: object (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- object_CSharpKeyword
- object
helpviewer_keywords:
- object keyword [C#]
ms.assetid: 93f60c0b-e17a-40a9-9362-cca5fb77b0e7
ms.openlocfilehash: b36703828e6027a89297ac88edaf2b55ec18f42e
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48779692"
---
# <a name="object-c-reference"></a>object (C# Başvurusu)

`object` Türü için bir diğer ad, <xref:System.Object> .NET içinde. C#, tüm türlerin, önceden tanımlanmış ve kullanıcı tanımlı başvuru türleri ve değer türleri birleşik tür sisteminde doğrudan veya dolaylı olarak devralınacak <xref:System.Object>. Her türden değer türü değişkenler için atayabilirsiniz `object`. Ne zaman bir değer türü bir değişkene dönüştürülür nesnesi için kabul edilecek *Kutulu*. Türündeki bir değişkene bir değer türüne dönüştürülür, onu olduğu söylenir *kutulanmamış*. Daha fazla bilgi için [kutulama ve kutudan çıkarma](../../../csharp/programming-guide/types/boxing-and-unboxing.md).

## <a name="example"></a>Örnek

Aşağıdaki örnekte gösterildiği nasıl türündeki değişkenler `object` herhangi bir veri türünün değerlerini kabul edebilir ve nasıl türündeki değişkenler `object` yöntemleri kullanabilirsiniz <xref:System.Object> .NET Framework.

[!code-csharp[csrefKeywordsTypes#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#16)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [Başvuru Türleri](reference-types.md)
- [Değer Türleri](value-types.md)
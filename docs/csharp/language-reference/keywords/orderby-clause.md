---
title: OrderBy yan tümcesinin - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- orderby
- orderby_CSharpKeyword
helpviewer_keywords:
- orderby clause [C#]
- orderby keyword [C#]
ms.assetid: 21f87f48-d69d-4e95-9a52-6fec47b37e1f
ms.openlocfilehash: fc6e47270c4ae035a6387bf0e8d29efcd42e902f
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53240989"
---
# <a name="orderby-clause-c-reference"></a>orderby tümcesi (C# Başvurusu)

Bir sorgu ifadesinde `orderby` yan tümcesi döndürülen dizi veya alt diziyi artan veya azalan düzende sıralanmasını (grubu) neden olur. Birden çok anahtar, bir veya daha fazla ikincil sıralama işlemlerini gerçekleştirmek için belirtilebilir. Sıralama, öğe türü için varsayılan karşılaştırıcı tarafından gerçekleştirilir. Varsayılan sıralama artan düzendedir. Özel bir karşılaştırıcı de belirtebilirsiniz. Ancak, yalnızca yöntem tabanlı sözdizimi kullanılarak kullanılabilir. Daha fazla bilgi için [veri sıralama](../../programming-guide/concepts/linq/sorting-data.md).

## <a name="example"></a>Örnek

Aşağıdaki örnekte, A'dan başlayarak alfabetik sırada sözcükleri ilk sorgu sıralar ve ikinci sorgu aynı sözcükler azalan düzende sıralar. ( `ascending` Anahtar sözcüğü atlanabilir ve varsayılan sıralama değerdir.)

[!code-csharp[cscsrefQueryKeywords#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#20)]

## <a name="example"></a>Örnek

Aşağıdaki örnek, ilk adlarına öğrencilerinin adların birincil bir sıralama ve ikincil sıralama gerçekleştirir.

[!code-csharp[cscsrefQueryKeywords#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#22)]

## <a name="remarks"></a>Açıklamalar

Derleme zamanında `orderby` yan tümcesi bir çağrısına çevrilir <xref:System.Linq.Enumerable.OrderBy%2A> yöntemi. Birden çok anahtarı `orderby` yan tümcesi çevirmek için <xref:System.Linq.Enumerable.ThenBy%2A> yöntemi çağırır.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [Sorgu anahtar sözcükleri (LINQ)](query-keywords.md)
- [Dil ile Tümleşik Sorgu (LINQ)](../../linq/index.md)
- [group yan tümcesi](group-clause.md)
- [C#'de LINQ Kullanmaya Başlama](../../programming-guide/concepts/linq/getting-started-with-linq.md)
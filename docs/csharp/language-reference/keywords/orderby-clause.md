---
title: OrderBy yan tümcesi C# -başvuru
ms.date: 07/20/2015
f1_keywords:
- orderby
- orderby_CSharpKeyword
helpviewer_keywords:
- orderby clause [C#]
- orderby keyword [C#]
ms.assetid: 21f87f48-d69d-4e95-9a52-6fec47b37e1f
ms.openlocfilehash: d88b2b40f63f0616cfd54e8abb62f1bc2183f776
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713306"
---
# <a name="orderby-clause-c-reference"></a>orderby tümcesi (C# Başvurusu)

Sorgu ifadesinde `orderby` yan tümcesi, döndürülen sıranın veya alt dizinin (Grup) artan veya azalan sırada sıralanmasını sağlar. Bir veya daha fazla ikincil sıralama işlemi gerçekleştirmek için birden çok anahtar belirtilebilir. Sıralama, öğe türü için varsayılan karşılaştırıcı tarafından gerçekleştirilir. Varsayılan sıralama düzeni artan. Ayrıca, özel bir karşılaştırıcı da belirtebilirsiniz. Ancak, yalnızca Yöntem tabanlı sözdizimi kullanılarak kullanılabilir. Daha fazla bilgi için bkz. [verileri sıralama](../../programming-guide/concepts/linq/sorting-data.md).

## <a name="example"></a>Örnek

Aşağıdaki örnekte, ilk sorgu kelimeleri bir ' dan başlayarak alfabetik sırada sıralar ve ikinci sorgu aynı sözcükleri azalan düzende sıralar. (`ascending` anahtar sözcüğü varsayılan sıralama değeridir ve atlanabilir.)

[!code-csharp[cscsrefQueryKeywords#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#20)]

## <a name="example"></a>Örnek

Aşağıdaki örnek, öğrencilerin soyadı üzerinde birincil bir sıralama ve ardından ilk adlarında ikinci bir sıralama gerçekleştirir.

[!code-csharp[cscsrefQueryKeywords#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#22)]

## <a name="remarks"></a>Açıklamalar

Derleme zamanında, `orderby` yan tümcesi <xref:System.Linq.Enumerable.OrderBy%2A> yöntemine yapılan çağrıya çevrilir. `orderby` yan tümcesindeki birden çok anahtar <xref:System.Linq.Enumerable.ThenBy%2A> yöntemi çağrılarına çeviri yapar.

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [Sorgu anahtar sözcükleri (LINQ)](query-keywords.md)
- [Dil ile Tümleşik Sorgu (LINQ)](../../linq/index.md)
- [group yan tümcesi](group-clause.md)
- [C#'de LINQ Kullanmaya Başlama](/dotnet/csharp/programming-guide/concepts/linq/)

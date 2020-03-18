---
title: maddesi uyarınca sipariş - C# Referans
ms.date: 07/20/2015
f1_keywords:
- orderby
- orderby_CSharpKeyword
helpviewer_keywords:
- orderby clause [C#]
- orderby keyword [C#]
ms.assetid: 21f87f48-d69d-4e95-9a52-6fec47b37e1f
ms.openlocfilehash: cd76b2c33fe1a1a986bc05e3c3ed5f22809686ed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173581"
---
# <a name="orderby-clause-c-reference"></a>orderby tümcesi (C# Başvurusu)

Sorgu ifadesinde, `orderby` yan tümce, döndürülen sıranın veya alt dizinin (grup) artan veya azalan sırada sıralanmasına neden olur. Bir veya daha fazla ikincil sıralama işlemi gerçekleştirmek için birden çok anahtar belirtilebilir. Sıralama öğesi türü için varsayılan karşılayıcı tarafından gerçekleştirilir. Varsayılan sıralama sırası yükseliyor. Özel bir karşılayıcı da belirtebilirsiniz. Ancak, yalnızca yöntem tabanlı sözdizimi kullanılarak kullanılabilir. Daha fazla bilgi için [bkz.](../../programming-guide/concepts/linq/sorting-data.md)

## <a name="example"></a>Örnek

Aşağıdaki örnekte, ilk sorgu sözcükleri A'dan başlayarak alfabetik sıraya göre sıralar, ikinci sorgu ise aynı sözcükleri azalan sırada sıralar. (Anahtar `ascending` kelime varsayılan sıralama değeridir ve atlanabilir.)

[!code-csharp[cscsrefQueryKeywords#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#20)]

## <a name="example"></a>Örnek

Aşağıdaki örnekte, öğrencilerin soyadlarına bir birincil sıralama ve daha sonra ilk adlarında ikincil sıralama gerçekleştirir.

[!code-csharp[cscsrefQueryKeywords#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#22)]

## <a name="remarks"></a>Açıklamalar

Derleme zamanında, `orderby` yan tümce <xref:System.Linq.Enumerable.OrderBy%2A> yönteme bir çağrıya çevrilir. `orderby` Yan tümcedeki birden <xref:System.Linq.Enumerable.ThenBy%2A> çok anahtar yöntem çağrılarına çevirir.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../index.md)
- [Sorgu Anahtar Kelimeleri (LINQ)](query-keywords.md)
- [C# üzerinde LINQ](../../linq/index.md)
- [group yan tümcesi](group-clause.md)
- [Dil ile Tümleşik Sorgu (LINQ)](../../programming-guide/concepts/linq/index.md)

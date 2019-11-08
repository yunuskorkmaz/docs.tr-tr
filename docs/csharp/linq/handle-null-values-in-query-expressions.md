---
title: Sorgu ifadelerinde null değerleri işle (LINQ ın C#)
description: İçindeki C#LINQ sorgu ifadelerinde null değerleri nasıl işleyeceğinizi öğrenin.
ms.date: 12/01/2016
ms.assetid: ac63ae8b-724d-4251-9334-528f4e884ae7
ms.openlocfilehash: c9a3aaec05fa029a8db66826bdcb4a1d106176e3
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736862"
---
# <a name="handle-null-values-in-query-expressions"></a>Sorgu ifadelerinde boş değerler işleme

Bu örnek, kaynak koleksiyonlarında olası null değerlerin nasıl işleneceğini gösterir. <xref:System.Collections.Generic.IEnumerable%601> gibi bir nesne koleksiyonu, değeri [null](../language-reference/keywords/null.md)olan öğeleri içerebilir. Bir kaynak koleksiyon null ise veya değeri null olan bir öğe içeriyorsa ve sorgunuz null değerleri işlemezse, sorguyu yürüttüğünüzde bir <xref:System.NullReferenceException> atılır.

## <a name="example"></a>Örnek

Aşağıdaki örnekte gösterildiği gibi, bir null başvurusu özel durumunun önüne geçmek için savunmaya büyük bir kod oluşturabilirsiniz:

[!code-csharp[csProgGuideLINQ#82](~/samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_1.cs)]

Önceki örnekte, `where` yan tümcesi Kategoriler dizisindeki tüm null öğeleri filtreler. Bu teknik, JOIN yan tümcesindeki null denetiminden bağımsızdır. Bu örnekte null değeri olan koşullu ifade, `Products.CategoryID` `Nullable<int>`için toplu olan `int?` türünde olduğundan işe yarar.

## <a name="example"></a>Örnek

JOIN yan tümcesinde, karşılaştırma anahtarlarından yalnızca biri null yapılabilir bir değer türü ise, diğerini sorgu ifadesinde null yapılabilen bir türe çevirebilirsiniz. Aşağıdaki örnekte, `EmployeeID` `int?`türünde değerler içeren bir sütun olduğunu varsayalım:

[!code-csharp[csProgGuideLINQ#83](~/samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_2.cs)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Nullable%601>
- [Dil ile Tümleşik Sorgu (LINQ)](index.md)
- [Null yapılabilir değer türleri](../language-reference/builtin-types/nullable-value-types.md)

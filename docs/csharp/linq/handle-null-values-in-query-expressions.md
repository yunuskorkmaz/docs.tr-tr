---
title: Sorgu ifadelerinde null değerleri işle (LINQ ın C#)
description: İçindeki C#LINQ sorgu ifadelerinde null değerleri nasıl işleyeceğinizi öğrenin.
ms.date: 12/01/2016
ms.assetid: ac63ae8b-724d-4251-9334-528f4e884ae7
ms.openlocfilehash: 38a5c5e4a869cc44be78f70cbf0e50166baaab16
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353327"
---
# <a name="handle-null-values-in-query-expressions"></a>Sorgu ifadelerinde boş değerler işleme

Bu örnek, kaynak koleksiyonlarında olası null değerlerin nasıl işleneceğini gösterir. @No__t-0 gibi bir nesne koleksiyonu, değeri [null](../language-reference/keywords/null.md)olan öğeleri içerebilir. Bir kaynak koleksiyon null ise veya değeri null olan bir öğe içeriyorsa ve sorgunuz null değerleri işlemezse, sorguyu yürüttüğünüzde <xref:System.NullReferenceException> atılır.

## <a name="example"></a>Örnek

Aşağıdaki örnekte gösterildiği gibi, bir null başvurusu özel durumunun önüne geçmek için savunmaya büyük bir kod oluşturabilirsiniz:

[!code-csharp[csProgGuideLINQ#82](~/samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_1.cs)]

Önceki örnekte `where` yan tümcesi Kategoriler dizisindeki tüm null öğeleri filtreler. Bu teknik, JOIN yan tümcesindeki null denetiminden bağımsızdır. Bu örnekte null değeri olan koşullu ifade, `Nullable<int>` için toplu olan `int?` türünde `Products.CategoryID` ' dır.

## <a name="example"></a>Örnek

JOIN yan tümcesinde, karşılaştırma anahtarlarından yalnızca biri null yapılabilir bir değer türü ise, diğerini sorgu ifadesinde null yapılabilen bir türe çevirebilirsiniz. Aşağıdaki örnekte, `EmployeeID` ' ın `int?` türünde değerler içeren bir sütun olduğunu varsayalım:

[!code-csharp[csProgGuideLINQ#83](~/samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_2.cs)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Nullable%601>
- [Dil ile Tümleşik Sorgu (LINQ)](index.md)
- [Null yapılabilir değer türleri](../programming-guide/nullable-types/index.md)

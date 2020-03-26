---
title: Sorgu ifadelerinde null değerlerini işleme (C#'da LINQ)
description: C#'daki LINQ sorgu ifadelerinde null değerleri nasıl işleyeceğinizi öğrenin.
ms.date: 12/01/2016
ms.assetid: ac63ae8b-724d-4251-9334-528f4e884ae7
ms.openlocfilehash: 3da490b72bd518df7be8c14b34655af8c6f84929
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249311"
---
# <a name="handle-null-values-in-query-expressions"></a>Sorgu ifadelerinde boş değerler işleme

Bu örnek, kaynak koleksiyonlarındaki olası null değerlerin nasıl işleyeceğini gösterir. Bir nesne koleksiyonu <xref:System.Collections.Generic.IEnumerable%601> gibi değeri [null](../language-reference/keywords/null.md)olan öğeler içerebilir. Kaynak koleksiyonu null ise veya değeri null olan bir öğe içeriyorsa ve <xref:System.NullReferenceException> sorgunuz null değerleri işlemiyorsa, sorguyu yürüttüğünüzde bir öğe atılır.

## <a name="example"></a>Örnek

Aşağıdaki örnekte gösterildiği gibi geçersiz bir başvuru özel durum önlemek için savunma kodlayabilirsiniz:

[!code-csharp[csProgGuideLINQ#82](~/samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_1.cs)]

Önceki örnekte, `where` yan tümce, kategoriler dizisindeki tüm null öğeleri filtreler. Bu teknik, birleştirme yan tümcesindeki null denetiminden bağımsızdır. Bu örnekte null olan koşullu `Products.CategoryID` ifade `int?` çalışır, çünkü `Nullable<int>`stenobun kısaltmasi.

## <a name="example"></a>Örnek

Birleştirme yan tümcesinde, karşılaştırma anahtarlarından yalnızca biri geçersiz bir değer türüyse, diğerini sorgu ifadesinde boşdeğer türüne atabilirsiniz. Aşağıdaki örnekte, tür `EmployeeID` `int?`değerlerini içeren bir sütun olduğunu varsayalım:

[!code-csharp[csProgGuideLINQ#83](~/samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_2.cs)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Nullable%601>
- [Dil ile Tümleşik Sorgu (LINQ)](index.md)
- [Nullable değer türleri](../language-reference/builtin-types/nullable-value-types.md)

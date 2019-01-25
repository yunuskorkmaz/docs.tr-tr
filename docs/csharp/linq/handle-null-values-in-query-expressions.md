---
title: (C# üzerinde LINQ) sorgu ifadelerinde boş değerler işleme
description: C# LINQ Sorgu ifadelerinde boş değerler işleme hakkında bilgi edinin.
ms.date: 12/01/2016
ms.assetid: ac63ae8b-724d-4251-9334-528f4e884ae7
ms.openlocfilehash: 14609aee2bbd1fbb487589bb41683a1f3cad1362
ms.sourcegitcommit: 5dcfeb59179e81071f54840d4902cbe00b184294
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54857573"
---
# <a name="handle-null-values-in-query-expressions"></a>Sorgu ifadelerinde boş değerler işleme

Bu örnek, kaynak koleksiyonları olası null değerlerin nasıl ele alınacağını gösterir. Bir nesne koleksiyonu gibi bir <xref:System.Collections.Generic.IEnumerable%601> değeri öğeleri içerebilir [null](../language-reference/keywords/null.md). Bir kaynak koleksiyonu null veya değeri null olan bir öğe içeriyor ve sorgunuzu null değerler işlemez bir <xref:System.NullReferenceException> sorgu yürütülürken oluşturulur.

## <a name="example"></a>Örnek

Aşağıdaki örnekte gösterildiği gibi bir null başvurusu özel durumu önlemek için biçimde geliştirmelisiniz kod yazabilirsiniz:

[!code-csharp[csProgGuideLINQ#82](~/samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_1.cs)]

Önceki örnekte, `where` yan tümcesi filtreler kategoriler dizisi null tüm öğeler kullanıma. Bu teknik, null denetimi JOIN yan tümcesi içinde bağımsızdır. Bu örnekte null koşullu ifadeyle çalışır çünkü `Products.CategoryID` türünde `int?` için Toplu özellik olduğu `Nullable<int>`.

## <a name="example"></a>Örnek

Karşılaştırma anahtarlarından birini bir boş değer atanabilir değer türü olduğundan, yalnızca bir JOIN yan tümcesinde, boş değer atanabilir bir tür diğer sorgu ifadesinde çevirebilirsiniz. Aşağıdaki örnekte, varsayımında `EmployeeID` türü değerleri içeren bir sütun `int?`:

[!code-csharp[csProgGuideLINQ#83](~/samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_2.cs)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Nullable%601>
- [Dil ile Tümleşik Sorgu (LINQ)](index.md)
- [Boş değer atanabilir türler](../programming-guide/nullable-types/index.md)

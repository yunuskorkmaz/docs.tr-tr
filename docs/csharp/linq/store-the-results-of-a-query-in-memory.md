---
title: Bellekte sorgunun sonuçlarını Store
description: Sonuçları depolamayı öğrenin.
ms.date: 11/30/2016
ms.assetid: 5b863961-1750-4cf9-9607-acea5054d15a
ms.openlocfilehash: 52d502a841c428bd90a26c803ba577e76c17197c
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37404307"
---
# <a name="store-the-results-of-a-query-in-memory"></a>Bellekte sorgunun sonuçlarını Store

Bir sorgu temel alabilir ve verileri düzenleme hakkında yönergeler kümesidir. Sorgular, gevşek, sonraki her öğe sonucu, istenen şekilde yürütülür. Kullanırken `foreach` sonuçlarını yinelemek için öğeler erişilen olarak döndürülür. Bir sorguyu değerlendirmeye ve çalıştırmadan sonuçlarını depolamak için bir `foreach` döngüsünde, yalnızca aşağıdaki yöntemlerden birini sorgu değişkeni üzerinde çağırın:

- <xref:System.Linq.Enumerable.ToList%2A>

- <xref:System.Linq.Enumerable.ToArray%2A>

- <xref:System.Linq.Enumerable.ToDictionary%2A>

- <xref:System.Linq.Enumerable.ToLookup%2A>

 Sorgu sonuçları depoladığınızda, döndürülen koleksiyon nesnesi için yeni bir değişken aşağıdaki örnekte gösterildiği gibi atamanızı öneririz:

## <a name="example"></a>Örnek

[!code-csharp[csProgGuideLINQ#25](~/samples/snippets/csharp/concepts/linq/how-to-store-the-results-of-a-query-in-memory_1.cs)]

## <a name="see-also"></a>Ayrıca bkz.

[Dil ile Tümleşik Sorgu (LINQ)](index.md)
---
title: Bellekte sorgunun sonuçlarını depolama
description: Sonuçları depolamak için nasıl.
ms.date: 11/30/2016
ms.assetid: 5b863961-1750-4cf9-9607-acea5054d15a
ms.openlocfilehash: 66a7a95c74db4062e76c54d4339ccb7343f44067
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "65633564"
---
# <a name="store-the-results-of-a-query-in-memory"></a>Bellekte sorgunun sonuçlarını depolama

Sorgu, temelde verilerin nasıl alınacağına ve düzenlenene yönelik bir yönerge ler kümesidir. Sorgular, sonuçtaki her sonraki öğe istendiği için tembelce yürütülür. Sonuçları doğrulamak `foreach` için kullandığınızda, öğeler erişilmiş olarak döndürülür. Bir sorguyu değerlendirmek ve bir `foreach` döngü yürütmeden sonuçlarını depolamak için sorgu değişkeninde aşağıdaki yöntemlerden birini aramaniz yeterlidir:

- <xref:System.Linq.Enumerable.ToList%2A>

- <xref:System.Linq.Enumerable.ToArray%2A>

- <xref:System.Linq.Enumerable.ToDictionary%2A>

- <xref:System.Linq.Enumerable.ToLookup%2A>

 Sorgu sonuçlarını depolarken, döndürülen koleksiyon nesnesini aşağıdaki örnekte gösterildiği gibi yeni bir değişkene atamanızı öneririz:

## <a name="example"></a>Örnek

[!code-csharp[csProgGuideLINQ#25](~/samples/snippets/csharp/concepts/linq/how-to-store-the-results-of-a-query-in-memory_1.cs)]

## <a name="see-also"></a>Ayrıca bkz.

- [Dil ile Tümleşik Sorgu (LINQ)](index.md)

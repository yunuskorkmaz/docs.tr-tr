---
title: 'Nasıl yapılır: Paralel İşlemleri Yürütmek için Parallel.Invoke Kullanma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- task parallelism in .NET
- parallel programming, task parallelism
ms.assetid: 6b3ecd79-dec9-4ce1-abf4-62e5392a59c6
ms.openlocfilehash: 7189c478e132a41971a364b833f0fabda6ff84d4
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588407"
---
# <a name="how-to-use-parallelinvoke-to-execute-parallel-operations"></a>Nasıl yapılır: Paralel İşlemleri Yürütmek için Parallel.Invoke Kullanma

Bu örnek, Görev Paralel Kitaplığı'nda kullanarak <xref:System.Threading.Tasks.Parallel.Invoke%2A> işlemleri nasıl paralelleştireceklerini gösterir. Paylaşılan bir veri kaynağında üç işlem gerçekleştirilir. Because none of the operations modifies the source, they can be executed in parallel in a straightforward manner.

> [!NOTE]
> TPL'de temsilciler tanımlamak için bu belgede lambda ifadeleri kullanılır. C# veya Visual Basic'teki lambda ifadelerine aşina değilseniz, [PLINQ ve TPL'deki Lambda İfadeleri'ne](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)bakın.

## <a name="example"></a>Örnek

[!code-csharp[TPL_Parallel#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallelinvoke.cs#06)]
[!code-vb[TPL_Parallel#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/parallelinvoke.vb#06)]

<xref:System.Threading.Tasks.Parallel.Invoke%2A>'ile, yalnızca aynı anda çalıştırmak istediğiniz eylemleri ifade eve ve çalışma zamanı ana bilgisayardaki çekirdek sayısına otomatik olarak ölçekleme de dahil olmak üzere tüm iş parçacığı zamanlama ayrıntılarını işler.

Bu örnek, verileri değil, işlemleri paralelleştirir. Alternatif bir yaklaşım olarak, PLINQ kullanarak LINQ sorgularını paralelleştirebilir ve sorguları sırayla çalıştırabilirsiniz. Alternatif olarak, PLINQ kullanarak verileri paralelleştirebilirsiniz. Başka bir seçenek sorguları ve görevleri paralelleştirmektir. Ortaya çıkan genel gider, nispeten az işlemciye sahip ana bilgisayardaki performansı düşürebilir, ancak birçok işlemciye sahip bilgisayarlarda çok daha iyi ölçeklendirilir.

## <a name="compile-the-code"></a>Kodu Derleme

Tüm örneği kopyalayıp bir Microsoft Visual Studio projesine yapıştırın ve **F5 tuşuna**basın.

## <a name="see-also"></a>Ayrıca bkz.

- [Paralel Programlama](../../../docs/standard/parallel-programming/index.md)
- [Nasıl yapılır: Bir Görevi ve Alt Öğelerini İptal Etme](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)
- [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)

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
ms.openlocfilehash: 665490601cad9ccd7881042aed576b95bbc07115
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139721"
---
# <a name="how-to-use-parallelinvoke-to-execute-parallel-operations"></a>Nasıl yapılır: Paralel İşlemleri Yürütmek için Parallel.Invoke Kullanma

Bu örnek, görev paralel kitaplığındaki <xref:System.Threading.Tasks.Parallel.Invoke%2A> kullanarak işlemleri nasıl paralel hale getirmek gösterir. Paylaşılan bir veri kaynağında üç işlem gerçekleştirilir. İşlemlerden hiçbiri kaynağı değiştirmediğinden, bu işlemler basit bir şekilde paralel olarak çalıştırılabilir.

> [!NOTE]
> TPL'de temsilciler tanımlamak için bu belgede lambda ifadeleri kullanılır. Veya Visual Basic içindeki C# lambda ifadeleriyle ilgili bilgi sahibi değilseniz bkz. [PLıNQ ve TPL içindeki lambda ifadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).

## <a name="example"></a>Örnek

[!code-csharp[TPL_Parallel#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallelinvoke.cs#06)]
[!code-vb[TPL_Parallel#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/parallelinvoke.vb#06)]

<xref:System.Threading.Tasks.Parallel.Invoke%2A>için, aynı anda hangi eylemleri çalıştırmak istediğinizi ifade edin ve çalışma zamanı, ana bilgisayardaki çekirdek sayısına otomatik olarak ölçekleme de dahil olmak üzere tüm iş parçacığı zamanlama ayrıntılarını işler.

Bu örnek, verileri değil, işlemleri paralelleştirin. Alternatif bir yaklaşım olarak, PLıNQ kullanarak LINQ sorgularını paralel hale getirmek yapabilir ve sorguları sırayla çalıştırabilirsiniz. Alternatif olarak, PLıNQ kullanarak verileri paralel hale getirmek yapabilirsiniz. Diğer bir seçenek de sorguları ve görevleri paralel hale getirmek. Elde edilen ek yükün görece az işlemcili konak bilgisayarlarda performansı düşürebilse de, çok işlemcili bilgisayarlarda çok daha iyi ölçeklenebilmesini sağlayabilir.

## <a name="compile-the-code"></a>Kodu derle

Tüm örneği kopyalayıp bir Microsoft Visual Studio projesine yapıştırın ve **F5**tuşuna basın.

## <a name="see-also"></a>Ayrıca bkz.

- [Paralel Programlama](../../../docs/standard/parallel-programming/index.md)
- [Nasıl yapılır: Bir Görevi ve Alt Öğelerini İptal Etme](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)
- [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)

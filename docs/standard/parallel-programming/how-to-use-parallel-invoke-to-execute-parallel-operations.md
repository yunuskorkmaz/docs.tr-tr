---
title: 'Nasıl yapılır: Paralel İşlemleri Yürütmek için parallel_invoke Kullanma'
description: .NET 'teki paylaşılan bir veri kaynağında paralel işlemler sağlayan görev paralel kitaplığı 'nda (TPL) Parallel. Invoke metodunu nasıl kullanacağınızı öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- task parallelism in .NET
- parallel programming, task parallelism
ms.assetid: 6b3ecd79-dec9-4ce1-abf4-62e5392a59c6
ms.openlocfilehash: 6ec8f03216cc6225e909f5dc3128469047826166
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94825487"
---
# <a name="how-to-use-parallelinvoke-to-execute-parallel-operations"></a>Nasıl yapılır: Paralel İşlemleri Yürütmek için parallel_invoke Kullanma

Bu örnek <xref:System.Threading.Tasks.Parallel.Invoke%2A> , görev paralel kitaplığı 'nda kullanarak nasıl paralel hale getirmek işlem yapılacağını gösterir. Paylaşılan bir veri kaynağında üç işlem gerçekleştirilir. İşlemler, kaynağı değiştirmediği için doğrudan paralel şekilde yürütülebilir.

> [!NOTE]
> TPL'de temsilciler tanımlamak için bu belgede lambda ifadeleri kullanılır. C# veya Visual Basic lambda ifadeleriyle ilgili bilgi sahibi değilseniz bkz. [PLıNQ ve TPL Içindeki lambda ifadeleri](lambda-expressions-in-plinq-and-tpl.md).

## <a name="example"></a>Örnek

[!code-csharp[TPL_Parallel#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallelinvoke.cs#06)]
[!code-vb[TPL_Parallel#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/parallelinvoke.vb#06)]

İle <xref:System.Threading.Tasks.Parallel.Invoke%2A> , aynı anda hangi eylemleri çalıştırmak istediğinizi ifade edersiniz ve çalışma zamanı, ana bilgisayardaki çekirdek sayısına otomatik olarak ölçekleme de dahil olmak üzere tüm iş parçacığı zamanlama ayrıntılarını işler.

Bu örnek, verileri değil, işlemleri paralelleştirin. Alternatif bir yaklaşım olarak, PLıNQ kullanarak LINQ sorgularını paralel hale getirmek yapabilir ve sorguları sırayla çalıştırabilirsiniz. Alternatif olarak, PLıNQ kullanarak verileri paralel hale getirmek yapabilirsiniz. Diğer bir seçenek de sorguları ve görevleri paralel hale getirmek. Elde edilen ek yükün görece az işlemcili konak bilgisayarlarda performansı düşürebilse de, çok işlemcili bilgisayarlarda daha iyi ölçeklendirme yapar.

## <a name="compile-the-code"></a>Kodu derle

Tüm örneği kopyalayıp bir Microsoft Visual Studio projesine yapıştırın ve **F5** tuşuna basın.

## <a name="see-also"></a>Ayrıca bkz.

- [Paralel programlama](index.md)
- [Nasıl yapılır: Bir Görevi ve Alt Öğelerini İptal Etme](how-to-cancel-a-task-and-its-children.md)
- [Paralel LINQ (PLINQ)](introduction-to-plinq.md)

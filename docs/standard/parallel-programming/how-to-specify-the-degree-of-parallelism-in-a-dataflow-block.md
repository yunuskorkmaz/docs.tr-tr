---
title: 'Nasıl yapılır: Veri Akışı Bloğunda Paralellik Derecesini Belirtme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dataflow block, specifying parallelism in TPL
- Task Parallel Library, dataflows
- TPL dataflow library, specifying parallelism
ms.assetid: e4088541-ee05-40db-95f5-147cfe62fde7
ms.openlocfilehash: 50399d6cd32fe310089395ac8c660b08151ba808
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73141660"
---
# <a name="how-to-specify-the-degree-of-parallelism-in-a-dataflow-block"></a>Nasıl yapılır: Veri Akışı Bloğunda Paralellik Derecesini Belirtme
Bu belge, aynı <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A?displayProperty=nameWithType> anda birden fazla ileti işlemek için bir yürütme veri akışı bloğu etkinleştirmek için özelliği ayarlamak için nasıl açıklanır. Bunu yapmak, uzun süren bir hesaplama gerçekleştiren ve iletileri paralel olarak işlemeden yararlanabilecek bir veri akışı bloğunuz olduğunda yararlıdır. Bu örnek, <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=nameWithType> aynı anda birden çok veri akışı işlemleri gerçekleştirmek için sınıfı kullanır; ancak, TPL Veri Akışı Kitaplığı'nın sağladığı <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType>önceden tanımlanmış yürütme bloğu türlerinden herhangi birinde <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType>en yüksek paralellik derecesini belirtebilirsiniz.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a>Örnek  
 Aşağıdaki örnek, iki veri akışı hesaplaması gerçekleştirir ve her hesaplama için gereken geçen süreyi yazdırır. İlk hesaplama, varsayılan olan 1'in en fazla paralellik derecesini belirtir. En fazla 1 paralellik derecesi veri akışı bloğunun iletileri seri olarak işlemesine neden olur. İkinci hesaplama, kullanılabilir işlemci sayısına eşit en yüksek paralellik derecesini belirtilmesi dışında, ilkine benzer. Bu, veri akışı bloğunun paralel olarak birden çok işlem gerçekleştirmesini sağlar.  
  
 [!code-csharp[TPLDataflow_DegreeOfParallelism#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_degreeofparallelism/cs/dataflowdegreeofparallelism.cs#1)]
 [!code-vb[TPLDataflow_DegreeOfParallelism#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_degreeofparallelism/vb/dataflowdegreeofparallelism.vb#1)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Varsayılan olarak, her önceden tanımlanmış veri akışı bloğu iletilerin alındığı sırada iletileri yayır.  1'den büyük bir paralellik derecesi belirttiğiniz zaman birden çok ileti aynı anda işlenir, ancak yine de alındıkları sırada yayılırlar.  
  
 <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A> özelliği en büyük paralellik derecesini temsil ettiğinden, veri akışı bloğu belirttiğinizden daha düşük derecede paralellikle çalışabilir. Veri akışı bloğu, işlevsel gereksinimlerini karşılamak veya kullanılabilir sistem kaynaklarının eksikliğini hesaba katmak için daha az bir paralellik derecesi kullanabilir. Veri akışı bloğu asla belirttiğinizden daha büyük bir paralellik derecesi seçmez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)

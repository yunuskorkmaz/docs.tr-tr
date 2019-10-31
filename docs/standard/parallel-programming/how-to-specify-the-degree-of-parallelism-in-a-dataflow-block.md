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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141660"
---
# <a name="how-to-specify-the-degree-of-parallelism-in-a-dataflow-block"></a>Nasıl yapılır: Veri Akışı Bloğunda Paralellik Derecesini Belirtme
Bu belgede, bir yürütme veri akışı bloğunun aynı anda birden fazla iletiyi işlemesini sağlamak için <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A?displayProperty=nameWithType> özelliğinin nasıl ayarlanacağı açıklanır. Bu, uzun süre çalışan bir hesaplama gerçekleştiren ve iletileri paralel olarak işlemenin avantajlarından faydalanabilecek bir veri akışı blobunun yapılması yararlıdır. Bu örnek, birden çok veri akışı işlemini eşzamanlı olarak gerçekleştirmek için <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=nameWithType> sınıfını kullanır; Ancak, TPL veri akışı kitaplığının sağladığı, <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType>ve <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType>sağladığı önceden tanımlanmış yürütme bloğu türlerinden herhangi birinde paralellik derecesi üst sınırını belirtebilirsiniz.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a>Örnek  
 Aşağıdaki örnek iki veri akışı hesaplamaları gerçekleştirir ve her hesaplama için gereken geçen süreyi yazdırır. İlk hesaplama, varsayılan değer olan 1 ' in en fazla paralellik derecesini belirtir. En Yüksek paralellik derecesi 1, veri akışı bloğunun seri hale getirilmiş iletileri işlemesini sağlar. İkinci hesaplama, kullanılabilir işlemcilerin sayısına eşit olan en yüksek paralellik derecesini belirttiğinden, birinciye benzer. Bu, veri akışı bloğunun paralel olarak birden çok işlem gerçekleştirmesini sağlar.  
  
 [!code-csharp[TPLDataflow_DegreeOfParallelism#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_degreeofparallelism/cs/dataflowdegreeofparallelism.cs#1)]
 [!code-vb[TPLDataflow_DegreeOfParallelism#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_degreeofparallelism/vb/dataflowdegreeofparallelism.vb#1)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Varsayılan olarak, her önceden tanımlı veri akışı bloğu iletileri iletilerin alındığı sırada yayar.  1 ' den büyük bir maksimum paralellik derecesi belirttiğinizde birden çok ileti aynı anda işlense de, bunlar alındıkları sırada yayılırlar.  
  
 <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A> özelliği en büyük paralellik derecesini temsil ettiğinden, veri akışı bloğu belirttiğinizden daha düşük derecede paralellikle çalışabilir. Veri akışı bloğu, işlevsel gereksinimlerini karşılamak için veya kullanılabilir sistem kaynaklarının yetersizliği nedeniyle hesaba daha az paralellik kullanır. Veri akışı bloğu, belirtenden daha fazla paralellik derecesini hiçbir şekilde seçmez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)

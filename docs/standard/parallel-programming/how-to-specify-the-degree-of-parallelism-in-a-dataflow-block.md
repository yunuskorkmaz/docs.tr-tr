---
title: "Nasıl yapılır: Veri Akışı Bloğunda Paralellik Derecesini Belirtme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dataflow block, specifying parallelism in TPL
- Task Parallel Library, dataflows
- TPL dataflow library, specifying parallelism
ms.assetid: e4088541-ee05-40db-95f5-147cfe62fde7
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c1ccd64a9acbc75a30984719671af2dc7dda6922
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-specify-the-degree-of-parallelism-in-a-dataflow-block"></a>Nasıl yapılır: Veri Akışı Bloğunda Paralellik Derecesini Belirtme
Bu belge nasıl ayarlanacağını açıklar <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A?displayProperty=nameWithType> aynı anda birden fazla iletiyi işlemek için bir yürütme veri akışı bloğu etkinleştirmek için özellik. Uzun süre çalışan hesaplama gerçekleştirir bir veri akışı bloğu varsa ve iletileri paralel işleme yararlanabilir Bunun yapılması yararlıdır. Bu örnekte <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=nameWithType> eşzamanlı olarak; ancak birden çok veri akışı işlemlerini gerçekleştirmek için sınıf, maksimum paralellik derecesi TPL veri akışı kitaplığı sağlar, önceden tanımlanmış yürütme blok türlerinden birini belirtebilirsiniz <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType>, ve <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType>.  
  
> [!TIP]
>  TPL veri akışı kitaplığı ( <xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> ad alanı) ile dağıtılmaz [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. Yüklemek için <xref:System.Threading.Tasks.Dataflow> ad alanı, projenizi açın [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], seçin **NuGet paketlerini Yönet** proje menüsünden ve çevrimiçi arama `Microsoft.Tpl.Dataflow` paket.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, iki veri akışı hesaplamalar gerçekleştirir ve her işlem için gereken süre yazdırır. İlk hesaplama varsayılan olan bir maksimum paralellik derecesi 1 ' in belirtir. Bir maksimum paralellik derecesi 1 iletileri seri olarak işlemek veri akışı bloğu neden olur. İkinci hesaplama ilk benzer bir en fazla kullanılabilir işlemci sayısına eşittir paralellik derecesini belirtir. Bu paralel olarak birden çok işlemlerini gerçekleştirmek veri akışı bloğu sağlar.  
  
 [!code-csharp[TPLDataflow_DegreeOfParallelism#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_degreeofparallelism/cs/dataflowdegreeofparallelism.cs#1)]
 [!code-vb[TPLDataflow_DegreeOfParallelism#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_degreeofparallelism/vb/dataflowdegreeofparallelism.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Örnek kodu kopyalayın ve bir Visual Studio projesi yapıştırın veya adlı bir dosyaya yapıştırın `DataflowDegreeOfParallelism.cs` (`DataflowDegreeOfParallelism.vb` için [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), ve ardından Visual Studio komut istemi penceresinde aşağıdaki komutu çalıştırın.  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowDegreeOfParallelism.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **Vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowDegreeOfParallelism.vb**  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Varsayılan olarak, her önceden tanımlanmış veri akışı bloğu iletileri alındığı sırada ileti yayar.  Maksimum paralellik 1'den büyük olan derecesi belirttiğinizde birden fazla ileti aynı anda işlenir ancak bunlar hala çıkışı bunlar alındığı sırada yayılır.  
  
 <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A> özelliği en büyük paralellik derecesini temsil ettiğinden, veri akışı bloğu belirttiğinizden daha düşük derecede paralellikle çalışabilir. Veri akışı bloğu küçük paralellik derecesi işlevsel gereksinimlerini karşılamak için veya mevcut sistem kaynaklarının yetersizliği için hesap için kullanabilirsiniz. Bir veri akışı bloğu, belirttiğiniz daha büyük bir paralellik derecesi hiçbir zaman seçer.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)

---
title: "Nasıl yapılır: Birden Fazla Kaynaktan Okumak için JoinBlock'u Kullanma"
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
- Task Parallel Library, dataflows
- TPL dataflow library, joining blocks in
- dataflow blocks, joining in TPL
ms.assetid: e9c1ada4-ac57-4704-87cb-2f5117f8151d
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: fa5f531257c0593f615e4620b56b2ef581ac143c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-use-joinblock-to-read-data-from-multiple-sources"></a>Nasıl yapılır: Birden Fazla Kaynaktan Okumak için JoinBlock'u Kullanma
Bu belge nasıl kullanılacağını açıklamaktadır <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> birden fazla kaynaktan veri bulunduğunda bir işlemi gerçekleştirmek için sınıf. Ayrıca, doyumsuz olmayan mod bir veri kaynağını daha verimli bir şekilde paylaşmak birden fazla birleştirme blokları etkinleştirmek için nasıl kullanılacağını gösterir.  
  
> [!TIP]
>  TPL veri akışı kitaplığı (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> ad alanı) ile dağıtılmaz [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. Yüklemek için <xref:System.Threading.Tasks.Dataflow> ad alanı, projenizi açın [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], seçin **NuGet paketlerini Yönet** proje menüsünden ve çevrimiçi arama `Microsoft.Tpl.Dataflow` paket.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, üç kaynak türleri, tanımlar `NetworkResource`, `FileResource`, ve `MemoryResource`ve kaynakları kullanılabilir duruma geldiğinde işlemleri gerçekleştirir. Bu örnek gerektiren bir `NetworkResource` ve `MemoryResource` ilk işlemi gerçekleştirmek için çifti ve `FileResource` ve `MemoryResource` ikinci bir işlem gerçekleştirmek için çifti. Tüm gerekli kaynaklar kullanılabilir olduğunda gerçekleşmesi bu işlemleri etkinleştirmek için bu örnek kullanır <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> sınıfı. Zaman bir <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> nesne tüm kaynaklardan gelen verileri alır, bu olduğundan, hedef verilerin yayar bir <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> nesnesi. Her ikisi de <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> nesnelerini okuma alanının paylaşılan havuzundan `MemoryResource` nesneleri.  
  
 [!code-csharp[TPLDataflow_NonGreedyJoin#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_nongreedyjoin/cs/nongreedyjoin.cs#1)]
 [!code-vb[TPLDataflow_NonGreedyJoin#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_nongreedyjoin/vb/nongreedyjoin.vb#1)]  
  
 Paylaşılan havuzu verimli kullanımını etkinleştirmek için `MemoryResource` nesneleri, bu örnek belirtir bir <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions> olan nesneyi <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions.Greedy%2A> özelliğini `False` oluşturmak için <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> doyumsuz olmayan modda hareket nesneleri. Bir her kaynaktan kullanılabilir hale gelene kadar doyumsuz olmayan birleştirme blok gelen tüm iletilerin erteler. Ertelenen iletilerini başka bir bloğu tarafından kabul edildi, birleştirme blok işlemi yeniden başlatır. Doyumsuz olmayan modu verileri için diğer blokları bekleyin gibi ilerleme gerçekleştirmek için bir veya daha fazla kaynak blokları paylaşmak birleştirme blokları sağlar. Bu örnekte, bir `MemoryResource` nesne eklenmiş olup `memoryResources` havuz, ilk birleştirme ikinci veri kaynağı almak için blok ilerleme yapabilir. Bu örnek doyumsuz modunu kullanacak şekilde olsaydı, varsayılan olarak, bir birleşim blok olduğu sürebilir `MemoryResource` nesne ve ikinci bir kaynak kullanılabilir olmasını bekleyin. Bir birleştirme blok kendi ikinci veri kaynağı varsa, ancak bunu ilerleme yapılamıyor, çünkü `MemoryResource` nesne bir birleşim bloğu tarafından alınmış.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Örnek kodu kopyalayın ve bir Visual Studio projesi yapıştırın veya adlı bir dosyaya yapıştırın `DataflowNonGreedyJoin.cs` (`DataflowNonGreedyJoin.vb` için [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), ve ardından Visual Studio komut istemi penceresinde aşağıdaki komutu çalıştırın.  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowNonGreedyJoin.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **Vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowNonGreedyJoin.vb**  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Doyumsuz olmayan birleştirmeler kullanımını da kilitlenme uygulamanızda önlemenize yardımcı olabilir. Bir yazılım uygulamasında *kilitlenme* iki veya daha çok işlemler her bir kaynak basılı tutun ve karşılıklı olarak başka bir kaynağın serbest bırakmak başka bir işlemin tamamlanmasını beklemek oluşur. İki tanımlayan bir uygulamayı göz önünde bulundurun <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> nesneleri. Her iki nesneleri iki paylaşılan kaynak bloklarından verilerini okur. Her iki birleştirme blokları birbirini diğer kaynağı yayımlamayı bekleyin çünkü doyumsuz modunda bir birleşim blok ilk kaynağından okur ve ikinci birleştirme bloğu ikinci kaynağından okur uygulama kilitlenme. Doyumsuz olmayan modda her birleştirme bloğu okuma kaynaklarının yalnızca tüm veriler kullanılabilir olduğunda ve bu nedenle, kilitlenme riski ortadan.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)

---
title: "Nasıl yapılır: Veri Akışı Bloklarının Bağlantısını Kaldırma"
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
- dataflow blocks, unlinking in TPL
- Task Parallel Library, dataflows
- TPL dataflow library, unlinking dataflow blocks
ms.assetid: 40f0208d-4618-47f7-85cf-4913d07d2d7d
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 41f1b83fab6ff44e69ac2f010f70e6e254341f5e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-unlink-dataflow-blocks"></a>Nasıl yapılır: Veri Akışı Bloklarının Bağlantısını Kaldırma
Bu belge, bir hedef veri akışı blok kaynağından bağlantısının nasıl kaldırılacağını açıklar.  
  
> [!TIP]
>  TPL veri akışı kitaplığı (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> ad alanı) ile dağıtılmaz [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. Yüklemek için <xref:System.Threading.Tasks.Dataflow> ad alanı, projenizi açın [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], seçin **NuGet paketlerini Yönet** proje menüsünden ve çevrimiçi arama `Microsoft.Tpl.Dataflow` paket.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, üç oluşturur <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> nesneleri, her hangi çağrılarının `TrySolution` bir değeri hesaplamak için yöntem. Bu örnek, yalnızca ilk çağrıda sonucundan gerektirir `TrySolution` tamamlamak için.  
  
 [!code-csharp[TPLDataflow_ReceiveAny#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_receiveany/cs/dataflowreceiveany.cs#1)]
 [!code-vb[TPLDataflow_ReceiveAny#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_receiveany/vb/dataflowreceiveany.vb#1)]  
  
 İlk değer almasını <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> bittikten nesnesi, bu örnek tanımlar `ReceiveFromAny(T)` yöntemi. `ReceiveFromAny(T)` Yöntemi kabul eden bir dizi <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> nesneleri ve bu nesnelerin her biri bağlantılar bir <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> nesnesi. Kullandığınızda <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> yöntemi bir kaynak veri akışı bloğu kaynak, bir hedef blok bağlamak için veri olarak kullanılabilir hale geldiğinde hedef iletileri yayar. Çünkü <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> sınıfı sunulur, ilk iletiyi kabul `ReceiveFromAny(T)` yöntemi çağrılarak sonucu üretir <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> yöntemi. Bu için sunulan ilk ileti oluşturur <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> nesnesi. <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> Yöntemi alır aşırı yüklenmiş bir sürümü olan bir <xref:System.Boolean> parametresi `unlinkAfterOne` , onu ayarlandığında `True`, hedef kaynak sunucudan bir iletiyi aldıktan sonra hedef bağlantısını kesmek için kaynak blok bildirir. Önemlidir <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> çünkü kendi kaynaklardan bağlantısını nesnesine kaynakları dizisi arasındaki ilişkiyi ve <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> nesne sonra gerekli artık <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> nesnesini bir ileti alır.  
  
 Kalan çağrılar etkinleştirmek için `TrySolution` bunlardan birini bir değeri hesaplar sonra sona erdirmek için `TrySolution` metodu bir <xref:System.Threading.CancellationToken> çağrısından sonra iptal nesne `ReceiveFromAny(T)` döndürür. <xref:System.Threading.SpinWait.SpinUntil%2A> Yöntemi döndürür bu <xref:System.Threading.CancellationToken> nesnesi iptal edilir.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Örnek kodu kopyalayın ve bir Visual Studio projesi yapıştırın veya adlı bir dosyaya yapıştırın `DataflowReceiveAny.cs` (`DataflowReceiveAny.vb` için [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), ve ardından Visual Studio komut istemi penceresinde aşağıdaki komutu çalıştırın.  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **Vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.vb**  
  
## <a name="robust-programming"></a>Güçlü Programlama  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)

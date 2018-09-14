---
title: 'Nasıl yapılır: Veri Akışı Bloklarının Bağlantısını Kaldırma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dataflow blocks, unlinking in TPL
- Task Parallel Library, dataflows
- TPL dataflow library, unlinking dataflow blocks
ms.assetid: 40f0208d-4618-47f7-85cf-4913d07d2d7d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bc0f266169a2d82bb76355febd58b2268907fe97
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45618918"
---
# <a name="how-to-unlink-dataflow-blocks"></a>Nasıl yapılır: Veri Akışı Bloklarının Bağlantısını Kaldırma
Bu belge, bir hedef veri akışı bloğu kaynağından bağlantısının nasıl kaldırılacağını açıklar.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a>Örnek  
 Aşağıdaki örnek, üç oluşturur <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> nesneler, her biri çağıran `TrySolution` bir değeri hesaplamak için yöntemi. Bu örnek yalnızca ilk çağrıda sonuçtan gerektirir `TrySolution` tamamlanması.  
  
 [!code-csharp[TPLDataflow_ReceiveAny#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_receiveany/cs/dataflowreceiveany.cs#1)]
 [!code-vb[TPLDataflow_ReceiveAny#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_receiveany/vb/dataflowreceiveany.vb#1)]  
  
 İlk değeri almaya <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> biten nesne, bu örnek tanımlar `ReceiveFromAny(T)` yöntemi. `ReceiveFromAny(T)` Yöntemi, bir dizi kabul <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> nesneler ve bağlantılar için bu nesnelerin her biri bir <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> nesne. Kullanırken <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> yöntemi bir kaynak veri akışı bloğunu hedef bloğa, kaynak bağlamak için veri kullanılabilir olduğunda hedef iletileri yayar. Çünkü <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> sınıf sunulur, ilk iletiyi kabul `ReceiveFromAny(T)` yöntemi çağırarak sonucunu üreten <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> yöntemi. Bu şekilde sunulan ilk ileti oluşturur <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> nesne. <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> Yöntemi, alan bir aşırı yüklenmiş sürümüne sahip bir <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions> nesnesi ile bir <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions.MaxMessages> özelliği, ayarlandığında `1`, hedef, kaynaktan bir ileti aldıktan sonra hedef bağlantısını kaldırmak için kaynak bloktaki bildirir . Önemlidir <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> kaynaktan çünkü bağlantısını için nesne dizisi kaynakları arasındaki ilişkiyi ve <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> nesne sonra gerekli artık <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> nesnesi bir ileti alır.  
  
 Kalan çağrılar için etkinleştirmek için `TrySolution` bunlardan biri bir değeri hesaplar sonra `TrySolution` yöntemi bir <xref:System.Threading.CancellationToken> çağrısından sonra iptal edilen bir nesne `ReceiveFromAny(T)` döndürür. <xref:System.Threading.SpinWait.SpinUntil%2A> Yöntemi döndürür bu <xref:System.Threading.CancellationToken> nesnesi iptal edildi.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Örnek kodu kopyalayın ve bir Visual Studio projesine yapıştırın veya adlı bir dosyaya yapıştırın `DataflowReceiveAny.cs` (`DataflowReceiveAny.vb` Visual Basic için), ve ardından bir Visual Studio komut istemi penceresinde aşağıdaki komutu çalıştırın.  
  
 Visual C#  
  
 **csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.cs**  
  
 Visual Basic  
  
 **Vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.vb**  

## <a name="see-also"></a>Ayrıca bkz.

- [Veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)

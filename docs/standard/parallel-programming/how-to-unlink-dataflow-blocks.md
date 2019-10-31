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
ms.openlocfilehash: b49cfc9730ba154202baf15093a54ba3ce0e2a8a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139301"
---
# <a name="how-to-unlink-dataflow-blocks"></a>Nasıl yapılır: Veri Akışı Bloklarının Bağlantısını Kaldırma
Bu belge, hedef veri akışı bloğunun kaynağından nasıl bağlantısını kaldırmayı açıklar.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a>Örnek  
 Aşağıdaki örnek, her biri bir değeri hesaplamak için `TrySolution` yöntemini çağıran üç <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> nesnesi oluşturur. Bu örnek, `TrySolution` için yalnızca ilk çağrıdan elde edilen sonucun bitmesini gerektirir.  
  
 [!code-csharp[TPLDataflow_ReceiveAny#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_receiveany/cs/dataflowreceiveany.cs#1)]
 [!code-vb[TPLDataflow_ReceiveAny#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_receiveany/vb/dataflowreceiveany.vb#1)]  
  
 Bunu izleyen ilk <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> nesnesinden değeri almak için, bu örnek `ReceiveFromAny(T)` yöntemini tanımlar. `ReceiveFromAny(T)` yöntemi bir <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> nesneleri dizisini kabul eder ve bu nesnelerin her birini bir <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> nesnesine bağlar. Kaynak veri akışı bloğunu hedef bloğa bağlamak için <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> yöntemini kullandığınızda, kaynak, veriler kullanılabilir hale geldiğinde iletileri hedefe yayar. <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> sınıfı yalnızca sunulan ilk iletiyi kabul ettiğinden, `ReceiveFromAny(T)` yöntemi <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> yöntemini çağırarak sonucunu üretir. Bu, <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> nesnesine sunulan ilk iletiyi oluşturur. <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> yöntemi, `1`olarak ayarlandığında, kaynak bloğunun kaynaktan bir ileti aldıktan sonra hedefin bağlantısını kesmek için bir <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions.MaxMessages> özelliğine sahip bir <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions> nesnesi alan aşırı yüklenmiş bir sürüme sahiptir. <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> nesnesi bir ileti aldıktan sonra, kaynak dizisi ve <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> nesnesi arasındaki ilişki artık gerekli olmadığından, <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> nesnenin kaynaklarından bağlantısı kaldırmak önemlidir.  
  
 `TrySolution` için kalan çağrıların, bir değer hesapladıktan sonra sona erdirmek için, `TrySolution` yöntemi `ReceiveFromAny(T)` dönüşe yapılan çağrıdan sonra iptal edilen bir <xref:System.Threading.CancellationToken> nesnesi alır. <xref:System.Threading.SpinWait.SpinUntil%2A> yöntemi bu <xref:System.Threading.CancellationToken> nesnesi iptal edildiğinde döndürür.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)

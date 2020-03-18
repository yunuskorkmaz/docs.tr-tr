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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139301"
---
# <a name="how-to-unlink-dataflow-blocks"></a>Nasıl yapılır: Veri Akışı Bloklarının Bağlantısını Kaldırma
Bu belge, hedef veri akışı bloğunun kaynağından nasıl çıkarılabildiğini açıklar.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a>Örnek  
 Aşağıdaki örnek, her <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> biri bir değeri `TrySolution` hesaplamak için yöntemi çağıran üç nesne oluşturur. Bu örnek, yalnızca bitirmek için `TrySolution` ilk çağrıdan sonucu gerektirir.  
  
 [!code-csharp[TPLDataflow_ReceiveAny#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_receiveany/cs/dataflowreceiveany.cs#1)]
 [!code-vb[TPLDataflow_ReceiveAny#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_receiveany/vb/dataflowreceiveany.vb#1)]  
  
 Bu örnek, tamamlayan <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> ilk nesneden değeri almak için `ReceiveFromAny(T)` yöntemi tanımlar. Yöntem `ReceiveFromAny(T)` bir <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> dizi nesne kabul eder ve bu nesnelerin <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> her birini bir nesneye bağlar. Kaynak veri <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> akışı bloğunu hedef bloğa bağlamak için metodu kullandığında, kaynak veri kullanılabilir hale geldiğinde iletileri hedefe yayır. <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> Sınıf yalnızca sunulduğu ilk iletiyi kabul ettiği `ReceiveFromAny(T)` için, <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> yöntem yöntemi çağırarak sonucunu üretir. Bu, <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> nesneye sunulan ilk iletiyi üretir. Yöntem, <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> hedef <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions> <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions.MaxMessages> `1`kaynaktan bir ileti aldıktan sonra kaynak bloğunun hedeften bağlantısını kaldırmasını söyleyen bir nesneyi bir özelliğe sahip alan aşırı yüklü bir sürüme sahiptir. Nesne bir ileti aldıktan sonra kaynak ve <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> nesne dizisi arasındaki ilişki artık gerekli olmadığından, nesnenin kaynaklarından bağlantısını kaldırması önemlidir. <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601>  
  
 Kalan `TrySolution` çağrıların bir değeri hesapladıktan sonra sona ermesini `TrySolution` sağlamak <xref:System.Threading.CancellationToken> için, yöntem geri döndürme `ReceiveFromAny(T)` çağrısından sonra iptal edilen bir nesne alır. Bu <xref:System.Threading.SpinWait.SpinUntil%2A> <xref:System.Threading.CancellationToken> nesne iptal edildiğinde yöntem döndürür.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)

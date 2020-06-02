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
ms.openlocfilehash: 8af978ca2ca237988dae8328656d70574dbc1f14
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288062"
---
# <a name="how-to-unlink-dataflow-blocks"></a>Nasıl yapılır: Veri Akışı Bloklarının Bağlantısını Kaldırma
Bu belge, hedef veri akışı bloğunun kaynağından nasıl bağlantısını kaldırmayı açıklar.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a>Örnek  
 Aşağıdaki örnek <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> , her biri `TrySolution` bir değeri hesaplamak için yöntemini çağıran üç nesne oluşturur. Bu örnek, yalnızca ilk çağrının `TrySolution` bitmesini gerektirir.  
  
 [!code-csharp[TPLDataflow_ReceiveAny#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_receiveany/cs/dataflowreceiveany.cs#1)]
 [!code-vb[TPLDataflow_ReceiveAny#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_receiveany/vb/dataflowreceiveany.vb#1)]  
  
 Bunu izleyen ilk nesneden değeri almak için <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> , bu örnek `ReceiveFromAny(T)` yöntemini tanımlar. `ReceiveFromAny(T)`Yöntemi nesne dizisini kabul eder <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> ve bu nesnelerin her birini bir nesnesine bağlar <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> . <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A>Kaynak veri akışı bloğunu bir hedef bloğa bağlamak için yöntemini kullandığınızda, kaynak verileri kullanılabilir hale geldiğinde, kaynak iletileri hedefe yayar. <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601>Sınıfı yalnızca sunulan ilk iletiyi kabul ettiğinden, yöntemi `ReceiveFromAny(T)` yöntemini çağırarak sonucunu üretir <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> . Bu, nesnesine sunulan ilk iletiyi oluşturur <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> . <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A>Yöntemi, olarak ayarlandığında bir özelliği olan bir nesneyi alan aşırı yüklenmiş bir sürüme sahiptir <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions> <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions.MaxMessages> `1` , hedef kaynaktan bir ileti aldıktan sonra kaynak bloğunu hedefin bağlantısını kesmeyi söyler. <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601>Kaynak dizisi ile nesne arasındaki ilişki <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> artık <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> nesne bir ileti aldıktan sonra gerekli olmadığından, nesnenin kaynaklarından bağlantısı kaldırmak önemlidir.  
  
 Kalan çağrıların bir `TrySolution` değer hesapladıktan sonra sona erdirmek için, `TrySolution` Bu yöntem, <xref:System.Threading.CancellationToken> dönüş çağrısının ardından iptal edilen bir nesneyi alır `ReceiveFromAny(T)` . <xref:System.Threading.SpinWait.SpinUntil%2A>Yöntemi, bu <xref:System.Threading.CancellationToken> nesne iptal edildiğinde döndürür.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri akışı](dataflow-task-parallel-library.md)

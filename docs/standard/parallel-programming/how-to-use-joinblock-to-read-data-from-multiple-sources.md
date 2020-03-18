---
title: "Nasıl yapılır: Birden Fazla Kaynaktan Okumak için JoinBlock'u Kullanma"
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, joining blocks in
- dataflow blocks, joining in TPL
ms.assetid: e9c1ada4-ac57-4704-87cb-2f5117f8151d
ms.openlocfilehash: 66fd7ed7a98b8be8f88f65ecb52710a1e40af778
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139743"
---
# <a name="how-to-use-joinblock-to-read-data-from-multiple-sources"></a>Nasıl yapılır: Birden Fazla Kaynaktan Okumak için JoinBlock'u Kullanma
Bu belge, birden <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> çok kaynaktan veri kullanılabilir olduğunda bir işlemi gerçekleştirmek için sınıfın nasıl kullanılacağını açıklar. Ayrıca, birden çok birleştirme bloğunun bir veri kaynağını daha verimli bir şekilde paylaşmasını sağlamak için açgözlü olmayan modun nasıl kullanılacağını da gösterir.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `NetworkResource`üç kaynak türü `FileResource`tanımlar, , , ve `MemoryResource`, kaynaklar kullanılabilir olduğunda işlemleri gerçekleştirir. Bu örnek, `NetworkResource` `MemoryResource` ikinci işlemi gerçekleştirmek için ilk `FileResource` işlemi `MemoryResource` gerçekleştirmek için bir ve çift ve çifti gerektirir. Gerekli tüm kaynaklar kullanılabilir olduğunda bu işlemlerin gerçekleşmesini <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> sağlamak için, bu örnek sınıfı kullanır. Bir <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> nesne tüm kaynaklardan veri aldığında, bu verileri hedefine yayıltır <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> ve bu örnekte bir nesnedir. Her <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> iki nesne de paylaşılan `MemoryResource` bir nesne havuzundan okunur.  
  
 [!code-csharp[TPLDataflow_NonGreedyJoin#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_nongreedyjoin/cs/nongreedyjoin.cs#1)]
 [!code-vb[TPLDataflow_NonGreedyJoin#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_nongreedyjoin/vb/nongreedyjoin.vb#1)]  
  
 Paylaşılan `MemoryResource` nesne havuzunun verimli kullanımını etkinleştirmek için, bu <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions> örnekte <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions.Greedy%2A> açgözlü olmayan `False` modda hareket eden nesneler oluşturmak <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> üzere ayarlanmış bir özellik olan bir nesne belirtilmiştir. Açgözlü olmayan bir birleştirme bloğu, her kaynaktan bir ileti kullanılabilir olana kadar gelen tüm iletileri erteler. Ertelenen iletilerden herhangi biri başka bir blok tarafından kabul edilirse, birleştirme bloğu işlemi yeniden başlatır. Açgözlü olmayan mod, diğer bloklar veri beklerken bir veya daha fazla kaynak bloğunu paylaşan birleştirme bloklarının ilerleme kaydetmesini sağlar. Bu örnekte, `MemoryResource` havuza bir `memoryResources` nesne eklenirse, ikinci veri kaynağını alan ilk birleştirme bloğu ileri ilerleme kaydedebilir. Bu örnekte varsayılan olan açgözlü mod kullanılırsa, bir birleştirme `MemoryResource` bloğu nesneyi alabilir ve ikinci kaynağın kullanılabilir olmasını bekleyebilir. Ancak, diğer birleştirme bloğunda ikinci veri kaynağı varsa, `MemoryResource` nesne diğer birleştirme bloğu tarafından alındığından ilerleme kaydedemez.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Açgözlü olmayan birleştirmelerin kullanımı, uygulamanızdaki kilitlenmeyi önlemenize de yardımcı olabilir. Bir yazılım uygulamasında, iki veya daha fazla işlemin her biri bir kaynağı tuttuğunda ve başka bir işlemin başka bir kaynağı serbest bırakılmasını karşılıklı olarak beklediğinde *kilitlenme* oluşur. İki <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> nesneyi tanımlayan bir uygulama düşünün. Her iki nesnenin her biri paylaşılan iki kaynak bloğundaki verileri okur. Açgözlü modda, bir birleştirme bloğu ilk kaynaktan okursa ve ikinci birleştirme bloğu ikinci kaynaktan okursa, her ikisi de birleştirme blokları karşılıklı olarak diğerinin kaynağını serbest bırakmasını beklediğinden uygulama kilitlenebilir. Açgözlü olmayan modda, her birleştirme bloğu yalnızca tüm veriler kullanılabilir olduğunda kendi kaynaklarından okur ve bu nedenle kilitlenme riski ortadan kalkar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)

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
ms.openlocfilehash: cd2f5c65f45d83ef23643dcc747a748bb8ba89d9
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290830"
---
# <a name="how-to-use-joinblock-to-read-data-from-multiple-sources"></a>Nasıl yapılır: Birden Fazla Kaynaktan Okumak için JoinBlock'u Kullanma
Bu belgede, <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> verileri birden çok kaynaktan kullanılabilir olduğunda bir işlemi gerçekleştirmek için sınıfının nasıl kullanılacağı açıklanmaktadır. Ayrıca, birden çok JOIN bloklarının bir veri kaynağını daha verimli bir şekilde paylaşmasını sağlamak için doyumsuz olmayan modu nasıl kullanacağınızı gösterir.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a>Örnek  
 Aşağıdaki örnek üç kaynak türünü tanımlar,, `NetworkResource` `FileResource` , ve `MemoryResource` , kaynakları kullanılabilir hale geldiğinde işlemleri gerçekleştirir. Bu örnek, `NetworkResource` `MemoryResource` `FileResource` `MemoryResource` ikinci işlemi gerçekleştirmek için ilk işlemi ve bir ve çiftini gerçekleştirmek üzere bir ve çifti gerektirir. Tüm gerekli kaynaklar kullanılabilir olduğunda bu işlemlerin gerçekleşmesini sağlamak için, bu örnek <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> sınıfını kullanır. Bir <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> nesne tüm kaynaklardan veri aldığında, bu verileri hedefine yayar ve bu örnek bir <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> nesnedir. Her iki <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> nesne de paylaşılan bir nesne havuzundan okundu `MemoryResource` .  
  
 [!code-csharp[TPLDataflow_NonGreedyJoin#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_nongreedyjoin/cs/nongreedyjoin.cs#1)]
 [!code-vb[TPLDataflow_NonGreedyJoin#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_nongreedyjoin/vb/nongreedyjoin.vb#1)]  
  
 Paylaşılan nesneler havuzunun verimli kullanımını sağlamak için `MemoryResource` Bu örnek, <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions> <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions.Greedy%2A> `False` <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> doyumsuz olmayan modda davranan nesneleri oluşturmak için özelliği olarak ayarlanmış bir nesneyi belirtir. Doyumsuz olmayan bir JOIN bloğu, her kaynaktan bir tane kullanılabilir olana kadar gelen tüm iletileri erteler. Ertelenen iletilerden herhangi biri başka bir blok tarafından kabul edildiyse, JOIN bloğu işlemi yeniden başlatır. Doyumsuz olmayan mod, diğer blokların veri beklemesi durumunda ileri ilerleme durumuna getirmek için bir veya daha fazla kaynak bloğunu paylaşan JOIN blokları sağlar. Bu örnekte, `MemoryResource` havuza bir nesne eklenirse `memoryResources` , ikinci veri kaynağını almak için ilk JOIN bloğu ilerlemeye devam edebilir. Bu örnek, varsayılan olan doyumsuz modunu kullanıyorsa, bir JOIN bloğu `MemoryResource` nesneyi alabilir ve ikinci kaynağın kullanılabilir hale gelmesini bekleyebilir. Ancak, diğer bir JOIN bloğunun ikinci veri kaynağı varsa, `MemoryResource` nesne diğer bir JOIN bloğu tarafından alındığından ileri ilerleme yapamaz.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Doyumsuz olmayan birleşimlerin kullanımı uygulamanızda kilitlenmeyi önlemenize de yardımcı olabilir. Bir yazılım uygulamasında, iki veya daha fazla işlem bir kaynağı her tutar ve başka bir işlemin başka bir kaynağı serbest bırakma işlemini karşılıklı olarak beklemek durumunda *kilitlenme* oluşur. İki nesneyi tanımlayan bir uygulama düşünün <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> . Her iki nesnenin her ikisi de iki paylaşılan kaynak blobundan okur. Doyumsuz modunda, bir JOIN bloğunun ilk kaynaktan okuduğu ve ikinci kaynaktan ikinci bir JOIN bloğunun okuduğu, uygulama kilitlenmeye neden olabileceğinden, her iki JOIN bloğu, kaynağını serbest bırakmalarını karşılıklı olarak bekler. Doyumsuz olmayan modda, her bir JOIN bloğu kaynaklarından yalnızca tüm veriler kullanılabilir olduğunda okur ve bu nedenle, kilitlenme riski ortadan kalkar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri akışı](dataflow-task-parallel-library.md)

---
title: 'İzlenecek Yol: Özel bir Veri Akışı Blok Türü Oluşturma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, creating custom dataflow blocks
- dataflow blocks, creating custom in TPL
ms.assetid: a6147146-0a6a-4d9b-ab0f-237b3c1ac691
ms.openlocfilehash: cb953952bbed90edd2db799e92d44ec9f062babf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139886"
---
# <a name="walkthrough-creating-a-custom-dataflow-block-type"></a>İzlenecek Yol: Özel bir Veri Akışı Blok Türü Oluşturma
TPL veri akışı kitaplığı çeşitli işlevleri etkinleştiren çeşitli veri akışı blok türleri sağlasa da, özel blok türleri de oluşturabilirsiniz. Bu belgede özel davranış uygulayan bir veri akışı blok türünün nasıl oluşturulacağı açıklanmaktadır.  
  
## <a name="prerequisites"></a>Prerequisites  
 Bu belgeyi okurken [veri akışını](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) okuyun.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="defining-the-sliding-window-dataflow-block"></a>Kayan pencere veri akışı bloğunu tanımlama  
 Giriş değerlerinin arabelleğe alınması ve sonra bir kayan pencere halinde çıktısını gerektiren bir veri akışı uygulaması düşünün. Örneğin, {0, 1, 2, 3, 4, 5} giriş değerleri ve bir pencere boyutu için, bir kayan pencere veri akışı bloğu, {0, 1, 2}, {1, 2, 3}, {2, 3, 4} ve {3, 4, 5} çıkış dizilerini üretir. Aşağıdaki bölümlerde, bu özel davranışı uygulayan bir veri akışı blok türü oluşturmanın iki yolu açıklanır. İlk teknik, bir <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> nesnesinin işlevlerini ve bir <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> nesnesini tek bir yayıcı bloğunda birleştirmek için <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> yöntemini kullanır. İkinci teknik, <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> türeten bir sınıfı tanımlar ve özel davranış gerçekleştirmek için mevcut işlevselliği birleştirir.  
  
## <a name="using-the-encapsulate-method-to-define-the-sliding-window-dataflow-block"></a>Kayan pencere veri akışı bloğunu tanımlamak için yalıt yöntemini kullanma  
 Aşağıdaki örnek, bir hedeften ve kaynaktan bir yayıcı bloğu oluşturmak için <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> yöntemini kullanır. Bir yayıcı bloğu, kaynak bloğunun ve hedef bloğunun veri alıcısı ve gönderici görevi görmesini sağlar.  
  
 Bu teknik, özel veri akışı işlevselliğine ihtiyacınız olduğunda faydalıdır, ancak ek yöntemler, özellikler veya alanlar sağlayan bir tür gerekmez.  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#1)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#1)]  
  
## <a name="deriving-from-ipropagatorblock-to-define-the-sliding-window-dataflow-block"></a>Kayan pencere veri akışı bloğunu tanımlamak için IPropagatorBlock 'dan türetme  
 Aşağıdaki örnekte `SlidingWindowBlock` sınıfı gösterilmektedir. Bu sınıf, bir kaynak ve bir veri hedefi olarak davranabilmesi için <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> türetilir. Önceki örnekte olduğu gibi, `SlidingWindowBlock` sınıfı var olan veri akışı blok türleri üzerine kurulmuştur. Ancak `SlidingWindowBlock` sınıfı, <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>, <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>ve <xref:System.Threading.Tasks.Dataflow.IDataflowBlock> arabirimleri için gereken yöntemleri de uygular. Bu yöntemlerin hepsi, tüm işleri önceden tanımlanmış veri akışı blok türü üyelerine iletir. Örneğin `Post` yöntemi, aynı zamanda bir <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> nesnesi olan `m_target` veri üyesine çalışır.  
  
 Bu teknik, özel veri akışı işlevselliğine ihtiyacınız olduğunda ve ayrıca ek yöntemler, özellikler veya alanlar sağlayan bir tür gerektirdiğinde yararlıdır. Örneğin, `SlidingWindowBlock` sınıfı, <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> ve <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceiveAll%2A> yöntemlerini sağlayabilmesi için <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601> de türetilir. `SlidingWindowBlock` sınıfı, kayan penceredeki öğelerin sayısını alan `WindowSize` özelliğini sağlayarak genişletilebilirliği de gösterir.  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#2)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#2)]  
  
## <a name="the-complete-example"></a>Tam Örnek  
 Aşağıdaki örnekte bu izlenecek yol için tüm kod gösterilmektedir. Ayrıca, her iki kayan pencere bloğunu bloğa yazan bir yöntemde nasıl kullanacağınızı, dosyadan okuduğunu ve sonuçları konsola nasıl yazdıracağını gösterir.  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#100)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#100)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)

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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139886"
---
# <a name="walkthrough-creating-a-custom-dataflow-block-type"></a>İzlenecek Yol: Özel bir Veri Akışı Blok Türü Oluşturma
TPL Veri Akışı Kitaplığı çeşitli işlevsellik sağlayan birkaç veri akışı bloğu türü sağlasa da, özel blok türleri de oluşturabilirsiniz. Bu belge, özel davranış uygulayan bir veri akışı bloğu türü oluşturmak için nasıl açıklanır.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu belgeyi okumadan önce [Veri Akışı'nı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) okuyun.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="defining-the-sliding-window-dataflow-block"></a>Kayan Pencere Veri Akışı Bloğunu Tanımlama  
 Giriş değerlerinin arabelleğe alınıp sonra sürgülü bir pencere şeklinde çıktısını gerektiren bir veri akışı uygulamasını düşünün. Örneğin, {0, 1, 2, 3, 4, 5} ve üç pencere boyutundaki giriş değerleri için, kayan bir pencere veri akışı bloğu çıkış dizilerini {0, 1, 2}, {1, 2, 3}, {2, 3, 4}ve {3, 4, 5} olarak üretir. Aşağıdaki bölümlerde, bu özel davranışı uygulayan bir veri akışı bloğu türü oluşturmanın iki yolu açıklayınız. İlk teknik, <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> bir nesnenin ve <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> nesnenin <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> işlevselliğini tek bir propagator bloğunda birleştirmek için yöntemi kullanır. İkinci teknik, özel davranış gerçekleştirmek için <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> varolan işlevselliği türeten ve birleştiren bir sınıf tanımlar.  
  
## <a name="using-the-encapsulate-method-to-define-the-sliding-window-dataflow-block"></a>Kayan Pencere Veri Akışı Bloğunu Tanımlamak için Kapsülleme Yöntemini Kullanma  
 Aşağıdaki örnek, <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> bir hedef ve kaynaktan bir propagator bloğu oluşturmak için yöntemi kullanır. Propagator bloğu, kaynak bloğu ve hedef bloğun alıcı ve veri gönderen olarak hareket etmesini sağlar.  
  
 Bu teknik, özel veri akışı işlevselliği gerektirdiğinde yararlıdır, ancak ek yöntemler, özellikler veya alanlar sağlayan bir tür gerekmez.  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#1)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#1)]  
  
## <a name="deriving-from-ipropagatorblock-to-define-the-sliding-window-dataflow-block"></a>Kayan Pencere Veri Akışı Bloğunu Tanımlamak için IPropagatorBlock'tan türeyen  
 Aşağıdaki örnek `SlidingWindowBlock` sınıfı gösterir. Bu sınıf, hem <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> kaynak hem de veri hedefi olarak hareket edilebilsin diye türetilmiştir. Önceki örnekte olduğu `SlidingWindowBlock` gibi, sınıf varolan veri akışı bloğu türleri üzerine inşa edilmiştir. Ancak, `SlidingWindowBlock` sınıf da <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>, , <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>ve <xref:System.Threading.Tasks.Dataflow.IDataflowBlock> arabirimleri tarafından gerekli olan yöntemleri uygular. Bu yöntemlerin tümü, önceden tanımlanmış veri akışı bloğu türü üyelerine iletilir. Örneğin, `Post` yöntem aynı zamanda bir `m_target` <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> nesne olan veri üyesi, çalışmayı erteler.  
  
 Bu teknik, özel veri akışı işlevselliği gerektirdiğinde ve ek yöntemler, özellikler veya alanlar sağlayan bir tür de gerektirdiğinde yararlıdır. Örneğin, `SlidingWindowBlock` sınıf da böylece <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601> <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> ve <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceiveAll%2A> yöntemleri sağlayabilir türetilmiştir. Sınıf `SlidingWindowBlock` ayrıca, kayan penceredeki öğe `WindowSize` sayısını alan özelliği sağlayarak genişletilebilirlik gösterir.  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#2)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#2)]  
  
## <a name="the-complete-example"></a>Tam Örnek  
 Aşağıdaki örnek, bu izbin tam kodunu gösterir. Ayrıca, her iki kayan pencere bloğunun nasıl kullanılacağını, bloya yazan, ondan okuyan ve sonuçları konsola yazdıran bir yöntemde nasıl kullanılacağını da gösterir.  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#100)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#100)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)

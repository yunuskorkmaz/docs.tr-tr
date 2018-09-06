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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7f07f1a2a7c393d70befc42a2c5b090c2c27320c
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43868623"
---
# <a name="walkthrough-creating-a-custom-dataflow-block-type"></a>İzlenecek Yol: Özel bir Veri Akışı Blok Türü Oluşturma
TPL veri akışı kitaplığı işlevleri çeşitli sağlayan birkaç veri akışı bloğu türleri sağlasa da, özel blok türleri oluşturabilirsiniz. Bu belge, özel davranış uygulayan bir veri akışı bloğu türünü oluşturmanın açıklar.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Okuma [veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) önce bu belgeyi okuyun.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="defining-the-sliding-window-dataflow-block"></a>Kayan pencere veri akışı bloğu tanımlama  
 Giriş değerleri arabelleğe alınmış ve ardından bir kayan pencere şekilde çıkış gerektiren bir veri akışı uygulamayı göz önünde bulundurun. Örneğin, giriş değeri {0, 1, 2, 3, 4, 5} ve bir pencere boyutu üç için {0, 1, 2}, çıkış dizileri kayan pencere veri akışı bloğu üretir {1, 2, 3}, {2, 3, 4} ve {3, 4, 5}. Aşağıdaki bölümlerde, bu özel davranış uygulayan bir veri akışı bloğu türünü oluşturmanın iki yolu açıklanmaktadır. İlk tekniği kullanan <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> işlevselliğini birleştirmek için yöntemi bir <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> nesnesi ve bir <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> nesnesine bir Yayıcı blok. İkinci yöntem, türetilen bir sınıf tanımlar <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> ve özel davranış gerçekleştirmek için mevcut işlevselliğini bir araya getirir.  
  
## <a name="using-the-encapsulate-method-to-define-the-sliding-window-dataflow-block"></a>Kullanarak kayan pencere veri akışı bloğu tanımlamak için bir metodu kapsüllemek  
 Aşağıdaki örnekte <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> bir Yayıcı blok bir hedef ve bir kaynak oluşturmak için yöntemi. Bir Yayıcı blok, bir kaynak blok ve bir alıcı ve gönderen veri görev yapacak bir hedef bloğu sağlar.  
  
 Özel veri akışı işlevselliğini gerektirir, ancak ek yöntemler, özellikler veya alanları sağlayan bir tür gerektirmeyen bu yöntem yararlı olur.  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#1)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#1)]  
  
## <a name="deriving-from-ipropagatorblock-to-define-the-sliding-window-dataflow-block"></a>Kayan pencere veri akışı bloğu tanımlamak için IPropagatorBlock türetme  
 Aşağıdaki örnekte gösterildiği `SlidingWindowBlock` sınıfı. Bu sınıfın türetildiği <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> böylece hem kaynak hem de veri hedefi olarak görev yapabilir. Önceki örnekte olduğu gibi `SlidingWindowBlock` sınıfı, mevcut veri akışı bloğu türleri üzerinde oluşturulur. Ancak, `SlidingWindowBlock` sınıfı da tarafından gerekli yöntemleri uygular <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>, <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>, ve <xref:System.Threading.Tasks.Dataflow.IDataflowBlock> arabirimleri. Bu yöntemler tüm İleri, önceden tanımlı veri akışı bloğu türü üyeleri çalışır. Örneğin, `Post` yöntemi erteler çalışmaya `m_target` ayrıca veri üyesi, bir <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> nesne.  
  
 Özel veri akışı işlevselliği gerektirdiği ve ayrıca ek yöntemler, özellikler veya alanları sağlayan bir tür gerektiren bu yararlı bir tekniktir. Örneğin, `SlidingWindowBlock` sınıf ayrıca türetilir <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601> sağlar, böylece <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> ve <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceiveAll%2A> yöntemleri. `SlidingWindowBlock` Sınıfı ayrıca sağlayarak genişletilebilirlik gösterir `WindowSize` özelliği kayan pencere içindeki öğelerin sayısını alır.  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#2)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#2)]  
  
## <a name="the-complete-example"></a>Tam Örnek  
 Aşağıdaki örnek, bu izlenecek yol için tam kod gösterilmektedir. Ayrıca, her iki kayan pencere blokları blokla yazar, buradan okur ve sonuçlarını konsola yazdırır bir yöntem kullanmak nasıl gösterir.  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#100)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#100)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Örnek kodu kopyalayın ve bir Visual Studio projesine yapıştırın veya adlı bir dosyaya yapıştırın `SlidingWindowBlock.cs` (`SlidingWindowBlock.vb` Visual Basic için) ve Visual Studio komut istemi penceresinde aşağıdaki komutu çalıştırın.  
  
 Visual C#  
  
 **csc.exe /r:System.Threading.Tasks.Dataflow.dll SlidingWindowBlock.cs**  
  
 Visual Basic  
  
 **Vbc.exe /r:System.Threading.Tasks.Dataflow.dll SlidingWindowBlock.vb**  

## <a name="see-also"></a>Ayrıca bkz.

- [Veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)

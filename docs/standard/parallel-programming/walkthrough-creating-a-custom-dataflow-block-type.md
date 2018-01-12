---
title: "İzlenecek Yol: Özel bir Veri Akışı Blok Türü Oluşturma"
ms.date: 03/30/2017
ms.prod: .net
ms.technology: dotnet-standard
ms.topic: article
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
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 54882ce5f646e9e790703e0951459a9fceac3bb6
ms.sourcegitcommit: 6a9030eb5bd0f00e1d144f81958adb195cfb1f6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-creating-a-custom-dataflow-block-type"></a>İzlenecek Yol: Özel bir Veri Akışı Blok Türü Oluşturma
TPL veri akışı kitaplığı işlevleri, çeşitli etkinleştirmek birkaç veri akışı blok türü sağlasa da, özel blok türleri de oluşturabilirsiniz. Bu belge, özel davranışı uygulayan bir veri akışı blok türü oluşturmayı açıklar.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Okuma [veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) önce bu belgeyi okuyun.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="defining-the-sliding-window-dataflow-block"></a>Kayan pencere veri akışı bloğu tanımlama  
 Giriş değerleri arabelleğe alınmış ve kayan bir pencere biçimde çıktı gerektiren bir veri akışı uygulaması göz önünde bulundurun. Örneğin, üç pencere boyutunu ve giriş değerler {0, 1, 2, 3, 4, 5} {0, 1, 2} çıkış dizileri kayan pencere veri akışı bloğu üretir {1, 2, 3}, {2, 3, 4} ve {3, 4, 5}. Aşağıdaki bölümlerde bu özel davranış uygulayan bir veri akışı blok türü oluşturmanın iki yolu açıklanmaktadır. İlk tekniği kullanan <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> işlevselliğini birleştirmek için yöntemi bir <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> nesne ve bir <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> bir yayılması bloğuna nesnesi. İkinci tekniği türeyen bir sınıf tanımlar <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> ve özel davranış gerçekleştirmek için varolan birleştirir.  
  
## <a name="using-the-encapsulate-method-to-define-the-sliding-window-dataflow-block"></a>Kullanarak kayan pencere veri akışı bloğu tanımlamak için yöntemi yalıtma  
 Aşağıdaki örnek kullanır <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> yöntemi bir hedef ve kaynak yayılması bloğu oluşturun. Bir kaynak bloğu ve bir alıcı ve veri göndereni görev yapması için hedef blok yayılması blok sağlar.  
  
 Özel veri akışı işlevselliği gerektiren ancak ek yöntemler, özellikler veya alanlar sağlayan bir türü gerektirmeyen Bu teknik yararlıdır.  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#1)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#1)]  
  
## <a name="deriving-from-ipropagatorblock-to-define-the-sliding-window-dataflow-block"></a>Kayan pencere veri akışı bloğu tanımlamak için IPropagatorBlock türetme  
 Aşağıdaki örnekte gösterildiği `SlidingWindowBlock` sınıfı. Bu sınıfın türetildiği <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> böylece hem kaynak hem de veri hedefi olarak davranamaz. Önceki örnekte olduğu gibi `SlidingWindowBlock` sınıfı, var olan veri akışı bloğu türlerinde oluşturulur. Ancak, `SlidingWindowBlock` sınıfı ayrıca gerekli olan yöntemleri uygulayan <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>, <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>, ve <xref:System.Threading.Tasks.Dataflow.IDataflowBlock> arabirimleri. Bu yöntemler tüm İleri önceden tanımlanmış veri akışı blok türü üyelerine çalışır. Örneğin, `Post` yöntemi erteler iş `m_target` de veri üyesi bir <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> nesnesi.  
  
 Özel veri akışı işlevselliği gerektirir ve ayrıca ek yöntemler, özellikler veya alanlar sağlayan bir türü gerektiren bu teknik yararlıdır. Örneğin, `SlidingWindowBlock` sınıfı ayrıca türetilen <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601> böylece bunu sağlayabilir <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> ve <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceiveAll%2A> yöntemleri. `SlidingWindowBlock` Sınıfı ayrıca sağlayarak genişletilebilirlik gösterir `WindowSize` özelliği kayan pencere öğelerinde sayısını alır.  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#2)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#2)]  
  
## <a name="the-complete-example"></a>Tam Örnek  
 Aşağıdaki örnek, bu kılavuz tam kod gösterilir. Ayrıca, her iki kayan pencere blokları bloğuna yazar, ondan okuyan ve sonuçlarını konsola yazdırır bir yöntem kullanmak nasıl gösterir.  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#100)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#100)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Örnek kodu kopyalayın ve bir Visual Studio projesi yapıştırın veya adlı bir dosyaya yapıştırın `SlidingWindowBlock.cs` (`SlidingWindowBlock.vb` için [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) ve Visual Studio komut istemi penceresinde aşağıdaki komutu çalıştırın.  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe /r:System.Threading.Tasks.Dataflow.dll SlidingWindowBlock.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **Vbc.exe /r:System.Threading.Tasks.Dataflow.dll SlidingWindowBlock.vb**  

## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)

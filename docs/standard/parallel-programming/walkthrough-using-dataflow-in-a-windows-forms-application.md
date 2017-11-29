---
title: "İzlenecek yol: Windows Forms Uygulaması'nda Veri Akışı Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TPL dataflow library, in Windows Forms
- Task Parallel Library, dataflows
- Windows Forms, and TPL
ms.assetid: 9c65cdf7-660c-409f-89ea-59d7ec8e127c
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d2775cc99020fd99d6e7d79cdf3e1ffcc3219146
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-using-dataflow-in-a-windows-forms-application"></a>İzlenecek yol: Windows Forms Uygulaması'nda Veri Akışı Kullanma
Bu belge, bir Windows Forms uygulaması'nda Görüntü işleme gerçekleştirmek veri akışı bloklarının bir ağ oluşturmak gösterilmiştir.  
  
 Bu örnek belirtilen klasöründen görüntü dosyaları yükler, bileşik bir görüntü oluşturur ve sonucu görüntüler. Örnek rota görüntülerine ağ üzerinden veri akışı modelini kullanır. Veri akışı modelinde iletileri göndererek bağımsız bir program bileşenlerinin birbirleriyle iletişim. Bir bileşen bir ileti aldığında, bazı eylemleri gerçekleştirir ve ardından sonucu başka bir bileşene geçirir. Bu, uygulama denetim yapıları, örneğin kullanan denetim akışı modelini, koşullu deyimler, döngüler ve benzeri işlemlerin bir programda sırasını denetlemek için karşılaştırın.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Okuma [veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) bu kılavuza başlamadan önce.  
  
> [!TIP]
>  TPL veri akışı kitaplığı (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> ad alanı) ile dağıtılmaz [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. Yüklemek için <xref:System.Threading.Tasks.Dataflow> ad alanı, projenizi açın [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], seçin **NuGet paketlerini Yönet** proje menüsünden ve çevrimiçi arama `Microsoft.Tpl.Dataflow` paket.  
 
  
## <a name="sections"></a>Bölümler  
 Bu kılavuz aşağıdaki bölümleri içerir:  
  
-   [Windows Forms uygulaması oluşturma](#winforms)  
  
-   [Veri akışı ağ oluşturma](#network)  
  
-   [Veri akışı ağ için kullanıcı arabirimi bağlanma](#ui)  
  
-   [Tam bir örnek](#complete)  
  
<a name="winforms"></a>   
## <a name="creating-the-windows-forms-application"></a>Windows Forms uygulaması oluşturma  
 Bu bölümde, temel Windows Forms uygulaması oluşturma ve denetimleri ana forma ekleme açıklar.  
  
#### <a name="to-create-the-windows-forms-application"></a>Form uygulama Windows oluşturmak için  
  
1.  İçinde [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], oluşturma bir [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] veya Visual Basic **Windows Forms uygulaması** projesi. Bu belgede, proje adı `CompositeImages`.  
  
2.  Form1.cs ana form için form tasarımcısında (Form1.vb için [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), ekleme bir <xref:System.Windows.Forms.ToolStrip> denetim.  
  
3.  Ekleme bir <xref:System.Windows.Forms.ToolStripButton> denetimini <xref:System.Windows.Forms.ToolStrip> denetim. Ayarlama <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> özelliğine <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> ve <xref:System.Windows.Forms.ToolStripItem.Text%2A> özelliğine **Klasör Seç**.  
  
4.  İkinci bir ekleme <xref:System.Windows.Forms.ToolStripButton> denetimini <xref:System.Windows.Forms.ToolStrip> denetim. Ayarlama <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> özelliğine <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, <xref:System.Windows.Forms.ToolStripItem.Text%2A> özelliğine **iptal**ve <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> özelliğine `False`.  
  
5.  Ekleme bir <xref:System.Windows.Forms.PictureBox> ana formuna nesnesi. Ayarlama <xref:System.Windows.Forms.Control.Dock%2A> özelliğine <xref:System.Windows.Forms.DockStyle.Fill>.  
  
<a name="network"></a>   
## <a name="creating-the-dataflow-network"></a>Veri akışı ağ oluşturma  
 Bu bölümde, görüntü işlemeyi gerçekleştirir veri akışı ağ oluşturmayı açıklar.  
  
#### <a name="to-create-the-dataflow-network"></a>Veri akışı ağ oluşturmak için  
  
1.  Bir başvuru System.Threading.Tasks.Dataflow.dll projenize ekleyin.  
  
2.  Sağlamak Bu Form1.cs (Form1.vb için [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) aşağıdakileri içerir `using` (`Using` içinde [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) deyimleri:  
  
     [!code-csharp[TPLDataflow_CompositeImages#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#1)]  
  
3.  Aşağıdaki veri üye ekleme `Form1` sınıfı:  
  
     [!code-csharp[TPLDataflow_CompositeImages#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#2)]  
  
4.  Aşağıdaki yöntemi ekleyin `CreateImageProcessingNetwork`, `Form1` sınıfı. Bu yöntem, görüntü işleme ağı oluşturur.  
  
     [!code-csharp[TPLDataflow_CompositeImages#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#3)]  
  
5.  Uygulama `LoadBitmaps` yöntemi.  
  
     [!code-csharp[TPLDataflow_CompositeImages#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#4)]  
  
6.  Uygulama `CreateCompositeBitmap` yöntemi.  
  
     [!code-csharp[TPLDataflow_CompositeImages#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#5)]  
  
    > [!NOTE]
    >  C# sürümü `CreateCompositeBitmap` yöntemi verimli işlenmesini etkinleştirmek için işaretçileri kullanır <xref:System.Drawing.Bitmap?displayProperty=nameWithType> nesneleri. Bu nedenle, etkinleştirmeniz gerekir **güvenli olmayan kod izin** kullanmak için seçenek projenizdeki [güvensiz](~/docs/csharp/language-reference/keywords/unsafe.md) anahtar sözcüğü. Güvenli olmayan kod içinde etkinleştirme hakkında daha fazla bilgi için bir [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] [sayfası, Proje Tasarımcısı (C#) yapı] bkz proje https://msdn.microsoft.com/library/kb4wyys2).  
  
 Aşağıdaki tabloda ağ üyeleri açıklanmaktadır.  
  
|Üye|Tür|Açıklama|  
|------------|----------|-----------------|  
|`loadBitmaps`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Bir klasörü yolunu giriş olarak alır ve bir koleksiyonunu oluşturur <xref:System.Drawing.Bitmap> nesneleri çıktı olarak.|  
|`createCompositeBitmap`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Bir koleksiyonunu alır <xref:System.Drawing.Bitmap> nesneleri giriş olarak ve bileşik bir bit eşlem çıktı olarak üretir.|  
|`displayCompositeBitmap`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|Bileşik bit eşlem formda görüntüler.|  
|`operationCancelled`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|İşlem iptal edilir ve başka bir klasör seçmek kullanıcının sağlayan belirtmek için bir resim görüntüler.|  
  
 Bir ağ oluşturmak için veri akışı blokları bağlanmak için bu örnek kullanır <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> yöntemi. <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> Yöntemi alır aşırı yüklenmiş bir sürümünü içeren bir <xref:System.Predicate%601> hedef blok kabul ediyor veya bir ileti reddeder belirler nesnesi. Bu filtreleme mekanizması yalnızca belirli değerleri almak ileti blokları sağlar. Bu örnekte, iki yoldan biriyle ağ dal. Ana dala görüntüleri diskten yükler, bileşik görüntüsünü oluşturur ve bu görüntüyü formda görüntüler. Alternatif şube geçerli işlemi iptal eder. <xref:System.Predicate%601> Nesneleri belirli iletileri reddederek alternatif şube geçmek için ana dala boyunca veri akışı blokları sağlar. Örneğin, kullanıcı veri akışı bloğu işlemi iptal `createCompositeBitmap` üreten `null` (`Nothing` içinde [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) çıktısını olarak. Veri akışı bloğu `displayCompositeBitmap` reddeder `null` için giriş değerleri ve bu nedenle, iletiyi sunulur `operationCancelled`. Veri akışı bloğu `operationCancelled` tüm iletileri kabul eder ve bu nedenle, işlemi iptal edildiğini belirtmek için bir görüntüsünü görüntüler.  
  
 Görüntü işleme ağı aşağıda gösterilmektedir.  
  
 ![Görüntü işleme ağı](../../../docs/standard/parallel-programming/media/dataflowwinforms.png "DataflowWinForms")  
  
 Çünkü `displayCompositeBitmap` ve `operationCancelled` veri akışı blokları hareket kullanıcı arabiriminde, onu önemlidir bu eylemler kullanıcı arabirimi iş parçacığı üzerinde gerçekleştirilir. Oluşturma sırasında Bunu başarmak için bu nesnelerin her sağlayan bir <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> olan nesneyi <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> özelliğini <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>. <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> Yöntemi oluşturur bir <xref:System.Threading.Tasks.TaskScheduler> geçerli eşitleme bağlamı üzerinde çalışmayı gerçekleştiren nesne. Çünkü `CreateImageProcessingNetwork` yönteminden işleyicisinden **Klasör Seç** düğmesi, kullanıcı arabiriminde çalıştığı iş parçacığı, işlemleri `displayCompositeBitmap` ve `operationCancelled` veri akışı blokları da çalıştırın kullanıcı arabirimi iş parçacığı.  
  
 Bu örnek bir paylaşılan iptal belirteci yerine ayarı kullanır. <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> özelliği olduğundan <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> özelliği kalıcı olarak veri akışı bloğu yürütme iptal eder. Bir iptal belirteci bu örnek bile kullanıcı bir veya daha fazla işlem iptal aynı veri akışı ağ birden çok kez yeniden kullanmanıza olanak sağlar. Kullanan bir örnek <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> kalıcı olarak bir veri akışı bloğu yürütme iptal etmek için bkz: [nasıl yapılır: veri akışı bloğunu iptal](../../../docs/standard/parallel-programming/how-to-cancel-a-dataflow-block.md).  
  
<a name="ui"></a>   
## <a name="connecting-the-dataflow-network-to-the-user-interface"></a>Veri akışı ağ için kullanıcı arabirimi bağlanma  
 Bu bölümde, veri akışı ağa bağlanmak için kullanıcı arabirimi açıklar. Bileşik görüntü oluşturma ve işlemin iptaline gelen başlatılan **Klasör Seç** ve **iptal** düğmeler. Kullanıcı bu düğmeleri seçtiğinde, uygun eylemi bir zaman uyumsuz olarak başlatılır.  
  
#### <a name="to-connect-the-dataflow-network-to-the-user-interface"></a>Veri akışı ağ kullanıcı arabirimine bağlamak için  
  
1.  Ana form için form designer'ı oluşturmak için bir olay işleyicisi <xref:System.Windows.Forms.ToolStripItem.Click> olayı için **Klasör Seç** düğmesi.  
  
2.  Uygulama <xref:System.Windows.Forms.ToolStripItem.Click> olayı için **Klasör Seç** düğmesi.  
  
     [!code-csharp[TPLDataflow_CompositeImages#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#6)]  
  
3.  Ana form için form designer'ı oluşturmak için bir olay işleyicisi <xref:System.Windows.Forms.ToolStripItem.Click> olayı için **iptal** düğmesi.  
  
4.  Uygulama <xref:System.Windows.Forms.ToolStripItem.Click> olayı için **iptal** düğmesi.  
  
     [!code-csharp[TPLDataflow_CompositeImages#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#7)]  
  
<a name="complete"></a>   
## <a name="the-complete-example"></a>Tam Örnek  
 Aşağıdaki örnek, bu kılavuz tam kod gösterilir.  
  
 [!code-csharp[TPLDataflow_CompositeImages#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#100)]  
  
 Aşağıdaki çizimde ortak \Sample Pictures\ klasörü için tipik çıkış gösterir.  
  
 ![Windows Forms uygulaması](../../../docs/standard/parallel-programming/media/tpldataflow-compositeimages.gif "TPLDataflow_CompositeImages")  
  
## <a name="next-steps"></a>Sonraki Adımlar  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)

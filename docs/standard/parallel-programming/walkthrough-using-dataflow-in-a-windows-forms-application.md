---
title: "İzlenecek yol: Windows Forms Uygulaması'nda Veri Akışı Kullanma"
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- TPL dataflow library, in Windows Forms
- Task Parallel Library, dataflows
- Windows Forms, and TPL
ms.assetid: 9c65cdf7-660c-409f-89ea-59d7ec8e127c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fd75bd14b2393d9b316d90070894f214dfa60c88
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61908810"
---
# <a name="walkthrough-using-dataflow-in-a-windows-forms-application"></a>İzlenecek yol: Windows Forms Uygulaması'nda Veri Akışı Kullanma
Bu belge, bir Windows Forms uygulamasında görüntü işleme gerçekleştiren veri akışı bloğu ağının nasıl oluşturulacağını gösterir.  
  
 Bu örnek belirtilen klasöründen görüntü dosyalarını yükler, bileşik bir görüntü oluşturur ve sonucu görüntüler. Örnek yol görüntülerine ağ üzerinden veri akışı modelini kullanır. Veri akışı modelinde, bir program bağımsız bileşenleri birbirleriyle iletiler göndererek iletişim. Bir bileşenin bir ileti aldığında, bir eylem gerçekleştirir ve ardından sonucu başka bir bileşene geçirir. Bu, denetim akışı modeli, bir uygulama denetim yapıları, örneğin kullanır, koşullu deyimler, döngüler ve benzeri işlemlerin bir programda sırasını denetlemek için ile karşılaştırın.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Okuma [veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) bu kılavuza başlamadan önce.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="sections"></a>Bölümler  
 Bu izlenecek yol aşağıdaki bölümleri içerir:  
  
- [Windows Forms uygulaması oluşturma](#winforms)  
  
- [Veri akışı ağ oluşturma](#network)  
  
- [Veri akışı ağ kullanıcı arabirimine bağlanma](#ui)  
  
- [Tam örnek](#complete)  
  
<a name="winforms"></a>   
## <a name="creating-the-windows-forms-application"></a>Windows Forms uygulaması oluşturma  
 Bu bölümde, temel Windows Forms uygulaması oluşturma ve ana formu için denetimler ekleme işlemleri açıklanmaktadır.  
  
#### <a name="to-create-the-windows-forms-application"></a>Formları uygulaması Windows oluşturmak için  
  
1. Bir Visual C# veya Visual Basic Visual Studio'da oluşturma **Windows Forms uygulaması** proje. Bu belgede, proje adı `CompositeImages`.  
  
2. Ana form için form tasarımcıda Form1.cs (Visual Basic için Form1.vb), ekleme bir <xref:System.Windows.Forms.ToolStrip> denetimi.  
  
3. Ekleme bir <xref:System.Windows.Forms.ToolStripButton> denetimini <xref:System.Windows.Forms.ToolStrip> denetimi. Ayarlama <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> özelliğini <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> ve <xref:System.Windows.Forms.ToolStripItem.Text%2A> özelliğini **Klasör Seç**.  
  
4. İkinci bir ekleme <xref:System.Windows.Forms.ToolStripButton> denetimini <xref:System.Windows.Forms.ToolStrip> denetimi. Ayarlama <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> özelliğini <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, <xref:System.Windows.Forms.ToolStripItem.Text%2A> özelliğini **iptal**ve <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> özelliğini `False`.  
  
5. Ekleme bir <xref:System.Windows.Forms.PictureBox> ana forma bir nesne. Ayarlama <xref:System.Windows.Forms.Control.Dock%2A> özelliğini <xref:System.Windows.Forms.DockStyle.Fill>.  
  
<a name="network"></a>   
## <a name="creating-the-dataflow-network"></a>Veri akışı ağ oluşturma  
 Bu bölümde, görüntü işleme gerçekleştiren veri akışı ağ oluşturmayı açıklar.  
  
#### <a name="to-create-the-dataflow-network"></a>Veri akışı ağı oluşturmak için  
  
1. Projenize System.Threading.Tasks.Dataflow.dll'ye birer başvuru ekleyin.  
  
2. Form1.cs (Visual Basic için Form1.vb) aşağıdaki içerdiğinden emin olun `using` (`Using` Visual Basic'te) ifadeleri:  
  
     [!code-csharp[TPLDataflow_CompositeImages#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#1)]  
  
3. Aşağıdaki veri üyelerini ekleyin `Form1` sınıfı:  
  
     [!code-csharp[TPLDataflow_CompositeImages#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#2)]  
  
4. Aşağıdaki yöntemi ekleyin `CreateImageProcessingNetwork`, `Form1` sınıfı. Bu yöntem, görüntü işleme ağı oluşturur.  
  
     [!code-csharp[TPLDataflow_CompositeImages#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#3)]  
  
5. Uygulama `LoadBitmaps` yöntemi.  
  
     [!code-csharp[TPLDataflow_CompositeImages#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#4)]  
  
6. Uygulama `CreateCompositeBitmap` yöntemi.  
  
     [!code-csharp[TPLDataflow_CompositeImages#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#5)]  
  
    > [!NOTE]
    >  C# sürümünü `CreateCompositeBitmap` yöntemi verimli işlenmesini etkinleştirmek için işaretçiler kullanır <xref:System.Drawing.Bitmap?displayProperty=nameWithType> nesneleri. Bu nedenle, etkinleştirmelisiniz **güvenli olmayan koda izin ver** seçeneğini kullanmak için projenizdeki [güvenli](~/docs/csharp/language-reference/keywords/unsafe.md) anahtar sözcüğü. Visual C# projesinde güvenli olmayan kod etkinleştirme hakkında daha fazla bilgi için bkz. [derleme sayfası, Proje Tasarımcısı (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).  
  
 Aşağıdaki tabloda, ağ üyelerini açıklar.  
  
|Üye|Tür|Açıklama|  
|------------|----------|-----------------|  
|`loadBitmaps`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Bir klasörü yolunu giriş olarak alır ve koleksiyonunu oluşturur <xref:System.Drawing.Bitmap> çıktı olarak nesneleri.|  
|`createCompositeBitmap`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Bir koleksiyonunu alır <xref:System.Drawing.Bitmap> nesneler giriş olarak ve birleşik bir bit eşlem çıktı olarak üretir.|  
|`displayCompositeBitmap`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|Bileşik bit eşlem formda görüntüler.|  
|`operationCancelled`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|İşlem iptal edilir ve başka bir klasör seçmek kullanıcının sağlayan belirtmek için bir resim görüntüler.|  
  
 Bir ağ oluşturmak için veri akışı bloklarının bağlanmak için bu örnekte <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> yöntemi. <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> Yöntemi alan aşırı yüklenmiş bir sürümünü içeren bir <xref:System.Predicate%601> nesnesini hedef blok kabul eder ya da bir ileti reddeder olup olmadığını belirler. Bu filtreleme mekanizması ileti blokları yalnızca belirli değerleri almasını sağlar. Bu örnekte, iki yoldan biriyle ağ dallara ayırabilirsiniz. Ana dal görüntüleri diskten yükler, bileşik görüntüsünü oluşturur ve o yansıma formda görüntülenir. Diğer dal, geçerli işlemi iptal eder. <xref:System.Predicate%601> Nesneleri belirli iletileri reddederek alternatif dala geçmek ana dal boyunca veri akışı blokları sağlar. Örneğin, kullanıcı işlemi, veri akışı bloğunu iptal ederse `createCompositeBitmap` üretir `null` (`Nothing` Visual Basic'te) çıktısını olarak. Veri akışı bloğu `displayCompositeBitmap` reddeder `null` giriş değerleri ve bu nedenle, ileti için sunulur `operationCancelled`. Veri akışı bloğu `operationCancelled` tüm iletileri kabul eder ve bu nedenle, işlemi iptal edildiğini belirten bir resim görüntüler.  
  
 Görüntü işleme ağı aşağıda gösterilmiştir:  
  
 ![Çizimi görüntü işleme ağı gösterir.](./media/walkthrough-using-dataflow-in-a-windows-forms-application/dataflow-winforms-image-processing.png)  
  
 Çünkü `displayCompositeBitmap` ve `operationCancelled` veri akışı blokları hareket kullanıcı arabiriminde, önemlidir bu eylemler kullanıcı arabirimi iş parçacığı üzerinde oluşur. Oluşturma sırasında bunu gerçekleştirmek için bu nesnelerin her sağlayan bir <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> nesnesi <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> özelliğini <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>. <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> Yöntemi oluşturur bir <xref:System.Threading.Tasks.TaskScheduler> geçerli eşitleme kapsamının üzerinde işini gerçekleştiren nesne. Çünkü `CreateImageProcessingNetwork` yöntemi işleyicisinden çağrılır **Klasör Seç** çalıştığı üzerinde kullanıcı arabirimi iş parçacığı, Eylemler için düğme `displayCompositeBitmap` ve `operationCancelled` veri akışı blokları da çalıştırın kullanıcı arabirimi iş parçacığı.  
  
 Bu örnekte ayar yerine paylaşılan bir iptal belirteci <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> özelliği olduğundan <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> özelliği veri akışı bloğu yürütme kalıcı olarak iptal eder. Bu örnekte, kullanıcı bir veya daha fazla operations bile iptal ettiğinde aynı veri akışı ağ birden çok kez yeniden kullanmak bir iptal belirteci sağlar. Kullanan bir örnek için <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> yürütme veri akışı bloğunun kalıcı olarak iptal etmek için bkz: [nasıl yapılır: Bir veri akışı bloğunu iptal etme](../../../docs/standard/parallel-programming/how-to-cancel-a-dataflow-block.md).  
  
<a name="ui"></a>   
## <a name="connecting-the-dataflow-network-to-the-user-interface"></a>Veri akışı ağ kullanıcı arabirimine bağlanma  
 Bu bölümde, veri akışı ağ kullanıcı arabirimine bağlamak açıklar. Bileşik görüntü oluşturmayı ve iptal işleminin dan başlatılan **Klasör Seç** ve **iptal** düğmeleri. Kullanıcı bu düğme seçtiğinde, uygun eylemi zaman uyumsuz olarak başlatılır.  
  
#### <a name="to-connect-the-dataflow-network-to-the-user-interface"></a>Veri akışı ağ kullanıcı arabirimine bağlamak için  
  
1. Ana form için form tasarımcısı için bir olay işleyicisi oluşturun <xref:System.Windows.Forms.ToolStripItem.Click> olayı **Klasör Seç** düğmesi.  
  
2. Uygulama <xref:System.Windows.Forms.ToolStripItem.Click> olayı **Klasör Seç** düğmesi.  
  
     [!code-csharp[TPLDataflow_CompositeImages#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#6)]  
  
3. Ana form için form tasarımcıda oluşturmak için bir olay işleyicisi <xref:System.Windows.Forms.ToolStripItem.Click> olayı **iptal** düğmesi.  
  
4. Uygulama <xref:System.Windows.Forms.ToolStripItem.Click> olayı **iptal** düğmesi.  
  
     [!code-csharp[TPLDataflow_CompositeImages#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#7)]  
  
<a name="complete"></a>   
## <a name="the-complete-example"></a>Tam Örnek  
 Aşağıdaki örnek, bu izlenecek yol için tam kod gösterilmektedir.  
  
 [!code-csharp[TPLDataflow_CompositeImages#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#100)]  
  
 Ortak \Sample Pictures\ klasörü için normal çıktı aşağıda gösterilmiştir.  
  
 ![Windows Forms uygulamalarındaki](../../../docs/standard/parallel-programming/media/tpldataflow-compositeimages.gif "TPLDataflow_CompositeImages")  

## <a name="see-also"></a>Ayrıca bkz.

- [Veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)

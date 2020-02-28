---
title: "İzlenecek yol: Windows Forms Uygulaması'nda Veri Akışı Kullanma"
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- TPL dataflow library, in Windows Forms
- Task Parallel Library, dataflows
- Windows Forms, and TPL
ms.assetid: 9c65cdf7-660c-409f-89ea-59d7ec8e127c
ms.openlocfilehash: 794253514edf63f02276e1ece21c60a85c534390
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159773"
---
# <a name="walkthrough-using-dataflow-in-a-windows-forms-application"></a>İzlenecek yol: Windows Forms Uygulaması'nda Veri Akışı Kullanma
Bu belgede, Windows Forms uygulamasında görüntü işlemeyi gerçekleştiren bir veri akışı bloğu ağı oluşturma işlemi gösterilir.  
  
 Bu örnek, belirtilen klasörden görüntü dosyalarını yükler, bileşik bir görüntü oluşturur ve sonucu görüntüler. Örnek, görüntüleri ağ üzerinden yönlendirmek için veri akışı modelini kullanır. Veri akışı modelinde, bir programın bağımsız bileşenleri ileti göndererek birbirleriyle iletişim kurar. Bir bileşen bir ileti aldığında, bazı işlemleri gerçekleştirir ve sonucu başka bir bileşene geçirir. Bunu, bir uygulamanın bir programdaki işlem sırasını denetlemek için denetim yapılarını (örneğin, koşullu deyimler, döngüler vb.) kullandığı denetim akışı modeliyle karşılaştırın.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu yönergeyi başlamadan önce [veri akışını](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) okuyun.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="sections"></a>Bölümler  
 Bu izlenecek yol aşağıdaki bölümleri içerir:  
  
- [Windows Forms uygulaması oluşturma](#winforms)  
  
- [Veri akışı ağını oluşturma](#network)  
  
- [Veri akışı ağını Kullanıcı arabirimine bağlama](#ui)  
  
- [Tüm örnek](#complete)  
  
<a name="winforms"></a>
## <a name="creating-the-windows-forms-application"></a>Windows Forms uygulaması oluşturma  
 Bu bölümde temel Windows Forms uygulamasının nasıl oluşturulacağı ve ana forma nasıl denetim ekleneceği açıklanmaktadır.  
  
### <a name="to-create-the-windows-forms-application"></a>Windows Forms uygulamasını oluşturmak için  
  
1. Visual Studio 'da bir görsel C# veya Visual Basic **Windows Forms uygulama** projesi oluşturun. Bu belgede, proje `CompositeImages`olarak adlandırılır.  
  
2. Ana form için form tasarımcısında, Form1.cs (Visual Basic için Form1. vb), bir <xref:System.Windows.Forms.ToolStrip> denetimi ekleyin.  
  
3. <xref:System.Windows.Forms.ToolStrip> denetimine <xref:System.Windows.Forms.ToolStripButton> denetimi ekleyin. <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> özelliğini <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> ve **klasör seç**<xref:System.Windows.Forms.ToolStripItem.Text%2A> özelliği olarak ayarlayın.  
  
4. <xref:System.Windows.Forms.ToolStrip> denetimine ikinci bir <xref:System.Windows.Forms.ToolStripButton> denetimi ekleyin. <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> özelliğini <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, **iptal**edilecek <xref:System.Windows.Forms.ToolStripItem.Text%2A> özelliğini ve <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> özelliğini `False`olarak ayarlayın.  
  
5. Ana forma <xref:System.Windows.Forms.PictureBox> nesne ekleyin. <xref:System.Windows.Forms.Control.Dock%2A> özelliğini <xref:System.Windows.Forms.DockStyle.Fill>olarak ayarlayın.  
  
<a name="network"></a>
## <a name="creating-the-dataflow-network"></a>Veri akışı ağını oluşturma  
 Bu bölümde, görüntü işlemeyi gerçekleştiren veri akışı ağının nasıl oluşturulacağı açıklanmaktadır.  
  
### <a name="to-create-the-dataflow-network"></a>Veri akışı ağını oluşturmak için  
  
1. Projenize System. Threading. Tasks. Dataflow. dll başvurusunu ekleyin.  
  
2. Form1.cs (Visual Basic için Form1. vb) içinde aşağıdaki `using` (`Using` Visual Basic) deyimlerini içerdiğinden emin olun:  
  
     [!code-csharp[TPLDataflow_CompositeImages#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#1)]  
  
3. Aşağıdaki veri üyelerini `Form1` sınıfına ekleyin:  
  
     [!code-csharp[TPLDataflow_CompositeImages#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#2)]  
  
4. Aşağıdaki yöntemi `CreateImageProcessingNetwork``Form1` sınıfına ekleyin. Bu yöntem, görüntü işleme ağını oluşturur.  
  
     [!code-csharp[TPLDataflow_CompositeImages#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#3)]  
  
5. `LoadBitmaps` yöntemini uygulayın.  
  
     [!code-csharp[TPLDataflow_CompositeImages#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#4)]  
  
6. `CreateCompositeBitmap` yöntemini uygulayın.  
  
     [!code-csharp[TPLDataflow_CompositeImages#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#5)]  
  
    > [!NOTE]
    > `CreateCompositeBitmap` C# yönteminin sürümü, <xref:System.Drawing.Bitmap?displayProperty=nameWithType> nesnelerinin verimli işlemesini sağlamak için işaretçiler kullanır. Bu nedenle, [unsafe](../../csharp/language-reference/keywords/unsafe.md) anahtar sözcüğünü kullanabilmeniz için projenizdeki **güvenli olmayan koda izin ver** seçeneğini etkinleştirmeniz gerekir. Visual C# projesinde güvenli olmayan kodun nasıl etkinleştirileceği hakkında daha fazla bilgi için bkz. [derleme sayfası, proje Tasarımcısı (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).  
  
 Aşağıdaki tablo, ağın üyelerini açıklar.  
  
|Üye|Tür|Açıklama|  
|------------|----------|-----------------|  
|`loadBitmaps`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Bir klasör yolunu girdi olarak alır ve çıkış olarak <xref:System.Drawing.Bitmap> nesnelerden oluşan bir koleksiyon oluşturur.|  
|`createCompositeBitmap`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|<xref:System.Drawing.Bitmap> nesnelerinin bir koleksiyonunu girdi olarak alır ve çıktı olarak bir bileşik bit eşlem üretir.|  
|`displayCompositeBitmap`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|Form üzerinde bileşik bit eşlemi görüntüler.|  
|`operationCancelled`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|İşlemin iptal edildiğini belirten bir resim görüntüler ve kullanıcının başka bir klasör seçmesini sağlar.|  
  
 Veri akışı bloklarını bir ağ oluşturacak şekilde bağlamak için, bu örnek <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> yöntemini kullanır. <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> yöntemi, hedef bloğunun bir iletiyi kabul edip etmeyeceğini belirleyen bir <xref:System.Predicate%601> nesnesini alan aşırı yüklenmiş bir sürüm içerir. Bu filtreleme mekanizması ileti bloklarının yalnızca belirli değerleri almasına olanak sağlar. Bu örnekte, ağ iki şekilde dallandırma yapabilir. Ana dal görüntüleri diskten yükler, bileşik görüntüyü oluşturur ve bu görüntüyü form üzerinde görüntüler. Alternatif dal geçerli işlemi iptal eder. <xref:System.Predicate%601> nesneleri, Ana daldaki veri akışı bloklarını, belirli iletileri reddeterek alternatif dala geçiş yapmak üzere etkinleştirir. Örneğin, Kullanıcı işlemi iptal ederse, veri akışı bloğu `createCompositeBitmap` çıktı olarak `null` (Visual Basic 'de`Nothing`) üretir. Veri akışı bloğu `displayCompositeBitmap` `null` giriş değerlerini reddeder ve bu nedenle ileti `operationCancelled`sunulur. Veri akışı bloğu `operationCancelled` tüm iletileri kabul eder ve bu nedenle, işlemin iptal edildiğini göstermek için bir resim görüntüler.  
  
 Aşağıdaki çizim görüntü işleme ağını göstermektedir:  
  
 ![Görüntü işleme ağını gösteren çizim.](./media/walkthrough-using-dataflow-in-a-windows-forms-application/dataflow-winforms-image-processing.png)  
  
 `displayCompositeBitmap` ve `operationCancelled` veri akışı blokları Kullanıcı arabiriminde işlem yaptığından, bu eylemlerin Kullanıcı arabirimi iş parçacığında gerçekleştirilmesi önemlidir. Bunu gerçekleştirmek için, oluşturma sırasında, bu nesnelerin her biri <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> özelliği <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>olarak ayarlanmış bir <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> nesnesi sağlar. <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> yöntemi, geçerli eşitleme bağlamında çalışmayı gerçekleştiren bir <xref:System.Threading.Tasks.TaskScheduler> nesnesi oluşturur. `CreateImageProcessingNetwork` yöntemi, Kullanıcı arabirimi iş parçacığında çalışan **Klasör Seç** düğmesinin işleyicisinden çağrıldığı için, `displayCompositeBitmap` ve `operationCancelled` veri akışı blokları için Eylemler kullanıcı arabirimi iş parçacığında da çalışır.  
  
 Bu örnek <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> özelliğini ayarlamak yerine paylaşılan bir iptal belirteci kullanır, çünkü <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> özelliği kalıcı olarak veri akışı blok yürütmeyi iptal eder. İptal belirteci, Kullanıcı bir veya daha fazla işlemi iptal ettiğinde bile, bu örneğin aynı veri akışı ağını birden çok kez yeniden kullanmasına olanak sağlar. Bir veri akışı bloğunun yürütülmesini kalıcı olarak iptal etmek için <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> kullanan bir örnek için bkz. [nasıl yapılır: veri akışı bloğunu iptal](../../../docs/standard/parallel-programming/how-to-cancel-a-dataflow-block.md)etme.  
  
<a name="ui"></a>
## <a name="connecting-the-dataflow-network-to-the-user-interface"></a>Veri akışı ağını Kullanıcı arabirimine bağlama  
 Bu bölümde, veri akışı ağının Kullanıcı arabirimine nasıl bağlanacağı açıklanmaktadır. Bileşik görüntünün ve işlemin iptalinin oluşturulması, **Klasör Seç** ve **iptal** düğmelerinden başlatılır. Kullanıcı bu düğmelerden birini seçtiğinde, uygun eylem zaman uyumsuz bir şekilde başlatılır.  
  
### <a name="to-connect-the-dataflow-network-to-the-user-interface"></a>Veri akışı ağını Kullanıcı arabirimine bağlamak için  
  
1. Ana form için form tasarımcısında, **Klasör Seç** düğmesine yönelik <xref:System.Windows.Forms.ToolStripItem.Click> olayı için bir olay işleyicisi oluşturun.  
  
2. **Klasör Seç** düğmesi için <xref:System.Windows.Forms.ToolStripItem.Click> olayını uygulayın.  
  
     [!code-csharp[TPLDataflow_CompositeImages#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#6)]  
  
3. Ana form için form tasarımcısında, **iptal** düğmesi için <xref:System.Windows.Forms.ToolStripItem.Click> olayı için bir olay işleyicisi oluşturun.  
  
4. **İptal** düğmesi için <xref:System.Windows.Forms.ToolStripItem.Click> olayını uygulayın.  
  
     [!code-csharp[TPLDataflow_CompositeImages#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#7)]  
  
<a name="complete"></a>
## <a name="the-complete-example"></a>Tam Örnek  
 Aşağıdaki örnekte bu izlenecek yol için tüm kod gösterilmektedir.  
  
 [!code-csharp[TPLDataflow_CompositeImages#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#100)]  
  
 Aşağıdaki çizimde ortak \ örnek resimler \ klasörü için tipik çıkış gösterilmektedir.  
  
 ![Windows Forms uygulaması](../../../docs/standard/parallel-programming/media/tpldataflow-compositeimages.gif "TPLDataflow_CompositeImages")  

## <a name="see-also"></a>Ayrıca bkz.

- [Veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)

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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159773"
---
# <a name="walkthrough-using-dataflow-in-a-windows-forms-application"></a>İzlenecek yol: Windows Forms Uygulaması'nda Veri Akışı Kullanma
Bu belge, Windows Forms uygulamasında görüntü işleme gerçekleştiren veri akışı blokları ağının nasıl oluşturulurunun gösterildiğini gösterir.  
  
 Bu örnek, belirtilen klasörden görüntü dosyalarını yükler, bileşik bir görüntü oluşturur ve sonucu görüntüler. Örnek, görüntüleri ağ üzerinden yönlendirmek için veri akışı modelini kullanır. Veri akışı modelinde, bir programın bağımsız bileşenleri mesaj göndererek birbirleriyle iletişim kurar. Bir bileşen bir ileti aldığında, bazı eylem gerçekleştirir ve sonra sonucu başka bir bileşene geçirir. Bunu, bir uygulamanın programdaki işlemlerin sırasını denetlemek için koşullu deyimler, döngüler ve benzeri denetim yapıları kullandığı denetim akışı modeliyle karşılaştırın.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izbiyi başlatmadan önce [Veri Akışı'nı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) okuyun.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="sections"></a>Bölümler  
 Bu izksiyon aşağıdaki bölümleri içerir:  
  
- [Windows Forms Uygulamasını Oluşturma](#winforms)  
  
- [Veri Akışı Ağı Oluşturma](#network)  
  
- [Veri Akışı Ağını Kullanıcı Arabirimine Bağlama](#ui)  
  
- [Tam Örnek](#complete)  
  
<a name="winforms"></a>
## <a name="creating-the-windows-forms-application"></a>Windows Forms Uygulamasını Oluşturma  
 Bu bölümde, temel Windows Forms uygulamasının nasıl oluşturulup ana forma denetimekleninsağlanmıştır.  
  
### <a name="to-create-the-windows-forms-application"></a>Windows Forms Uygulamasını Oluşturmak İçin  
  
1. Visual Studio'da Visual C# veya Visual Basic **Windows Forms Application** project oluşturun. Bu belgede, proje adı `CompositeImages`.  
  
2. Ana form için form tasarımcısı, Form1.cs (Visual Basic için Form1.vb), bir <xref:System.Windows.Forms.ToolStrip> denetim ekleyin.  
  
3. <xref:System.Windows.Forms.ToolStrip> Denetime bir <xref:System.Windows.Forms.ToolStripButton> denetim ekleyin. <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> Özelliği <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> ve <xref:System.Windows.Forms.ToolStripItem.Text%2A> özelliği **Klasör'ü Seç'e**ayarlayın.  
  
4. <xref:System.Windows.Forms.ToolStrip> Denetime ikinci <xref:System.Windows.Forms.ToolStripButton> bir denetim ekleyin. <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> <xref:System.Windows.Forms.ToolStripItem.Text%2A> <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> `False` **Cancel**Özelliği, İptal Etme özelliğine, özelliği de . <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A>  
  
5. Ana <xref:System.Windows.Forms.PictureBox> forma bir nesne ekleyin. Özelliği <xref:System.Windows.Forms.Control.Dock%2A> ' <xref:System.Windows.Forms.DockStyle.Fill>ye ayarlayın.  
  
<a name="network"></a>
## <a name="creating-the-dataflow-network"></a>Veri Akışı Ağı Oluşturma  
 Bu bölümde, görüntü işleme gerçekleştiren veri akışı ağının nasıl oluşturulacak açıklanmaktadır.  
  
### <a name="to-create-the-dataflow-network"></a>Veri Akışı Ağı Oluşturmak İçin  
  
1. Projenize System.Threading.Tasks.Dataflow.dll adresine bir başvuru ekleyin.  
  
2. Form1.cs (Visual Basic için Form1.vb) `using` aşağıdaki`Using` ifadeleri içerdiğinden emin olun:  
  
     [!code-csharp[TPLDataflow_CompositeImages#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#1)]  
  
3. `Form1` Sınıfa aşağıdaki veri üyelerini ekleyin:  
  
     [!code-csharp[TPLDataflow_CompositeImages#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#2)]  
  
4. Sınıfa aşağıdaki `CreateImageProcessingNetwork`yöntemi ekleyin. `Form1` Bu yöntem görüntü işleme ağı oluşturur.  
  
     [!code-csharp[TPLDataflow_CompositeImages#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#3)]  
  
5. Yöntemi `LoadBitmaps` uygulayın.  
  
     [!code-csharp[TPLDataflow_CompositeImages#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#4)]  
  
6. Yöntemi `CreateCompositeBitmap` uygulayın.  
  
     [!code-csharp[TPLDataflow_CompositeImages#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#5)]  
  
    > [!NOTE]
    > Yöntemin `CreateCompositeBitmap` C# sürümü, nesnelerin verimli bir şekilde <xref:System.Drawing.Bitmap?displayProperty=nameWithType> işlenmesini sağlamak için işaretçilerkullanır. Bu nedenle, [güvenli olmayan](../../csharp/language-reference/keywords/unsafe.md) anahtar sözcüğü kullanmak için projenizde **güvenli olmayan koda izin** ver seçeneğini etkinleştirmeniz gerekir. Visual C# projesinde güvenli olmayan kodu niçin etkinleştirin, [bkz.](/visualstudio/ide/reference/build-page-project-designer-csharp)  
  
 Aşağıdaki tabloda ağ üyeleri açıklanmaktadır.  
  
|Üye|Tür|Açıklama|  
|------------|----------|-----------------|  
|`loadBitmaps`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Giriş olarak bir klasör yolunu alır <xref:System.Drawing.Bitmap> ve çıktı olarak nesnelerin bir koleksiyon üretir.|  
|`createCompositeBitmap`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Nesnelerin bir <xref:System.Drawing.Bitmap> koleksiyonunu girdi olarak alır ve çıktı olarak bileşik bit eşlemi üretir.|  
|`displayCompositeBitmap`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|Formdaki bileşik bit eşlemi görüntüler.|  
|`operationCancelled`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|İşlemin iptal edildiğini belirtmek için bir resim görüntüler ve kullanıcının başka bir klasör seçmesini sağlar.|  
  
 Veri akışı bloklarını ağ oluşturmak üzere bağlamak <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> için bu örnek yöntemi kullanır. Yöntem, <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> hedef bloğun bir iletiyi kabul edip etmediğini belirleyen bir <xref:System.Predicate%601> nesne alan aşırı yüklü bir sürüm içerir. Bu filtreleme mekanizması ileti bloklarının yalnızca belirli değerleri almasını sağlar. Bu örnekte, ağ iki şekilde dallanabilir. Ana dal görüntüleri diskten yükler, bileşik görüntü oluşturur ve bu görüntüyü formda görüntüler. Alternatif dal geçerli işlemi iptal eder. Nesneler, <xref:System.Predicate%601> ana dal daki veri akışı bloklarının belirli iletileri reddederek alternatif dala geçmesini sağlar. Örneğin, kullanıcı işlemi iptal ederse, veri akışı `createCompositeBitmap` `null` bloğu`Nothing` çıktı olarak (Visual Basic'te) üretir. Veri akışı `displayCompositeBitmap` bloğu `null` giriş değerlerini reddeder ve bu nedenle `operationCancelled`ileti . Veri akışı `operationCancelled` bloğu tüm iletileri kabul eder ve bu nedenle işlemin iptal edildiğini belirtmek için bir görüntü görüntüler.  
  
 Aşağıdaki resimde görüntü işleme ağı gösterilmektedir:  
  
 ![Görüntü işleme ağını gösteren çizim.](./media/walkthrough-using-dataflow-in-a-windows-forms-application/dataflow-winforms-image-processing.png)  
  
 `displayCompositeBitmap` Ve `operationCancelled` veri akışı blokları kullanıcı arabiriminde hareket ettiği için, bu eylemlerin kullanıcı arabirimi iş parçacığında oluşması önemlidir. Bunu gerçekleştirmek için, inşaat sırasında, bu <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> nesnelerin her <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> biri <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>özelliği ayarlanmış bir nesne sağlar. Yöntem, <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> geçerli <xref:System.Threading.Tasks.TaskScheduler> eşitleme bağlamında çalışma gerçekleştiren bir nesne oluşturur. Yöntem, kullanıcı arabirimi iş parçacığı üzerinde çalışan **Klasörü Seç** düğmesinin işleyicisinden `displayCompositeBitmap` çağrıldığından, kullanıcı arabirimi iş parçacığında da veri akışı bloklarının `operationCancelled` eylemleri çalışır. `CreateImageProcessingNetwork`  
  
 Bu örnek, <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> özellik veri akışı bloğu yürütmesini kalıcı olarak iptal ettiği için özelliği ayarlamak yerine paylaşılan bir iptal belirteci kullanır. İptal belirteci, kullanıcı bir veya daha fazla işlemi iptal etse bile, bu örneğin aynı veri akışı ağını birden çok kez yeniden kullanmasını sağlar. Veri akışı bloğunun yürütülmesini kalıcı olarak iptal etmek için kullanan <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> bir örnek için [bkz.](../../../docs/standard/parallel-programming/how-to-cancel-a-dataflow-block.md)  
  
<a name="ui"></a>
## <a name="connecting-the-dataflow-network-to-the-user-interface"></a>Veri Akışı Ağını Kullanıcı Arabirimine Bağlama  
 Bu bölümde, veri akışı ağının kullanıcı arabirimine nasıl bağlanılabildiğini açıklanmaktadır. Bileşik görüntünün oluşturulması ve işlemin iptali Klasör **Seç** ve **İptal** düğmelerinden başlatılır. Kullanıcı bu düğmelerden birini seçtiğinde, uygun eylem eşzamanlı bir şekilde başlatılır.  
  
### <a name="to-connect-the-dataflow-network-to-the-user-interface"></a>Veri Akışı Ağını Kullanıcı Arabirimine Bağlamak İçin  
  
1. Ana formun form tasarımcısında, **Klasör** seç düğmesi <xref:System.Windows.Forms.ToolStripItem.Click> için olay için bir olay işleyicisi oluşturun.  
  
2. Klasör <xref:System.Windows.Forms.ToolStripItem.Click> seç düğmesi **Choose Folder** için olayı uygulayın.  
  
     [!code-csharp[TPLDataflow_CompositeImages#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#6)]  
  
3. Ana formiçin form tasarımcısında, **İptal** düğmesi için <xref:System.Windows.Forms.ToolStripItem.Click> olay için bir olay işleyicisi oluşturun.  
  
4. İptal <xref:System.Windows.Forms.ToolStripItem.Click> düğmesi için **Cancel** etkinliği uygulayın.  
  
     [!code-csharp[TPLDataflow_CompositeImages#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#7)]  
  
<a name="complete"></a>
## <a name="the-complete-example"></a>Tam Örnek  
 Aşağıdaki örnek, bu izbin tam kodunu gösterir.  
  
 [!code-csharp[TPLDataflow_CompositeImages#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#100)]  
  
 Aşağıdaki resimde ortak \Örnek Resimler\ klasörü için tipik çıktı gösterilmektedir.  
  
 ![Windows Formları Uygulaması](../../../docs/standard/parallel-programming/media/tpldataflow-compositeimages.gif "TPLDataflow_CompositeImages")  

## <a name="see-also"></a>Ayrıca bkz.

- [Veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)

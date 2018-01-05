---
title: "Görünüm durumu Tasarımcı kaldırma bir XAML dosyasına ekler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a801ce22-8699-483c-a392-7bb3834aae4f
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5da4423b5f6106bde106de739a8a33e351d17c3d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="removing-the-view-state-the-designer-adds-to-an-xaml-file"></a>Görünüm durumu Tasarımcı kaldırma bir XAML dosyasına ekler
Bu örnek türeyen bir sınıf oluşturmak nasıl gösterir <xref:System.Windows.Markup.XamlWriter> ve kaldırır XAML dosyası durumunu görüntüleyin. [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)]Görünüm durumu bilinen XAML belgesine bilgi yazar. Görünüm durumu, çalışma zamanında gerekli olmayan düzen konumlandırma gibi tasarım zamanında, gerekli olan bilgileri ifade eder. [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)]Bu bilgiler, düzenlenebilir XAML belgeye ekler. [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)]Görünüm durumu ile XAML dosyası Yazar `mc:Ignorable` XAML dosyası çalışma zamanı yüklediğinde, bu bilgileri yüklenmedi şekilde özniteliği. Bu örnek XAML düğümleri işlerken, Görünüm durumu bilgisini kaldırır bir sınıfın nasıl oluşturulacağı gösterilmektedir.  
  
## <a name="discussion"></a>Tartışma  
 Bu örnek nasıl özel bir yazıcı oluşturulacağını gösterir.  
  
 Özel bir XAML yazıcısı oluşturmak için öğesinden devralınan bir sınıf oluşturmanız <xref:System.Windows.Markup.XamlWriter>. XAML yazıcılar genellikle içe gibi bir "İç" XAML yazıcı izlemek için normaldir. Bu "İç ' yazıcılarının zorlayıcı iş ve işleme yığını geri kalanı için temsilci seçme için birden çok giriş noktası olmasını sağlayarak XAML yazıcılarının kalan yığınını başvuru olarak.  
  
 Bu örnekte, ilgi birkaç öğe yok. Yazılmakta öğesi Tasarımcı Ad alanından olup olmadığını görmek için onay biridir. Bu ayrıca diğer türlerinin bir iş akışında Tasarımcı Ad alanından çıkışı şeritler olduğunu unutmayın.  
  
```csharp
static Boolean IsDesignerAttachedProperty(XamlMember xamlMember)  
{  
    return xamlMember.IsAttachable &&  
        xamlMember.PreferredXamlNamespace.Equals(c_sapNamespaceURI, StringComparison.OrdinalIgnoreCase);  
}  
  
const String c_sapNamespaceURI = "http://schemas.microsoft.com/netfx/2009/xaml/activities/presentation";  

// The next item of interest is the constructor, where the utilization of the inner XAML writer is seen.  
public ViewStateCleaningWriter(XamlWriter innerWriter)  
{  
    this.InnerWriter = innerWriter;  
    this.MemberStack = new Stack<XamlMember>();  
}  
  
XamlWriter InnerWriter {get; set; }  
Stack<XamlMember> MemberStack {get; set; }  
```  
  
 Bu aynı zamanda bir yığın düğümü akışı geçişi sırasında kullanılan XAML üyelerinin oluşturur. Bu örnek, kalan çalışma büyük ölçüde yer <!--zz  <xref:System.Windows.Markup.XamlWriter.WriteStartMember%2A>--> `System.Windows.Markup.XamlWriter.WriteStartMember` yöntemi.  
  
```csharp
public override void WriteStartMember(XamlMember xamlMember)  
{  
    MemberStack.Push(xamlMember);

    if (IsDesignerAttachedProperty(xamlMember))  
    {  
        m_attachedPropertyDepth++;  
    }  
  
    if (m_attachedPropertyDepth > 0)  
    {  
        return;  
    }  
  
    InnerWriter.WriteStartMember(xamlMember);  
}  
```  
  
 Sonraki yöntemleri sonra bunlar hala bir görünüm durumu kapsayıcıda bulunan olup olmadığını denetleyin ve gerekiyorsa, dönün ve yazıcı yığın aşağı düğümü geçmeyin.  
  
```csharp
public override void WriteValue(Object value)  
{  
    if (m_attachedPropertyDepth > 0)  
    {  
        return;  
    }  
  
    InnerWriter.WriteValue(value);  
}  
```  
  
 Özel bir XAML yazan kullanmak için onu XAML yazıcılarının yığınında zincir gerekir. Aşağıdaki kod bu nasıl kullanılabileceğini gösterir.  
  
```csharp 
XmlWriterSettings writerSettings = new XmlWriterSettings {  Indent = true };  
XmlWriter xmlWriter = XmlWriter.Create(File.OpenWrite(args[1]), writerSettings);  
XamlXmlWriter xamlWriter = new XamlXmlWriter(xmlWriter, new XamlSchemaContext());  
XamlServices.Save(new ViewStateCleaningWriter(ActivityXamlServices.CreateBuilderWriter(xamlWriter)), ab);  
```  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1. Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ViewStateCleaningWriter.sln çözüm dosyasını açın.  
  
2. Bir komut istemi açın ve burada ViewStageCleaningWriter.exe yerleşik dizinine gidin.  
  
3. ViewStateCleaningWriter.exe Workflow1.xaml dosyasını çalıştırın.  

   Yürütülebilir dosya için sözdizimi aşağıdaki örnekte gösterilir.  
  
   ```console
   ViewStateCleaningWriter.exe [input file] [output file]
   ```
   
   Bu bir XAML dosyasına çıkarır \[çıkışdosyası], kaldırılan tüm görünüm durum bilgilerini sahiptir.  
  
> [!NOTE]
> İçin bir <xref:System.Activities.Statements.Sequence> iş akışı, bir dizi sanallaştırma ipuçları kaldırılır. Bu, düzeni yüklendiği sonraki sefer yeniden hesaplamak Tasarımcı neden olur. Bu örnek için kullandığınızda, bir <xref:System.Activities.Statements.Flowchart>, tüm konumlandırma ve yönlendirme bilgilerini satır kaldırılır ve ekranın sol tarafındaki Yığılmış Tasarımcı içine sonraki yüklemeyi, tüm etkinlikler.  
  
#### <a name="to-create-a-sample-xaml-file-for-use-with-this-sample"></a>Bu örnek ile kullanmak için bir örnek XAML dosyası oluşturmak için  
  
1. Açık [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2. Yeni bir iş akışı konsol uygulaması oluşturun.  
  
3. Birkaç etkinlikleri tuvale sürükleyip  
  
4. İş akışı XAML dosyasını kaydedin.  
  
5. Ekli özellikler durumunu görmek için XAML dosyasını inceleyin.  
  
> [!IMPORTANT]
> Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ViewStateCleaningWriter`

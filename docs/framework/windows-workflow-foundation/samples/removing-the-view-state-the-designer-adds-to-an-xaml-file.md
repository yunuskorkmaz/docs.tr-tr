---
title: Tasarımcı bir XAML dosyasına eklediği görünüm durumunu kaldırma-WF
ms.date: 03/30/2017
ms.assetid: a801ce22-8699-483c-a392-7bb3834aae4f
ms.openlocfilehash: f431275140e821aa5ec4d2235322f06be87d5ee2
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715616"
---
# <a name="removing-the-view-state-the-designer-adds-to-an-xaml-file"></a>Tasarımcı bir XAML dosyasına eklediği görünüm durumunu kaldırma

Bu örnek, <xref:System.Xaml.XamlWriter> türetilen ve bir XAML dosyasından görünüm durumunu kaldıran bir sınıfın nasıl oluşturulacağını gösterir. Windows İş Akışı Tasarımcısı, görüntüleme durumu olarak bilinen XAML belgesine bilgi yazar. Görünüm durumu, çalışma zamanında gerekli olmayan, tasarım zamanında (düzen konumlandırma gibi) gerekli olan bilgilere başvurur. İş Akışı Tasarımcısı, bu bilgileri XAML belgesine düzenlendiğinden ekler. İş Akışı Tasarımcısı, görünüm durumunu XAML dosyasına `mc:Ignorable` özniteliğiyle yazar, bu nedenle çalışma zamanı XAML dosyasını yüklediğinde bu bilgiler yüklenmez. Bu örnek, XAML düğümlerini işlerken görünüm durumu bilgisini kaldıran bir sınıfın nasıl oluşturulacağını gösterir.

## <a name="discussion"></a>Tartışma

Bu örnek, özel bir yazıcı oluşturmayı gösterir.

Özel bir XAML yazıcısı oluşturmak için <xref:System.Xaml.XamlWriter>devralan bir sınıf oluşturun. XAML yazarları genellikle iç içe geçmişse, "iç" XAML yazıcısının izlenmesi tipik bir davranıştır. Bu "iç" yazarlar, diğer XAML yazıcı yığınına başvuru olarak düşünülebilir. böylece, iş yapmak için birden çok giriş noktasına sahip olabilirsiniz ve sonra yığının geri kalanına işleme atayabilirsiniz.

Bu örnekte, ilgilendiğiniz birkaç öğe vardır. Bunlardan biri, yazılan öğenin tasarımcı ad alanından olup olmadığını görmekte olan bir denetim olur. Bu Ayrıca, bir iş akışındaki tasarımcı ad alanından diğer türlerin kullanımını da kaldırır.

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

Bu, düğüm akışından geçiş sırasında kullanılan XAML üyeleri yığınını da oluşturur. Bu örneğin kalan işi büyük ölçüde `WriteStartMember` yönteminde bulunur.

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

Sonraki Yöntemler bundan sonra bir görünüm durumu kapsayıcısında içerilip içerilmediğini kontrol eder ve istiyorsanız düğümü yazıcı yığınına geri geçirmez.

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

Özel bir XAML yazıcısını kullanmak için, XAML yazıcılarının bir yığınında birlikte zincirlemesi gerekir. Aşağıdaki kod, bunun nasıl kullanılabileceğini gösterir.

```csharp
XmlWriterSettings writerSettings = new XmlWriterSettings {  Indent = true };
XmlWriter xmlWriter = XmlWriter.Create(File.OpenWrite(args[1]), writerSettings);
XamlXmlWriter xamlWriter = new XamlXmlWriter(xmlWriter, new XamlSchemaContext());
XamlServices.Save(new ViewStateCleaningWriter(ActivityXamlServices.CreateBuilderWriter(xamlWriter)), ab);
```

## <a name="to-use-this-sample"></a>Bu örneği kullanmak için

1. Visual Studio 2010 kullanarak, ViewStateCleaningWriter. sln çözüm dosyasını açın.

2. Bir komut istemi açın ve Viewstagectaaningwriter. exe ' nin oluşturulduğu dizine gidin.

3. Workflow1. xaml dosyasında ViewStateCleaningWriter. exe ' yi çalıştırın.

   Yürütülebilir dosya için sözdizimi aşağıdaki örnekte gösterilmiştir.

   ```console
   ViewStateCleaningWriter.exe [input file] [output file]
   ```

   Bu, tüm görünüm durumu bilgilerini kaldıran \[çıkışdosyası] öğesine bir XAML dosyası verir.

> [!NOTE]
> <xref:System.Activities.Statements.Sequence> bir iş akışı için bir dizi sanallaştırma ipucu kaldırılır. Bu, tasarımcının bir sonraki yüklenilişinde düzeni yeniden hesaplamasını sağlar. Bu örneği bir <xref:System.Activities.Statements.Flowchart>için kullandığınızda, tüm konumlandırma ve çizgi yönlendirme bilgileri kaldırılır ve tasarımcı 'ya sonraki yükleme sırasında tüm etkinlikler ekranın sol tarafında yığılır.

## <a name="to-create-a-sample-xaml-file-for-use-with-this-sample"></a>Bu örnekle kullanılacak örnek bir XAML dosyası oluşturmak için

1. Visual Studio 2010 ' i açın.

2. Yeni bir Iş akışı konsol uygulaması oluşturun.

3. Birkaç etkinliği tuval üzerine sürükleyip bırakın

4. İş akışı XAML dosyasını kaydedin.

5. Görünüm durumu ekli özelliklerini görmek için XAML dosyasını inceleyin.

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ViewStateCleaningWriter`

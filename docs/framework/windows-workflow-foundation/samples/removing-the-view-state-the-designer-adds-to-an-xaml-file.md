---
title: Bir XAML dosyasına - WF ekler Tasarımcı görünüm durumunu kaldırma
ms.date: 03/30/2017
ms.assetid: a801ce22-8699-483c-a392-7bb3834aae4f
ms.openlocfilehash: 71a2aadeefd53b391f4589ed9dc32d9cd6e3183a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62004945"
---
# <a name="removing-the-view-state-the-designer-adds-to-an-xaml-file"></a>Tasarımcı görünüm durumunu kaldırma bir XAML dosyasına eklediği

Bu örnek, türetilen bir sınıf oluşturmak nasıl gösterir <xref:System.Xaml.XamlWriter> ve kaldırır bir XAML dosyası durumunu görüntüleyin. [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] Görünüm durumu bilinen XAML belgesine bilgilerini yazar. Görünüm durumu çalışma zamanında gerekli değildir yerleşim konumlandırma gibi tasarım zamanında gerekli olan bilgileri ifade eder. [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)] Bu bilgiler düzenlemiş XAML belgeye ekler. [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)] Görünüm durumu ile XAML dosyasına yazar `mc:Ignorable` özniteliği için çalışma zamanı XAML dosya yüklendiğinde bu bilgileri yüklü değil. Bu örnek, Görünüm durumu bilgilerinin XAML düğümleri işlenirken kaldıran bir sınıf oluşturmak nasıl gösterir.

## <a name="discussion"></a>Tartışma

Bu örnek, özel bir yazıcı oluşturma işlemini gösterir.

Özel bir XAML yazıcısı oluşturmak için devralınan bir sınıf oluşturma <xref:System.Xaml.XamlWriter>. XAML yazıcılar genellikle iç içe gibi "İç" bir XAML yazıcı izlemek için tipik bir durumdur. Bu "İç ' yazıcılar düşünülebilir çalışmak ve sonra işleme yığını geri kalanı için temsilci seçmek için birden çok giriş noktası olmasını sağlayarak, XAML yazıcılar kalan yığın başvuru olarak.

Bu örnekte, ilgilenilen birkaç öğe yok. Yazılmakta olan öğe bir tasarımcı ad alanından olup olmadığını görmek için onay biridir. Bu da bir iş akışında Tasarımcı ad alanı diğer türlerden kullanımını göz şeritler olduğunu unutmayın.

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

Bu aynı zamanda bir yığın düğümü akışı geçişi sırasında kullanılan XAML üyelerinin oluşturur. Bu örnek, kalan iş büyük ölçüde bulunan `WriteStartMember` yöntemi.

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

Sonraki yöntem sonra bunlar yine de bir görünüm durumu kapsayıcıda bulunan olup olmadığını denetleyin ve bu durumda, dönüş ve yazıcı yığın düğüm geçirmeyin.

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

Özel bir XAML yazıcı kullanmak için bu XAML yazıcılar yığında zincir gerekir. Aşağıdaki kod bunu nasıl kullanılabileceğini gösterir.

```csharp
XmlWriterSettings writerSettings = new XmlWriterSettings {  Indent = true };
XmlWriter xmlWriter = XmlWriter.Create(File.OpenWrite(args[1]), writerSettings);
XamlXmlWriter xamlWriter = new XamlXmlWriter(xmlWriter, new XamlSchemaContext());
XamlServices.Save(new ViewStateCleaningWriter(ActivityXamlServices.CreateBuilderWriter(xamlWriter)), ab);
```

## <a name="to-use-this-sample"></a>Bu örneği kullanmak için

1. Visual Studio 2010 kullanarak ViewStateCleaningWriter.sln çözüm dosyasını açın.

2. Bir komut istemi açın ve burada ViewStageCleaningWriter.exe oluşturulmuştur dizine gidin.

3. ViewStateCleaningWriter.exe Workflow1.xaml dosya üzerinde çalıştırın.

   Yürütülebilir dosya için söz dizimi aşağıdaki örnekte gösterilmiştir.

   ```console
   ViewStateCleaningWriter.exe [input file] [output file]
   ```

   Bu bir XAML dosyasına çıkarır \[outfile], sahip olduğu tüm görünüm durumu bilgilerini kaldırıldı.

> [!NOTE]
> İçin bir <xref:System.Activities.Statements.Sequence> iş akışı, bir dizi sanallaştırma ipuçları kaldırılır. Bu, sonraki yüklendiğinde düzenini yeniden hesapla Tasarımcı neden olur. Bu örnek için kullandığınızda bir <xref:System.Activities.Statements.Flowchart>, tüm konumlandırma ve yönlendirme bilgilerini satır kaldırılır ve ekranın sol tarafında yığılma Tasarımcı içinde sonraki yüklemeyi, tüm etkinlikler.

## <a name="to-create-a-sample-xaml-file-for-use-with-this-sample"></a>Bu örnek ile kullanmak için örnek bir XAML dosyası oluşturmak için

1. Visual Studio 2010'u açın.

2. Yeni bir iş akışı konsol uygulaması oluşturun.

3. Sürükle ve bırak tuvale birkaç etkinlikleri

4. İş akışı XAML dosyasını kaydedin.

5. Ekli özellikler durumunu görmek için XAML dosyasını inceleyin.

> [!IMPORTANT]
> Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ViewStateCleaningWriter`
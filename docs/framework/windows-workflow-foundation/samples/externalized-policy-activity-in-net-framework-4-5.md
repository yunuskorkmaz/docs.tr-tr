---
title: .NET Framework 4.5 te dış ilke etkinliği
ms.date: 03/30/2017
ms.assetid: 92fd6f92-23a1-4adf-b96a-2754ea93ad3e
ms.openlocfilehash: 2ec358dbe2ba2b60df707d1ce580bb88e4c4ba1b
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57706383"
---
# <a name="externalized-policy-activity-in-net-framework-45"></a>.NET Framework 4.5 te dış ilke etkinliği

Bu örnek, varolan yürütme ExternalizedPolicy4 etkinlik nasıl imkan gösterir [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] Windows Workflow Foundation (WF 3.5) <xref:System.Workflow.Activities.Rules.RuleSet> nesneler [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] Windows Workflow kurallar altyapısı kullanarak doğrudan Foundation (WF 4.5) WF 3. 5 ', birlikte gönderilir. Bu etkinlik kullanarak açın ve tüm mevcut WF 3.5 yürütme <xref:System.Workflow.Activities.Rules.RuleSet>. WF 3.5 kural Windows Workflow Foundation bir parçası olarak dahil edilen altyapısı hakkında daha fazla bilgi için lütfen okuyun [Windows Workflow Foundation kurallar altyapısı giriş](https://go.microsoft.com/fwlink/?LinkId=166079). Geçiş hakkında daha fazla bilgi için kurallar [!INCLUDE[wf1](../../../../includes/wf1-md.md)] içinde [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)], adresindeki geçiş rehberini okuyun [geçiş kılavuzuna](../migration-guidance.md).

## <a name="projects-in-this-sample"></a>Bu örnekte projeleri

|Proje adı|Açıklama|Ana dosyaları|
|-|-|-|
|ExternalizedPolicy4|ExternalizedPolicy4 etkinlik ve iş WF 4.5 Tasarımcısı içerir.|**ExternalizedPolicy4.cs**: etkinlik tanımı.<br /><br /> **ExternalizedPolicy4Designer.xaml**: Özel Tasarımcısı ExternalizedPolicy4 etkinliği. Kuralları Düzenleyicisi'ni kullanır (<xref:System.Workflow.Activities.Rules.Design.RuleSetDialog>) WF 3.5 kural altyapısından.|
|ImperativeCodeClientSample|Yapılandırır ve kesin C# kod (tasarımcı kullanılan) kullanarak ExternalizedPolicy4 uygulama kullanarak iş akışını çalıştıran örnek istemci uygulaması.|**ApplyDiscount.rules**: İle dosya [!INCLUDE[wf1](../../../../includes/wf1-md.md)] kural tanımlar.<br /><br /> **Order.cs**: Bir müşteri sipariş temsil eden tür. Bu tür nesneler için kuralları uygulanır.<br /><br /> **Program.cs**: Yapılandırır ve bir Policy4 etkinliğinde ApplyDiscount.rules sırada nesnelerin örneklerini için tanımlanan kuralları uygulamak için bir iş akışı çalıştırır.<br /><br /> App.config: Yapılandırma dosyası ile kuralları dosyasının yolu.|
|DesignerClientSample|Örnek yapılandırır ve ExternalPolicy4 uygulamayı kullanarak iş akışını çalıştıran istemci uygulama [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Tasarımcısı.|**Sequence1.XAML**: Kuralı değerlendirme gerçekleştirmek için bir Policy4 etkinliğini kullanan sıralı iş akışı.<br /><br /> **Program.cs**: Sequence1.xaml içinde tanımlanan iş akışı örneğini çalıştırır.|

## <a name="the-externalizedpolicy4-activity"></a>ExternalizedPolicy4 etkinliği

ExternalizedPolicy4 etkinliği bir <xref:System.Activities.NativeActivity> sağlayan WF 3.5 yürütme <xref:System.Workflow.Activities.Rules.RuleSet> 4.5 WF iş akışlarını içindeki nesneleri. Aşağıdaki örnek, etkinlik ortak nesne modelini basitleştirilmiş bir tanımıdır.

```
public class ExternalizedPolicy4Activity<TResult>: CodeActivity
{
    public string RulesFilePath

    public string RuleSetName

    [RequiredArgument]
    public InArgument<T> TargetObject

    [RequiredArgument]
    public OutArgument<T> ResultObject

    public OutArgument<ValidationErrorCollection> ValidationErrors
}
```

|Özellik|Açıklama|
|-|-|
|RuleSetFilePath|.NET Framework 3.5 yoluna <xref:System.Workflow.Activities.Rules.RuleSet> dosya Etkinliği yürütüldüğünde değerlendirilecek.|
|RuleSetName|Adını <xref:System.Workflow.Activities.Rules.RuleSet> .rules dosya içinde kullanılacak.|
|TargetObject|Nesne <xref:System.Workflow.Activities.Rules.Rule> nesneler <xref:System.Workflow.Activities.Rules.RuleSet> karşı değerlendirilir.|
|ResultObject|Kural uygulandıktan sonra elde edilen nesnenin (örneğin, kuralları, giriş bağımsız değişkeni karşı uygulanır ve sonuç sonuç değişkeninde depolanır.|
|ValidationError|Doğrulama sırasında WF 3.5 kural altyapısı tarafından döndürülen doğrulama hatalarının listesini <xref:System.Workflow.Activities.Rules.RuleSet> karşı yürütmeden önce hedef nesne.|

## <a name="externalizedpolicy4-activity-designer"></a>ExternalizedPolicy4 etkinlik Tasarımcısı

ExternalizedPolicy4 Tasarımcı, kod yazmaya gerek kalmadan var olan bir kural kümesi kullanmak için bir etkinlik yapılandırmanıza olanak sağlar. Yalnızca .rules dosyasının bulunduğu yolu ayarlayın ve belirtin <xref:System.Workflow.Activities.Rules.RuleSet> kullanmak istediğiniz adı. Ayrıca değiştirmenizi sağlar <xref:System.Workflow.Activities.Rules.RuleSet>. Çözümü derledikten sonra bunu araç kutusundan Microsoft.Samples.Activities.Rules bölümünde bulunabilir. Tasarımcı .rules dosya seçmenizi sağlar ve bir <xref:System.Workflow.Activities.Rules.RuleSet>. Zaman **Düzenle RuleSet** düğmesine tıklandığında, WF 3.5 <xref:System.Workflow.Activities.Rules.Design.RuleSetDialog> görüntülenir. Bu iletişim kutusunu yeniden barındırılan WF 3.5 kural Düzenleyicisi olan ve görüntüleyip ExternalizedPolicy4 etkinliği yürütür kuralları düzenlemek için kullanılır.

## <a name="policy4-and-externalpolicy4"></a>Policy4 ve ExternalPolicy4

İlke etkinlik oluşturma ve bir .NET Framework 3.5 kural kümesi WF 4.5 iş akışında yürütme sağlar. <xref:System.Workflow.Activities.Rules.RuleSet> Policy4 etkinliğinde XAML tanımı seri hale getirilmiş satır içidir. Mevcut bir kullanmayı ExternalizedPolicy4 örnek dış gösterir <xref:System.Workflow.Activities.Rules.RuleSet> (bir .rules dosyasında yer alan).

## <a name="use-this-sample"></a>Bu örneği kullanın

Hiçbir özel kurulum, bu örneği çalıştırmak için gereklidir. Visual Studio içinde çözümü açın ve sonra basın **F5** uygulamayı çalıştırın.

Bu örnek, iki istemci uygulamalarını içerir: ImperativeCodeClientSample ve DesignerClientSample. ImperativeCodeClientSample istemci, yapılandırma ve C# kesin kod kullanarak ExternalizedPolicy4 etkinlik çalıştırma işlemi gösterilmektedir. DesignerClientSample, yapılandırma ve tasarımcı kullanarak ExternalizedPolicy4 etkinlik çalıştırma işlemi gösterilmektedir.

### <a name="run-the-imperativecodeclientsample-application"></a>ImperativeCodeClientSample uygulamayı çalıştırın

1.  Visual Studio kullanarak açma *Policy4sample.sln* çözüm dosyası.

2.  İçinde **Çözüm Gezgini**, sağ **ImperativeCodeClientSample** proje ve ardından **başlangıç projesi olarak ayarla**.

3.  Projeyi çalıştırmak için basın **Ctrl**+**F5**.

### <a name="run-the-designerclientsample-application"></a>DesignerClientSample uygulamayı çalıştırın

1.  Visual Studio kullanarak açma *Policy4sample.sln* çözüm dosyası.

2.  İçinde **Çözüm Gezgini**, sağ **DesignerClientSample** proje ve ardından **başlangıç projesi olarak ayarla**.

3.  Tuşuna **Ctrl**+**Shift**+**B** Projeyi derlemek için.

4.  Tuşuna **Ctrl**+**F5** projeyi çalıştırın.

> [!IMPORTANT]
> Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.
>
> Bu örnek, şu dizinde bulunur:
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Rules-ExternalizedPolicy4`

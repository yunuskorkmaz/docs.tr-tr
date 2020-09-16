---
title: .NET Framework 4.5’te Dış İlke Etkinliği
ms.date: 03/30/2017
ms.assetid: 92fd6f92-23a1-4adf-b96a-2754ea93ad3e
ms.openlocfilehash: 00b671f169696728610e8ee32f874b44fbff9e33
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556921"
---
# <a name="externalized-policy-activity-in-net-framework-45"></a>.NET Framework 4.5’te Dış İlke Etkinliği

Bu örnek, ExternalizedPolicy4 etkinliğinin, <xref:System.Workflow.Activities.Rules.RuleSet> [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] WF 3,5 ' te sunulan Rules altyapısını kullanarak doğrudan WINDOWS Workflow FOUNDATION (WF 4,5) içindeki mevcut .NET Framework 3,5 WINDOWS Workflow FOUNDATION (WF 3,5) nesnelerinin nasıl yürütülmeye izin verdiğini gösterir. Bu etkinliği kullanarak var olan WF 3,5 'yi açabilir ve çalıştırabilirsiniz <xref:System.Workflow.Activities.Rules.RuleSet> . Windows Workflow Foundation kapsamında yer alan WF 3,5 kural altyapısı hakkında daha fazla bilgi için lütfen [Windows Workflow Foundation kuralları altyapısına giriş](/previous-versions/dotnet/articles/aa480193(v=msdn.10))makalesini okuyun. İçindeki içine kuralları geçirme hakkında daha fazla bilgi için [!INCLUDE[wf1](../../../../includes/wf1-md.md)] [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] , bkz. [Geçiş Kılavuzu](../migration-guidance.md).

## <a name="projects-in-this-sample"></a>Bu örnekteki projeler

|Proje Adı|Description|Ana dosyalar|
|-|-|-|
|ExternalizedPolicy4|ExternalizedPolicy4 etkinliğini ve onun WF 4,5 tasarımcısını içerir.|**ExternalizedPolicy4.cs**: etkinlik tanımı.<br /><br /> **ExternalizedPolicy4Designer. xaml**: ExternalizedPolicy4 etkinliği için özel tasarımcı. <xref:System.Workflow.Activities.Rules.Design.RuleSetDialog>WF 3,5 kural altyapısından Rules düzenleyicisini () kullanır.|
|ImperativeCodeClientSample|ExternalizedPolicy4 uygulaması kullanarak bir iş akışını yapılandıran ve çalıştıran örnek istemci uygulaması (tasarımcı kullanılmaz).|**ApplyDiscount. Rules**: [!INCLUDE[wf1](../../../../includes/wf1-md.md)] kural tanımlarına sahip dosya.<br /><br /> **Order.cs**: bir müşteri siparişini temsil eden tür. Kurallar bu türden nesnelere uygulanır.<br /><br /> **Program.cs**: ApplyDiscount içinde tanımlanan kuralları uygulamak için Policy4 etkinliğine sahip bir iş akışını yapılandırır ve çalıştırır. sıralama nesnelerinin örneklerine yönelik kurallar.<br /><br /> App.config: kural dosyasının yolunu içeren yapılandırma dosyası.|
|DesignerClientSample|Tasarımcıda bir ExternalPolicy4 uygulaması kullanarak bir iş akışını yapılandıran ve çalıştıran örnek istemci uygulaması [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .|**Sequence1. xaml**: kural değerlendirmesi gerçekleştirmek için Policy4 etkinliğini kullanan sıralı iş akışı.<br /><br /> **Program.cs**: Sequence1. xaml içinde tanımlanan iş akışı örneğini çalıştırır.|

## <a name="the-externalizedpolicy4-activity"></a>ExternalizedPolicy4 etkinliği

ExternalizedPolicy4 etkinliği, <xref:System.Activities.NativeActivity> <xref:System.Workflow.Activities.Rules.RuleSet> WF 4,5 iş AKıŞLARıNıN içinde WF 3,5 nesnelerinin yürütülmesini sağlayan bir ' dir. Aşağıdaki örnek, etkinliğin ortak nesne modelinin basitleştirilmiş bir tanımıdır.

```csharp
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
|RuleSetFilePath|<xref:System.Workflow.Activities.Rules.RuleSet>Etkinlik yürütüldüğünde değerlendirilecek .NET Framework 3,5 dosyasının yolu.|
|RuleSetName|<xref:System.Workflow.Activities.Rules.RuleSet>. Rules dosyası içinde kullanılacak adı.|
|TargetObject|<xref:System.Workflow.Activities.Rules.Rule>İçindeki nesnelerin üzerinde <xref:System.Workflow.Activities.Rules.RuleSet> değerlendirildiği nesne.|
|ResultObject|Kurallar uygulandıktan sonra elde edilen nesne (örneğin, kurallar giriş bağımsız değişkenine göre uygulanır ve sonuç sonuç bağımsız değişkeninde saklanır.)|
|Doğrulama hatası|Yürütmeden önce hedef nesneye karşı doğrulanırken WF 3,5 kural altyapısının döndürdüğü doğrulama hatalarının listesi <xref:System.Workflow.Activities.Rules.RuleSet> .|

## <a name="externalizedpolicy4-activity-designer"></a>ExternalizedPolicy4 Etkinlik Tasarımcısı

ExternalizedPolicy4 Tasarımcısı, bir etkinliği kod yazmadan mevcut bir RuleSet 'i kullanacak şekilde yapılandırmanıza olanak tanır. Yalnızca. Rules dosyasının bulunduğu yolu ayarlamanız ve <xref:System.Workflow.Activities.Rules.RuleSet> kullanmak istediğiniz adı belirtmeniz yeterlidir. Ayrıca, değiştirmenizi sağlar <xref:System.Workflow.Activities.Rules.RuleSet> . Çözüm oluşturulduktan sonra, Microsoft. Samples. Activities. Rules bölümündeki araç kutusunda bulunabilir. Tasarımcı bir. Rules dosyası ve bir seçmenizi sağlar <xref:System.Workflow.Activities.Rules.RuleSet> . **RuleSet 'ı Düzenle** DÜĞMESINE tıklandığında WF 3,5 <xref:System.Workflow.Activities.Rules.Design.RuleSetDialog> görüntülenir. Bu iletişim kutusu, yeniden barındırılan WF 3,5 kurallar düzenleyicidir ve ExternalizedPolicy4 etkinliğinin yürütüldüğü kuralları görüntülemek ve düzenlemek için kullanılır.

## <a name="policy4-and-externalpolicy4"></a>Policy4 ve ExternalPolicy4

Ilke etkinliği, bir WF 4,5 iş akışında .NET Framework 3,5 RuleSet oluşturmanıza ve çalıştırmanıza olanak tanır. , <xref:System.Workflow.Activities.Rules.RuleSet> Policy4 ACTIVITY xaml tanımında satır içi olarak serileştirilir. ExternalizedPolicy4 örneği, var olan bir dış öğenin <xref:System.Workflow.Activities.Rules.RuleSet> (. Rules dosyasında bulunur) nasıl kullanılacağını gösterir.

## <a name="use-this-sample"></a>Bu örneği kullanın

Bu örneği çalıştırmak için özel bir kurulum gerekmez. Visual Studio 'da çözümü açın ve **F5** tuşuna basarak uygulamayı çalıştırın.

Bu örnek iki istemci uygulaması içerir: ImperativeCodeClientSample ve DesignerClientSample. ImperativeCodeClientSample istemcisi C# kesinlik kodu kullanılarak ExternalizedPolicy4 etkinliğinin nasıl yapılandırılacağını ve çalıştırılacağını gösterir. DesignerClientSample, Tasarımcıyı kullanarak ExternalizedPolicy4 etkinliğinin nasıl yapılandırılacağını ve çalıştırılacağını gösterir.

### <a name="run-the-imperativecodeclientsample-application"></a>ImperativeCodeClientSample uygulamasını çalıştırma

1. Visual Studio 'yu kullanarak *Policy4Sample. sln* çözüm dosyasını açın.

2. **Çözüm Gezgini**' de, **ImperativeCodeClientSample** projesine sağ tıklayın ve ardından **Başlangıç projesi olarak ayarla**' yı seçin.

3. Projeyi çalıştırmak için **CTRL** + **F5**tuşuna basın.

### <a name="run-the-designerclientsample-application"></a>DesignerClientSample uygulamasını çalıştırma

1. Visual Studio 'yu kullanarak *Policy4Sample. sln* çözüm dosyasını açın.

2. **Çözüm Gezgini**, **DesignerClientSample** projesine sağ tıklayın ve ardından **Başlangıç projesi olarak ayarla**' yı seçin.

3. **Ctrl** + **Shift** + Projeyi derlemek için CTRL SHIFT**B** tuşlarına basın.

4. **Ctrl** + Projeyi çalıştırmak için CTRL**F5** tuşuna basın.

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .
>
> Bu örnek aşağıdaki dizinde bulunur:
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Rules-ExternalizedPolicy4`

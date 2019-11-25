---
title: .NET Framework 4.5’te Dış İlke Etkinliği
ms.date: 03/30/2017
ms.assetid: 92fd6f92-23a1-4adf-b96a-2754ea93ad3e
ms.openlocfilehash: efc8b8169a6b984e003444c4669122ce6fa7f9d0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283159"
---
# <a name="externalized-policy-activity-in-net-framework-45"></a>.NET Framework 4.5’te Dış İlke Etkinliği

Bu örnek, ExternalizedPolicy4 etkinliğinin, WF 3,5 ' te sunulan Rules altyapısını kullanarak doğrudan [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] Windows Workflow Foundation (WF 4,5) <xref:System.Workflow.Activities.Rules.RuleSet> nesnelerinin mevcut .NET Framework 3,5 Windows Workflow Foundation (WF 3,5) nasıl yürütülmeye izin verdiğini gösterir. Bu etkinliği kullanarak var olan WF 3,5 <xref:System.Workflow.Activities.Rules.RuleSet>açabilir ve çalıştırabilirsiniz. Windows Workflow Foundation kapsamında yer alan WF 3,5 kural altyapısı hakkında daha fazla bilgi için lütfen [Windows Workflow Foundation kuralları altyapısına giriş](https://go.microsoft.com/fwlink/?LinkId=166079)makalesini okuyun. Kuralları [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)][!INCLUDE[wf1](../../../../includes/wf1-md.md)] geçirme hakkında daha fazla bilgi için, bkz. [Geçiş Kılavuzu](../migration-guidance.md).

## <a name="projects-in-this-sample"></a>Bu örnekteki projeler

|Proje adı|Açıklama|Ana dosyalar|
|-|-|-|
|ExternalizedPolicy4|ExternalizedPolicy4 etkinliğini ve onun WF 4,5 tasarımcısını içerir.|**ExternalizedPolicy4.cs**: etkinlik tanımı.<br /><br /> **ExternalizedPolicy4Designer. xaml**: ExternalizedPolicy4 etkinliği için özel tasarımcı. WF 3,5 kural altyapısından kural düzenleyicisini (<xref:System.Workflow.Activities.Rules.Design.RuleSetDialog>) kullanır.|
|ImperativeCodeClientSample|Bir ExternalizedPolicy4 uygulamasını kullanarak bir iş akışını yapılandıran ve bu uygulama çalıştıran örnek istemci uygulaması C# , zorunlu kod (tasarımcı olmadan) kullanır.|**ApplyDiscount. Rules**: [!INCLUDE[wf1](../../../../includes/wf1-md.md)] kural tanımlarına sahip dosya.<br /><br /> **Order.cs**: bir müşteri siparişini temsil eden tür. Kurallar bu türden nesnelere uygulanır.<br /><br /> **Program.cs**: ApplyDiscount içinde tanımlanan kuralları uygulamak için Policy4 etkinliğine sahip bir iş akışını yapılandırır ve çalıştırır. sıralama nesnelerinin örneklerine yönelik kurallar.<br /><br /> App. config: kural dosyasının yolunu içeren yapılandırma dosyası.|
|DesignerClientSample|[!INCLUDE[wf1](../../../../includes/wf1-md.md)] tasarımcısında bir ExternalPolicy4 uygulaması kullanarak bir iş akışını yapılandıran ve çalıştıran örnek istemci uygulaması.|**Sequence1. xaml**: kural değerlendirmesi gerçekleştirmek için Policy4 etkinliğini kullanan sıralı iş akışı.<br /><br /> **Program.cs**: Sequence1. xaml içinde tanımlanan iş akışı örneğini çalıştırır.|

## <a name="the-externalizedpolicy4-activity"></a>ExternalizedPolicy4 etkinliği

ExternalizedPolicy4 etkinliği, WF 4,5 iş akışlarında WF 3,5 <xref:System.Workflow.Activities.Rules.RuleSet> nesneleri yürütmeye izin veren bir <xref:System.Activities.NativeActivity>. Aşağıdaki örnek, etkinliğin ortak nesne modelinin basitleştirilmiş bir tanımıdır.

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
|RuleSetFilePath|Etkinlik yürütüldüğünde değerlendirilecek .NET Framework 3,5 <xref:System.Workflow.Activities.Rules.RuleSet> dosyasının yolu.|
|RuleSetName|. Rules dosyası içinde kullanılacak <xref:System.Workflow.Activities.Rules.RuleSet> adı.|
|TargetObject|<xref:System.Workflow.Activities.Rules.RuleSet> <xref:System.Workflow.Activities.Rules.Rule> nesnelerinin üzerinde değerlendirildiği nesne.|
|ResultObject|Kurallar uygulandıktan sonra elde edilen nesne (örneğin, kurallar giriş bağımsız değişkenine göre uygulanır ve sonuç sonuç bağımsız değişkeninde saklanır.)|
|ValidationError|Yürütmeden önce hedef nesneye karşı <xref:System.Workflow.Activities.Rules.RuleSet> doğrulanırken WF 3,5 kural altyapısının döndürdüğü doğrulama hatalarının listesi.|

## <a name="externalizedpolicy4-activity-designer"></a>ExternalizedPolicy4 Etkinlik Tasarımcısı

ExternalizedPolicy4 Tasarımcısı, bir etkinliği kod yazmadan mevcut bir RuleSet 'i kullanacak şekilde yapılandırmanıza olanak tanır. Yalnızca. Rules dosyasının bulunduğu yolu ayarlamanız ve kullanmak istediğiniz <xref:System.Workflow.Activities.Rules.RuleSet> adı belirtmeniz yeterlidir. Ayrıca, <xref:System.Workflow.Activities.Rules.RuleSet>değiştirmenize de olanak tanır. Çözüm oluşturulduktan sonra, Microsoft. Samples. Activities. Rules bölümündeki araç kutusunda bulunabilir. Tasarımcı bir. Rules dosyası ve bir <xref:System.Workflow.Activities.Rules.RuleSet>seçmenizi sağlar. **RuleSet 'ı Düzenle** düğmesine TıKLANDıĞıNDA, WF 3,5 <xref:System.Workflow.Activities.Rules.Design.RuleSetDialog> görüntülenir. Bu iletişim kutusu, yeniden barındırılan WF 3,5 kurallar düzenleyicidir ve ExternalizedPolicy4 etkinliğinin yürütüldüğü kuralları görüntülemek ve düzenlemek için kullanılır.

## <a name="policy4-and-externalpolicy4"></a>Policy4 ve ExternalPolicy4

Ilke etkinliği, bir WF 4,5 iş akışında .NET Framework 3,5 RuleSet oluşturmanıza ve çalıştırmanıza olanak tanır. <xref:System.Workflow.Activities.Rules.RuleSet>, Policy4 Activity XAML tanımında satır içi olarak serileştirilir. ExternalizedPolicy4 örneği, var olan bir dış <xref:System.Workflow.Activities.Rules.RuleSet> (. Rules dosyasında bulunur) nasıl kullanılacağını gösterir.

## <a name="use-this-sample"></a>Bu örneği kullanın

Bu örneği çalıştırmak için özel bir kurulum gerekmez. Visual Studio 'da çözümü açın ve **F5** tuşuna basarak uygulamayı çalıştırın.

Bu örnek iki istemci uygulaması içerir: ImperativeCodeClientSample ve DesignerClientSample. ImperativeCodeClientSample istemcisi, ExternalizedPolicy4 etkinliğinin kesinlik kodu kullanılarak C# nasıl yapılandırılacağını ve çalıştırılacağını gösterir. DesignerClientSample, Tasarımcıyı kullanarak ExternalizedPolicy4 etkinliğinin nasıl yapılandırılacağını ve çalıştırılacağını gösterir.

### <a name="run-the-imperativecodeclientsample-application"></a>ImperativeCodeClientSample uygulamasını çalıştırma

1. Visual Studio 'yu kullanarak *Policy4Sample. sln* çözüm dosyasını açın.

2. **Çözüm Gezgini**' de, **ImperativeCodeClientSample** projesine sağ tıklayın ve ardından **Başlangıç projesi olarak ayarla**' yı seçin.

3. Projeyi çalıştırmak için **Ctrl**+**F5**tuşuna basın.

### <a name="run-the-designerclientsample-application"></a>DesignerClientSample uygulamasını çalıştırma

1. Visual Studio 'yu kullanarak *Policy4Sample. sln* çözüm dosyasını açın.

2. **Çözüm Gezgini**, **DesignerClientSample** projesine sağ tıklayın ve ardından **Başlangıç projesi olarak ayarla**' yı seçin.

3. Projeyi derlemek için **Ctrl**+**SHIFT**+**B** tuşlarına basın.

4. Projeyi çalıştırmak için **Ctrl**+**F5** tuşuna basın.

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://go.microsoft.com/fwlink/?LinkId=150780) gidin.
>
> Bu örnek aşağıdaki dizinde bulunur:
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Rules-ExternalizedPolicy4`

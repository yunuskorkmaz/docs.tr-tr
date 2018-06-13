---
title: .NET Framework 4.5 ilke etkinlik
ms.date: 03/30/2017
ms.assetid: 8e375e0c-d7c1-4d69-88ab-36d52db0aa7e
ms.openlocfilehash: 52f0cdd3714367598c83f72e2a8203c2ae27eb4e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33518906"
---
# <a name="policy-activity-in-net-framework-45"></a>.NET Framework 4.5 ilke etkinlik
Windows Workflow Foundation Policy4 etkinlik verir [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] (WF 3.5) <xref:System.Workflow.Activities.Rules.RuleSet> Windows Workflow Foundation kullanılacak nesneleri [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF 4.5) WF 3. 5 ' sevk kurallar altyapısı kullanarak doğrudan. Bu etkinlik kullanarak oluşturma ve WF 3.5 yürütme <xref:System.Workflow.Activities.Rules.RuleSet>. Windows Workflow Foundation bir parçası olarak dahil edilen WF 3.5 kurallar altyapısı hakkında daha fazla bilgi için Windows Workflow Foundation kurallar altyapısı giriş okuyun. Geçiş hakkında daha fazla bilgi için WF kuralları [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)], Lütfen okuyun [Geçiş Kılavuzu](../../../../docs/framework/windows-workflow-foundation/migration-guidance.md).  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Rules-Policy4`  
  
## <a name="projects-in-this-sample"></a>Bu örnek proje  
  
|Proje adı|Açıklama|Ana dosyaları|  
|------------------|-----------------|----------------|  
|Policy4|Policy4 etkinlik içerir ve kendi [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Tasarımcısı.|**Policy4.cs**: Policy4 etkinlik tanımı.<br /><br /> **PolicyDesigner.xaml**: özel Tasarımcısı Policy4 etkinliği. Kuralları Düzenleyicisi'ni kullanır ([RuleSetDialog sınıfı](http://go.microsoft.com/fwlink/?LinkId=150378)) gelen [!INCLUDE[wf1](../../../../includes/wf1-md.md)] kurallar altyapısı.|  
|ImperativeCodeClientSample|Örnek yapılandırır ve kesinlik temelli C# kod kullanarak bir Policy4 uygulaması kullanarak bir iş akışı çalıştıran istemci uygulaması (hiçbir [!INCLUDE[wf1](../../../../includes/wf1-md.md)] kullanılan Designer).|**ApplyDiscount.rules**: ile dosya [!INCLUDE[wf1](../../../../includes/wf1-md.md)] kural tanımlar.<br /><br /> **Order.cs**: Müşteri siparişi temsil eden tür. Kuralları, bu tür nesnelere uygulanır.<br /><br /> **Program.cs**: yapılandırır ve sipariş nesnelerinin örneklerini ApplyDiscount.rules tanımlanmış kuralları uygulamak için Policy4 etkinlik sahip bir iş akışı çalıştırır.<br /><br /> **App.config**: kuralları dosyasının yolunu yapılandırma dosyası.|  
|DesignerClientSample|Örnek yapılandırır ve bir Policy4 uygulaması kullanarak bir iş akışı çalıştıran istemci uygulamanın [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Tasarımcısı.|**Sequence1.XAML**: Policy4 etkinlik kural değerlendirmesi gerçekleştirmek için kullandığı sıralı iş akışı.<br /><br /> `Program.cs`: Sequence1.xaml içinde tanımlanan iş akışı örneğini çalıştırır.|  
  
## <a name="the-policy4-activity"></a>Policy4 etkinliği  
 Öğesinden türeyen bir sınıf Policy4 etkinliktir <xref:System.Activities.NativeActivity%601> yürütmek için iş akışlarını tanır [!INCLUDE[wf1](../../../../includes/wf1-md.md)] RuleSets. Aşağıdaki kod örneği, etkinlik ortak OM Basitleştirilmiş tanımıdır.  
  
```csharp  
public class Policy4Activity<TResult>: NativeActivity<TResult>  
{  
    public RuleSet RuleSet  
  
    [IsRequired]  
    public InArgument Input  
  
    public OutArgument<ValidationErrorCollection> ValidationErrors  
}  
```  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|RuleSet|WF [RuleSet sınıfı](http://go.microsoft.com/fwlink/?LinkId=150379) etkinlik çalıştırıldığında değerlendirilecek .NET Framework 3.5 için.|  
|TargetObject|Nesneyle kurallarında [RuleSet sınıfı](http://go.microsoft.com/fwlink/?LinkId=150379) değerlendirilir.|  
|ValidationError|Tarafından döndürülen doğrulama hataları listesine [!INCLUDE[wf1](../../../../includes/wf1-md.md)] kuralı altyapısı doğrularken .NET Framework 3.5 için [RuleSet sınıfı](http://go.microsoft.com/fwlink/?LinkId=150379) karşı yürütmeden önce hedef nesne.|  
  
## <a name="policy4-activity-designer"></a>Policy4 etkinlik Tasarımcısı  
 Policy4 Tasarımcısı Policy4 etkinlik kod yazmak zorunda kalmadan yapılandırma yeteneği ekler. Çözümü derledikten sonra şu araç kutusunda bölümünde bulunabilir **Microsoft.Samples.Activities.Rules**.  
  
 WF Tasarımcısı, hedef nesnesi ve bir RuleSet yapılandırmanıza olanak sağlar. Zaman **Düzenle RuleSet** düğmesine tıklandığında, WF [RuleSetDialog sınıfı](http://go.microsoft.com/fwlink/?LinkId=150378) için [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] görüntülenir. Bu iletişim kutusunu yeniden barındırılır [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] kurallar düzenleyicisinde. Düzenleyici oluşturmak ve Policy4 etkinlik yürütür kuralları düzenlemek için kullanın.  
  
## <a name="using-this-sample"></a>Bu örnek kullanma  
 Hiçbir özel ayarlama, bu örneği çalıştırmak için gereklidir. Yalnızca Visual Studio'da Çözüm açmak ve uygulamayı çalıştırmak için F5 tuşuna basın.  
  
 Bu örnek iki istemci uygulamaları içerir: ImperativeCodeClientSample ve DesignerClientSample. ImperativeCodeClientSample istemci, yapılandırma ve C# kesinlik temelli kodu kullanarak Policy40 etkinliği çalıştırma gösterilmektedir. DesignerClientSample, yapılandırma ve çalıştırma Tasarımcısı'nı kullanarak Policy4 etkinliği gösterilmektedir.  
  
#### <a name="to-run-the-imperativecodeclientsample-client-application"></a>ImperativeCodeClientSample istemci uygulamasını çalıştırmak için  
  
1.  Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], Policy4Sample.sln çözüm dosyasını açın.  
  
2.  İçinde **Çözüm Gezgini**, sağ **ImperativeCodeClientSample** proje ve ardından **başlangıç projesi olarak ayarla**.  
  
3.  Projeyi çalıştırmak için CTRL + F5 tuşuna basın.  
  
#### <a name="to-run-the-imperativecodeclientsample-client-application"></a>ImperativeCodeClientSample istemci uygulamasını çalıştırmak için  
  
1.  Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], Policy4Sample.sln çözüm dosyasını açın.  
  
2.  İçinde **Çözüm Gezgini**, sağ **DesignerClientSample** projesi.  
  
    -   Seçin **başlangıç projesi olarak ayarla**.  
  
3.  Projeyi derlemek için CTRL + SHIFT + B tuşuna basın.  
  
4.  Projeyi çalıştırmak için CTRL + F5 tuşuna basın.
---
title: .NET Framework 4. 5'te ilke etkinliği
ms.date: 03/30/2017
ms.assetid: 8e375e0c-d7c1-4d69-88ab-36d52db0aa7e
ms.openlocfilehash: 9d8983f2f1d3f75beffeacfff4b673f6c23c4204
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2018
ms.locfileid: "45646096"
---
# <a name="policy-activity-in-net-framework-45"></a>.NET Framework 4. 5'te ilke etkinliği
Windows Workflow Foundation'da Policy4 etkinliği sağlar [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] (WF 3.5) <xref:System.Workflow.Activities.Rules.RuleSet> Windows Workflow Foundation'da kullanılmak üzere nesneleri [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF 4.5) kullanarak WF 3. 5'sevk kurallar altyapısı tarafından doğrudan. Bu etkinlik kullanarak oluşturabilir ve WF 3.5 yürütme <xref:System.Workflow.Activities.Rules.RuleSet>. WF 3.5 kural Windows Workflow Foundation bir parçası olarak dahil edilen altyapısı hakkında daha fazla bilgi için Windows Workflow Foundation kurallar altyapısı giriş okuyun. Geçiş hakkında daha fazla bilgi için WF kuralları [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)], okuyun [geçiş kılavuzuna](../../../../docs/framework/windows-workflow-foundation/migration-guidance.md).  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Rules-Policy4`  
  
## <a name="projects-in-this-sample"></a>Bu örnekte projeleri  
  
|Proje adı|Açıklama|Ana dosyaları|  
|------------------|-----------------|----------------|  
|Policy4|Policy4 etkinlik içerir ve kendi [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Tasarımcısı.|**Policy4.cs**: Policy4 etkinlik tanımı.<br /><br /> **PolicyDesigner.xaml**: özel Tasarımcısı Policy4 etkinliği. Kuralları Düzenleyicisi'ni kullanır ([RuleSetDialog sınıfı](https://go.microsoft.com/fwlink/?LinkId=150378)) öğesinden [!INCLUDE[wf1](../../../../includes/wf1-md.md)] kurallar altyapısı.|  
|ImperativeCodeClientSample|Örnek yapılandırır ve kesin C# kod kullanarak bir Policy4 uygulaması kullanarak iş akışını çalıştıran istemci uygulaması (hiçbir [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Tasarımcısı kullanılır).|**ApplyDiscount.rules**: ile dosya [!INCLUDE[wf1](../../../../includes/wf1-md.md)] kural tanımlar.<br /><br /> **Order.cs**: bir müşteri sipariş temsil eden tür. Bu tür nesneler için kuralları uygulanır.<br /><br /> **Program.cs**: yapılandırır ve bir Policy4 etkinliğinde ApplyDiscount.rules sırada nesnelerin örneklerini için tanımlanan kuralları uygulamak için bir iş akışı çalıştırır.<br /><br /> **App.config**: yapılandırma dosyası kuralları dosyasının yolu.|  
|DesignerClientSample|Örnek yapılandırır ve bir Policy4 uygulamasında kullanarak iş akışını çalıştıran istemci uygulama [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Tasarımcısı.|**Sequence1.XAML**: kural değerlendirmelerini gerçekleştirmek için bir Policy4 etkinliğini kullanan sıralı iş akışı.<br /><br /> `Program.cs`: Sequence1.xaml içinde tanımlanan iş akışı örneğini çalıştırır.|  
  
## <a name="the-policy4-activity"></a>Policy4 etkinliği  
 Türetilen bir sınıf Policy4 etkinliktir <xref:System.Activities.NativeActivity%601> yürütmek iş akışlarını sağlayan [!INCLUDE[wf1](../../../../includes/wf1-md.md)] RuleSets. Aşağıdaki kod örneği, etkinlik ortak OM basitleştirilmiş bir tanımıdır.  
  
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
|Kural kümesi|WF [RuleSet sınıfı](https://go.microsoft.com/fwlink/?LinkId=150379) etkinlik yürütüldüğünde değerlendirilecek .NET Framework 3.5 için.|  
|TargetObject|Nesneyle kurallarında [RuleSet sınıfı](https://go.microsoft.com/fwlink/?LinkId=150379) değerlendirilir.|  
|ValidationError|Tarafından döndürülen doğrulama hatalarının listesini [!INCLUDE[wf1](../../../../includes/wf1-md.md)] doğrulama sırasında .NET Framework 3.5 kural altyapısı [RuleSet sınıfı](https://go.microsoft.com/fwlink/?LinkId=150379) karşı yürütmeden önce hedef nesne.|  
  
## <a name="policy4-activity-designer"></a>Policy4 etkinlik Tasarımcısı  
 Policy4 Tasarımcı bir Policy4 etkinliği kod yazmak zorunda kalmadan yapılandırma yeteneği ekler. Çözümü derledikten sonra bunu araç kutusundan bölümünde bulunabilir **Microsoft.Samples.Activities.Rules**.  
  
 WF Tasarımcısı bir hedef nesnesi ile bir RuleSet yapılandırmanıza olanak sağlar. Zaman **Düzenle RuleSet** düğmesine tıklandığında, WF [RuleSetDialog sınıfı](https://go.microsoft.com/fwlink/?LinkId=150378) için [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] görüntülenir. Bu iletişim kutusunu yeniden barındırılır [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] kuralları Düzenleyicisi. Düzenleyici, oluşturmak ve Policy4 etkinliği yürütür kuralları düzenlemek için kullanın.  
  
## <a name="using-this-sample"></a>Bu örnek kullanma  
 Bu örneği çalıştırmak için özel kurulması gerekir. Yalnızca Visual Studio içinde çözümü açın ve uygulamayı çalıştırmak için F5 tuşuna basın.  
  
 Bu örnek iki istemci uygulamalarını içerir: ImperativeCodeClientSample ve DesignerClientSample. ImperativeCodeClientSample istemci, yapılandırma ve C# kesin kod kullanarak Policy40 etkinlik çalıştırma işlemi gösterilmektedir. DesignerClientSample, yapılandırma ve tasarımcı kullanarak Policy4 etkinlik çalıştırma işlemi gösterilmektedir.  
  
#### <a name="to-run-the-imperativecodeclientsample-client-application"></a>ImperativeCodeClientSample istemci uygulamayı çalıştırmak için  
  
1.  Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], Policy4Sample.sln çözüm dosyasını açın.  
  
2.  İçinde **Çözüm Gezgini**, sağ **ImperativeCodeClientSample** proje ve ardından **başlangıç projesi olarak ayarla**.  
  
3.  Projeyi çalıştırmak için CTRL + F5 tuşlarına basın.  
  
#### <a name="to-run-the-imperativecodeclientsample-client-application"></a>ImperativeCodeClientSample istemci uygulamayı çalıştırmak için  
  
1.  Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], Policy4Sample.sln çözüm dosyasını açın.  
  
2.  İçinde **Çözüm Gezgini**, sağ **DesignerClientSample** proje.  
  
    -   Seçin **başlangıç projesi olarak ayarla**.  
  
3.  Projeyi derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
4.  Projeyi çalıştırmak için CTRL + F5 tuşlarına basın.
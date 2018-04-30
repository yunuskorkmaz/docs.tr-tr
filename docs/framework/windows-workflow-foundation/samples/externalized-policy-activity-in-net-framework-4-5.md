---
title: .NET Framework 4.5 externalized ilke etkinlik
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92fd6f92-23a1-4adf-b96a-2754ea93ad3e
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f131d644d58359cec305b83c136e6fe7f68a1b93
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="externalized-policy-activity-in-net-framework-45"></a>.NET Framework 4.5 externalized ilke etkinlik
Bu örnek varolan yürütme ExternalizedPolicy4 etkinlik nasıl sağladığını gösterir [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] Windows Workflow Foundation (WF 3.5) <xref:System.Workflow.Activities.Rules.RuleSet> nesnelerini [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] Windows Workflow kurallar altyapısı kullanarak doğrudan Foundation (WF 4.5) Bu WF 3. 5 ' gönderilmektedir. Bu etkinlik kullanarak açın ve varolan tüm WF 3.5 yürütme <xref:System.Workflow.Activities.Rules.RuleSet>. Windows Workflow Foundation bir parçası olarak dahil edilen WF 3.5 kurallar altyapısı hakkında daha fazla bilgi için lütfen okuyun [Windows Workflow Foundation kurallar altyapısı giriş](http://go.microsoft.com/fwlink/?LinkId=166079). Geçiş hakkında daha fazla bilgi için kurallar [!INCLUDE[wf1](../../../../includes/wf1-md.md)] içinde [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)], lütfen adresindeki Geçiş Kılavuzu okuyun [Geçiş Kılavuzu](../../../../docs/framework/windows-workflow-foundation/migration-guidance.md).  
  
## <a name="projects-in-this-sample"></a>Bu örnek proje  
  
|Proje adı|Açıklama|Ana dosyaları|  
|-|-|-|  
|ExternalizedPolicy4|ExternalizedPolicy4 etkinlik ve onun WF 4.5 Tasarımcısı içerir.|**ExternalizedPolicy4.cs**: etkinlik tanımı.<br /><br /> **ExternalizedPolicy4Designer.xaml**: özel Tasarımcısı ExternalizedPolicy4 etkinliği. Kuralları Düzenleyicisi'ni kullanır (<xref:System.Workflow.Activities.Rules.Design.RuleSetDialog>) WF 3.5 kuralları altyapısından.|  
|ImperativeCodeClientSample|Yapılandırır ve kesinlik temelli C# kod (tasarımcı kullanılan) kullanarak ExternalizedPolicy4 uygulama kullanarak bir iş akışı çalışan örnek istemci uygulaması.|**ApplyDiscount.rules**: ile dosya [!INCLUDE[wf1](../../../../includes/wf1-md.md)] kural tanımlar.<br /><br /> **Order.cs**: Müşteri siparişi temsil eden tür. Kuralları, bu tür nesnelere uygulanır.<br /><br /> **Program.cs**: yapılandırır ve sipariş nesnelerinin örneklerini ApplyDiscount.rules tanımlanmış kuralları uygulamak için Policy4 etkinlik sahip bir iş akışı çalıştırır.<br /><br /> App.config: Kuralları dosyasının yolunu ile yapılandırma dosyası.|  
|DesignerClientSample|Örnek yapılandırır ve ExternalPolicy4 uygulamada kullanarak bir iş akışı çalıştıran istemci uygulamanın [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Tasarımcısı.|**Sequence1.XAML**: Policy4 etkinlik kural değerlendirmesi gerçekleştirmek için kullandığı sıralı iş akışı.<br /><br /> **Program.cs**: Sequence1.xaml içinde tanımlanan iş akışı örneğini çalıştırır.|  
  
## <a name="the-externalizedpolicy4-activity"></a>ExternalizedPolicy4 etkinliği  
 ExternalizedPolicy4 etkinliği bir <xref:System.Activities.NativeActivity> sağlayan WF 3.5 yürütme <xref:System.Workflow.Activities.Rules.RuleSet> WF 4.5 iş akışları içindeki nesneleri. Aşağıdaki örnekte, etkinlik ortak nesne modelinin basitleştirilmiş bir tanımıdır.  
  
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
|RuleSetFilePath|.NET Framework 3.5 yoluna <xref:System.Workflow.Activities.Rules.RuleSet> etkinlik çalıştırıldığında değerlendirilecek dosya.|  
|RuleSetName|Adını <xref:System.Workflow.Activities.Rules.RuleSet> .rules dosyasında kullanılacak.|  
|TargetObject|Nesne <xref:System.Workflow.Activities.Rules.Rule> nesnelerini <xref:System.Workflow.Activities.Rules.RuleSet> karşı değerlendirilir.|  
|ResultObject|Kurallar uygulandıktan sonra elde edilen nesnenin (örneğin, kurallar, giriş bağımsız değişkeni karşı uygulanır ve sonuç sonuç değişkeninde depolanır.|  
|ValidationError|Doğrularken WF 3.5 kurallar altyapısı tarafından döndürülen doğrulama hataları listesine <xref:System.Workflow.Activities.Rules.RuleSet> karşı yürütmeden önce hedef nesne.|  
  
## <a name="externalizedpolicy4-activity-designer"></a>ExternalizedPolicy4 etkinlik Tasarımcısı  
 ExternalizedPolicy4 Tasarımcısı kod yazmadan varolan RuleSet kullanmak için bir etkinlik yapılandırmanıza olanak sağlar. Yalnızca .rules dosyasının bulunduğu yolu ayarlayın ve belirtin <xref:System.Workflow.Activities.Rules.RuleSet> kullanmak istediğiniz adı. Ayrıca değiştirmenizi sağlar <xref:System.Workflow.Activities.Rules.RuleSet>. Çözümü derledikten sonra araç kutusunda Microsoft.Samples.Activities.Rules bölümünde bulunabilir. Tasarımcı .rules dosya seçmenize olanak sağlar ve bir <xref:System.Workflow.Activities.Rules.RuleSet>. Zaman **Düzenle RuleSet** düğmesine tıklandığında, WF 3.5 <xref:System.Workflow.Activities.Rules.Design.RuleSetDialog> görüntülenir. Bu iletişim kutusunu yeniden barındırılan WF 3.5 kuralları düzenleyicidir ve görüntülemek ve ExternalizedPolicy4 etkinlik yürütür kuralları düzenlemek için kullanılır.  
  
## <a name="policy4-and-externalpolicy4"></a>Policy4 ve ExternalPolicy4  
 [.NET Framework 4.5 ilke etkinlik](../../../../docs/framework/windows-workflow-foundation/samples/policy-activity-in-net-framework-4-5.md) etkinlik oluşturma ve .NET Framework 3.5 RuleSet WF 4.5 iş akışında yürütme olanak tanır. <xref:System.Workflow.Activities.Rules.RuleSet> Serileştirilmiş satır içi olarak Policy4 etkinliğinde XAML tanımı. Mevcut bir kullanmayı ExternalizedPolicy4 örnek dış gösterir <xref:System.Workflow.Activities.Rules.RuleSet> (.rules dosyasında yer alan).  
  
## <a name="using-this-sample"></a>Bu örnek kullanma  
 Hiçbir özel kurulum, bu örneği çalıştırmak için gereklidir. Çözümde açmak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], uygulamayı çalıştırmak için F5 tuşuna basın.  
  
 Bu örnek iki istemci uygulamaları içerir: ImperativeCodeClientSample ve DesignerClientSample. ImperativeCodeClientSample istemci, yapılandırma ve C# kesinlik temelli kodu kullanarak ExternalizedPolicy4 etkinliği çalıştırma gösterilmektedir. DesignerClientSample, yapılandırma ve çalıştırma Tasarımcısı'nı kullanarak ExternalizedPolicy4 etkinliği gösterilmektedir.  
  
#### <a name="to-run-the-imperativecodeclientsample-application"></a>ImperativeCodeClientSample uygulamayı çalıştırmak için  
  
1.  Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], Policy4sample.sln çözüm dosyasını açın.  
  
2.  İçinde **Çözüm Gezgini**, sağ **ImperativeCodeClientSample** proje ve ardından **başlangıç projesi olarak ayarla**.  
  
3.  Projeyi çalıştırmak için CTRL + F5 tuşuna basın.  
  
#### <a name="to-run-the-designerclientsample-application"></a>DesignerClientSample uygulamayı çalıştırmak için  
  
1.  Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], Policy4sample.sln çözüm dosyasını açın.  
  
2.  İçinde **Çözüm Gezgini**, sağ **DesignerClientSample** proje ve ardından **başlangıç projesi olarak ayarla**.  
  
3.  Projeyi derlemek için CTRL + SHIFT + B tuşuna basın.  
  
4.  Projeyi çalıştırmak için CTRL + F5 tuşuna basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Rules-ExternalizedPolicy4`

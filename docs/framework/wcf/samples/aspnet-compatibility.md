---
title: ASP.NET Uyumluluğu
ms.date: 03/30/2017
ms.assetid: c8b51f1e-c096-4c42-ad99-0519887bbbc5
ms.openlocfilehash: f621a3f13fafee67a015d463898a10aaf9104008
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33806227"
---
# <a name="aspnet-compatibility"></a>ASP.NET Uyumluluğu
Bu örnek nasıl etkinleştirileceğini göstermektedir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uyumluluk modunda Windows Communication Foundation (WCF). Çalışan hizmetleri [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uyumluluk modu katılmak tam olarak [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulama kanal ve yapabilirsiniz kullanımı [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dosya/URL yetkilendirmesi, oturum durumu gibi özellikleri ve <xref:System.Web.HttpContext> sınıfı. <xref:System.Web.HttpContext> Sınıfı, tanımlama bilgileri, oturumlar ve diğer erişmesine olanak tanır [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] özellikleri. Bu mod HTTP aktarımını bağlamaları kullanın ve hizmet IIS'de barındırılması gerekir gerektirir.  
  
 Bu örnekte, istemci bir konsol uygulaması (bir yürütülebilir dosya) ve Internet Information Services (IIS) barındırılan hizmetindeki.  
  
> [!NOTE]
>  Kurulum yordam ve yapılandırma yönergeleri Bu örneği için bu konunun sonunda yer alır.  
  
> [!NOTE]
>  Bu örnek gerektiren bir [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] çalıştırmak için uygulama havuzu. Yeni bir uygulama havuzu oluşturmak için veya varsayılan uygulama havuzunu değiştirmek için aşağıdaki adımları izleyin.  
>   
>  1.  Açık **Denetim Masası**.  Açık **Yönetimsel Araçlar** altında uygulaması **sistem ve güvenlik** başlığı. Açık **Internet Information Services (IIS) Yöneticisi** uygulaması.  
> 2.  Treeview içinde genişletin **bağlantıları** bölmesi. Seçin **uygulama havuzları** düğümü.  
> 3.  Varsayılan uygulama havuzunu kullanmak üzere ayarlamak için [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (hangi uyumsuzluk sorunlara neden olan sitelerle), sağ **DefaultAppPool** liste öğesi ve seçin **temel ayarlar...** . Ayarlama **.Net Framework sürüm** aşağı açılır **.Net Framework v4.0.30128** (veya üstü).  
> 4.  Kullanan yeni bir uygulama havuzu oluşturmak için [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (diğer uygulamalar için uyumluluğu korumak için), sağ **uygulama havuzları** düğümü ve select **uygulama havuzu Ekle...** . Yeni uygulama havuzu adını ve ayarlayın **.Net Framework sürüm** aşağı açılır **.Net Framework v4.0.30128** (veya üstü). Kurulumu çalıştıran altındaki adımları sonra sağ **ServiceModelSamples** seçin ve uygulama **yönetmek uygulama**, **Gelişmiş ayarlar...** . Ayarlama **uygulama havuzu** yeni bir uygulama havuzu için.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebHost\ASPNetCompatibility`  
  
 Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md), hesap makinesi hizmetinin uygular. `ICalculator` Sözleşme olarak değiştirildi `ICalculatorSession` çalışan bir sonuç tutarken gerçekleştirilecek işlem kümesi izin vermek sözleşme.  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculatorSession  
{  
    [OperationContract]  
    void Clear();  
    [OperationContract]  
    void AddTo(double n);  
    [OperationContract]  
    void SubtractFrom(double n);  
    [OperationContract]  
    void MultiplyBy(double n);  
    [OperationContract]  
    void DivideBy(double n);  
    [OperationContract]  
    double Result();  
}  
```  
  
 Hizmet durumu, bir hesaplama gerçekleştirmek için birden çok hizmet işlemleri adlı gibi her bir istemci için özelliğini kullanarak korur. İstemcisi, çağırarak geçerli sonucu alabilir `Result` ve çağırarak sıfır sonucu temizleyebilirsiniz `Clear`.  
  
 Hizmet kullandığı [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] her istemci oturumu için sonucunu depolamak için oturumu. Bu hizmet için birden fazla çağrı boyunca her istemci için çalışan sonuç korumak hizmet sağlar.  
  
> [!NOTE]
>  [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] oturum durumu ve WCF oturumları çok farklı noktalardır.  Bkz: [oturum](../../../../docs/framework/wcf/samples/session.md) WCF oturumları hakkındaki ayrıntılar için.  
  
 Hizmet intimate bir bağımlılığı olduğundan [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] oturum durumu ve gerektirir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] düzgün çalışması için uyumluluk modunda. Bu gereksinimleri uygulayarak bildirimli olarak ifade edilir `AspNetCompatibilityRequirements` özniteliği.  
  
```  
[AspNetCompatibilityRequirements(RequirementsMode =  
                       AspNetCompatibilityRequirementsMode.Required)]  
public class CalculatorService : ICalculatorSession  
{  
    double Result  
    {  // store result in AspNet Session  
       get {  
          if (HttpContext.Current.Session["Result"] != null)  
             return (double)HttpContext.Current.Session["Result"];  
          return 0.0D;  
       }  
       set  
       {  
          HttpContext.Current.Session["Result"] = value;  
       }  
    }  
    public void Clear()  
    {  
        Result = 0.0D;  
    }  
    public void AddTo(double n)  
    {  
        Result += n;  
    }  
    public void SubtractFrom(double n)  
    {  
        Result -= n;  
    }  
    public void MultiplyBy(double n)  
    {  
        Result *= n;  
    }  
    public void DivideBy(double n)  
    {  
        Result /= n;  
    }  
    public double Result()  
    {  
        return Result;  
    }  
}  
```  
  
 Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir. İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.  
  
```  
0, + 100, - 50, * 17.65, / 2 = 441.25  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirilen mutlaka [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Çözüm oluşturulduktan sonra ServiceModelSamples uygulamada ayarlamak için Setup.bat çalıştırmak [!INCLUDE[iisver](../../../../includes/iisver-md.md)]. ServiceModelSamples dizin şimdi olarak görünmesi gereken bir [!INCLUDE[iisver](../../../../includes/iisver-md.md)] uygulama.  
  
4.  Tek veya çapraz bilgisayar yapılandırmasında örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [AppFabric barındırma ve kalıcılığı örnekleri](http://go.microsoft.com/fwlink/?LinkId=193961)

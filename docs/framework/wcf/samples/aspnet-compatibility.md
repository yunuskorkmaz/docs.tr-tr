---
title: ASP.NET Uyumluluğu
ms.date: 03/30/2017
ms.assetid: c8b51f1e-c096-4c42-ad99-0519887bbbc5
ms.openlocfilehash: eeb09914fc90848c987127c789379549917063f6
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43800186"
---
# <a name="aspnet-compatibility"></a>ASP.NET Uyumluluğu
Bu örnek, ASP.NET uyumluluk modunun Windows Communication Foundation (WCF) etkinleştirme gösterir. ASP.NET özellikleri gibi dosya/URL yetkilendirme, oturum durumu ASP.NET modu tam ASP.NET uygulama ardışık düzeninizde katılır ve yapabilirsiniz uyumluluğu çalışan hizmetleri kullanımını ve <xref:System.Web.HttpContext> sınıfı. <xref:System.Web.HttpContext> Sınıfı tanımlama bilgileri, oturumları ve diğer ASP.NET özellikleri erişim sağlar. Bu mod, HTTP aktarımı bağlamaları kullanın ve hizmeti IIS'de barındırılan gerekir gerektirir.  
  
 Bu örnekte, istemci bir konsol uygulaması (bir yürütülebilir dosya) ve hizmet Internet Information Services (IIS) içinde barındırılır.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergeleri Bu konunun sonunda yer alır.  
  
Bu örnek gerektiren bir [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] çalıştırmak için uygulama havuzu. Yeni bir uygulama havuzu oluşturmak veya varsayılan uygulama havuzunu değiştirmek için şu adımları izleyin.  

1.  Açık **Denetim Masası**.  Açık **Yönetimsel Araçlar** uygulaması altında **sistem ve güvenlik** başlığı. Açık **Internet Information Services (IIS) Yöneticisi'ni** uygulaması.  

2.  Ağaç görünümünde genişletin **bağlantıları** bölmesi. Seçin **uygulama havuzları** düğümü.  

3.  Varsayılan uygulama havuzunu kullanmak için ayarlanacak [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (hangi uyumsuzluk sorunlara neden var olan siteler ile), sağ **DefaultAppPool** seçin ve liste öğesi **temel ayarları...** . Ayarlama **.Net Framework sürümü** aşağı açılır **.Net Framework v4.0.30128** (veya üzeri).  

4.  Kullanan yeni bir uygulama havuzu oluşturmak için [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (diğer uygulamalar için uyumluluğu korumak için), sağ **uygulama havuzları** düğümünü seçip alt **uygulama havuzu Ekle...** . Yeni uygulama havuzu ad verin ve ayarlayın **.Net Framework sürümü** aşağı açılır **.Net Framework v4.0.30128** (veya üzeri). Aşağıdaki adımlar Kurulumu çalıştırmayı sonra sağ **ServiceModelSamples** seçin ve uygulama **uygulamasını Yönet**, **Gelişmiş ayarlar...** . Ayarlama **uygulama havuzu** yeni uygulama havuzu için.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebHost\ASPNetCompatibility`  
  
 Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md), hesaplayıcı hizmet uygular. `ICalculator` Sözleşme olarak değiştirilmiş `ICalculatorSession` çalışan bir sonuç tutarken gerçekleştirilecek işlemleri bir dizi izin vermek sözleşme.  
  
```csharp  
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
  
 Hizmet durumu, bir hesaplama gerçekleştirmek için birden çok hizmet işlemleri adlandırılır gibi her istemci için özellik kullanarak korur. İstemci, çağırarak geçerli sonucu alabilirsiniz `Result` ve sonucu çağırarak sıfıra temizleyebilirsiniz `Clear`.  
  
 Hizmet, her bir istemci oturumu için sonucunu depolamak için ASP.NET oturum kullanır. Bu, birden çok hizmete çağrı arasında her istemci için çalışan sonucu korumak bir hizmet sağlar.  
  
> [!NOTE]
> ASP.NET oturum durumu ve WCF oturumları çok farklı noktalardır. Bkz: [oturumu](../../../../docs/framework/wcf/samples/session.md) WCF oturumları hakkında ayrıntılı bilgi için.
  
 Hizmet, ASP.NET oturum durumu tutun bir bağımlılığı ve düzgün çalışması için ASP.NET uyumluluk modunun gerektirir. Bu gereksinimleri uygulayarak bildirimli olarak ifade edilir `AspNetCompatibilityRequirements` özniteliği.  
  
```csharp  
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
  
 Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir. İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.  
  
```console
0, + 100, - 50, * 17.65, / 2 = 441.25  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Gerçekleştirilen mutlaka [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Çözüm oluşturulduktan sonra ServiceModelSamples uygulamada ayarlamak için Setup.bat çalıştırma [!INCLUDE[iisver](../../../../includes/iisver-md.md)]. ServiceModelSamples dizin artık olarak görünmesi gereken bir [!INCLUDE[iisver](../../../../includes/iisver-md.md)] uygulama.  
  
4.  Tek veya çoklu bilgisayar yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [AppFabric barındırma ve Kalıcılık örnekleri](https://go.microsoft.com/fwlink/?LinkId=193961)

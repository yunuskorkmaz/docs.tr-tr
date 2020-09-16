---
title: ASP.NET Uyumluluğu
ms.date: 03/30/2017
ms.assetid: c8b51f1e-c096-4c42-ad99-0519887bbbc5
ms.openlocfilehash: b1d1a72b9ac3041a1547ac42a33eb7d3e1f87a63
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90553217"
---
# <a name="aspnet-compatibility"></a>ASP.NET Uyumluluğu

Bu örnek, Windows Communication Foundation (WCF) ' de ASP.NET uyumluluk modunun nasıl etkinleştirileceğini gösterir. ASP.NET uyumluluk modunda çalışan hizmetler, ASP.NET uygulama ardışık düzenine tam olarak katılır ve dosya/URL yetkilendirmesi, oturum durumu ve sınıf gibi ASP.NET özelliklerden yararlanalabilirler <xref:System.Web.HttpContext> . <xref:System.Web.HttpContext>Sınıfı, tanımlama bilgilerine, oturumlara ve diğer ASP.NET özelliklerine erişim sağlar. Bu mod, bağlamaların HTTP aktarımını kullanmasını gerektirir ve hizmetin kendisi IIS 'de barındırılmalıdır.

Bu örnekte, istemci bir konsol uygulaması (yürütülebilir) ve hizmet Internet Information Services (IIS) içinde barındırılır.

> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.

Bu örnek, çalıştırmak için bir .NET Framework 4 uygulama havuzu gerektirir. Yeni bir uygulama havuzu oluşturmak veya varsayılan uygulama havuzunu değiştirmek için aşağıdaki adımları izleyin.

1. **Denetim Masası 'nı**açın.  **Sistem ve güvenlik** başlığı altında **Yönetimsel Araçlar** uygulamasını açın. **Internet Information Services (IIS) Yöneticisi** uygulamasını açın.

2. **Bağlantılar** bölmesinde TreeView ' ı genişletin. **Uygulama havuzları** düğümünü seçin.

3. Varsayılan uygulama havuzunu .NET Framework 4 ' ü kullanacak şekilde ayarlamak için (mevcut sitelerde uyumsuzluk sorunlarına neden olabilir), **DefaultAppPool** liste öğesine sağ tıklayın ve **temel ayarlar...** seçeneğini belirleyin. **.NET Framework sürüm** çekmeyi, **.NET Framework v 4.0.30128** (veya üzeri) olarak ayarlayın.

4. .NET Framework 4 kullanan yeni bir uygulama havuzu oluşturmak için (diğer uygulamaların uyumluluğunu korumak için), **uygulama havuzları** düğümüne sağ tıklayın ve **Uygulama Havuzu Ekle...** seçeneğini belirleyin. Yeni uygulama havuzunu adlandırın ve **.NET Framework sürüm** çekmeyi **.NET Framework v 4.0.30128** (veya üzeri) olarak ayarlayın. Aşağıdaki kurulum adımlarını çalıştırdıktan sonra, **servicemodelsamples** uygulamasına sağ tıklayın ve **Uygulamayı Yönet**, **Gelişmiş ayarlar..**. seçeneğini belirleyin. **Uygulama havuzunu** yeni uygulama havuzuna ayarlayın.

> [!IMPORTANT]
> Örnekler bilgisayarınızda zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebHost\ASPNetCompatibility`

Bu örnek, bir Hesaplayıcı hizmeti uygulayan [kullanmaya](getting-started-sample.md)Başlarken ' i temel alır. `ICalculator`Sözleşme, `ICalculatorSession` çalışan bir sonuç tutarken bir dizi işlemin gerçekleştirilmesine izin veren sözleşme olarak değiştirilmiştir.

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

Bu hizmet, bir hesaplama gerçekleştirmek için birden çok hizmet işlemi çağrılıp her bir istemci için özelliği kullanarak durumu korur. İstemci çağırarak geçerli sonucu alabilir `Result` ve çağırarak sıfıra sıfır sonucunu temizleyebilir `Clear` .

Hizmet, her istemci oturumu için sonucu depolamak üzere ASP.NET oturumunu kullanır. Bu, hizmetin, her istemci için çalışan sonucu hizmete birden çok çağrıda korumasına olanak tanır.

> [!NOTE]
> ASP.NET oturum durumu ve WCF oturumları çok farklı şeylere sahiptir. WCF oturumları hakkında ayrıntılar için bkz. [oturum](session.md) .

Hizmetin ASP.NET oturum durumu üzerinde bir intimate bağımlılığı vardır ve ASP.NET uyumluluk modunun düzgün şekilde çalışmasını gerektirir. Bu gereksinimler özniteliği uygulanarak bildirimli olarak ifade edilir `AspNetCompatibilityRequirements` .

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

Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir. İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.

```console
0, + 100, - 50, * 17.65, / 2 = 441.25
Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için

1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.

2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.

3. Çözüm oluşturulduktan sonra, ServiceModelSamples uygulamasını IIS 7,0 ' de ayarlamak için Setup.bat çalıştırın. ServiceModelSamples dizini artık bir IIS 7,0 uygulaması olarak görünmelidir.

4. Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [AppFabric barındırma ve kalıcılık örnekleri](/previous-versions/appfabric/ff383418(v=azure.10))

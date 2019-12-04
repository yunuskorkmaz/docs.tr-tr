---
title: ASP.NET Uyumluluğu
ms.date: 03/30/2017
ms.assetid: c8b51f1e-c096-4c42-ad99-0519887bbbc5
ms.openlocfilehash: 0938075464a0f2739bdb2a9d8ed1f16f61edff2b
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716167"
---
# <a name="aspnet-compatibility"></a>ASP.NET Uyumluluğu

Bu örnek, Windows Communication Foundation (WCF) ' de ASP.NET uyumluluk modunun nasıl etkinleştirileceğini gösterir. ASP.NET uyumluluk modunda çalışan hizmetler, ASP.NET uygulama ardışık düzenine tam olarak katılır ve dosya/URL yetkilendirmesi, oturum durumu ve <xref:System.Web.HttpContext> sınıfı gibi ASP.NET özelliklerden yararlanalabilirler. <xref:System.Web.HttpContext> sınıfı, tanımlama bilgilerine, oturumlara ve diğer ASP.NET özelliklerine erişim sağlar. Bu mod, bağlamaların HTTP aktarımını kullanmasını gerektirir ve hizmetin kendisi IIS 'de barındırılmalıdır.

Bu örnekte, istemci bir konsol uygulaması (yürütülebilir) ve hizmet Internet Information Services (IIS) içinde barındırılır.

> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.

Bu örnek, çalıştırmak için bir .NET Framework 4 uygulama havuzu gerektirir. Yeni bir uygulama havuzu oluşturmak veya varsayılan uygulama havuzunu değiştirmek için aşağıdaki adımları izleyin.

1. **Denetim Masası 'nı**açın.  **Sistem ve güvenlik** başlığı altında **Yönetimsel Araçlar** uygulamasını açın. **Internet Information Services (IIS) Yöneticisi** uygulamasını açın.

2. **Bağlantılar** bölmesinde TreeView ' ı genişletin. **Uygulama havuzları** düğümünü seçin.

3. Varsayılan uygulama havuzunu .NET Framework 4 ' ü kullanacak şekilde ayarlamak için (mevcut sitelerde uyumsuzluk sorunlarına neden olabilir), **DefaultAppPool** liste öğesine sağ tıklayın ve **temel ayarlar...** seçeneğini belirleyin. **.NET Framework sürüm** çekmeyi, **.NET Framework v 4.0.30128** (veya üzeri) olarak ayarlayın.

4. .NET Framework 4 kullanan yeni bir uygulama havuzu oluşturmak için (diğer uygulamaların uyumluluğunu korumak için), **uygulama havuzları** düğümüne sağ tıklayın ve **Uygulama Havuzu Ekle...** seçeneğini belirleyin. Yeni uygulama havuzunu adlandırın ve **.NET Framework sürüm** çekmeyi **.NET Framework v 4.0.30128** (veya üzeri) olarak ayarlayın. Aşağıdaki kurulum adımlarını çalıştırdıktan sonra, **servicemodelsamples** uygulamasına sağ tıklayın ve **Uygulamayı Yönet**, **Gelişmiş ayarlar..** . seçeneğini belirleyin. **Uygulama havuzunu** yeni uygulama havuzuna ayarlayın.

> [!IMPORTANT]
> Örnekler bilgisayarınızda zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebHost\ASPNetCompatibility`

Bu örnek, bir Hesaplayıcı hizmeti uygulayan [kullanmaya](../../../../docs/framework/wcf/samples/getting-started-sample.md)Başlarken ' i temel alır. `ICalculator` sözleşmesi, çalışan bir sonuç tutarken bir dizi işlemin gerçekleştirilmesine izin veren `ICalculatorSession` sözleşmesi olarak değiştirilmiştir.

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

Bu hizmet, bir hesaplama gerçekleştirmek için birden çok hizmet işlemi çağrılıp her bir istemci için özelliği kullanarak durumu korur. İstemci, `Result` çağırarak geçerli sonucu alabilir ve `Clear`çağırarak sonucu sıfıra temizleyebilir.

Hizmet, her istemci oturumu için sonucu depolamak üzere ASP.NET oturumunu kullanır. Bu, hizmetin, her istemci için çalışan sonucu hizmete birden çok çağrıda korumasına olanak tanır.

> [!NOTE]
> ASP.NET oturum durumu ve WCF oturumları çok farklı şeylere sahiptir. WCF oturumları hakkında ayrıntılar için bkz. [oturum](../../../../docs/framework/wcf/samples/session.md) .

Hizmetin ASP.NET oturum durumu üzerinde bir intimate bağımlılığı vardır ve ASP.NET uyumluluk modunun düzgün şekilde çalışmasını gerektirir. Bu gereksinimler `AspNetCompatibilityRequirements` özniteliği uygulanarak bildirimli olarak ifade edilir.

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

1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.

2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.

3. Çözüm derlendikten sonra, ServiceModelSamples uygulamasını IIS 7,0 ' de ayarlamak için Setup. bat dosyasını çalıştırın. ServiceModelSamples dizini artık bir IIS 7,0 uygulaması olarak görünmelidir.

4. Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [AppFabric barındırma ve kalıcılık örnekleri](https://go.microsoft.com/fwlink/?LinkId=193961)

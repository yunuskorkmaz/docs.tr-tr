---
title: Sorun giderme Get ile Windows Communication Foundation Eğitmenleri
ms.date: 01/25/2019
ms.assetid: 69a21511-0871-4c41-9a53-93110e84d7fd
ms.openlocfilehash: 8089e0fee262d07be591069982b1aacfbeae2521
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791475"
---
# <a name="troubleshoot-the-get-started-with-windows-communication-foundation-tutorials"></a>Sorun giderme Get ile Windows Communication Foundation Eğitmenleri

Bu makalede, en yaygın sorunlar ve hatalar adımları izlediğinizde yüz için çözümler sağlar. [Öğreticisi: Windows Communication Foundation uygulamalarla çalışmaya başlama](getting-started-tutorial.md). 
  
## <a name="common-problems"></a>Yaygın sorunlar

**Proje dosyaları my sabit sürücüde bulamıyorum.**

 Visual Studio proje dosyalarında kaydeder *C:\Users\\&lt;kullanıcı adı&gt;\source\repos*.  

**Bulamıyorum *App.config* tarafından oluşturulan dosya *Svcutil.exe*.**

 Visual Studio'da **varolan öğeyi Ekle** penceresi varsayılan olarak yalnızca şu uzantılara sahip dosyaları görüntüler: 
- *.cs* 
- *.resx* 
- *.Settings*
- *.xsd* 
- *.wsdl*

Tüm dosya türlerini görüntülemek için seçin **tüm dosyalar (\*.\*)**  sağ alt köşesindeki açılır listesinde **varolan öğeyi Ekle** penceresi.  
  
## <a name="common-errors"></a>Sık karşılaşılan hatalar

### <a name="compile-the-service-application"></a>Hizmet uygulaması derleme 

**Hata BC30420 'GettingStartedHost.Module1' içinde 'Sub Main' bulunamadı.**

Visual Basic uygulama için yanlış giriş noktasıdır. Aşağıdaki değişikliği yapın:

   1. İçinde **Çözüm Gezgini** penceresinde **GettingStartedHost** klasöre tıklayın ve ardından **özellikleri** kısayol menüsünden.
    a. İçinde **GettingStartedHost** penceresinde için **Başlangıç nesnesi**seçin **Service.Program** (veya belirli uygulamanız için giriş noktası) listeden. 
    b. Ana menüden **dosya** > **Tümünü Kaydet**.

### <a name="run-the-service-application"></a>Hizmet uygulaması çalıştırma 

**HTTP URL kaydedemedi ' http:\// +: 8000/GettingStarted/CalculatorService '. İşleminiz, bu ad alanı için erişim hakları yok.** 

 Uygun erişim için yönetici ayrıcalıklarıyla Windows Communication Foundation (WCF) hizmetini barındıran işlemi başlatın:
- Visual Studio için: Visual Studio programda seçin **Başlat** menüsüne ve ardından **daha fazla** > **yönetici olarak çalıştır** kısayol menüsünden.
- Bir konsol penceresi için: Seçin **komut istemi** içinde **Başlat** menüsüne ve ardından **daha fazla** > **farklı çalıştır yönetici** kısayolu menüsü.
- Windows Gezgini için: Yürütülebilir dosyayı seçin ve ardından **yönetici olarak çalıştır** kısayol menüsünden.

### <a name="compile-the-client-application"></a>İstemci uygulaması derleme

**'CalculatorClient' için bir tanım içermiyor '\<yöntem adı >' ve hiçbir uzantı metodu '\<yöntem adı >' kabul eden bir ilk bağımsız değişken türü 'CalculatorClient' bulunamadı (bir using eksik yönergesi veya bir bütünleştirilmiş kod Başvurusu?)**  

WITH mark yöntemleri `ServiceOperationAttribute` özniteliği genel kullanıma sunulur. Atlarsanız `ServiceOperationAttribute` bir yöntemde özniteliğinden `ICalculator` arabirimi, derleme sırasında bu hata iletisini alırsınız.  

**'CalculatorClient' bulunamadı tür veya ad alanı adı (bir using eksik yönergeniz veya derleme başvurunuz?)**

 Eklemezseniz bu hata iletisini *generatedProxy.cs* (veya *generatedProxy.vb*) dosyası ile oluşturulmuş istemci projenize *Svcutil.exe* aracı .  

### <a name="run-the-client-application"></a>İstemci uygulamasını çalıştırın

**İşlenmeyen özel durum: System.ServiceModel.EndpointNotFoundException: Bağlanılamadı ' http:\//localhost:8000/GettingStarted/CalculatorService '. 10061 TCP hata kodu: Hedef makine etkin olarak reddettiğinden hiçbir bağlantı kurulamadı.**

İstemci uygulama hizmeti başlatmadan çalıştırırsanız, bu hata oluşur. İlk olarak hizmeti başlatmak için ana bilgisayar uygulaması çalıştırın ve ardından istemci uygulamasını çalıştırın.

### <a name="use-the-svcutilexe-tool"></a>Svcutil.exe aracını kullanma
   
**'Svcutil' iç ya da dış komut, çalıştırılabilir program veya toplu iş dosyası tanınmıyor.**

 *Svcutil.exe* sistem yolunda olmalıdır. Visual Studio Komut İstemi'ni kullanmak için en kolay çözümdür bakın. Gelen **Başlat** menüsünde **Visual Studio \<sürüm >** dizin ve select **VS için geliştirici komut istemi \<sürüm >**. Bu komut istemi, Visual Studio'nun bir parçası olarak gönderildiğini tüm araçları için doğru konuma sistem yolunu ayarlar.  
  
### <a name="run-the-service-and-client-applications"></a>Hizmet ve istemci uygulamaları çalıştırın

**System.ServiceModel.Security.SecurityNegotiationException: SOAP güvenlik anlaşması ' http:\//localhost:8000/GettingStarted/CalculatorService ' hedefi için ' http:\//localhost:8000/GettingStarted/CalculatorService ' başarısız oldu**  

Ağ bağlantısı yok etki alanına katılmış bir bilgisayarda bu hata oluşur. Bilgisayarınız ağa bağlanmak veya güvenlik için hem hizmet hem de istemci kapatın. 

Güvenliğin devre dışı bırakmak için:

- Bir hizmeti oluşturan kodu değiştirin `WSHttpBinding` aşağıdaki kod ile:  
  
    ```csharp
    // Step 3: Add a service endpoint.
    selfhost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(SecurityMode.None), "CalculatorService");  
    ```

- Yapılandırma dosyasında istemci güncelleştirme  **\<Güvenlik >** öğesi altında  **\<bağlama >** öğesi aşağıdaki gibi:  
  
    ```xml
    <binding name="WSHttpBinding_ICalculator" security mode="None" />
    ```  

## <a name="see-also"></a>Ayrıca bkz.  
 [WCF uygulamaları ile çalışmaya başlama](getting-started-tutorial.md)  
 [WCF sorun giderme hızlı başlangıç](wcf-troubleshooting-quickstart.md)  
 [Kurulum sorunlarını giderme](troubleshooting-setup-issues.md)

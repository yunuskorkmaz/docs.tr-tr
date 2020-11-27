---
title: Windows Communication Foundation öğreticileri ile çalışmaya başlama hakkında sorun giderme
ms.date: 01/25/2019
ms.assetid: 69a21511-0871-4c41-9a53-93110e84d7fd
ms.openlocfilehash: 4d471372419996c5bc490c2d0fdd83927428a41e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96281345"
---
# <a name="troubleshoot-the-get-started-with-windows-communication-foundation-tutorials"></a>Windows Communication Foundation öğreticileri ile çalışmaya başlama hakkında sorun giderme

Bu makalede, öğreticideki adımları uyguladığınızda kullanabileceğiniz en yaygın sorunlara ve hatalara yönelik çözümler sunulmaktadır [: Windows Communication Foundation uygulamalarını kullanmaya başlama](getting-started-tutorial.md).
  
## <a name="common-problems"></a>Sık karşılaşılan sorunlar

**Sabit sürücimde proje dosyalarını bulamıyorum.**

 Visual Studio, proje dosyalarını *C:\Users \\ &lt; Kullanıcı adı &gt; \source\repos* konumuna kaydeder.  

***Svcutil.exe* tarafından oluşturulan *App.config* dosyayı bulamıyorum.**

 Visual Studio 'da, **Varolan öğe Ekle** penceresi yalnızca aşağıdaki uzantılara sahip dosyaları varsayılan olarak görüntüler:

- *.cs*
- *.resx*
- *. ayarlar*
- *. xsd*
- *. wsdl*

Tüm dosya türlerini göstermek için, **Varolan öğe Ekle** penceresinin sağ alt köşesindeki aşağı açılan listeden **tüm dosyalar ( \* . \* )** öğesini seçin.  
  
## <a name="common-errors"></a>Sık karşılaşılan hatalar

### <a name="compile-the-service-application"></a>Hizmet uygulamasını derle

**' GettingStartedHost. Module1 ' içinde hata BC30420 ' Sub Main ' bulunamadı.**

Visual Basic uygulaması için giriş noktası yanlış. Aşağıdaki değişikliği yapın:

   1. **Çözüm Gezgini** penceresinde **GettingStartedHost** klasörünü seçin ve sonra kısayol menüsünden **Özellikler** ' i seçin.
    a. **GettingStartedHost** penceresinde, **Başlangıç nesnesi** için, listeden **Service. program** (veya belirli bir uygulama için giriş noktası) seçin.
    b. Ana menüden **Dosya**  >  **Tümünü Kaydet**' i seçin.

### <a name="run-the-service-application"></a>Hizmet uygulamasını çalıştırma

**HTTP, ' http: \/ /+: 8000/GettingStarted/Hesaplatorservice ' URL 'sini kaydedemedi. İşleminizin bu ad alanına erişim hakları yok.**

 Uygun erişim için, yönetici ayrıcalıklarıyla Windows Communication Foundation (WCF) hizmetini barındıran işlemi başlatın:

- Visual Studio için: **Başlat** menüsünde Visual Studio **programını seçin ve** ardından  >  kısayol menüsünde **yönetici olarak çalıştır** ' ı seçin.
- Konsol penceresi için: **Başlat** menüsünde **komut istemi** ' ni seçin ve ardından kısayol menüsünde yönetici olarak **daha fazla**  >  **Çalıştır** ' ı seçin.
- Windows Gezgini için: yürütülebilir dosyayı seçin ve ardından kısayol menüsünde **yönetici olarak çalıştır** ' ı seçin.

### <a name="compile-the-client-application"></a>İstemci uygulamasını derle

**' Hesaplatorclient ', ' ' için bir tanım içermiyor \<method name> ve ' \<method name> Hesaplatorclient ' türünde bir ilk bağımsız değişken kabul eden hiçbir ' ' genişletme yöntemi bulunamadı (bir using yönergeniz veya derleme başvurunuz eksik olabilir mi?)**  

Yalnızca özniteliği ile işaretlediğiniz Yöntemler `ServiceOperationAttribute` publicolarak sunulur. `ServiceOperationAttribute`Arabirimindeki bir yöntemden özniteliği atlarsanız `ICalculator` , derleme sırasında bu hata iletisini alırsınız.  

**' Hesaplatorclient ' tür veya ad alanı adı bulunamadı (bir using yönergeniz veya derleme başvurunuz mu eksik?)**

 Bu hatayı, *Svcutil.exe* aracı ile oluşturduğunuz zaman istemci Projenize *GeneratedProxy.cs* (veya *generatedProxy. vb*) dosyasını eklememeniz durumunda alırsınız.  

### <a name="run-the-client-application"></a>İstemci uygulamasını çalıştırma

**İşlenmeyen özel durum: System. ServiceModel. EndpointNotFoundException: ' http: \/ /localhost: 8000/GettingStarted/Hesaplatorservice ' ile bağlantı kurulamadı. TCP hata kodu 10061: hedef makine etkin bir şekilde reddettiğinden bağlantı kurulamadı.**

Bu hata, istemci uygulamasını önce hizmeti başlatmadan çalıştırırsanız oluşur. İlk olarak, hizmeti başlatmak için konak uygulamayı çalıştırın ve ardından istemci uygulamasını çalıştırın.

### <a name="use-the-svcutilexe-tool"></a>Svcutil.exe aracını kullanma

**' Svcutil ' bir iç veya dış komut, çalıştırılabilir program veya toplu iş dosyası olarak tanınmıyor.**

 *Svcutil.exe* sistem yolunda olmalıdır. En kolay çözüm, Visual Studio komut istemi ' ni kullanmaktır. **Başlat** menüsünde **Visual Studio \<version>** dizinini seçin ve ardından **\<version> vs için geliştirici komut istemi** seçin. Bu komut istemi, sistem yolunu, Visual Studio 'nun bir parçası olarak gönderilen tüm araçların doğru konumlarına ayarlar.  
  
### <a name="run-the-service-and-client-applications"></a>Hizmeti ve istemci uygulamalarını çalıştırma

**System. ServiceModel. Security. SecurityNegotiationException: "http: \/ /localhost: 8000/GettingStarted/Hesaplatorservice ' hedefi IÇIN SOAP güvenlik anlaşması ' http: \/ /localhost: 8000/GettingStarted/hesaplamaservice ' başarısız oldu**  

Bu hata, ağ bağlantısı olmayan, etki alanına katılmış bir bilgisayarda oluşur. Bilgisayarınızı ağa bağlayın veya hem hizmet hem de istemci için güvenliği devre dışı bırakın.

Güvenliği devre dışı bırakmak için:

- Hizmeti için, öğesini oluşturan kodu `WSHttpBinding` aşağıdaki kodla değiştirin:  
  
    ```csharp
    // Step 3: Add a service endpoint.
    selfhost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(SecurityMode.None), "CalculatorService");  
    ```

- İstemci için yapılandırma dosyasında öğesi **\<security>** altındaki öğesini **\<binding>** aşağıdaki gibi güncelleştirin:  
  
    ```xml
    <binding name="WSHttpBinding_ICalculator">
      <security mode="None" />
    </binding
    ```  

## <a name="see-also"></a>Ayrıca bkz.  

 [WCF uygulamalarını kullanmaya başlama](getting-started-tutorial.md)  
 [WCF sorun giderme hızlı başlangıç](wcf-troubleshooting-quickstart.md)  
 [Kurulum sorunlarını giderme](troubleshooting-setup-issues.md)

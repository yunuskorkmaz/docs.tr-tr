---
title: Windows Communication Foundation öğreticileri ile başlayın sorun giderme
ms.date: 01/25/2019
ms.assetid: 69a21511-0871-4c41-9a53-93110e84d7fd
ms.openlocfilehash: 92e986370fe1b6e067d9f8aebc73179c1ac6a20f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183086"
---
# <a name="troubleshoot-the-get-started-with-windows-communication-foundation-tutorials"></a>Windows Communication Foundation öğreticileri ile başlayın sorun giderme

Bu makalede, Öğretici'deki adımları izlediğinizde karşılaşabileceğiniz en yaygın sorunlar ve hatalar için çözümler [sunar: Windows Communication Foundation uygulamalarıyla başlayın.](getting-started-tutorial.md)
  
## <a name="common-problems"></a>Sık karşılaşılan sorunlar

**Sabit diskimdeki proje dosyalarını bulamıyorum.**

 Visual Studio proje dosyalarını *\\&lt;C:\Users&gt;kullanıcı adı \source\repos'ta*kaydeder.  

***Ben Svcutil.exe*tarafından oluşturulan *App.config* dosyası bulamıyorum.**

 Visual Studio'da, **Varolan Öğe Ekle** penceresinde yalnızca varsayılan olarak aşağıdaki uzantılara sahip dosyalar görüntülenir:

- *Cs*
- *.resx*
- *.ayarlar*
- *Xsd*
- *.wsdl*

Tüm dosya türlerini görüntülemek için, **Varolan Öğe Ekle** penceresinin sağ alt köşesindeki açılır listede **Tüm Dosyalar (\*.\*)** öğesini seçin.  
  
## <a name="common-errors"></a>Sık karşılaşılan hatalar

### <a name="compile-the-service-application"></a>Servis uygulamasını derleme

**Hata BC30420 'Alt Main' 'GettingStartedHost.Module1' bulunamadı.**

Giriş noktası Visual Basic uygulaması için yanlıştır. Aşağıdaki değişikliği yapın:

   1. Solution **Explorer** penceresinde, **GettingStartedHost** klasörünü seçin ve ardından kısayol menüsünden **Özellikler'i** seçin.
    a. Başlangıç **nesnesi**için **GettingStartedHost** penceresinde, listeden **Service.Program'ı** (veya belirli uygulamanızın giriş noktasını) seçin.
    b. Ana menüden **Dosya** > **Yı Kaydet'i**seçin.

### <a name="run-the-service-application"></a>Hizmet uygulamasını çalıştırma

**HTTP URL'yi kaydedemedi 'http:\//+:8000/GettingStarted/CalculatorService'. İşleminizin bu ad alanına erişim hakları yok.**

 Doğru erişim için, Windows Communication Foundation (WCF) hizmetini barındıran işlemi yönetim ayrıcalıklarıyla başlatın:

- Visual Studio için: **Başlat** menüsünde Visual Studio programını seçin ve ardından kısayol menüsünden yönetici olarak **Daha Fazla** > **Çalıştır'ı** seçin.
- Konsol penceresi için: **Başlat** menüsünde **Komut İstemi'ni** seçin ve ardından kısayol menüsünden **Daha Fazla** > **Çalıştır yöneticisini** seçin.
- Windows Gezgini için: Yürütülebilir'i seçin ve ardından kısayol menüsünden **yönetici olarak çalıştır'ı** seçin.

### <a name="compile-the-client-application"></a>İstemci uygulamasını derleme

**'CalculatorClient', '\<yöntem adı>' için bir tanım\<içermiyor ve hiçbir uzantı yöntemi ' yöntem adı>' türünden ilk bağımsız değişkeni kabul edilebilir (bir kullanma yönergesi veya derleme başvurusu eksik mi?)**  

Yalnızca öznitelik ile `ServiceOperationAttribute` işaretlediğiniz bu yöntemler genel olarak açıklanır. Özniteliği arabirimdeki `ServiceOperationAttribute` bir yöntemden atlarsanız, derleme sırasında bu hata iletisini alırsınız. `ICalculator`  

**'CalculatorClient' türü veya ad alanı adı bulunamadı (bir yönergeyi veya derleme başvuruyu eksik mi?)**

 *Svcutil.exe* aracıyla oluşturduğunuzda istemci projenize *generatedProxy.cs* (veya *generatedProxy.vb)* dosyasını eklemezseniz bu hatayı alırsınız.  

### <a name="run-the-client-application"></a>İstemci uygulamasını çalıştırma

**İşlenmemiş Özel Durum: System.ServiceModel.EndpointNotFoundException: 'http:\//localhost:8000/GettingStarted/CalculatorService'e bağlanamadı. TCP hata kodu 10061: Hedef makine etkin olarak reddettiğinden bağlantı yapılamaz.**

Bu hata, istemci uygulamasını önce hizmeti başlatmadan çalıştırıyorsanız oluşur. Önce hizmeti başlatmak için ana bilgisayar uygulamasını çalıştırın ve ardından istemci uygulamasını çalıştırın.

### <a name="use-the-svcutilexe-tool"></a>Svcutil.exe aracını kullanın

**'Svcutil' dahili veya harici komut, çalışabilir program veya toplu dosya olarak tanınmaz.**

 *Svcutil.exe* sistem yolunda olmalı. En kolay çözüm Visual Studio komut istemini kullanmaktır. **Başlat** menüsünden Visual ** \<Studio sürüm>** dizinini seçin ve ardından VS ** \<sürümü için Geliştirici Komut Komut Ustem>'ı **seçin. Bu komut istemi Visual Studio'nun bir parçası olarak gönderilen tüm araçlar için doğru konumlara sistem yolunu ayarlar.  
  
### <a name="run-the-service-and-client-applications"></a>Hizmet ve istemci uygulamalarını çalıştırma

**System.ServiceModel.Security.SecurityNegotiationException: 'http: /localhost:8000/GettingStarted/CalculatorService'\/hedef için 'http:\//localhost:8000/GettingStarted/CalculatorService' ile SOAP güvenlik müzakeresi başarısız oldu**  

Bu hata, ağ bağlantısı olmayan etki alanı birleştirilmiş bir bilgisayarda oluşur. Bilgisayarınızı ağa bağlayın veya hem hizmet hem de istemci için güvenliği kapatın.

Güvenliği kapatmak için:

- Hizmet için, aşağıdaki kodu oluşturan `WSHttpBinding` kodu değiştirin:  
  
    ```csharp
    // Step 3: Add a service endpoint.
    selfhost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(SecurityMode.None), "CalculatorService");  
    ```

- İstemci için yapılandırma dosyasında, ** \<bağlama>** öğesi altındaki ** \<güvenlik>** öğesini aşağıdaki gibi güncelleştirin:  
  
    ```xml
    <binding name="WSHttpBinding_ICalculator" security mode="None" />
    ```  

## <a name="see-also"></a>Ayrıca bkz.  
 [WCF uygulamaları ile başlayın](getting-started-tutorial.md)  
 [WCF sorun giderme hızlı başlat](wcf-troubleshooting-quickstart.md)  
 [Sorun giderme kurulum sorunları](troubleshooting-setup-issues.md)

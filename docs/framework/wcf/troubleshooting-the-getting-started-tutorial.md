---
title: Başlarken Öğreticisi Sorun Giderme
ms.date: 03/30/2017
ms.assetid: 69a21511-0871-4c41-9a53-93110e84d7fd
ms.openlocfilehash: 43128743ba16aefc8669ace85070a16d80145a71
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43519427"
---
# <a name="troubleshooting-the-getting-started-tutorial"></a>Başlarken Öğreticisi Sorun Giderme
Bu konuda bunların nasıl çözüleceğine ile çalışmaya başlama Öğreticisi ile çalışırken en sık karşılaşılan sorunlar listelenmiştir.  
  
**Sabit Sürücümün proje dosyalarını bulmak oluşturamıyorum.**

 Visual Studio, proje dosyaları içinde c:\users kaydeder\\<user name>\Documents\\< Visual Studio sürümü\>\Projects.  
  
**Hizmet uygulaması çalıştırma denemesi: HTTP URL'si kaydedemedi `http://+:8000/ServiceModelSamples/Service/`.** 
 **İşleminizi bu ad alanı için erişim haklarına sahip değil.** 

 Bir WCF hizmetini barındıran işlemi yönetici ayrıcalıklarıyla çalıştırılmalıdır. Hizmet çalışıyorsa, gelen Visual Studio içinde Visual Studio'yu yönetici olarak çalıştırmanız gerekir. Bunu yapmak için **Başlat**, sağ **Visual Studio \< *sürüm* >**  seçip **yönetici olarak çalıştır**. Konsol penceresinde komut satırı isteminden hizmeti çalıştırıyorsanız, konsol penceresinde benzer şekilde bir yönetici olarak başlatmanız gerekir. Tıklayın **Başlat**, sağ **komut istemi** seçip **yönetici olarak çalıştır**.  
  
**Svcutil.exe aracını çalışılıyor: 'svcutil' iç ya da dış komut, çalıştırılabilir program ya da toplu iş dosyası tanınmıyor.**

 Svcutil.exe sistem yolunda olmalıdır. Kolay çözümü, komut istemini kullanmaktır. Tıklayın **Başlat**seçin **tüm programlar**, **Visual Studio \< *sürüm*>**,  **Visual Studio Araçları**, ve **Visual Studio için geliştirici komut istemi**. Bu komut istemi, Visual Studio'nun bir parçası olarak gönderildiğini tüm araçları için doğru konuma sistem yolunu ayarlar.  

**Svcutil.exe'yi oluşturulan App.config dosyasını bulmak yüklenemiyor.**

 **Varolan öğeyi Ekle** iletişim varsayılan olarak yalnızca şu uzantılara sahip dosyaları görüntüler: .cs, .resx, .settings, .xsd, .wsdl. Tüm dosya türlerini seçerek görmek istediğinizi belirtebilirsiniz **tüm dosyalar (\*.\*)**  alt sağ köşesinde aşağı açılan liste kutusunda **varolan öğeyi Ekle** iletişim kutusu.  


**İstemci uygulaması derleme: 'CalculatorClient' için bir tanım içermiyor '\<yöntem adı >' ve hiçbir genişletme yönteminin '\<yöntem adı >' 'CalculatorClient' türünde bir ilk bağımsız değişken kabul eden bulunamadı (olduğunuz eksik bir kullanma yönergeniz veya derleme başvurunuz?)**  

İle işaretlenmiş yöntemler `ServiceOperationAttribute` dışında tüm dünyada kullanıma sunulur. Kaçırdıysanız `ServiceOperationAttribute` metotlarından birini özniteliğinden `ICalculator` arabirimi, bu hata iletisini özniteliği eksik işlemi çağrıda bir istemci uygulaması derlerken alın.  

**İstemci uygulaması derleme: 'CalculatorClient' bulunamadı tür veya ad alanı adı (bir using eksik yönergeniz veya derleme başvurunuz?)**

 İstemci projenize Proxy.cs veya Proxy.vb dosya eklemezseniz bu hatayı alırsınız.  

**İstemcisi çalıştıran: işlenmeyen özel durum: System.ServiceModel.EndpointNotFoundException: bağlanamadı `http://localhost:8000/ServiceModelSamples/Service/CalculatorService`. TCP hata kodu 10061: hedef makine etkin olarak reddettiğinden hiçbir bağlantı kurulamadı.**

Hizmet çalıştırmadan istemci uygulaması, bu hata meydana gelir.  
  
**İşlenmeyen özel durum: System.ServiceModel.Security.SecurityNegotiationException: SOAP güvenlik anlaşması `http://localhost:8000/ServiceModelSamples/Service/CalculatorService` hedefi için `http://localhost:8000/ServiceModelSamples/Service/CalculatorService` başarısız oldu**  

Ağ bağlantısı yok. etki alanına katılmış bir bilgisayarda bu hata oluşur. Bilgisayarınız ağa bağlanmak veya hem istemci hem de hizmet için güvenliği devre dışı. Hizmet için şu WSHttpBinding oluşturan kodu değiştirin.  
  
```csharp
// Step 3 of the hosting procedure: Add a service endpoint  
selfhost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(SecurityMode.None), "CalculatorService");  
```

İstemci için değiştirme  **\<Güvenlik >** öğesi altında  **\<bağlama >** aşağıdaki öğe:  
  
```xml
<security mode="Node" />  
```  

## <a name="see-also"></a>Ayrıca Bkz.  
 [Başlangıç Öğreticisi](../../../docs/framework/wcf/getting-started-tutorial.md)  
 [WCF Sorun Giderme Hızlı Başlangıcı](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md)  
 [Kurulum Sorunlarını Giderme](../../../docs/framework/wcf/troubleshooting-setup-issues.md)

---
title: Federasyon Örneği
ms.date: 03/30/2017
ms.assetid: 7e9da0ca-e925-4644-aa96-8bfaf649d4bb
ms.openlocfilehash: 9ec462f88c0e3a039b7f288554be3e28f13ece08
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144675"
---
# <a name="federation-sample"></a>Federasyon Örneği
Bu örnek federe güvenliği gösteriyor.  
  
## <a name="sample-details"></a>Örnek Ayrıntılar  
 Windows Communication Foundation (WCF), federe güvenlik mimarilerinin dağıtılamı için destek `wsFederationHttpBinding`sağlar. İstek/yanıt iletişimi `wsFederationHttpBinding` için temel aktarım mekanizması olarak HTTP'nin kullanımını ve kodlama için tel biçimi olarak Metin/XML'i içeren güvenli, güvenilir ve birlikte çalışabilir bir bağlama sağlar. WCF'deki Federasyon hakkında daha fazla bilgi için [Federasyon'a](../../../../docs/framework/wcf/feature-details/federation.md)bakın.  
  
 Senaryo 4 parçadan oluşur:  
  
- BookStore hizmeti  
  
- Kitapçı STS  
  
- HomeRealm STS  
  
- Kitabevi İstemcisi  
  
 BookStore hizmeti iki işlemi `BrowseBooks` `BuyBook`destekler ve . `BrowseBooks` Bu işlem için anonim erişim sağlar, ancak `BuyBooks` operasyona erişmek için kimlik doğrulaması erişim gerektirir. Kimlik doğrulaması BookStore STS tarafından verilen bir belirteç biçimindedir. BookStore Hizmeti için yapılandırma dosyası, istemcileri BookStore `wsFederationHttpBinding`STS'ye işaret eder.  
  
```xml  
<wsFederationHttpBinding>  
<!-- This is the Service binding for the BuyBooks endpoint. It redirects clients to the BookStore STS -->  
    <binding name='BuyBookBinding'>  
        <security mode="Message">  
            <message>  
                <issuerMetadata  
  address='http://localhost/FederationSample/BookStoreSTS/STS.svc/mex' >  
                    <identity>  
                        <dns value ='BookStoreSTS.com'/>  
                    </identity>  
                </issuerMetadata>  
            </message>  
        </security>  
    </binding>  
</wsFederationHttpBinding>  
```  
  
 BookStore STS daha sonra istemcilerin HomeRealm STS tarafından verilen bir belirteç kullanarak kimlik doğrulamasını gerektirir. Yine, BookStore STS için yapılandırma dosyası kullanarak HomeRealm STS istemcileri `wsFederationHttpBinding`puan.  
  
```xml  
<wsFederationHttpBinding>  
 <!-- This is the binding for the clients requesting tokens from this STS. It redirects clients to the HomeRealm STS -->  
    <binding name='BookStoreSTSBinding'>  
        <security mode='Message'>  
            <message>  
                <issuerMetadata  
 address='http://localhost/FederationSample/HomeRealmSTS/STS.svc/mex' >  
                    <identity>  
                        <dns value ='HomeRealmSTS.com' />  
                    </identity>  
                </issuerMetadata>  
            </message>  
        </security>  
    </binding>  
</wsFederationHttpBinding>  
```  
  
 `BuyBook` İşleme erişirken olayların sırası aşağıdaki gibidir:  
  
1. İstemci, Windows kimlik bilgilerini kullanarak HomeRealm STS'ye kimlik doğrulaması yaptı.  
  
2. HomeRealm STS, BookStore STS'ye kimlik doğrulamak için kullanılabilecek bir belirteç yayınlar.  
  
3. İstemci, HomeRealm STS tarafından verilen belirteci kullanarak BookStore STS'ye doğrulanır.  
  
4. BookStore STS, BookStore Hizmeti'nin kimliğini doğrulamak için kullanılabilecek bir belirteç verir.  
  
5. İstemci, BookStore STS tarafından verilen belirteci kullanarak BookStore hizmetine kimlik doğrular.  
  
6. İstemci işlem `BuyBook` erişimi.  
  
 Bu örneğin nasıl ayarlanıp çalıştırılabildiğini ilgili aşağıdaki yönergeleri izleyin.  
  
> [!NOTE]
> Bu örneği çalıştırmak için **wwwroot** dizinine yazma izinlerine sahip olmalısınız.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. SDK komut penceresini açın. Örnek yolda Kurulum.bat'ı çalıştırın. Bu, örnek için gereken sanal dizinleri oluşturur ve gerekli sertifikaları uygun izinlerle yükler.  
  
    > [!NOTE]
    > Setup.bat toplu dosyası, Windows SDK Komut İstemi'nden çalıştırılmak üzere tasarlanmıştır. MSSDK ortamı değişkeninin SDK'nın yüklendiği dizine işaret etmesini gerektirir. Bu ortam değişkeni otomatik olarak bir Windows SDK Komut İstemi içinde ayarlanır. Windows Vista'da, kurulum IIS yönetici komut dosyalarını kullandığından IIS 6.0 Yönetim Uyumluluğunun yüklü olduğundan emin olmalısınız. Windows Vista'da kurulum komut dosyasının çalıştırılması için yönetici ayrıcalıkları gerekiyor.  
  
2. Visual Studio'da FederationSample.sln'yi açın ve **Yapı** menüsünden **Çözüm Oluştur'u** seçin. Bu ortak proje dosyaları, Kitabevi hizmeti, Kitabevi STS, HomeRealm STS oluşturur ve IIS bunları dağıtır. Bu da Kitabevi istemci uygulaması oluşturur ve yürütülebilir BookStoreClient.exe'yi FederationSample\BookStoreClient\bin\Debug klasörüne yerleştirir.  
  
3. BookStoreClient.exe'yi çift tıklatın. BookStoreClient penceresi görüntülenir.  
  
4. **Kitaplara Gözat'ı**tıklayarak kitapçıda bulunan kitaplara göz atabilirsiniz.  
  
5. Belirli bir kitabı satın almak için, listedeki kitabı seçin ve **Kitap Satın Al'ı**tıklatın. Uygulama başlatılır ve HomeRealm Güvenlik Belirteç Hizmeti ile Windows kimlik doğrulaması kullanarak kimlik doğrulaması.  
  
     Örnek, kullanıcıların 15 ABD doları veya daha az maliyetli kitap satın almasına olanak sağlayacak şekilde yapılandırılmıştır. 15 TL'den fazla maliyetli kitap satın almaya çalışmak, istemcinin Book Store Hizmeti'nden Erişim Reddedilen bir ileti almasına neden olabilir.  
  
    > [!NOTE]
    > Örnek, bir satın alma işleminden sonra kullanıcının kredi limitini güncelleştirmez. Kullanıcının (sabit) kredi limiti dahilinde sürekli olarak kitap satın alabilirsiniz.  
  
#### <a name="to-clean-up"></a>Temizlemek için  
  
1. Cleanup'ı çalıştır.yarasa. Bu, kurulum sırasında oluşturulan sanal dizinleri siler ve kurulum sırasında yüklenen sertifikaları da kaldırır.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Federation`  

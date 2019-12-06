---
title: Federasyon Örneği
ms.date: 03/30/2017
ms.assetid: 7e9da0ca-e925-4644-aa96-8bfaf649d4bb
ms.openlocfilehash: c143ad9315df94a2d836a2c2c742ffa9a7728511
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837889"
---
# <a name="federation-sample"></a>Federasyon Örneği
Bu örnekte, Federasyon güvenliği gösterilmektedir.  
  
## <a name="sample-details"></a>Örnek Ayrıntılar  
 Windows Communication Foundation (WCF) `wsFederationHttpBinding`aracılığıyla Federal Güvenlik mimarilerini dağıtmaya yönelik destek sağlar. `wsFederationHttpBinding`, istek/yanıt iletişimi için temel alınan aktarım mekanizması olarak HTTP kullanımını ve kodlama için Tel biçimi olarak metin/XML kullanımını içeren güvenli, güvenilir ve birlikte çalışabilen bir bağlama sağlar. WCF 'de Federasyon hakkında daha fazla bilgi için bkz. [Federasyon](../../../../docs/framework/wcf/feature-details/federation.md).  
  
 Senaryo 4 parçadan oluşur:  
  
- Kitaplığı hizmeti  
  
- Kitaplığı STS  
  
- HomeRealm STS  
  
- Kitaplığı Istemcisi  
  
 Kitaplığı hizmeti, `BrowseBooks` ve `BuyBook`iki işlemi destekler. `BrowseBooks` işleme anonim erişimine izin verir, ancak `BuyBooks` işlemine erişmek için kimliği doğrulanmış erişim gerektirir. Kimlik doğrulaması, kitaplığı STS tarafından verilen belirtecin biçimini alır. Kitaplığı hizmeti için yapılandırma dosyası, istemcileri `wsFederationHttpBinding`kullanarak kitaplara yönlendirir.  
  
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
  
 Bu durumda, daha sonra, istemcilerin HomeRealm STS tarafından verilen bir belirteç kullanarak kimlik doğrulaması yapması gerekir. Yine, kitaplığı STS için yapılandırma dosyası, istemcileri `wsFederationHttpBinding`kullanarak HomeRealm STS 'ye yönlendirir.  
  
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
  
 `BuyBook` işlemine erişirken olayların sırası aşağıdaki gibidir:  
  
1. İstemci, Windows kimlik bilgilerini kullanarak HomeRealm STS 'nin kimliğini doğrular.  
  
2. HomeRealm STS, kitaplığı STS ' de kimlik doğrulaması için kullanılabilecek bir belirteç yayınlar.  
  
3. İstemci, HomeRealm STS tarafından verilen belirteci kullanarak kitaplığı STS 'de kimlik doğrulaması yapar.  
  
4. Kitaplığı STS, kitaplığı hizmetinde kimlik doğrulaması yapmak için kullanılabilecek bir belirteç verir.  
  
5. İstemci, kitaplığı STS tarafından verilen belirteci kullanarak Kitaplığı hizmeti için kimlik doğrulaması yapar.  
  
6. İstemci `BuyBook` işlemine erişir.  
  
 Bu örneği ayarlama ve çalıştırma hakkında aşağıdaki yönergelere bakın.  
  
> [!NOTE]
> Bu örneği çalıştırmak için **Wwwroot** dizinine yazma izinleriniz olmalıdır.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. SDK komut penceresini açın. Örnek yolda Setup. bat dosyasını çalıştırın. Bu, örnek için gereken sanal dizinleri oluşturur ve uygun izinlere sahip gerekli sertifikaları kurar.  
  
    > [!NOTE]
    > Setup. bat toplu iş dosyası bir Windows SDK komut Isteminden çalıştırılmak üzere tasarlanmıştır. MSSDK ortam değişkeninin, SDK 'nın yüklü olduğu dizine işaret olmasını gerektirir. Bu ortam değişkeni bir Windows SDK komut Istemi içinde otomatik olarak ayarlanır. Windows Vista 'da, kurulum IIS Yönetici betikleri kullandığından, IIS 6,0 yönetim uyumluluğuna emin olmanız gerekir. Windows Vista 'da kurulum betiğini çalıştırmak için yönetici ayrıcalıkları gerekir.  
  
2. Visual Studio 'da FederationSample. sln ' yi açın ve **derleme** menüsünden **çözüm oluştur** ' u seçin. Bu, ortak proje dosyalarını, kitaplığı hizmeti, kitaplığı STS, HomeRealm STS 'yi oluşturur ve bunları IIS 'de dağıtır. Bu Ayrıca, kitaplığı istemci uygulamasını oluşturur ve Boosample\bookstoreclient\bin\debug klasörüne yürütülebilir BookStoreClient. exe ' yi koyar.  
  
3. BookStoreClient. exe ' ye çift tıklayın. BookStoreClient penceresi görüntülenir.  
  
4. Kitaplarda bulunan kitaplara **gözatıp**' ye tıklayarak kitapçığa gidebilirsiniz.  
  
5. Belirli bir kitabı satın almak için listeden kitabı seçin ve **kitabı satın al**' a tıklayın. Uygulama başlatılır ve Barındırmerealm güvenlik belirteci hizmeti ile Windows kimlik doğrulamasını kullanarak kimlik doğrular.  
  
     Örnek, kullanıcıların $15 veya daha az bir kitap satın almasını sağlamak üzere yapılandırılmıştır. $15 'den daha fazla maliyet satın alma girişimi, istemcinin kitap mağazası hizmetinden bir erişim reddedildi iletisi almasıyla sonuçlanır.  
  
    > [!NOTE]
    > Örnek, bir satın alma işleminden sonra kullanıcının kredi limitini güncelleştirmez. Kullanıcıların (Sabit) kredi limiti içindeki kitapları tekrar tekrar satın alabilirsiniz.  
  
#### <a name="to-clean-up"></a>Temizlemek için  
  
1. Cleanup. bat dosyasını çalıştırın. Bu, ayarlama sırasında oluşturulan sanal dizinleri siler ve kurulum sırasında yüklenen sertifikaları da kaldırır.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Federation`  

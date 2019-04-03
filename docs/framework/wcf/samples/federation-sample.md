---
title: Federasyon Örneği
ms.date: 03/30/2017
ms.assetid: 7e9da0ca-e925-4644-aa96-8bfaf649d4bb
ms.openlocfilehash: e9f0c47a1bafe715a40d150a77543ca71a249920
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816609"
---
# <a name="federation-sample"></a>Federasyon Örneği
Bu örnek, Federasyon güvenlik gösterir.  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 Windows Communication Foundation (WCF), Federal güvenlik mimariler aracılığıyla dağıtmak için destek sağlar `wsFederationHttpBinding`. `wsFederationHttpBinding` Kullanımını HTTP temel aktarma mekanizması olarak istek/yanıt iletişim ve metin/XML olarak kodlamak için kablo biçimini içeren bir güvenli, güvenilir ve birlikte çalışabilen bağlama sağlar. Wcf'de Federasyon hakkında daha fazla bilgi için bkz: [Federasyon](../../../../docs/framework/wcf/feature-details/federation.md).  
  
 Senaryo 4 parçalarını oluşur:  
  
-   Hizmet Kitaplığı  
  
-   STS kitaplığı  
  
-   STS HomeRealm  
  
-   İstemci Kitaplığı  
  
 İki işlem kitaplığı hizmet destekler `BrowseBooks` ve `BuyBook`. Anonim erişime izin veren `BrowseBooks` işlemi, ancak erişim için kimliği doğrulanmış erişim gerektiren `BuyBooks` işlemi. Kimlik doğrulama Kitaplığı'nı STS tarafından verilen belirteci alır. Kitaplığı STS kullanarak istemcileri kitaplığı hizmeti için yapılandırma dosyasını işaret `wsFederationHttpBinding`.  
  
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
  
 Kitaplığı STS, ardından istemcilerin HomeRealm STS tarafından verilen bir belirteç kullanarak kimlik doğrulaması gerektirir. Yapılandırma dosyası kitaplığı STS HomeRealm STS kullanarak istemcileri yeniden işaret `wsFederationHttpBinding`.  
  
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
  
 Erişirken olayların sırasını `BuyBook` işlemi aşağıdaki gibidir:  
  
1.  İstemci, Windows kimlik bilgilerini kullanarak HomeRealm STS'ye kimliğini doğrular.  
  
2.  HomeRealm STS kitaplığı STS'ye kimlik doğrulaması için kullanılabilecek bir belirteç verir.  
  
3.  İstemci Kitaplığı sts'ye HomeRealm STS tarafından verilen belirteci kullanarak kimliğini doğrular.  
  
4.  Kitaplığı STS kitaplığı hizmete kimlik doğrulaması için kullanılabilecek bir belirteç verir.  
  
5.  İstemci Kitaplığı hizmet kitaplığı STS tarafından verilen belirteci kullanarak kimliğini doğrular.  
  
6.  İstemcisinin eriştiği `BuyBook` işlemi.  
  
 Ayarlanmış ve bu örneği çalıştırmak hakkında aşağıdaki yönergelere bakın.  
  
> [!NOTE]
>  Yazma izinlerine sahip olmalıdır **wwwroot** Bu örneği çalıştırmak için dizin.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  SDK komut penceresi açın. Örnek yolunda Setup.bat çalıştırın. Bu örnek için gerekli sanal dizinler oluşturur ve uygun izinlere sahip gerekli sertifikaları yükler.  
  
    > [!NOTE]
    >  Setup.bat toplu iş dosyası, bir Windows SDK Komut İstemi'nden çalıştırılmak üzere tasarlanmıştır. MSSDK ortam değişkeni'nın SDK'ın yüklendiği dizini gösterecek gerektiriyor. Bu ortam değişkeni, bir Windows SDK komut istemi içinde otomatik olarak ayarlanır. Üzerinde [!INCLUDE[wv](../../../../includes/wv-md.md)], ayarlama, IIS Yöneticisi betikleri kullandığından, IIS 6.0 Yönetim uyumluluğu yüklü emin olmanız gerekir. Kurulum betiği çalıştırma [!INCLUDE[wv](../../../../includes/wv-md.md)] yönetici ayrıcalıkları gerektirir.  
  
2.  Visual Studio'da FederationSample.sln açın ve seçin **Çözümü Derle** gelen **derleme** menüsü. Bu kitaplığı hizmet kitaplığı STS, HomeRealm STS, ortak proje dosyalarını oluşturur ve bunları IIS içinde dağıtır. Bu ayrıca kitaplığı istemci uygulaması oluşturur ve yürütülebilir BookStoreClient.exe FederationSample\BookStoreClient\bin\Debug klasörüne yerleştirir.  
  
3.  BookStoreClient.exe çift tıklayın. BookStoreClient penceresi görüntülenir.  
  
4.  Tıklayarak kitaplığı içinde kullanılabilir olan kitapları göz atabilirsiniz **Gözat Books**.  
  
5.  Belirli bir kitap satın almak için kitabı listeden seçin ve **satın kitap**. Uygulama başlatıldığında ve HomeRealm güvenlik belirteci hizmeti ile Windows kimlik doğrulaması kullanarak kimliğini doğrular.  
  
     , 15 ABD Doları maliyet kitapların satın almak kullanıcılara izin verecek şekilde yapılandırılmış ya da daha az örnektir. Birden çok erişim reddedildi iletisi kitap Store hizmetten alma istemci sonuçları 15 ABD Doları maliyet kitapların satın çalışılıyor.  
  
    > [!NOTE]
    >  Örnek kullanıcının kredi limiti, satın almanızdan sonra güncelleştirilmez. Art arda kullanıcının (sabit) kredi sınırına içinde books satın alabilirsiniz.  
  
#### <a name="to-clean-up"></a>Temizlemek için  
  
1.  CleanUp.bat çalıştırın. Bu yedekleme kümesi sırasında oluşturulan sanal dizinleri siler ve Kurulum sırasında yüklenen sertifikaların da kaldırır.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Federation`  
  

---
title: "Federasyon Örneği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7e9da0ca-e925-4644-aa96-8bfaf649d4bb
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a13632318902ce08678a01c3e63b3d12cc2f4f20
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="federation-sample"></a>Federasyon Örneği
Bu örnek federe güvenlik gösterir.  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]Federasyon güvenlik mimarileri üzerinden dağıtmak için destek sağlar `wsFederationHttpBinding`. `wsFederationHttpBinding` Kullanmayı HTTP temelindeki iletim mekanizması olarak istek/yanıt iletişimi ve Text/XML kodlama için kablo biçiminde içerir güvenli, güvenilir ve birlikte çalışabilir bağlama sağlar. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]İçinde Federasyon [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], bkz: [Federasyon](../../../../docs/framework/wcf/feature-details/federation.md).  
  
 Senaryo 4 parçalarını oluşur:  
  
-   Kitap hizmeti  
  
-   STS kitaplığı  
  
-   HomeRealm STS  
  
-   İstemci Kitaplığı  
  
 İki işlem kitap hizmeti destekler `BrowseBooks` ve `BuyBook`. Anonim erişime izin verir `BrowseBooks` işlemi, ancak erişim için kimlik doğrulamalı erişim gerektiren `BuyBooks` işlemi. Kimlik doğrulama kitaplığı STS tarafından verilmiş bir belirteç biçimini alır. Kitap STS kullanarak istemcileri kitap hizmeti için yapılandırma dosyasını işaret `wsFederationHttpBinding`.  
  
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
  
 Kitap STS, ardından istemciler HomeRealm STS tarafından verilmiş bir belirteç kullanarak kimlik doğrulaması gerektirir. Kitap STS için yapılandırma dosyası HomeRealm STS kullanarak istemcileri yeniden işaret `wsFederationHttpBinding`.  
  
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
  
 Erişirken olayların sırası `BuyBook` işlemi aşağıdaki gibidir:  
  
1.  İstemci, Windows kimlik bilgilerini kullanarak HomeRealm STS kimliğini doğrular.  
  
2.  HomeRealm STS kitap STS kimliğini doğrulamak için kullanılan bir belirteci verir.  
  
3.  İstemci Kitaplığı HomeRealm STS tarafından verilen belirteç kullanılarak STS kimliğini doğrular.  
  
4.  Kitap STS kitap hizmete kimliğini doğrulamak için kullanılan bir belirteci verir.  
  
5.  İstemci Kitaplığı hizmeti kitap STS tarafından verilen belirteç kullanarak kimliğini doğrular.  
  
6.  İstemcisinin eriştiği `BuyBook` işlemi.  
  
 Ayarlanmış ve bu örneği çalıştırmak hakkında aşağıdaki yönergelere bakın.  
  
> [!NOTE]
>  Yazma izinlerine sahip olmalıdır **wwwroot** Bu örneği çalıştırmak için dizin.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  SDK komut penceresi açın. Örnek yolunda Setup.bat çalıştırın. Bu örnek için gerekli sanal dizinler oluşturur ve gerekli sertifikaları uygun izinlerle birlikte yükler.  
  
    > [!NOTE]
    >  Setup.bat toplu iş dosyası, Windows SDK komut isteminden çalıştırılması için tasarlanmıştır. MSSDK ortam değişkeni SDK yüklendiği dizinine işaret gerektiriyor. Bu ortam değişkeni, Windows SDK komut istemi içinde otomatik olarak ayarlanır. Üzerinde [!INCLUDE[wv](../../../../includes/wv-md.md)], IIS 6.0 Yönetim uyumluluğu kurma IIS Yönetici komut dosyaları kullandığından yüklü emin olmanız gerekir. Kurulum komut dosyası çalıştırma [!INCLUDE[wv](../../../../includes/wv-md.md)] yönetici ayrıcalıkları gerekiyor.  
  
2.  Visual Studio'da FederationSample.sln açın ve seçin **yapı çözümü** gelen **yapı** menüsü. Bu kitap hizmet, kitap STS, HomeRealm STS, ortak proje dosyalarını oluşturur ve IIS içinde dağıtır. Bu ayrıca kitap istemci uygulaması oluşturur ve yürütülebilir BookStoreClient.exe FederationSample\BookStoreClient\bin\Debug klasörüdür.  
  
3.  BookStoreClient.exe çift tıklayın. BookStoreClient penceresi görüntülenir.  
  
4.  Tıklayarak kitap kullanılabilir books göz atabilirsiniz **Gözat Books**.  
  
5.  Belirli bir kitap satın almak için kitap listeden seçin ve **satın kitap**. Uygulama başlatıldığında ve HomeRealm güvenlik belirteci hizmeti Windows kimlik doğrulaması kullanarak kimliğini doğrular.  
  
     Örnek $15 maliyet books satın yapmalarına izin vermek için yapılandırılmış veya daha az. Birden çok kitap depolama Hizmeti'nden bir erişim reddedildi iletisi alma istemci $15 sonuçlarında maliyet books satın çalışılıyor.  
  
    > [!NOTE]
    >  Örnek satın alma sonra kullanıcının kredi sınırını güncelleştirmez. Art arda defterleri kullanıcının (sabit) kredi sınırı içinde satın alabilirsiniz.  
  
#### <a name="to-clean-up"></a>Temizlemek için  
  
1.  CleanUp.bat çalıştırın. Bu yukarı kümesi sırasında oluşturulan sanal dizinleri siler ve Kurulum sırasında yüklenen sertifikaların de kaldırır.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Federation`  
  
## <a name="see-also"></a>Ayrıca Bkz.

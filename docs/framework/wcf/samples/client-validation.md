---
title: İstemci Doğrulaması
ms.date: 03/30/2017
ms.assetid: f0c1f805-1a81-4d0d-a112-bf5e2e87a631
ms.openlocfilehash: 641d5e84c09575574ff6b06888d156c4b4aa0a38
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040108"
---
# <a name="client-validation"></a>İstemci Doğrulaması
Hizmetler, istemci proxy türlerinin otomatik olarak oluşturulmasını ve yapılandırılmasını sağlamak için sık sık meta verileri yayımlar. Hizmet güvenilmediği zaman, istemci uygulamaları, meta verilerin güvenlik, işlemler, hizmet sözleşmesinin türü vb. ile ilgili olarak istemci uygulama ilkesine uygun olduğunu doğrulamalıdır. Aşağıdaki örnek, hizmet uç noktasının kullanımı güvenli olduğundan emin olmak için hizmet uç noktasını doğrulayan bir istemci uç noktası davranışının nasıl yazılacağını gösterir.  
  
 Hizmet dört hizmet uç noktasını kullanıma sunar. İlk uç nokta, WSDualHttpBinding kullanır, ikinci uç nokta NTLM kimlik doğrulaması kullanır, üçüncü uç nokta işlem akışına izin vermez ve dördüncü uç nokta sertifika tabanlı kimlik doğrulaması kullanır.  
  
 İstemci, hizmeti için <xref:System.ServiceModel.Description.MetadataResolver> meta verileri almak üzere sınıfını kullanır. İstemci, bir doğrulama davranışı kullanarak çift yönlü bağlamaları, NTLM kimlik doğrulamasını ve işlem akışını engelleme ilkesini uygular. Hizmetin meta <xref:System.ServiceModel.Description.ServiceEndpoint> verilerinden içeri aktarılan her bir örnek için, istemci uygulaması, bağlanmak üzere bir Windows Communication Foundation ( `InternetClientValidatorBehavior` WCF) istemcisini kullanmaya <xref:System.ServiceModel.Description.ServiceEndpoint> çalışmadan önce, uç nokta davranışının bir örneğini içine ekler. uç nokta. Davranışın `Validate` yöntemi, hizmette herhangi bir işlem çağrılmadan önce çalışır ve öğesini `InvalidOperationExceptions`oluşturarak istemci ilkesini uygular.  
  
### <a name="to-build-the-sample"></a>Örneği oluşturmak için  
  
1. Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)bölümündeki yönergeleri izleyin.  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Örneği aynı bilgisayarda çalıştırmak için  
  
1. Yönetici ayrıcalıklarına sahip bir Visual Studio Geliştirici Komut İstemi açın ve örnek yükleme klasöründen Setup. bat dosyasını çalıştırın. Bu, örneği çalıştırmak için gereken tüm sertifikaları kurar.  
  
2. Hizmet uygulamasını \Service\bin\debugkonumundan çalıştırın.  
  
3. İstemci uygulamasını \Client\bin\debugkonumundan çalıştırın. İstemci etkinliği istemci konsol uygulamasında görüntülenir.  
  
4. İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
5. Örnek ile işiniz bittiğinde Cleanup. bat çalıştırarak sertifikaları kaldırın. Diğer güvenlik örnekleri aynı sertifikaları kullanır.  
  
### <a name="to-run-the-sample-across-computers"></a>Örneği bilgisayarlar arasında çalıştırmak için  
  
1. Sunucusunda, Visual Studio 'nun yönetici ayrıcalıklarıyla çalışması için Geliştirici Komut İstemi yazın `setup.bat service`. Bağımsız`service` değişkeniyle birlikte çalıştırmak `setup.bat` , bilgisayarın tam etki alanı adına sahip bir hizmet sertifikası oluşturur ve hizmet sertifikasını Service. cer adlı bir dosyaya aktarır.  
  
2. Sunucusunda, App. config dosyasını yeni sertifika adını yansıtacak şekilde düzenleyin. Diğer bir deyişle, `findValue` [ \<ServiceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) öğesindeki özniteliğini bilgisayarın tam etki alanı adıyla değiştirin.  
  
3. Service. cer dosyasını hizmet dizininden istemci bilgisayarındaki istemci dizinine kopyalayın.  
  
4. İstemcisinde, yönetici ayrıcalıklarına sahip bir Visual Studio Geliştirici Komut İstemi açın ve yazın `setup.bat client`. Bağımsız `setup.bat` değişkeniyle birlikte `client` çalıştırmak, Client.com adlı bir istemci sertifikası oluşturur ve istemci sertifikasını Client. cer adlı bir dosyaya aktarır.  
  
5. Client.cs dosyasında, `findValue` MEX uç noktasının adres değerini değiştirin ve varsayılan sunucu sertifikasını hizmetinizin yeni adresiyle eşleşecek şekilde ayarlamak için. Bunu, localhost yerine sunucunun tam etki alanı adıyla değiştirerek yapabilirsiniz. Derlemesine.  
  
6. Client. cer dosyasını istemci dizininden sunucusundaki hizmet dizinine kopyalayın.  
  
7. İstemcide, yönetici ayrıcalıklarıyla açılan bir Geliştirici Komut İstemi Visual Studio için ImportServiceCert. bat dosyasını çalıştırın. Bu, hizmet sertifikasını Service. cer dosyasından CurrentUser-Trustedkişiler deposuna aktarır.  
  
8. Sunucusunda, yönetici ayrıcalıklarıyla açılmış bir Visual Studio için Geliştirici Komut İstemi ImportClientCert. bat dosyasını çalıştırın. Bu, istemci sertifikasını Client. cer dosyasından LocalMachine-Trustedkişiler deposuna aktarır.  
  
9. Hizmet bilgisayarında, Visual Studio 'da hizmet projesini derleyin ve Service. exe ' yi çalıştırın.  
  
10. İstemci bilgisayarda, Client. exe ' yi çalıştırın.  
  
    1. İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-clean-up-after-the-sample"></a>Örnekten sonra temizlemek için  
  
- Örneği çalıştırmayı bitirdikten sonra Samples klasöründe Cleanup. bat dosyasını çalıştırın.  
  
    > [!NOTE]
    > Bu betik, bilgisayarlar arasında bu örneği çalıştırırken bir istemcideki hizmet sertifikalarını kaldırmaz. Bilgisayarlar arasında sertifika kullanan WCF örnekleri çalıştırırsanız, CurrentUser-Trustedkişiler deposuna yüklenmiş olan hizmet sertifikalarını temizlediğinizden emin olun. Bunu yapmak için şu komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>. For example: certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Verileri Kullanma](../../../../docs/framework/wcf/feature-details/using-metadata.md)

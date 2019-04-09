---
title: İstemci Doğrulaması
ms.date: 03/30/2017
ms.assetid: f0c1f805-1a81-4d0d-a112-bf5e2e87a631
ms.openlocfilehash: 637b6bd26407feb3213503310396a20bf1c8bdcd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59177339"
---
# <a name="client-validation"></a>İstemci Doğrulaması
Hizmetleri otomatik olarak oluşturmayı ve istemci proxy türlerinin yapılandırılmasını etkinleştirmek için meta verileri sık sık yayımlayın. Hizmetin güvenilir olmadığı durumlarda, istemci uygulamalarının meta veriler ile ilgili güvenlik, işlemler, hizmet sözleşme türü istemci uygulamanın İlkesi vb. uygun olduğunu doğrulamalıdır. Aşağıdaki örnek, bir istemci, hizmet uç noktası kullanmanın güvenli olduğundan emin olmak için hizmet uç noktası doğrular uç nokta davranışı yazma gösterilmiştir.  
  
 Hizmet, dört hizmet uç noktalarını kullanıma sunar. WSDualHttpBinding ilk uç noktayı kullanır, ikinci uç nokta NTLM kimlik doğrulamasını kullanan, üçüncü uç nokta işlem akışını etkinleştirir ve dördüncü uç noktası sertifika tabanlı kimlik doğrulaması kullanır.  
  
 İstemcinin kullandığı <xref:System.ServiceModel.Description.MetadataResolver> hizmet için meta verileri almak için sınıf. İstemci, çift yönlü bağlamaları, NTLM kimlik doğrulaması ve doğrulama davranışını kullanarak işlem akışını yasaklanması bir ilke uygular. Her <xref:System.ServiceModel.Description.ServiceEndpoint> istemci uygulama hizmet meta verilerden içe aktarıldı örneği bir örneğini ekler `InternetClientValidatorBehavior` uç nokta davranışı <xref:System.ServiceModel.Description.ServiceEndpoint> bağlanmak için bir Windows Communication Foundation (WCF) istemcisi kullanmayı denemeden önce uç noktası. Davranışın `Validate` yöntemi herhangi bir hizmet işlemi çağrılmadan önce çalışır ve oluşturma tarafından istemcinin ilkeyi zorlar `InvalidOperationExceptions`.  
  
### <a name="to-build-the-sample"></a>Örneği oluşturmak için  
  
1.  Çözümü derlemek için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Örneği aynı bilgisayarda çalıştırmak için  
  
1.  Yönetici ayrıcalıklarıyla Visual Studio için geliştirici komut istemi açın ve örnek yükleme klasöründen Setup.bat çalıştırın. Bu örneği çalıştırmak için gerekli olan tüm sertifikaları yükler.  
  
2.  Hizmet uygulaması \service\bin\Debug çalıştırın.  
  
3.  \Client\bin\Debug istemci uygulamasını çalıştırın. İstemci etkinliği istemci konsol uygulamasında görüntülenir.  
  
4.  İstemci ve hizmet iletişim kurabildiğini bilmiyorsanız bkz [WCF örnekleri için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
5.  Örnek ile tamamladığınızda Cleanup.bat çalıştırarak sertifikaları kaldırın. Diğer güvenlik örnekleri aynı sertifikalarını kullanın.  
  
### <a name="to-run-the-sample-across-computers"></a>Bilgisayarlar arasında örneği çalıştırmak için  
  
1.  Geliştirici komut istemi Visual Studio'yu yönetici ayrıcalıklarıyla çalıştırmak için sunucu üzerinde yazın `setup.bat service`. Çalışan `setup.bat` ile `service` bağımsız değişkeni bilgisayarın tam etki alanı adı ile bir hizmet sertifikası oluşturur ve hizmet sertifikası Service.cer adlı bir dosyaya dışarı aktarır.  
  
2.  Sunucu üzerinde App.config yeni sertifika adını yansıtacak şekilde düzenleyin. Diğer bir deyişle, değişiklik `findValue` özniteliğini [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) öğesi bilgisayarın tam etki alanı adı.  
  
3.  Service.cer dosya hizmeti dizinden istemci bilgisayarda istemci dizinine kopyalayın.  
  
4.  İstemcide, yönetici ayrıcalıklarına ve türü ile Visual Studio için geliştirici komut istemi açın `setup.bat client`. Çalışan `setup.bat` ile `client` bağımsız değişkeni Client.com adlı bir istemci sertifikası oluşturur ve istemci sertifikasını Client.cer adlı bir dosyaya dışarı aktarır.  
  
5.  Client.cs dosyasında MEX uç nokta adresi değerini değiştirmeniz ve `findValue` varsayılan sunucu sertifikası hizmetinizin yeni adresiyle eşleşecek şekilde ayarlamak için. Localhost sunucunun tam etki alanı adıyla değiştirerek bunu yapabilirsiniz. Yeniden oluşturun.  
  
6.  Client.cer dosyayı istemci dizin sunucusundaki hizmet dizinine kopyalayın.  
  
7.  İstemcide ImportServiceCert.bat yönetici ayrıcalıklarıyla açılan bir Visual Studio için geliştirici komut isteminden çalıştırın. Bu hizmet sertifikası Service.cer dosyasından CurrentUser - TrustedPeople deposuna aktarır.  
  
8.  Sunucusunda, yönetici ayrıcalıklarıyla açılan bir Visual Studio için geliştirici Komut İstemi'nde ImportClientCert.bat çalıştırın. Bu istemci sertifikası LocalMachine - TrustedPeople deposu Client.cer dosyasından alır.  
  
9. Hizmet bilgisayarda Visual Studio'da hizmet projesi oluşturup seçin, sonra da service.exe çalıştırın.  
  
10. İstemci bilgisayarda client.exe çalıştırın.  
  
    1.  İstemci ve hizmet iletişim kurabildiğini bilmiyorsanız bkz [WCF örnekleri için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-clean-up-after-the-sample"></a>Sonra örnek temizlemek için  
  
-   Bu örneği çalıştırmadan tamamladıktan sonra Cleanup.bat samples klasöründe çalıştırın.  
  
    > [!NOTE]
    >  Bu betik, bu örnek, bilgisayarlar arasında çalıştırırken bir istemcide hizmet sertifikaları kaldırmaz. Bu bilgisayarlar arasında sertifikalar kullanmak, içinde CurrentUser - yüklü hizmet sertifikalarını temizlendiğinden emin WCF örnekleri çalıştırırsanız TrustedPeople depolayın. Bunu yapmak için aşağıdaki komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>. For example: certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Verileri Kullanma](../../../../docs/framework/wcf/feature-details/using-metadata.md)

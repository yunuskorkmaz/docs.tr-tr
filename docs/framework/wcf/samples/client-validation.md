---
title: İstemci Doğrulaması
ms.date: 03/30/2017
ms.assetid: f0c1f805-1a81-4d0d-a112-bf5e2e87a631
ms.openlocfilehash: 6678ef7232b115f2bcb80b5f64621866f82b1f29
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90553538"
---
# <a name="client-validation"></a>İstemci Doğrulaması
Hizmetler, istemci proxy türlerinin otomatik olarak oluşturulmasını ve yapılandırılmasını sağlamak için sık sık meta verileri yayımlar. Hizmet güvenilmediği zaman, istemci uygulamaları, meta verilerin güvenlik, işlemler, hizmet sözleşmesinin türü vb. ile ilgili olarak istemci uygulama ilkesine uygun olduğunu doğrulamalıdır. Aşağıdaki örnek, hizmet uç noktasının kullanımı güvenli olduğundan emin olmak için hizmet uç noktasını doğrulayan bir istemci uç noktası davranışının nasıl yazılacağını gösterir.  
  
 Hizmet dört hizmet uç noktasını kullanıma sunar. İlk uç nokta, WSDualHttpBinding kullanır, ikinci uç nokta NTLM kimlik doğrulaması kullanır, üçüncü uç nokta işlem akışına izin vermez ve dördüncü uç nokta sertifika tabanlı kimlik doğrulaması kullanır.  
  
 İstemci, <xref:System.ServiceModel.Description.MetadataResolver> hizmeti için meta verileri almak üzere sınıfını kullanır. İstemci, bir doğrulama davranışı kullanarak çift yönlü bağlamaları, NTLM kimlik doğrulamasını ve işlem akışını engelleme ilkesini uygular. <xref:System.ServiceModel.Description.ServiceEndpoint>Hizmetin meta verilerinden içeri aktarılan her bir örnek için, istemci uygulaması `InternetClientValidatorBehavior` , <xref:System.ServiceModel.Description.ServiceEndpoint> uç noktaya bağlanmak için BIR Windows Communication Foundation (WCF) istemcisini kullanmaya çalışmadan önce, uç nokta davranışının bir örneğini ekler. Davranışın yöntemi, `Validate` hizmette herhangi bir işlem çağrılmadan önce çalışır ve öğesini oluşturarak istemci ilkesini uygular `InvalidOperationExceptions` .  
  
### <a name="to-build-the-sample"></a>Örneği oluşturmak için  
  
1. Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)bölümündeki yönergeleri izleyin.  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Örneği aynı bilgisayarda çalıştırmak için  
  
1. Yönetici ayrıcalıklarına sahip bir Visual Studio Geliştirici Komut İstemi açın ve örnek yüklemesi klasöründen Setup.bat çalıştırın. Bu, örneği çalıştırmak için gereken tüm sertifikaları kurar.  
  
2. Hizmet uygulamasını \Service\bin\debugkonumundan çalıştırın.  
  
3. İstemci uygulamasını \Client\bin\debugkonumundan çalıştırın. İstemci etkinliği istemci konsol uygulamasında görüntülenir.  
  
4. İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
5. Örnek ile işiniz bittiğinde Cleanup.bat çalıştırarak sertifikaları kaldırın. Diğer güvenlik örnekleri aynı sertifikaları kullanır.  
  
### <a name="to-run-the-sample-across-computers"></a>Örneği bilgisayarlar arasında çalıştırmak için  
  
1. Sunucusunda, Visual Studio 'nun yönetici ayrıcalıklarıyla çalışması için Geliştirici Komut İstemi yazın `setup.bat service` . `setup.bat`Bağımsız değişkeniyle birlikte çalıştırmak, `service` bilgisayarın tam etki alanı adına sahip bir hizmet sertifikası oluşturur ve hizmet sertifikasını Service. cer adlı bir dosyaya aktarır.  
  
2. Sunucusunda, yeni sertifika adını yansıtmak için App.config düzenleyin. Diğer bir deyişle, `findValue` [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) öğesindeki özniteliğini bilgisayarın tam etki alanı adıyla değiştirin.  
  
3. Service. cer dosyasını hizmet dizininden istemci bilgisayarındaki istemci dizinine kopyalayın.  
  
4. İstemcisinde, yönetici ayrıcalıklarına sahip bir Visual Studio Geliştirici Komut İstemi açın ve yazın `setup.bat client` . `setup.bat`Bağımsız değişkeniyle birlikte çalıştırmak, `client` Client.com adlı bir istemci sertifikası oluşturur ve Istemci sertifikasını Client. cer adlı bir dosyaya aktarır.  
  
5. Client.cs dosyasında, MEX uç noktasının adres değerini değiştirin ve `findValue` varsayılan sunucu sertifikasını hizmetinizin yeni adresiyle eşleşecek şekilde ayarlamak için. Bunu, localhost yerine sunucunun tam etki alanı adıyla değiştirerek yapabilirsiniz. Derlemesine.  
  
6. Client. cer dosyasını istemci dizininden sunucusundaki hizmet dizinine kopyalayın.  
  
7. İstemcisinde ImportServiceCert.bat, yönetici ayrıcalıklarıyla açılmış bir Visual Studio Geliştirici Komut İstemi çalıştırın. Bu, hizmet sertifikasını Service. cer dosyasından CurrentUser-Trustedkişiler deposuna aktarır.  
  
8. Sunucusunda, yönetici ayrıcalıklarıyla açılmış bir Visual Studio Geliştirici Komut İstemi ImportClientCert.bat çalıştırın. Bu, istemci sertifikasını Client. cer dosyasından LocalMachine-Trustedkişiler deposuna aktarır.  
  
9. Hizmet bilgisayarında, Visual Studio 'da hizmet projesini derleyin ve service.exe çalıştırın.  
  
10. İstemci bilgisayarda client.exe ' yi çalıştırın.  
  
    1. İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-clean-up-after-the-sample"></a>Örnekten sonra temizlemek için  
  
- Örneği çalıştırmayı bitirdikten sonra Samples klasöründe Cleanup.bat çalıştırın.  
  
    > [!NOTE]
    > Bu betik, bilgisayarlar arasında bu örneği çalıştırırken bir istemcideki hizmet sertifikalarını kaldırmaz. Bilgisayarlar arasında sertifika kullanan WCF örnekleri çalıştırırsanız, CurrentUser-Trustedkişiler deposuna yüklenmiş olan hizmet sertifikalarını temizlediğinizden emin olun. Bunu yapmak için şu komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>. For example: certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Verileri Kullanma](../feature-details/using-metadata.md)

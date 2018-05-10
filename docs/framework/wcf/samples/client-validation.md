---
title: İstemci Doğrulaması
ms.date: 03/30/2017
ms.assetid: f0c1f805-1a81-4d0d-a112-bf5e2e87a631
ms.openlocfilehash: 6e34ca8e1bb14f610e363c02eaeb94b7fa5e27c7
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
---
# <a name="client-validation"></a>İstemci Doğrulaması
Hizmetleri sık otomatik oluşturma ve istemci proxy türlerinin yapılandırılmasını etkinleştirmek için meta veri yayımlama. Hizmet güvenilir olmadığı durumlarda, istemci uygulamaları meta verileri istemci uygulama ilkesi güvenlik işlemleri, hizmet sözleşmesini türü ile ilgili vb. uyduğunu doğrulamalıdır. Aşağıdaki örnek, bir istemci bu hizmet uç noktası güvenli olduğundan emin olmak için hizmet uç noktası doğrulama uç noktası davranışı yazma gösterilmiştir.  
  
 Hizmet dört Hizmeti uç noktalarını kullanıma sunar. İlk uç nokta WSDualHttpBinding kullanır, ikinci uç nokta NTLM kimlik doğrulaması kullanır, üçüncü endpoint işlem akışını sağlar ve dördüncü uç nokta sertifika tabanlı kimlik doğrulaması kullanır.  
  
 İstemcinin kullandığı <xref:System.ServiceModel.Description.MetadataResolver> hizmet için meta verileri almak için sınıf. İstemci, çift yönlü bağlamaları, NTLM kimlik doğrulaması ve doğrulama davranışını kullanarak işlem akışı yasaklanması bir ilke zorlar. Her <xref:System.ServiceModel.Description.ServiceEndpoint> hizmetin meta verilerini, istemci uygulaması içeri örneği ekler örneği `InternetClientValidatorBehavior` uç noktası davranışı <xref:System.ServiceModel.Description.ServiceEndpoint> bağlanmak için bir Windows Communication Foundation (WCF) istemcisi kullanmayı denemeden önce uç noktası. Davranışın `Validate` yöntemi hizmette herhangi bir işlem çağrılmadan önce çalışır ve istemci ilkesini atma tarafından zorlar `InvalidOperationExceptions`.  
  
### <a name="to-build-the-sample"></a>Örneği oluşturmak için  
  
1.  Çözümü derlemek için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Aynı bilgisayara örneği çalıştırmak için  
  
1.  Yönetici ayrıcalıklarına sahip bir Visual Studio komut istemi açın ve Setup.bat örnek yükleme klasöründen çalıştırın. Bu örneği çalıştırmak için gerekli tüm sertifikalar yükler.  
  
2.  Hizmet uygulaması \service\bin\Debug çalıştırın.  
  
3.  İstemci uygulaması \client\bin\Debug çalıştırın. İstemci etkinliği istemci konsol uygulaması görüntülenir.  
  
4.  İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
5.  Sertifikaları örnekle tamamladığınızda Cleanup.bat çalıştırarak kaldırın. Diğer güvenlik örnekleri aynı sertifikaları kullanır.  
  
### <a name="to-run-the-sample-across-computers"></a>Bilgisayarlar arasında örneği çalıştırmak için  
  
1.  Sunucuda, yönetici ayrıcalıklarıyla çalıştırın Visual Studio komut istemi türü `setup.bat service`. Çalışan `setup.bat` ile `service` bağımsız değişkeni bilgisayarın tam etki alanı adı ile bir hizmet sertifikası oluşturur ve hizmet sertifikası Service.cer adlı bir dosyaya aktarır.  
  
2.  Sunucuda, App.config yeni sertifika yansıtacak şekilde düzenleyin. Diğer bir deyişle, değişiklik `findValue` özniteliğini [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) bilgisayarın tam etki alanı adını öğesi.  
  
3.  Service.cer dosya hizmeti dizininden istemci bilgisayarda istemci dizinine kopyalayın.  
  
4.  İstemci üzerinde yönetici ayrıcalıklarına ve tür ile Visual Studio komut istemini açın `setup.bat client`. Çalışan `setup.bat` ile `client` bağımsız değişkeni Client.com adlı bir istemci sertifikası oluşturur ve istemci sertifikasını Client.cer adlı bir dosyaya aktarır.  
  
5.  Client.cs dosyasında MEX uç noktası adresi değerini değiştirin ve `findValue` hizmetinizin yeni adresi eşleştirmek için varsayılan sunucu sertifikası ayarlama. Bunun için localhost sunucunun tam etki alanı adı ile değiştirerek. Yeniden oluşturma.  
  
6.  Client.cer dosyasını istemci dizininden sunucusunda hizmet dizinine kopyalayın.  
  
7.  İstemci üzerinde yönetici ayrıcalıklarına sahip açılan bir Visual Studio komut istemi ImportServiceCert.bat çalıştırın. Bu hizmet sertifikası Service.cer dosyadan Currentuser'a - TrustedPeople deposunu alır.  
  
8.  Sunucu üzerinde yönetici ayrıcalıklarına sahip açılan bir Visual Studio komut istemi ImportClientCert.bat çalıştırın. Bu istemci sertifikası LocalMachine - TrustedPeople deposunda Client.cer dosyadan alır.  
  
9. Hizmet bilgisayarda Visual Studio'da hizmet projeyi oluşturun ve service.exe çalıştırın.  
  
10. İstemci bilgisayarda client.exe çalıştırın.  
  
    1.  İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-clean-up-after-the-sample"></a>Örnek sonra temizlemek için  
  
-   Örnek çalıştıran tamamladıktan sonra Cleanup.bat samples klasöründen çalıştırın.  
  
    > [!NOTE]
    >  Bu komut, bu örnek bilgisayarlar arasında çalıştırırken bir istemcide hizmet sertifikaları kaldırmaz. Bilgisayarlar arasında sertifikalar kullanmak, Currentuser'a - yüklü hizmet sertifikalarını temizlediğinizden emin WCF örnekleri çalıştırırsanız TrustedPeople depolar. Bunu yapmak için aşağıdaki komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>. For example: certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Meta Verileri Kullanma](../../../../docs/framework/wcf/feature-details/using-metadata.md)

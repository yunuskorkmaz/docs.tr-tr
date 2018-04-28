---
title: 'Nasıl yapılır: Geliştirme Sırasında Kullanmak için Geçici Sertifikalar Oluşturma'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- certificates [WCF], creating temporary certificates
- temporary certificates [WCF]
ms.assetid: bc5f6637-5513-4d27-99bb-51aad7741e4a
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ccbc8c6fa638c674dea28c312b2dedbc9d41968a
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="how-to-create-temporary-certificates-for-use-during-development"></a>Nasıl yapılır: Geliştirme Sırasında Kullanmak için Geçici Sertifikalar Oluşturma
Güvenli hizmeti veya kullanan istemci geliştirirken [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], kimlik bilgisi olarak kullanılacak bir X.509 sertifikası sağlamak genellikle gereklidir. Sertifika genellikle bilgisayar güvenilen kök sertifika yetkilileri deposunda bulunan kök yetkisine sahip bir sertifika zinciri parçasıdır. Bir sertifika zinciri sahip genellikle kök yetkilisi kuruluşunuz ya da iş birimi olduğu sertifikalar kümesini kapsam sağlar. Bu geliştirme anında benzetmek için güvenlik gereksinimlerini karşılamak için iki sertifika oluşturabilirsiniz. İlk olan otomatik olarak imzalanan bir sertifika olduğundan güvenilen kök sertifika yetkilileri deposunda yerleştirilir ve ikinci sertifikayla birinciden oluşturulur ve yerel makine konumunun kişisel deposunda ya kişisel deposuna yerleştirilir Geçerli kullanıcı konumu. Bu konuda kullanarak bu iki sertifika oluşturmak için adımlarda size yol [sertifika oluşturma Aracı (MakeCert.exe)](http://go.microsoft.com/fwlink/?LinkId=248185), tarafından sağlanan [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] SDK.  
  
> [!IMPORTANT]
>  Sertifika Oluşturma Aracı'nı oluşturur sertifikalar yalnızca sınama amacıyla sağlanır. Bir hizmet veya istemci dağıtımı sırasında bir sertifika yetkilisi tarafından sağlanan uygun bir sertifika kullandığınızdan emin olun. Bu da gelen olabilir bir [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] sertifika kuruluşunuzdaki sunucuda veya bir üçüncü taraf.  
>   
>  Varsayılan olarak, [Makecert.exe (sertifika oluşturma aracı)](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d) , kök yetkilisi çağrılır sertifikaları oluşturur "kök Teşkilatı **."** "Kök Teşkilatı" güvenilen kök sertifika yetkilileri deposunda olmadığı için bu bu sertifikaları güvenli hale getirir. Güvenilen kök sertifika yetkilileri yerleştirilen otomatik olarak imzalanan sertifika oluşturma deposu daha yakından dağıtım ortamınızı taklit eden bir geliştirme ortamı oluşturmanıza olanak sağlar.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] bkz: oluşturma ve sertifikalarını kullanarak [sertifikalarla çalışma](../../../../docs/framework/wcf/feature-details/working-with-certificates.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)] bir kimlik bilgisi bir sertifika kullanılarak bkz [güvenli hale getirme hizmetler ve istemcileri](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md). Microsoft Authenticode teknolojisini kullanarak hakkında bir öğretici için bkz: [Authenticode genel bakış ve öğreticiler](http://go.microsoft.com/fwlink/?LinkId=88919).  
  
### <a name="to-create-a-self-signed-root-authority-certificate-and-export-the-private-key"></a>Otomatik olarak imzalanan kök yetkilisi sertifikası oluşturma ve özel anahtarı dışarı aktar  
  
1.  MakeCert.exe aracı aşağıdaki anahtarlarla kullanın:  
  
    1.  `-n` `subjectName`. Konu adı belirtir. Kuraldır konu adıyla öneki için "CN =" "Ortak adı" için.  
  
    2.  `-r`. Sertifika otomatik olarak imzalanan olacağını belirtir.  
  
    3.  `-sv` `privateKeyFile`. Özel anahtar kapsayıcısı içeren dosyayı belirtir.  
  
     Örneğin, aşağıdaki komut bir konu adı ile otomatik olarak imzalanan bir sertifika oluşturur "CN = TempCA."  
  
    ```  
    makecert -n "CN=TempCA" -r -sv TempCA.pvk TempCA.cer  
    ```  
  
     Özel anahtarını korumak için bir parola girmeniz istenir. Bu kök sertifikası tarafından imzalanmış bir sertifika oluşturmak için bu parola gereklidir.  
  
### <a name="to-create-a-new-certificate-signed-by-a-root-authority-certificate"></a>Bir kök yetkilisi sertifikası tarafından imzalanmış yeni bir sertifika oluşturmak için  
  
1.  MakeCert.exe aracı aşağıdaki anahtarlarla kullanın:  
  
    1.  `-sk` `subjectKey`. Özel anahtarı tutan ilgilinin anahtar kapsayıcısının konumu. Bir anahtar kapsayıcısı mevcut değilse oluşturulur. -Sk veya - sv seçeneklerin ikisi kullanılırsa, JoeSoft adlı bir anahtar kapsayıcısı varsayılan olarak oluşturulur.  
  
    2.  `-n` `subjectName`. Konu adı belirtir. Kuraldır konu adıyla öneki için "CN =" "Ortak adı" için.  
  
    3.  `-iv` `issuerKeyFile`. Verenin özel anahtar dosyası belirtir.  
  
    4.  `-ic` `issuerCertFile`. Verenin sertifikasının konumunu belirtir.  
  
     Örneğin, aşağıdaki komut tarafından imzalanmış bir sertifika oluşturur `TempCA` kök yetkilisi sertifikası bir konu adı ile `"CN=SignedByCA"` özel anahtarı kullanarak.  
  
    ```  
    makecert -sk SignedByCA -iv TempCA.pvk -n "CN=SignedByCA" -ic TempCA.cer SignedByCA.cer -sr currentuser -ss My  
    ```  
  
## <a name="installing-a-certificate-in-the-trusted-root-certification-authorities-store"></a>Güvenilen Kök Sertifika Yetkilileri deposuna sertifika yüklemek  
 Kendinden imzalı bir sertifika oluşturulduktan sonra güvenilen kök sertifika yetkilileri deposunda yükleyebilirsiniz. İmzalı sertifika bu noktada sertifikalarla bilgisayar tarafından güvenilmiyor. Artık ihtiyacınız hemen bu nedenle, sertifika deposundan silin. Bu kök yetkilisi sertifikası sildiğinizde, ile imzalanmış tüm diğer sertifikalar yetkisiz haline gelir. Kök yetkilisi sertifikaları adlı bir grup sertifikaların gerektiğinde kapsamlı olabilir yalnızca bir sistemdir. Örneğin, eşler arası uygulamalarında genellikle gerek yoktur kök yetkilisi için sağlanan sertifikaya göre yalnızca tek bir kimlik güven olduğundan.  
  
#### <a name="to-install-a-self-signed-certificate-in-the-trusted-root-certification-authorities"></a>Güvenilen kök sertifika yetkilileri otomatik olarak imzalanan bir sertifika yüklemek için  
  
1.  Sertifika ek bileşenini açın. Daha fazla bilgi için bkz: [nasıl yapılır: MMC ek bileşeni ile sertifikaları görüntüleme](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).  
  
2.  Sertifika ya da depolanacağı klasörü açın **yerel bilgisayar** veya **geçerli kullanıcı**.  
  
3.  Açık **güvenilen kök sertifika yetkilileri** klasör.  
  
4.  Sağ tıklatın **sertifikaları** klasörü ve tıklatın **tüm görevler**, ardından **alma**.  
  
5.  Ekrandaki sihirbazını izleyin TempCa.cer deposuna içeri aktarma yönergeleri.  
  
## <a name="using-certificates-with-wcf"></a>WCF ile sertifikaları kullanma  
 Geçici sertifikalar ayarladıktan sonra sertifikaları belirten bir istemci kimlik bilgisi türü WCF çözümleri geliştirmek için kullanabilirsiniz. Örneğin, aşağıdaki XML yapılandırması ileti güvenliği ve sertifika istemci kimlik bilgisi türü belirtir.  
  
#### <a name="to-specify-a-certificate-as-the-client-credential-type"></a>İstemci kimlik bilgisi türü bir sertifika belirtmek için  
  
-   Hizmet yapılandırma dosyasında aşağıdaki XML ileti ve sertifika için istemci kimlik bilgisi türü için kullanılan güvenlik modunu ayarlamak için kullanın.  
  
    ```xml  
    <bindings>       
      <wsHttpBinding>  
        <binding name="CertificateForClient">  
          <security>  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    ```  
  
 Bir istemci yapılandırma dosyasında aşağıdaki XML sertifikanın kullanıcı deposunda bulunan olduğunu ve SubjectName alanın değeri "CohoWinery." için arama yaparak bulunabilir belirtmek için kullanın.  
  
```xml  
<behaviors>  
  <endpointBehaviors>  
    <behavior name="CertForClient">  
      <clientCredentials>  
        <clientCertificate findValue="CohoWinery" x509FindType="FindBySubjectName" />  
       </clientCredentials>  
     </behavior>  
   </endpointBehaviors>  
</behaviors>  
```  
  
 WCF'de sertifika kullanma hakkında daha fazla bilgi için bkz: [sertifikalarla çalışma](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Tüm geçici kök yetkilisi sertifikalardan sildiğinizden emin olun **güvenilen kök sertifika yetkilileri** ve **kişisel** sertifikayı sağ tıklatıp sonra tıklatarak klasörleri  **Silme**.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sertifikalarla Çalışma](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Nasıl yapılır: MMC Ek Bileşeni ile Sertifikaları Görüntüleme](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)  
 [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)

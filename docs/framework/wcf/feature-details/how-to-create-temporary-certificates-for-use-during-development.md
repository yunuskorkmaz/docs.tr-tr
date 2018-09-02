---
title: 'Nasıl yapılır: Geliştirme Sırasında Kullanmak için Geçici Sertifikalar Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], creating temporary certificates
- temporary certificates [WCF]
ms.assetid: bc5f6637-5513-4d27-99bb-51aad7741e4a
ms.openlocfilehash: d3b051c7ea152606721388ea35b6f508eada1c5d
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43385183"
---
# <a name="how-to-create-temporary-certificates-for-use-during-development"></a>Nasıl yapılır: Geliştirme Sırasında Kullanmak için Geçici Sertifikalar Oluşturma
Güvenli hizmet veya Windows Communication Foundation (WCF) kullanan istemci geliştirirken, genellikle bir kimlik bilgisi olarak kullanılacak bir X.509 sertifikası sağlamak gereklidir. Sertifika bilgisayar güvenilen kök sertifika yetkilileri deposunda bulunan kök yetkilisi sertifikalarıyla oluşan bir zincir, genellikle parçasıdır. Bir sertifika zinciri olan sertifika genellikle kök yetkilisi kuruluşunuz veya iş birimi olduğu kümesi kapsam olanak tanır. Bu geliştirme zamanında benzetmek için güvenlik gereksinimlerini karşılamak için iki sertifika oluşturabilirsiniz. İlk otomatik olarak imzalanan bir sertifika olduğundan güvenilen kök sertifika yetkilileri deposunda yerleştirilir ve ikinci sertifikayı ilk konumdan oluşturulur ve yerel makine konumun Kişisel depolama alanı kişisel mağazasında şirket içinde veya yerleştirilir. Geçerli kullanıcı konumu. Bu konuda kullanarak bu iki sertifikaları oluşturma adımlarında size kılavuzluk eder [sertifika oluşturma Aracı (MakeCert.exe)](https://go.microsoft.com/fwlink/?LinkId=248185), tarafından sağlanan [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] SDK.  
  
> [!IMPORTANT]
>  Sertifika Oluşturma aracı oluşturur sertifikalar yalnızca sınama amacıyla sağlanır. Bir hizmet veya istemci dağıtımı sırasında bir sertifika yetkilisi tarafından sağlanan uygun bir sertifikayı kullanmak emin olun. Bu da gelen olabilir bir [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] sertifika kuruluşunuzdaki sunucuya veya bir üçüncü taraf.  
>   
>  Varsayılan olarak, [Makecert.exe (sertifika oluşturma aracı)](https://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d) , kök yetkilisi adlı sertifikalar oluşturur "kök Ajans **."** "Kök Ajans" güvenilen kök sertifika yetkilileri deposunda olmadığından bu bu sertifikaları güvenli hale getirir. Güvenilen kök sertifika yetkilileri yerleştirilir, otomatik olarak imzalanan bir sertifika oluşturmak store dağıtım ortamınızı daha yakından taklit eden bir geliştirme ortamı olarak oluşturmanıza olanak sağlar.  
  
 Oluşturma ve sertifikaları kullanma hakkında daha fazla bilgi için bkz. [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md). Bir kimlik bilgisi olarak bir sertifika kullanma hakkında daha fazla bilgi için bkz. [Hizmetleri güvenli hale getirme ve istemciler](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md). Microsoft Authenticode teknolojisi kullanılarak hakkında bir öğretici için bkz [Authenticode genel bakış ve öğreticiler](https://go.microsoft.com/fwlink/?LinkId=88919).  
  
### <a name="to-create-a-self-signed-root-authority-certificate-and-export-the-private-key"></a>Otomatik olarak imzalanan kök yetkilisi sertifikası oluşturma ve özel anahtarı dışarı aktar  
  
1.  MakeCert.exe aracı ile aşağıdaki anahtarlar kullanın:  
  
    1.  `-n` `subjectName`. Konu adını belirtir. Kuraldır konu adıyla önek olarak eklemek için "CN =" "Ortak adı" için.  
  
    2.  `-r`. Sertifika otomatik olarak imzalanan olacağını belirtir.  
  
    3.  `-sv` `privateKeyFile`. Özel anahtar kapsayıcısı içeren dosyayı belirtir.  
  
     Örneğin, aşağıdaki komut bir konu adı ile otomatik olarak imzalanan bir sertifika oluşturur. "CN = TempCA."  
  
    ```  
    makecert -n "CN=TempCA" -r -sv TempCA.pvk TempCA.cer  
    ```  
  
     Özel anahtarını korumak için bir parola girmeniz istenir. Bu kök sertifika tarafından imzalanmış bir sertifika oluşturmak için bu parola gereklidir.  
  
### <a name="to-create-a-new-certificate-signed-by-a-root-authority-certificate"></a>Kök yetkilisi sertifikası tarafından imzalanmış yeni bir sertifika oluşturmak için  
  
1.  MakeCert.exe aracı ile aşağıdaki anahtarlar kullanın:  
  
    1.  `-sk` `subjectKey`. Özel anahtarı tutan öznenin anahtar kapsayıcısı konumunu. Bir anahtar kapsayıcı mevcut değilse oluşturulur. -Sk veya - sv seçeneğinin kullanılması durumunda JoeSoft adlı bir anahtar kapsayıcı varsayılan olarak oluşturulur.  
  
    2.  `-n` `subjectName`. Konu adını belirtir. Kuraldır konu adıyla önek olarak eklemek için "CN =" "Ortak adı" için.  
  
    3.  `-iv` `issuerKeyFile`. Verenin özel anahtar dosyasını belirtir.  
  
    4.  `-ic` `issuerCertFile`. Verenin sertifika konumunu belirtir.  
  
     Örneğin, aşağıdaki komutu tarafından imzalanmış bir sertifika oluşturur `TempCA` kök yetkilisi sertifikası konu adı ile `"CN=SignedByCA"` verenin özel anahtarı kullanarak.  
  
    ```  
    makecert -sk SignedByCA -iv TempCA.pvk -n "CN=SignedByCA" -ic TempCA.cer SignedByCA.cer -sr currentuser -ss My  
    ```  
  
## <a name="installing-a-certificate-in-the-trusted-root-certification-authorities-store"></a>Güvenilen kök sertifika yetkilileri Store sertifika yükleme  
 Kendinden imzalı bir sertifika oluşturulduktan sonra güvenilen kök sertifika yetkilileri deposunda yükleyebilirsiniz. İmzalanmış herhangi bir sertifika ile bu noktada sertifika, bilgisayar tarafından güvenilmiyor. Artık ihtiyacınız hemen sonra bu nedenle, sertifika deposundan silin. İle imzalanmış tüm sertifikaları bu kök yetkilisi sertifikası sildiğinizde, yetkisiz haline gelir. Kök yetkilisi sertifikaları yapabildiği sertifikaların bir grup gerektiğinde kapsamlandırılabilir olarak yalnızca bir mekanizması mevcuttur. Örneğin, eşler arası uygulamalar, genellikle gerek yoktur kök yetkilisi için yalnızca bir bireyin kimliği tarafından sağlanan, sertifika güven için.  
  
#### <a name="to-install-a-self-signed-certificate-in-the-trusted-root-certification-authorities"></a>Güvenilen kök sertifika yetkilileri otomatik olarak imzalanan bir sertifika yüklemek için  
  
1.  Sertifika ek bileşenini açın. Daha fazla bilgi için [nasıl yapılır: MMC ek bileşeni ile sertifikaları görüntüleme](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).  
  
2.  Sertifika ya da depolamak için klasörü açın **yerel bilgisayar** veya **geçerli kullanıcının**.  
  
3.  Açık **güvenilen kök sertifika yetkilileri** klasör.  
  
4.  Sağ tıklayın **sertifikaları** klasörü ve tıklatın **tüm görevler**, ardından **alma**.  
  
5.  Ekrandaki Sihirbazı izleyin TempCa.cer depoya içeri aktarma yönergeleri.  
  
## <a name="using-certificates-with-wcf"></a>WCF ile sertifikaları kullanma  
 Geçici sertifikalar ayarladıktan sonra sertifikaları bir istemci kimlik bilgisi türü belirtin WCF çözümleri geliştirmek için kullanabilirsiniz. Örneğin, aşağıdaki XML yapılandırması ileti güvenliği ve bir sertifika istemci kimlik bilgileri türünü belirtir.  
  
#### <a name="to-specify-a-certificate-as-the-client-credential-type"></a>Sertifika istemci kimlik bilgisi türü belirtmek için  
  
-   Hizmet yapılandırma dosyasında aşağıdaki XML iletisi ve sertifika için istemci kimlik bilgisi türü güvenlik modu ayarlamak için kullanın.  
  
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
  
 Bir istemci için yapılandırma dosyasında, sertifikası olan bir kullanıcının deposunda bulunamadı ve SubjectName alanın değeri "CohoWinery." için arama yaparak bulunabilir belirtmek için aşağıdaki XML kullanın.  
  
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
  
 WCF'de sertifikaları kullanma hakkında daha fazla bilgi için bkz. [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Geçici kök yetkilisi sertifikalarını sildiğinizden emin olun **güvenilen kök sertifika yetkilileri** ve **kişisel** sertifikayı sağ tıklatıp sonra tıklatarak klasörleri  **Silme**.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sertifikalarla Çalışma](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Nasıl yapılır: MMC Ek Bileşeni ile Sertifikaları Görüntüleme](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)  
 [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)

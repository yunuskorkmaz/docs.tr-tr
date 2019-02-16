---
title: Taşıma Güveliği Kullanarak İletileri Güvenli Hale Getirme
ms.date: 03/30/2017
ms.assetid: 9029771a-097e-448a-a13a-55d2878330b8
ms.openlocfilehash: 354b014825b3282e494cf75637fb2434acdb2dbe
ms.sourcegitcommit: 0069cb3de8eed4e92b2195d29e5769a76111acdd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/16/2019
ms.locfileid: "56332357"
---
# <a name="securing-messages-using-transport-security"></a>Taşıma Güveliği Kullanarak İletileri Güvenli Hale Getirme
Bu bölümde, kuyruğa gönderilen iletileri güvenli hale getirmek için kullanabileceğiniz bir Message Queuing (MSMQ) aktarım güvenliği açıklanmaktadır.  
  
> [!NOTE]
>  Bu konu içinde okumadan önce okumanızı önerilir [güvenlik kavramları](../../../../docs/framework/wcf/feature-details/security-concepts.md).  
  
 Aşağıdaki çizimde Windows Communication Foundation (WCF) kullanan kuyruğa alınan iletişim kavramsal modelin sağlar. Bu çizim ve terminolojisi Aktarım güvenlik kavramları açıklamak için kullanılır.  
  
 ![Uygulama diyagramı kuyruğa](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "dağıtılmış-kuyruk-Şekil")  
  
 Ne zaman gönderme kuyruğa alınan iletileri ile WCF kullanarak <xref:System.ServiceModel.NetMsmqBinding>, WCF ileti bir MSMQ iletisinin gövdesi olarak eklenir. Aktarım güvenliği (MSMQ İleti üstbilgileri veya özellikleri ve ileti gövdesi) tüm MSMQ İleti güvenliğini sağlar. MSMQ iletisinin gövdesini olduğundan, aktarım güvenliği kullanarak aynı zamanda WCF ileti güvenliğini sağlar.  
  
 Anahtar kavram aktarım güvenliği arkasındaki istemci iletinin hedef sıraya almak için güvenlik gereksinimlerini karşılamak sahip olur. İleti iletiyi alan uygulama için burada güvenli ileti güvenliği budur.  
  
 Aktarım güvenliği kullanarak <xref:System.ServiceModel.NetMsmqBinding> ve <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> MSMQ iletileri güvenliği nasıl etkilediğini aktarım sırasında iletim sırası ve hedef sıra arasında güvenli bir yerde gösterir:  
  
-   İletinin emin olmak için imzalama değiştirilmiş değil.  
  
-   İletinin görülen veya değiştirilmiş emin olmak için şifreleme. Bu önerilir ancak isteğe bağlıdır.  
  
-   Tanımlayan takası ileti gönderen hedef sıra Yöneticisi.  
  
 MSMQ, bağımsız olarak kimlik doğrulaması, hedef kuyruk bir erişim denetimi listesi (ACL) istemci hedef kuyruğa ileti gönderme izni olup olmadığını denetlemek için vardır. Alıcı uygulamanın hedef kuyruktan ileti alma izni de denetlenir.  
  
## <a name="wcf-msmq-transport-security-properties"></a>WCF MSMQ taşıma güvenlik özellikleri  
 MSMQ Güvenliği Windows kimlik doğrulaması için kullanır. İstemci kimliği için Windows Güvenlik tanımlayıcısı (SID) kullanır ve istemci kimlik doğrulaması yapılırken sertifika yetkilisi olarak Active Directory dizin hizmeti kullanır. Bu, MSMQ Active Directory Tümleştirmesi ile yüklü olmasını gerektirir. SID Windows etki alanı, istemciyi tanımlamak için kullanıldığından, hem istemci hem de hizmet aynı Windows etki alanının parçası olduğunda bu güvenlik seçeneği yalnızca anlam ifade eder.  
  
 MSMQ Active Directory ile kayıtlı değil iletisiyle bir sertifika ekleme olanağı da sağlar. Bu durumda, ileti iliştirilmiş sertifika kullanılarak imzalanıp imzalanmadığını sağlar.  
  
 WCF MSMQ taşıma güvenlik bir parçası olarak bu iki seçenek sağlar ve bunlar aktarım güvenliği için bu önemli adım.  
  
 Varsayılan olarak, aktarım güvenliği etkinleştirilir.  
  
 Bu temel alındığında, aşağıdaki bölümlerde ayrıntılı aktarım güvenliği özellikleri birlikte <xref:System.ServiceModel.NetMsmqBinding> ve <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.  
  
#### <a name="msmq-authentication-mode"></a>MSMQ kimlik doğrulama modu  
 <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> İleti güvenliğini sağlamak için Windows etki alanı güvenlik veya bir dış sertifika tabanlı güvenlik kullanılıp kullanılmayacağını belirler. WCF sıraya alınan taşıma kanalının her iki kimlik doğrulama modları kullanan `CertificateValidationMode` hizmet yapılandırmasında belirtilen. Sertifika geçerliliğini denetlemek için kullanılan mekanizma sertifika doğrulama modunu belirtir.  
  
 Aktarım güvenliği açık olduğunda varsayılan ayardır <xref:System.ServiceModel.MsmqAuthenticationMode.WindowsDomain>.  
  
#### <a name="windows-domain-authentication-mode"></a>Windows etki alanı kimlik doğrulama modu  
 Windows güvenliğini kullanarak seçeneğine Active Directory Tümleştirme gerektirir. <xref:System.ServiceModel.MsmqAuthenticationMode.WindowsDomain> Varsayılan Aktarım güvenlik modudur. Bu ayarlandığında, WCF kanalı Windows SID MSMQ iletisine ve Active Directory'den alınan iç sertifikasını kullanır. MSMQ İleti güvenliğini sağlamak için bu bir iç sertifika kullanır. Alıcı sırası Yöneticisi, arama ve istemcinin kimliğini doğrulamak için eşleşen bir sertifika bulmak için Active Directory kullanır ve SID aynı zamanda, istemcinin eşleştiğini denetler. Bir sertifika varsa bu kimlik doğrulama adımı yürütülür, ya da durumunda, dahili olarak oluşturulan `WindowsDomain` kimlik doğrulama modu veya durumunda, harici olarak oluşturulan `Certificate` kimlik doğrulama modu, hedef sıra olsa bile iletiye ekli kimlik doğrulaması gerektiren olarak işaretlenmedi.  
  
> [!NOTE]
>  Bir kuyruğu oluştururken, sıranın kuyruğa ileti gönderme istemci kimlik doğrulaması gerektirdiğini belirtmek için kimliği doğrulanmış bir kuyruk olarak sıranın işaretleyebilirsiniz. Bu, kimliği doğrulanmamış ileti kuyrukta kabul edildiğini sağlar.  
  
 SID ile bağlı ileti istemci kuyruğa ileti göndermek için yetkili olduğundan emin olmak için hedef sıra ACL denetlemek için de kullanılır.  
  
#### <a name="certificate-authentication-mode"></a>Sertifika kimlik doğrulaması modu  
 Sertifika kimlik doğrulaması modunu kullanma seçimi, Active Directory Tümleştirme gerektirmez. Aslında, bazı durumlarda, MSMQ (olmadan, Active Directory ile tümleştirme) çalışma grubu modunda yüklendiğinde veya ne zaman SOAP Güvenilir Mesajlaşma Protokolü (SRMP) kullanarak izin ver aktarım kuyruğa, yalnızca ileti göndermek için Protokolü gibi <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate> çalışır.  
  
 Bir WCF ileti gönderirken <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate>, WCF kanalı için MSMQ iletisinin bir Windows SID'ye eklemez. Bu nedenle, hedef sıra ACL için izin vermelidir `Anonymous` kuyruğa göndermek için kullanıcı erişim. Alıcı sırası Yöneticisi MSMQ iletisinin bir sertifikayla imzalanmış, ancak herhangi bir kimlik doğrulaması gerçekleştirmez denetler.  
  
 İçinde sertifika, talepleri ve kimlik bilgileri ile doldurulur <xref:System.ServiceModel.ServiceSecurityContext> WCF sıraya alınan aktarım kanalı tarafından. Hizmet, gönderenin kendi kimlik doğrulaması gerçekleştirmek için bu bilgileri kullanabilirsiniz.  
  
### <a name="msmq-protection-level"></a>MSMQ koruma düzeyi  
 Koruma düzeyi, ile müdahaleye uğramadığından emin olmak için MSMQ iletisinin korumak nasıl belirler. İçinde belirtilen <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> özelliği. Varsayılan değer <xref:System.Net.Security.ProtectionLevel.Sign> şeklindedir.  
  
#### <a name="sign-protection-level"></a>Oturum koruma düzeyi  
 Kullanırken dahili olarak oluşturulan sertifikayı kullanarak MSMQ iletisinin imzalanmış `WindowsDomain` kimlik doğrulaması modu veya harici olarak oluşturulmuş bir sertifika kullanırken `Certificate` kimlik doğrulama modu.  
  
#### <a name="sign-and-encrypt-protection-level"></a>İmzalamak ve şifrelemek koruma düzeyi  
 Kullanırken dahili olarak oluşturulan sertifikayı kullanarak MSMQ iletisinin imzalanmış `WindowsDomain` kimlik doğrulama modu veya kullanırken, harici olarak oluşturulan sertifika `Certificate` kimlik doğrulama modu.  
  
 İleti imzalama yanı sıra, MSMQ ileti hedef sıra barındıran alıcı sırası yöneticisinin ait olduğu Active Directory'den elde edilen sertifikanın ortak anahtarı kullanılarak şifrelenir. Gönderme sıra yöneticisini MSMQ İleti Aktarım sırasında şifrelenir sağlar. Alıcı sırası Yöneticisi, kendi iç sertifika özel anahtarını kullanarak MSMQ mesajın şifresini çözer ve Kuyruktaki iletinin (kimliği doğrulanmış ve yetkili değilse) düz metin olarak depolar.  
  
> [!NOTE]
>  İletiyi şifrelemek için Active Directory erişimi gereklidir (`UseActiveDirectory` özelliği <xref:System.ServiceModel.NetMsmqBinding> ayarlanmalıdır `true`) ve her ikisi de kullanılabilir <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate> ve <xref:System.ServiceModel.MsmqAuthenticationMode.WindowsDomain>.  
  
#### <a name="none-protection-level"></a>Hiçbiri koruma düzeyi  
 Bu örtük olduğunda <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> ayarlanır <xref:System.Net.Security.ProtectionLevel.None>. Bu, herhangi bir kimlik doğrulama modları için geçerli bir değer olamaz.  
  
> [!NOTE]
>  MSMQ iletisinin imzalandıysa, MSMQ İleti (iç veya dış) bağımsız olarak, kuyruğun durumunu diğer bir deyişle, kuyruk veya kimliği doğrulanmış eklenmiş bir sertifika ile imzalanmış olup olmadığını denetler.  
  
### <a name="msmq-encryption-algorithm"></a>MSMQ şifreleme algoritması  
 Şifreleme algoritması MSMQ İleti şifrelemek için kullanılacak algoritmayı belirtir. Bu özellik yalnızca kullanılan <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> ayarlanır <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.  
  
 Desteklenen algoritmalar `RC4Stream` ve `AES` ve varsayılan `RC4Stream`.  
  
 Kullanabileceğiniz `AES` yalnızca gönderenin MSMQ 4.0 yüklü varsa algoritması. Ayrıca, hedef sıra MSMQ 4. 0'da barındırılması gerekir.  
  
### <a name="msmq-hash-algorithm"></a>MSMQ karma algoritması  
 Karma algoritması MSMQ iletisinin bir dijital imza oluşturmak için kullanılan algoritmayı belirtir. Alıcı Kuyruk yöneticisi, MSMQ iletinin kimliğini doğrulamak için bu aynı algoritması kullanır. Bu özellik yalnızca kullanılan <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> ayarlanır <xref:System.Net.Security.ProtectionLevel.Sign> veya <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.  
  
 Desteklenen algoritmalar `MD5`, `SHA1`, `SHA256`, ve `SHA512`. Varsayılan, `SHA1` değeridir.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Kuyruklara Genel Bakış](queues-overview.md)
- [Güvenlik Kavramları](../../../../docs/framework/wcf/feature-details/security-concepts.md)
- [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)

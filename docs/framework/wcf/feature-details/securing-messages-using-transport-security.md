---
title: "Taşıma Güveliği Kullanarak İletileri Güvenli Hale Getirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9029771a-097e-448a-a13a-55d2878330b8
caps.latest.revision: "21"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: d40dc1540e4270fc0f80178207edf7b8277d7a73
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="securing-messages-using-transport-security"></a>Taşıma Güveliği Kullanarak İletileri Güvenli Hale Getirme
Bu bölümde, kuyruğa gönderilen iletileri güvenli hale getirmek için kullanabileceğiniz Message Queuing (MSMQ) taşıma güvenliği anlatılmaktadır.  
  
> [!NOTE]
>  Bu konuyu okumadan önce okumanız önerilir [güvenlik kavramları](../../../../docs/framework/wcf/feature-details/security-concepts.md).  
  
 Aşağıdaki çizimde kuyruğa alınan iletişim kullanmanın kavramsal model sağlar [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]. Bu çizim ve terminolojisi Aktarım güvenlik kavramları açıklamak için kullanılır.  
  
 ![Sıraya alınan uygulama diyagramı](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "dağıtılmış-sıra-Şekil")  
  
 Ne zaman gönderme sıraya alınan iletileri kullanarak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ile <xref:System.ServiceModel.NetMsmqBinding>, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ileti MSMQ İleti gövdesi olarak eklenmiş olmasıdır. Taşıma güvenliği MSMQ iletinin tamamını (MSMQ ileti üstbilgilerini veya özellikleri ve ileti gövdesini) güvenliğini sağlar. MSMQ İleti gövdesini olduğu için taşıma güveliği kullanarak da korur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ileti.  
  
 Taşıma güvenliği arkasında anahtar kavram, istemci iletinin hedef sıraya almak için güvenlik gereksinimlerini karşılayacak biçimde sahip olur. Bu, ileti güvenliği, ileti iletiyi alan uygulama için burada güvenlidir olur.  
  
 Taşıma güvenliği kullanarak <xref:System.ServiceModel.NetMsmqBinding> ve <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> MSMQ iletileri güvenliği nasıl etkilediğini aktarım sırasında iletim sırası ve hedef sırası arasında güvenli olduğu anlamına gelir:  
  
-   Emin olmak için ileti imzalama değiştirilmiş değil.  
  
-   İletinin görülen veya değiştirilmiş emin olmak için şifreleme. Bu, önerilir ancak isteğe bağlıdır.  
  
-   Takası iletiyi gönderenin tanımlayan hedef sıra Yöneticisi.  
  
 MSMQ, bağımsız olarak kimlik doğrulaması, hedef sıra bir erişim denetim listesi (ACL) istemci hedef kuyruğa ileti gönderme izni olup olmadığını denetlemek için vardır. Alma işlemini yapan uygulamanın iletiyi hedef sıradan alma izni için de denetlenir.  
  
## <a name="wcf-msmq-transport-security-properties"></a>WCF MSMQ taşıma güvenlik özellikleri  
 MSMQ Windows güvenliği kimlik doğrulaması için kullanır. İstemci tanımlamak için Windows Güvenlik tanımlayıcısı (SID) kullanır ve Active Directory dizin hizmeti sertifika yetkilisi olarak istemci kimlik doğrulaması kullanır. Bu, Active Directory Tümleştirme ile yüklenmesi MSMQ gerektirir. Windows etki alanı SID'si istemciyi tanımlamak için kullanıldığından, hem istemci hem de hizmet aynı Windows etki alanının parçası olduğunda bu güvenlik seçeneği yalnızca anlamlıdır.  
  
 MSMQ Active Directory ile kayıtlı değil ileti sertifikayla ekleme özelliği de sağlar. Bu durumda, ileti ekli sertifikayla imzalanmış sağlar.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]her ikisi de sağlar MSMQ bir parçası olarak bu seçenekler aktarım güvenliği ve bunlar taşıma güvenliği için anahtar Özet.  
  
 Taşıma güvenliği varsayılan olarak açıktır.  
  
 Bu temel bilgiler verildiğinde, aşağıdaki bölümlerde ayrıntı aktarma güvenlik özellikleri birlikte <xref:System.ServiceModel.NetMsmqBinding> ve <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.  
  
#### <a name="msmq-authentication-mode"></a>MSMQ kimlik doğrulama modu  
 <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> İleti güvenliğini sağlamak için Windows etki alanı güvenlik veya bir dış sertifika tabanlı güvenlik kullanılıp kullanılmayacağını belirler. Her iki kimlik doğrulama modda [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sıraya alınan aktarım kanalı kullanan `CertificateValidationMode` hizmet yapılandırmasında belirtilen. Sertifika geçerliliğini denetlemek için kullanılan mekanizma sertifika doğrulama modunu belirtir.  
  
 Taşıma güvenliği açık olduğunda varsayılan ayardır <xref:System.ServiceModel.MsmqAuthenticationMode.WindowsDomain>.  
  
#### <a name="windows-domain-authentication-mode"></a>Windows etki alanı kimlik doğrulama modu  
 Windows güvenliği kullanarak seçimi Active Directory Tümleştirme gerektirir. <xref:System.ServiceModel.MsmqAuthenticationMode.WindowsDomain>Varsayılan Aktarım güvenlik modudur. Bu ayarlandığında [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kanal MSMQ iletisine Windows SID ve Active Directory'den alınan iç sertifikasını kullanır. MSMQ İleti güvenliğini sağlamak için bu bir iç sertifikayı kullanır. Alıcı sırası Yöneticisi'ni arayın ve istemci kimlik doğrulaması için eşleşen bir sertifika bulmak için Active Directory'yi kullanır ve SID aynı zamanda istemci eşleşmesini denetler. Bu kimlik doğrulama adımı bir sertifika varsa yürütüldüğünde, durumunda ya da dahili olarak oluşturulan `WindowsDomain` kimlik doğrulama modu veya durumunda harici olarak oluşturulan `Certificate` kimlik doğrulama modu, hedef sıra olsa bile iletiye ekli kimlik doğrulaması gerektiren olarak işaretlenmemiş.  
  
> [!NOTE]
>  Bir kuyruk oluştururken, sıranın kuyruğa ileti gönderme istemci kimlik doğrulaması gerektirdiğini belirtmek için kimliği doğrulanmış bir sıra olarak sıranın işaretleyebilirsiniz. Bu, kimliği doğrulanmamış bir iletiler kuyrukta kabul edildiğini sağlar.  
  
 SID iliştirilmiş ileti ayrıca istemcinin kuyruğa ileti gönderme yetkisi olduğundan emin olmak için hedef sıra ACL karşı denetlemek için kullanılır.  
  
#### <a name="certificate-authentication-mode"></a>Sertifika kimlik doğrulama modu  
 Sertifika kimlik doğrulaması modunu kullanma seçimi Active Directory Tümleştirme gerektirmez. Aslında, bazı durumlarda, MSMQ (olmadan, Active Directory Tümleştirme) çalışma grubu modunda yüklendiğinde veya ne zaman SOAP Güvenilir Mesajlaşma Protokolü (SRMP) kullanarak izin ver Aktarım Protokolü sıraya ileti, yalnızca gönderme gibi <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate> çalışır.  
  
 Gönderirken bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ile ileti <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate>, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kanal değil attach bir Windows SID'ye MSMQ iletisi. Bu nedenle, hedef sıra ACL için izin vermelidir `Anonymous` sıraya göndermek için kullanıcı erişimi. Alıcı Sıra Yöneticisi MSMQ iletisi sertifikayla imzalanmış olmasına rağmen herhangi bir kimlik doğrulaması gerçekleştirmez olup olmadığını denetler.  
  
 İçinde sertifika talep ve kimlik bilgileri ile doldurulur <xref:System.ServiceModel.ServiceSecurityContext> tarafından [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] taşıma kanalı sıraya alındı. Hizmet, gönderenin kendi kimlik doğrulaması gerçekleştirmek için bu bilgileri kullanabilirsiniz.  
  
### <a name="msmq-protection-level"></a>MSMQ koruma düzeyi  
 Koruma düzeyi, değiştirilmiş değil emin olmak için MSMQ iletisi korumak nasıl belirler. İçinde belirtilen <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> özelliği. Varsayılan değer <xref:System.Net.Security.ProtectionLevel.Sign> şeklindedir.  
  
#### <a name="sign-protection-level"></a>Oturum koruma düzeyi  
 MSMQ iletisi kullanırken dahili olarak oluşturulan sertifika kullanılarak imzalanmıştır `WindowsDomain` kimlik doğrulama modu veya kullanırken, harici olarak oluşturulan bir sertifika `Certificate` kimlik doğrulama modu.  
  
#### <a name="sign-and-encrypt-protection-level"></a>İmzalamak ve şifrelemek koruma düzeyi  
 MSMQ iletisi kullanırken dahili olarak oluşturulan sertifika kullanılarak imzalanmıştır `WindowsDomain` kimlik doğrulama modu veya kullanırken, harici olarak oluşturulan sertifika `Certificate` kimlik doğrulama modu.  
  
 İleti imzalama yanı sıra, MSMQ ileti hedef sıra barındıran alıcı sırası yöneticisinin ait olduğu Active Directory'den elde edilen sertifikanın ortak anahtarı kullanılarak şifrelenir. Gönderme sırası manager MSMQ iletisi aktarım sırasında şifrelenir sağlar. Alıcı Sıra Yöneticisi kendi iç sertifika özel anahtarı kullanılarak MSMQ mesajın şifresini çözer ve düz metin olarak sırasındaki ileti (kimliği doğrulanmış ve yetkilendirilmiş varsa) depolar.  
  
> [!NOTE]
>  İletiyi şifrelemek için Active Directory erişimi gereklidir (`UseActiveDirectory` özelliği <xref:System.ServiceModel.NetMsmqBinding> ayarlanmalıdır `true`) ve ikisi ile kullanılabilir <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate> ve <xref:System.ServiceModel.MsmqAuthenticationMode.WindowsDomain>.  
  
#### <a name="none-protection-level"></a>Hiçbiri koruma düzeyi  
 Bu kapsanan zaman <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> ayarlanır <xref:System.Net.Security.ProtectionLevel.None>. Bu diğer kimlik doğrulama modu için geçerli bir değer olamaz.  
  
> [!NOTE]
>  MSMQ iletisi kaydolduysanız MSMQ İleti (iç veya dış) bağımsız olarak kuyruğun durumunu diğer bir deyişle, kuyruk veya kimliği doğrulanmış ekli sertifikayla imzalanmış olup olmadığını denetler.  
  
### <a name="msmq-encryption-algorithm"></a>MSMQ şifreleme algoritması  
 Şifreleme algoritması hattaki MSMQ iletiyi şifrelemek için kullanılacak algoritmayı belirtir. Bu özellik yalnızca kullanılır <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> ayarlanır <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.  
  
 Desteklenen algoritmaları `RC4Stream` ve `AES` ve varsayılan değer `RC4Stream`.  
  
 Kullanabileceğiniz `AES` yalnızca gönderenin MSMQ 4.0 yüklü varsa algoritması. Ayrıca, hedef sıra MSMQ 4. 0'da barındırılması gerekir.  
  
### <a name="msmq-hash-algorithm"></a>MSMQ karma algoritması  
 Karma algoritması MSMQ iletinin dijital imzasını oluşturmak için kullanılan algoritmayı belirtir. Alıcı Sıra Yöneticisi MSMQ iletinin kimliğini doğrulamak için bu aynı algoritması kullanır. Bu özellik yalnızca kullanılır <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> ayarlanır <xref:System.Net.Security.ProtectionLevel.Sign> veya <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.  
  
 Desteklenen algoritmaları `MD5`, `SHA1`, `SHA256`, ve `SHA512`. Varsayılan, `SHA1` değeridir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Message Queuing](http://msdn.microsoft.com/en-us/ff917e87-05d5-478f-9430-0f560675ece1)  
 [Güvenlik Kavramları](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
 [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)

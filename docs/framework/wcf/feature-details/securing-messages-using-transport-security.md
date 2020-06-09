---
title: Taşıma Güveliği Kullanarak İletileri Güvenli Hale Getirme
ms.date: 03/30/2017
ms.assetid: 9029771a-097e-448a-a13a-55d2878330b8
ms.openlocfilehash: 7d160f6f0d1d29e34ca3365501b86d1a736de67b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84589948"
---
# <a name="securing-messages-using-transport-security"></a>Taşıma Güveliği Kullanarak İletileri Güvenli Hale Getirme
Bu bölümde, bir kuyruğa gönderilen iletileri güvenli hale getirmek için kullanabileceğiniz Message Queuing (MSMQ) aktarım güvenliği açıklanmaktadır.  
  
> [!NOTE]
> Bu konuyu okumadan önce [güvenlik kavramlarını](security-concepts.md)okumanız önerilir.  
  
 Aşağıdaki çizimde Windows Communication Foundation (WCF) kullanarak sıraya alınmış iletişimin kavramsal bir modeli verilmiştir. Bu çizim ve terminoloji, taşıma güvenlik kavramlarını açıklamak için kullanılır.  
  
 ![Kuyruğa alınmış uygulama diyagramı](media/distributed-queue-figure.jpg "Dağıtılmış kuyruk-şekil")  
  
 İle WCF kullanarak sıraya alınan iletileri gönderirken <xref:System.ServiceModel.NetMsmqBinding> , WCF ILETISI msmq iletisinin bir gövdesi olarak eklenir. Taşıma güvenliği tüm MSMQ iletisini (MSMQ ileti üstbilgileri veya özellikleri ve ileti gövdesi) korur. MSMQ iletisinin gövdesi olduğundan, taşıma güvenliği kullanmak WCF iletisini de korur.  
  
 Aktarım güvenliği arkasındaki anahtar kavramı, istemcinin hedef sıraya ileti almak için güvenlik gereksinimlerini karşılamasına olanak sağlar. Bu, iletinin iletiyi alan uygulama için güvenliğinin sağlandığı Ileti güvenliğinin aksine olur.  
  
 İle aktarım güvenliği <xref:System.ServiceModel.NetMsmqBinding> , <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> MSMQ iletilerinin iletim kuyruğu ile güvenli hale getirilmesi gereken hedef sıra arasında nasıl güvenli hale getirilçalıştığını etkiler:  
  
- Üzerinde oynanmadığından emin olmak için ileti imzalanıyor.  
  
- Görmemesini veya üzerinde oynanmamasını sağlamak için iletiyi şifreleme. Bu önerilir, ancak isteğe bağlıdır.  
  
- Red olmayan bir iletinin gönderisini tanımlayan hedef kuyruk yöneticisi.  
  
 MSMQ 'da, kimlik doğrulamasından bağımsız olarak, hedef sıranın, istemcinin iletiyi hedef sıraya gönderme izni olup olmadığını denetlemek için bir erişim denetim listesi (ACL) vardır. Alıcı uygulama Ayrıca, hedef sıradan iletiyi alma izni için de denetlenir.  
  
## <a name="wcf-msmq-transport-security-properties"></a>WCF MSMQ taşıma güvenlik özellikleri  
 MSMQ, kimlik doğrulaması için Windows güvenliği kullanır. İstemciyi tanımlamak için Windows güvenlik tanımlayıcısını (SID) kullanır ve istemcinin kimliğini doğrularken sertifika yetkilisi olarak Active Directory dizin hizmetini kullanır. Bu, Active Directory tümleştirmeyle MSMQ yüklenmesini gerektirir. İstemciyi tanımlamak için Windows etki alanı SID 'SI kullanıldığından, bu güvenlik seçeneği yalnızca istemci ve hizmet aynı Windows etki alanının parçası olduğunda anlamlıdır.  
  
 MSMQ Ayrıca, Active Directory kayıtlı olmayan iletiyle bir sertifika ekleyebilme olanağı da sağlar. Bu durumda, iletinin ekli sertifika kullanılarak imzalanmış olmasını sağlar.  
  
 WCF, MSMQ aktarım güvenliği 'nin bir parçası olarak her iki seçeneği de sağlar ve aktarım güvenliği için anahtar özetlerdir.  
  
 Varsayılan olarak, taşıma güvenliği açıktır.  
  
 Bu temel bilgiler söz konusu olduğunda, aşağıdaki bölümlerde ve ile paketlenmiş aktarım güvenliği özellikleri ayrıntılı olarak sunulur <xref:System.ServiceModel.NetMsmqBinding> <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> .  
  
#### <a name="msmq-authentication-mode"></a>MSMQ kimlik doğrulama modu  
 <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>İletiyi güvenli hale getirmek Için Windows etki alanı güvenliğinin veya dış sertifika tabanlı güvenliğin kullanılıp kullanılmayacağını belirler. Her iki kimlik doğrulama modunda de, kuyruğa alınan aktarım kanalı `CertificateValidationMode` hizmet yapılandırmasında belirtilen ' ı kullanır. Sertifika doğrulama modu, sertifikanın geçerliliğini denetlemek için kullanılan mekanizmayı belirtir.  
  
 Taşıma güvenliği açık olduğunda, varsayılan ayar olur <xref:System.ServiceModel.MsmqAuthenticationMode.WindowsDomain> .  
  
#### <a name="windows-domain-authentication-mode"></a>Windows etki alanı kimlik doğrulama modu  
 Windows güvenliği kullanma seçeneği Active Directory tümleştirme gerektirir. <xref:System.ServiceModel.MsmqAuthenticationMode.WindowsDomain>, varsayılan aktarım güvenliği modudur. Bu ayarlandığında, WCF kanalı Windows SID 'sini MSMQ iletisine iliştirir ve Active Directory elde edilen iç sertifikasını kullanır. MSMQ, iletinin güvenliğini sağlamak için bu iç sertifikayı kullanır. Alma kuyruğu Yöneticisi, istemcinin kimliğini doğrulamak için eşleşen bir sertifika aramak ve bulmak için Active Directory kullanır ve SID 'nin aynı zamanda istemciyle eşleşip eşleşmediğini denetler. Bu kimlik doğrulama adımı, kimlik doğrulama modu için dahili olarak oluşturulan `WindowsDomain` veya kimlik doğrulama modunda harici olarak oluşturulan bir sertifika, `Certificate` hedef sıra kimlik doğrulaması gerektiren olarak işaretlenmese bile iletiye iliştirildiyse yürütülür.  
  
> [!NOTE]
> Bir kuyruk oluştururken, sıranın sıraya ileti göndermesi gerektiğini belirtmek için kuyruğu kimliği doğrulanmış bir sıra olarak işaretleyebilirsiniz. Bu, kuyrukta hiçbir kimliği doğrulanmamış ileti kabul edilmesini sağlar.  
  
 İleti ile birlikte gelen SID, istemcinin kuyruğa ileti gönderme yetkisine sahip olduğundan emin olmak için hedef sıranın ACL 'sine karşı kontrol etmek için de kullanılır.  
  
#### <a name="certificate-authentication-mode"></a>Sertifika kimlik doğrulama modu  
 Sertifika kimlik doğrulama modunu kullanma seçeneği Active Directory tümleştirme gerektirmez. Aslında, MSMQ çalışma grubu modunda (Active Directory tümleştirme olmadan) veya iletileri kuyruğa göndermek için SOAP Güvenilir Mesajlaşma Protokolü (SRMP) aktarım protokolü kullanılırken, bazı durumlarda, yalnızca <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate> işe yarar.  
  
 İle bir WCF iletisi gönderilirken <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate> , WCF kanalı MSMQ iletisine bir Windows SID 'si eklemez. Bu nedenle, hedef kuyruk ACL 'SI, `Anonymous` Kullanıcı erişiminin sıraya gönderilmesi için izin vermelidir. Alma kuyruğu Yöneticisi MSMQ iletisinin sertifikayla imzalanıp imzalanmadığını denetler, ancak herhangi bir kimlik doğrulaması gerçekleştirmez.  
  
 Talepleri ve kimlik bilgilerini içeren sertifika, <xref:System.ServiceModel.ServiceSecurityContext> WCF sıraya alınan aktarım kanalında tarafından doldurulur. Hizmet, gönderenin kimlik doğrulamasını gerçekleştirmek için bu bilgileri kullanabilir.  
  
### <a name="msmq-protection-level"></a>MSMQ koruma düzeyi  
 Koruma düzeyi, ile oynanmamasını sağlamak için MSMQ iletisini nasıl koruyabileceğinizi belirler. Bu, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> özelliğinde belirtilmiştir. Varsayılan değer: <xref:System.Net.Security.ProtectionLevel.Sign>.  
  
#### <a name="sign-protection-level"></a>İmza koruma düzeyi  
 MSMQ iletisi, kimlik doğrulama modu kullanılırken `WindowsDomain` kimlik doğrulama modu veya harici olarak oluşturulan bir sertifika kullanıldığında dahili olarak oluşturulan sertifika kullanılarak imzalanır `Certificate` .  
  
#### <a name="sign-and-encrypt-protection-level"></a>Koruma düzeyini imzalama ve şifreleme  
 MSMQ iletisi, kimlik doğrulama modu `WindowsDomain` kullanılırken kimlik doğrulama modu veya dışarıdan oluşturulan sertifika kullanılırken dahili olarak oluşturulan sertifika kullanılarak imzalanır `Certificate` .  
  
 İletiyi imzalamaya ek olarak, MSMQ iletisi, hedef kuyruğu barındıran alma kuyruğu yöneticisine ait olan Active Directory tarafından alınan sertifikanın ortak anahtarı kullanılarak şifrelenir. Gönderme kuyruğu Yöneticisi, MSMQ iletisinin aktarım sırasında şifrelenmesini sağlar. Alma kuyruğu Yöneticisi, iç sertifikasının özel anahtarını kullanarak MSMQ iletisinin şifresini çözer ve iletiyi açık metin halinde kuyruktaki (kimliği doğrulanmış ve yetkilendirirse) depolar.  
  
> [!NOTE]
> İletiyi şifrelemek için Active Directory erişim gerekir ( `UseActiveDirectory` öğesinin özelliği <xref:System.ServiceModel.NetMsmqBinding> olarak ayarlanmalıdır `true` ) ve hem hem de ile kullanılabilir <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate> <xref:System.ServiceModel.MsmqAuthenticationMode.WindowsDomain> .  
  
#### <a name="none-protection-level"></a>Hiçbiri koruma düzeyi  
 Bu, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> olarak ayarlandığında kapsanır <xref:System.Net.Security.ProtectionLevel.None> . Bu, diğer herhangi bir kimlik doğrulama modu için geçerli bir değer olamaz.  
  
> [!NOTE]
> MSMQ iletisi imzalanmışsa, MSMQ iletinin, sıranın durumundan (iç veya dış) bağımsız olarak imzalanıp imzalanmadığını, yani kimliği doğrulanmış sırayı denetler.  
  
### <a name="msmq-encryption-algorithm"></a>MSMQ şifreleme algoritması  
 Şifreleme algoritması, kabloda MSMQ iletisini şifrelemek için kullanılacak algoritmayı belirtir. Bu özellik yalnızca <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> olarak ayarlandıysa kullanılır <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> .  
  
 Desteklenen algoritmalar `RC4Stream` ve `AES` varsayılandır `RC4Stream` .  
  
 `AES`Algoritmayı yalnızca GÖNDERICI MSMQ 4,0 yüklüyse kullanabilirsiniz. Ayrıca, hedef sıra MSMQ 4,0 üzerinde barındırılmalıdır.  
  
### <a name="msmq-hash-algorithm"></a>MSMQ karma algoritması  
 Karma algoritması, MSMQ iletisinin dijital imzasını oluşturmak için kullanılan algoritmayı belirtir. Alma kuyruğu Yöneticisi, MSMQ iletisinin kimliğini doğrulamak için aynı algoritmayı kullanır. Bu özellik yalnızca <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> veya olarak ayarlandıysa kullanılır <xref:System.Net.Security.ProtectionLevel.Sign> <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> .  
  
 Desteklenen algoritmalar,, `MD5` `SHA1` `SHA256` ve `SHA512` . Varsayılan değer: `SHA1`.

 MD5/SHA1 ile ilgili çarpışma sorunları nedeniyle, Microsoft SHA256 veya daha iyi bir performans öneriyor.
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kuyruklar Genel Bakış](queues-overview.md)
- [Güvenlik kavramları](security-concepts.md)
- [Hizmet ve İstemcileri Güvenli Hale Getirme](securing-services-and-clients.md)

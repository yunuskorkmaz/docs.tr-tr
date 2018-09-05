---
title: Bilgileri Açıklama
ms.date: 03/30/2017
ms.assetid: 4064c89f-afa6-444a-aa7e-807ef072131c
ms.openlocfilehash: 057984dada86019cd8e0a619523d717d0045062f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43508016"
---
# <a name="information-disclosure"></a>Bilgileri Açıklama
Bilgilerin açıklanması, bir saldırganın bir sistem hakkında değerli bilgiler sağlar. Bu nedenle, her zaman ve mi kötü niyetli bir kullanıcı tarafından kullanılabilir, devamlılığımız bilgiler göz önünde bulundurun. Aşağıdaki olası bilgi ifşası saldırıları listeler ve her risk azaltma işlemleri sağlar.  
  
## <a name="message-security-and-http"></a>İleti güvenliği ve HTTP  
 Bir HTTP Aktarım katmanı üzerinden ileti düzeyi güvenliği kullanıyorsanız, ileti düzeyi güvenliği HTTP üst bilgilerini korumaz dikkat edin. HTTP üst bilgilerini korumak için tek yolu, HTTP yerine HTTPS aktarımı kullanmaktır. HTTPS aktarımı Güvenli Yuva Katmanı (SSL) protokolü kullanılarak şifrelenmesi HTTP üst bilgileri de dahil olmak üzere tüm ileti, neden olur.  
  
## <a name="policy-information"></a>İlke bilgileri  
 İlke güvende tutmanın özellikle nerede ilkede hassas verilen belirtecin gereksinimleri veya belirteci veren bilgi ifşa Federasyon senaryolarında önemlidir. Bu gibi durumlarda verilen belirteç koymak için talep türü gibi hizmeti hakkında bilgi almak veya kötü amaçlı belirteci verenler için istemcilerin yeniden yönlendirme saldırganların engel olmak için Federasyon hizmet uç noktası İlkesi güvenliğini sağlamak için önerilir. Örneğin, bir saldırganın federasyon güven zincirinde bir adam-de-ortadaki adam saldırısı yürütülen bir veren sonlandırmak için yapılandırarak kullanıcı adı/parola çiftleri keşfedin. İlke alma işlemi aracılığıyla bağlantıları elde Federasyon istemcilerinin elde edilen bir federasyon güven zincirinde verenler güvendikleri doğrulamanız önerilir. Federasyon senaryoları hakkında daha fazla bilgi için bkz. [Federasyon](../../../../docs/framework/wcf/feature-details/federation.md).  
  
## <a name="memory-dumps-can-reveal-claim-information"></a>Bellek dökümleri talep bilgilerini ortaya koyabilir  
 Bir uygulama başarısız olduğunda, günlük dosyaları gibi Dr tarafından üretilen olanlar gibi. Watson, talep bilgilerini içerebilir. Bu bilgiler gibi destek ekipleri diğer varlıklara verilebilir; Aksi takdirde, özel veri içeren talep bilgileri de dışarı aktarılır. Bu günlük dosyaları için bilinmeyen varlıkların göndererek değil azaltabilirsiniz. Daha fazla bilgi için [Windows Server 2003](https://go.microsoft.com/fwlink/?LinkId=89160).  
  
## <a name="endpoint-addresses"></a>Uç Noktası Adresleri  
 Bir uç nokta adresi bir uç noktasıyla iletişim için gereken bilgileri içerir. SOAP güvenliği, tam olarak bir istemci ve sunucu arasında bir simetrik anahtar anlaşması için değiştirilen güvenlik anlaşma iletileri adresi eklemeniz gerekir. Güvenlik görüşmeleri önyükleme işlemi olduğundan, bu işlem sırasında adres üstbilgileri şifrelenemez. Bu nedenle, adresi herhangi bir gizli veri içermemelidir; Aksi takdirde, bilgi ifşası saldırılarına yol açar.  
  
## <a name="certificates-transferred-unencrypted"></a>Sertifikaları şifrelenmemiş aktarılan  
 Bir istemcinin kimliğini doğrulamak için bir X.509 sertifikası kullandığınızda, sertifikanın SOAP üstbilgisi içinde açıkta aktarılır. Olası kişisel bilgileri (PII) ifşaatı bunun farkında olun. Bunun için bir sorun değildir `TransportWithMessageCredential` modu, tüm ileti aktarım düzeyi güvenlik ile şifrelenir burada.  
  
## <a name="service-references"></a>Hizmet başvuruları  
 Bir hizmet başvurusu, başka bir hizmete bir başvurudur. Örneğin, bir hizmet, bir istemcinin bir işlemi sırasında bir hizmet başvurusu iletebilir. Hizmet başvurusunu da ile kullanılan bir *kimlik doğrulama güven*, hedef sorumlunun kimlik gibi uygulama verileri veya hedef kimlik bilgilerini açığa çıkarmaktan önce sağlar. bir iç bileşeni. Uzak güven kimlik doğrulanamıyor veya yanlış, gönderen veri kendisi, uygulama veya kullanıcıya tehlikeye atabilecek duyurulmuştur emin olmanız gerekir.  
  
 Risk azaltma işlemleri şunlardır:  
  
-   Hizmet başvurularını güvenilir olarak kabul edilir. Bunlar üzerinde oynanmadığını değil emin olmak için hizmet başvurusu örnekleri aktarma zaman dikkatli olun.  
  
-   Bazı uygulamalar, uzak konak tarafından kanıtlanmış hizmet başvurusu ve güven verilerini dayalı güven etkileşimli kurma izin veren bir kullanıcı deneyimi sunabilir. WCF böyle bir özellik için genişletilebilirlik noktaları sağlar, ancak kullanıcı bunları uygulanan gerekir.  
  
## <a name="ntlm"></a>NTLM  
 Varsayılan olarak, Windows etki alanı ortamında kimliğini doğrulamak ve kullanıcılara yetki vermek için Kerberos protokolü Windows kimlik doğrulaması kullanır. Kerberos protokolü için herhangi bir nedenle kullanılamıyorsa, NT LAN Manager (NTLM) bir geri dönüş olarak kullanılır. Ayarlayarak bu davranışı devre dışı bırakabilirsiniz <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> özelliğini `false`. NTLM izin verirken dikkat edilmesi gereken konular şunlardır:  
  
-   NTLM için istemci kullanıcı adını gösterir. Kullanıcı adı gizli tutulması gerekiyorsa, ardından ayarlayın `AllowNTLM` bağlama özelliği `false`.  
  
-   NTLM kimlik doğrulaması sağlamaz. Bu nedenle, istemci bir kimlik doğrulama protokolü NTLM kullandığınızda, doğru hizmet ile iletişim kurduğunu garanti edemez.  
  
### <a name="specifying-client-credentials-or-invalid-identity-forces-ntlm-usage"></a>İstemci kimlik bilgileri veya geçersiz kimlik zorlar NTLM kullanımını belirtme  
 Bir istemci oluştururken, istemci kimlik bilgileri olmadan bir etki alanı adı belirterek veya bir geçersiz bir sunucu kimliğini belirterek Kerberos protokolü yerine kullanılacak NTLM neden (varsa `AlllowNtlm` özelliği `true`). NTLM kimlik doğrulaması yapmak için bilgi büyük olasılıkla partilere açık.  
  
 Örneğin, aşağıdaki Visual C# kodu gösterildiği gibi Windows istemci kimlik bilgileri olmadan bir etki alanı adı belirtmek mümkündür.  
  
```  
MyChannelFactory.Credentials.Windows.ClientCredential = new System.Net.NetworkCredential("username", "password");  
```  
  
 Kod, bir etki alanı adı belirtmiyor ve NTLM kullanılır.  
  
 Etki alanı belirtildi, ancak geçersiz hizmet asıl adı uç nokta kimlik özelliği kullanılarak belirtilir NTLM kullanılır. Uç nokta kimliğini nasıl belirtildiğine hakkında daha fazla bilgi için bkz. [kimlik doğrulama ile hizmet kimliği](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Güvenlik Konuları](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [Ayrıcalıkların Yükseltilmesi](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)  
 [Hizmet Reddi](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 [İzinsiz Değişiklik](../../../../docs/framework/wcf/feature-details/tampering.md)  
 [Desteklenmeyen Senaryolar](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)  
 [Yeniden Yürütme Saldırıları](../../../../docs/framework/wcf/feature-details/replay-attacks.md)

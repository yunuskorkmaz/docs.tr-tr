---
title: Bilgileri Açıklama
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4064c89f-afa6-444a-aa7e-807ef072131c
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c603032e175fd8390abea2db625321d3e3558c1a
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="information-disclosure"></a>Bilgileri Açıklama
Bilgilerin açığa çıkmasına bir sistemi hakkında değerli bilgiler sağlamasına olanak sağlar. Bu nedenle, her zaman ve ortaya bilgiler, kötü niyetli bir kullanıcı tarafından kullanılıp kullanılamayacağını göz önünde bulundurun. Aşağıdaki olası bilgileri açığa saldırıları listeler ve bunları azaltmanın yollarını her sağlar.  
  
## <a name="message-security-and-http"></a>İleti güvenliği ve HTTP  
 Bir HTTP Aktarım katmanı üzerinden ileti düzeyi güvenlik kullanıyorsanız, ileti düzeyi güvenlik HTTP üstbilgileri korumaz unutmayın. HTTP üst bilgilerini korumak için tek yolu, HTTP yerine HTTPS aktarımı kullanmaktır. HTTPS aktarımı Güvenli Yuva Katmanı (SSL) protokolü kullanılarak şifrelenmesi için HTTP üstbilgileri dahil olmak üzere tüm iletinin neden olur.  
  
## <a name="policy-information"></a>İlke bilgilerini  
 İlke güvenliğini sağlamanın özellikle hassas verilen belirteç gereksinimleri veya belirteç verenin bilgileri ilkesinde Burada sunulan Federasyon senaryolarında önemlidir. Bu durumlarda verilen belirteç koymak için talep türü gibi hizmeti hakkında bilgi almak veya istemciler için kötü amaçlı belirteci verenler yönlendirme saldırganların önlemek için federasyon hizmetinin İlkesi uç nokta güvenliğini sağlamak için önerilir. Örneğin, bir saldırganın man-in--middle saldırı yürütülen bir veren sonlandırmak için federe güven zinciri yapılandırarak kullanıcı adı/parola çiftlerini bulmak. Ayrıca, bağlantıları ilke alma işlemi aracılığıyla elde Federasyon istemcileri edinilen federe güven zincirinde verenler güven doğrulamanız önerilir. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] Federasyon senaryolarında bkz [Federasyon](../../../../docs/framework/wcf/feature-details/federation.md).  
  
## <a name="memory-dumps-can-reveal-claim-information"></a>Bellek dökümlerini talep bilgilerini ortaya çıkarabilir  
 Bir uygulama başarısız olduğunda, günlük dosyalarını olanlar Dr tarafından üretilen gibi. Watson, talep bilgilerini içerebilir. Bu bilgileri destek ekiplerini gibi diğer varlıklar için verilebilir; Aksi takdirde, özel verileri içeren talep bilgileri de aktarılır. Bu günlük dosyaları için bilinmeyen varlıkların göndererek değil azaltabilirsiniz. Daha fazla bilgi için bkz: [Windows Server 2003](http://go.microsoft.com/fwlink/?LinkId=89160).  
  
## <a name="endpoint-addresses"></a>Uç Noktası Adresleri  
 Bir uç nokta adresi bir uç nokta ile iletişim kurmak için gereken bilgileri içerir. SOAP Güvenliği tam olarak bir istemci ve sunucu arasında bir simetrik anahtar anlaşması için alınıp verilen güvenlik anlaşma iletileri adresi içermesi gerekir. Güvenlik görüşmeleri önyükleme bir işlem olduğundan, adres üstbilgileri bu işlem sırasında şifrelenemez. Bu nedenle, adres gizli herhangi bir veri içermemesi gerekir; Aksi takdirde, bilgi ifşası saldırılara yol açar.  
  
## <a name="certificates-transferred-unencrypted"></a>Sertifikaları şifrelenmemiş aktarılan  
 Bir istemci kimlik doğrulaması için bir X.509 sertifikası kullandığınızda, sertifika temiz SOAP üstbilgisi içine aktarılır. Olası bir kişisel bilgileri (PII) açığa çıkması bunun farkında olun. Bu bir sorun için değil `TransportWithMessageCredential` burada tüm ileti şifrelenir ile aktarım düzeyinde güvenlik modu.  
  
## <a name="service-references"></a>Hizmet başvuruları  
 Hizmet başvurusu başka bir hizmet başvurudur. Örneğin, bir hizmet bir işlem sırasında istemciye hizmet başvurusu iletebilir. Hizmet başvurusu ayrıca ile kullanılan bir *kimlik doğrulayıcı güven*, uygulama verileri veya hedef için kimlik bilgileri gibi bilgileri açıklamadan önce hedef asıl kimliğini sağlar iç bir bileşenidir. Uzak güven kimliği doğrulanamıyor veya yanlış gönderen hiçbir veri kendisi, uygulama veya kullanıcıya tehlikeye atabilecek duyurulmuştur olmanız gerekir.  
  
 Azaltıcı Etkenler aşağıdakileri içerir:  
  
-   Hizmet başvuruları güvenilir olarak kabul edilir. Bunlar ile oynanmadığını emin olmak için hizmet başvurusu örnekleri aktarma zaman dikkatli olun.  
  
-   Bazı uygulamalar, uzak ana bilgisayar tarafından kanıtlanmış hizmet başvurusu ve güven verilerini dayalı güvenin etkileşimli kurma izin veren bir kullanıcı deneyimi sunabilir. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Genişletilebilirlik noktaları gibi bir tesis ancak kullanıcı için gereken bunları uygulanan sağlar.  
  
## <a name="ntlm"></a>NTLM  
 Varsayılan olarak, Windows etki alanı ortamında kimliğini doğrulamak ve kullanıcılara yetki vermek için Kerberos protokolünü Windows kimlik doğrulaması kullanır. Kerberos protokolü için herhangi bir nedenle kullanılamaz, NT LAN Yöneticisi (NTLM) bir geri dönüş olarak kullanılır. Ayarlayarak bu davranışı devre dışı bırakabilirsiniz <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> özelliğine `false`. NTLM izin verirken dikkat edilmesi gereken konular şunlardır:  
  
-   NTLM istemci kullanıcı adı gösterir. Kullanıcı adı gizli tutulması gerekiyorsa, daha sonra ayarlamak `AllowNTLM` özelliği için bağlama üzerinde `false`.  
  
-   NTLM kimlik doğrulaması sağlamaz. Bu nedenle, istemci, NTLM kimlik doğrulama protokolü olarak kullandığınızda, doğru hizmete bağlanıyor garanti edemez.  
  
### <a name="specifying-client-credentials-or-invalid-identity-forces-ntlm-usage"></a>İstemci kimlik bilgileri veya geçersiz kimlik zorlar NTLM kullanımını belirtme  
 Bir istemci oluştururken, istemci kimlik bilgileri bir etki alanı adı olmadan belirterek veya geçersiz sunucu kimlik belirtmeyi yerine Kerberos protokolünün kullanılması için NTLM neden olur (varsa `AlllowNtlm` özelliği ayarlanmış `true`). NTLM kimlik doğrulaması yapmak için bilgi potansiyel olarak bildirilen.  
  
 Örneğin, aşağıdaki Visual C# kodu gösterildiği gibi bir etki alanı adı olmadan Windows istemci kimlik bilgileri belirtmek mümkündür.  
  
```  
MyChannelFactory.Credentials.Windows.ClientCredential = new System.Net.NetworkCredential("username", "password");  
```  
  
 Kod bir etki alanı adı belirtmiyor ve bu nedenle NTLM kullanılır.  
  
 Etki alanı belirtildi, ancak geçersiz hizmet asıl adı uç noktası kimlik özelliği kullanılarak belirtilir NTLM kullanılır. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] uç noktası kimlik belirtilen bkz [hizmet kimliği ve kimlik doğrulama](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Güvenlik Konuları](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [Ayrıcalıkların Yükseltilmesi](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)  
 [Hizmet Reddi](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 [İzinsiz Değişiklik](../../../../docs/framework/wcf/feature-details/tampering.md)  
 [Desteklenmeyen Senaryolar](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)  
 [Yeniden Yürütme Saldırıları](../../../../docs/framework/wcf/feature-details/replay-attacks.md)

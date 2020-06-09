---
title: Bilgileri Açıklama
ms.date: 03/30/2017
ms.assetid: 4064c89f-afa6-444a-aa7e-807ef072131c
ms.openlocfilehash: a58ac4dd3715052031c7fb5c1da480c0d01396ea
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596870"
---
# <a name="information-disclosure"></a>Bilgileri Açıklama

Bilgilerin açığa çıkması, saldırganın bir sistem hakkında değerli bilgiler sağlamasına olanak sağlar. Bu nedenle, hangi bilgileri öğrendiklerinizi ve kötü niyetli bir kullanıcı tarafından kullanılıp kullanılamayacağını her zaman düşünün. Aşağıda olası bilgilerin açığa çıkması saldırıları listelenmekte ve her biri için azaltmalar sunulmaktadır.

## <a name="message-security-and-http"></a>İleti güvenliği ve HTTP

Bir HTTP aktarım katmanı üzerinden ileti düzeyinde güvenlik kullanıyorsanız, ileti düzeyi güvenliğin HTTP üstbilgilerini korumadığı farkında olun. HTTP üstbilgilerini korumanın tek yolu HTTP yerine HTTPS taşıması kullanmaktır. HTTPS taşıması HTTP üstbilgileri dahil olmak üzere iletinin tamamının Güvenli Yuva Katmanı (SSL) protokolü kullanılarak şifrelenmesini sağlar.

## <a name="policy-information"></a>İlke bilgileri

İlkenin güvenli tutulması, özellikle hassas verilen belirteç gereksinimlerinin veya belirteç verenin bilgilerinin ilkede açığa çıkarılan Federasyon senaryolarında önemlidir. Bu durumlarda, saldırganların hizmet hakkında, verilen belirtece yerleştirilecek talepler türü veya istemcileri kötü amaçlı belirteç verenler için yeniden yönlendirme gibi bilgileri almasını engellemek için Federasyon Hizmeti 'nin ilke uç noktasının güvenli hale getirilmesine yönelik olması önerilir. Örneğin, bir saldırgan, Federasyon güven zincirini, ortadaki adam saldırısı gerçekleştiren bir verende sona erecek şekilde yeniden yapılandırarak Kullanıcı adı/parola çiftlerini bulabilir. Ayrıca, ilke alma yoluyla bağlamalarını elde eden Federasyon istemcilerinin, edinilen federasyon güven zincirindeki verenler için güvendiklerini doğrulayın. Federasyon senaryoları hakkında daha fazla bilgi için bkz. [Federasyon](federation.md).

## <a name="memory-dumps-can-reveal-claim-information"></a>Bellek dökümleri, talep bilgilerini açığa çıkarır

Bir uygulama başarısız olduğunda, Dr. Watson tarafından üretilen gibi günlük dosyaları talep bilgilerini içerebilir. Bu bilgiler, destek takımları gibi diğer varlıklara aktarılmamalıdır; Aksi takdirde, özel verileri içeren talep bilgileri de verilir. Günlük dosyalarını bilinmeyen varlıklara göndermemek için bunu azaltabilirsiniz.

## <a name="endpoint-addresses"></a>Uç Noktası Adresleri

Uç nokta adresi, bir uç nokta ile iletişim kurmak için gereken bilgileri içerir. SOAP Güvenliği, istemci ile sunucu arasında bir simetrik anahtar üzerinde anlaşmak için değiştirilen güvenlik anlaşması iletilerinde tam olarak adresi içermelidir. Güvenlik anlaşması bir önyükleme işlemi olduğundan, bu işlem sırasında adres üst bilgileri şifrelenemez. Bu nedenle, adres hiçbir gizli veri içermemelidir; Aksi takdirde, bilgilerin açığa çıkması saldırılarına yol açar.

## <a name="certificates-transferred-unencrypted"></a>Sertifikalar şifrelenmemiş olarak aktarıldı

Bir istemcinin kimliğini doğrulamak için bir X. 509.952 sertifikası kullandığınızda, sertifika SOAP üstbilgisinin içinde açık olarak aktarılır. Bunu, kişisel olarak tanımlanabilen bilgileri (PII) açığa çıkabilecek bir açıklama olarak unutmayın. Bu, mod için bir sorun değildir `TransportWithMessageCredential` ; burada iletinin tamamı aktarım düzeyi güvenlik ile şifrelenir.

## <a name="service-references"></a>Hizmet başvuruları

Hizmet başvurusu, başka bir hizmete başvurudur. Örneğin, bir hizmet, bir işlem sırasında bir istemciye hizmet başvurusu geçirebilir. Hizmet başvurusu, uygulama verileri veya hedef kimlik bilgileri gibi bilgileri kapatmadan önce hedef Sorumlunun kimliğini sağlayan bir *güven Kimliği Doğrulayıcısı*ile de kullanılır. Uzak güven kimliği doğrulanamazsa veya yanlışsa, gönderici kendisini, uygulamayı veya kullanıcıyı tehlikeye atabilecek hiçbir veri açıklanmamalıdır.

Azaltmaları şunları içerir:

- Hizmet başvurularının güvenilir olduğu varsayılır. Bakım yapılmamasını sağlamak için hizmet başvuru örneklerini aktarırken dikkatli olun.

- Bazı uygulamalar, hizmet başvurusunda bulunan verilere ve uzak ana bilgisayar tarafından kanıtlanan güven verilerine göre etkileşimli güven oluşturulmasına izin veren bir kullanıcı deneyimi sunabilir. WCF böyle bir tesis için genişletilebilirlik noktaları sağlar, ancak kullanıcı bunları uygulamalıdır.

## <a name="ntlm"></a>NTLM

Varsayılan olarak, Windows etki alanı ortamında Windows kimlik doğrulaması, kullanıcıların kimliğini doğrulamak ve yetkilendirmek için Kerberos protokolünü kullanır. Kerberos protokolü bir nedenle kullanılmıyorsa, geri dönüş olarak NT LAN Manager (NTLM) kullanılır. Özelliğini olarak ayarlayarak bu davranışı devre dışı bırakabilirsiniz <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> `false` . NTLM 'ye izin verirken dikkat edilecek sorunlar şunlardır:

- NTLM, istemci kullanıcı adını gösterir. Kullanıcı adının gizli tutulması gerekiyorsa, `AllowNTLM` bağlamasındaki özelliğini olarak ayarlayın `false` .

- NTLM sunucu kimlik doğrulaması sağlamaz. Bu nedenle, kimlik doğrulama protokolü olarak NTLM kullandığınızda istemci doğru hizmetle iletişim kurmasını güvence altına alamaz.

### <a name="specifying-client-credentials-or-invalid-identity-forces-ntlm-usage"></a>Istemci kimlik bilgilerini belirtme veya geçersiz kimlik NTLM kullanımını zorlar

İstemci oluştururken, bir etki alanı adı olmadan istemci kimlik bilgilerini belirtme veya geçersiz bir sunucu kimliği belirtme, Kerberos protokolü yerine NTLM 'nin kullanılmasına neden olur ( `AllowNtlm` özellik olarak ayarlandıysa `true` ). NTLM sunucu kimlik doğrulaması yapamadığı için bilgiler büyük olasılıkla açıklanamaz.

Örneğin, aşağıdaki Visual C# kodunda gösterildiği gibi, etki alanı adı olmadan Windows istemci kimlik bilgilerini belirtmek mümkündür.

```csharp
MyChannelFactory.Credentials.Windows.ClientCredential = new System.Net.NetworkCredential("username", "password");
```

Kod, bir etki alanı adı belirtmez ve bu nedenle NTLM kullanılacaktır.

Etki alanı belirtilmişse, ancak Endpoint Identity özelliği kullanılarak geçersiz bir hizmet asıl adı belirtilmişse, NTLM kullanılır. Uç nokta kimliğinin nasıl belirtildiği hakkında daha fazla bilgi için bkz. [hizmet kimliği ve kimlik doğrulaması](service-identity-and-authentication.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Güvenlik konuları](security-considerations-in-wcf.md)
- [Ayrıcalıkların Yükseltilmesi](elevation-of-privilege.md)
- [Hizmet Reddi](denial-of-service.md)
- [İzinsiz Değişiklik](tampering.md)
- [Desteklenmeyen Senaryolar](unsupported-scenarios.md)
- [Yeniden Yürütme Saldırıları](replay-attacks.md)

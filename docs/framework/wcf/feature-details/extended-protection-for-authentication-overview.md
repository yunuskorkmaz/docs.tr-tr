---
title: Kimlik Doğrulama için Genişletilmiş Koruma Genel Bakış
ms.date: 03/30/2017
ms.assetid: 3d2ceffe-a7bf-4bd9-a5a2-9406423bd7f8
ms.openlocfilehash: 400bf7987b5fcd4ec75628d19a30739dd5f23b08
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964611"
---
# <a name="extended-protection-for-authentication-overview"></a>Kimlik Doğrulama için Genişletilmiş Koruma Genel Bakış
Kimlik Doğrulaması için Genişletilmiş Koruma, bir saldırganın istemcinin kimlik bilgilerini aldığı ve bunları sunucuya ileten, ortadaki adam (MITı) saldırılarına karşı korunmaya yardımcı olur.  
  
 Üç katılımcı içeren bir senaryo düşünün: bir istemci, sunucu ve saldırgan. Sunucu `https://server`URL 'ye sahiptir, ancak saldırgan URL 'YI `https://attacker`. Saldırgan, istemci, sunucu gibi saldırgana erişmesini ister. Saldırgan daha sonra sunucuya bir istek gönderir. Saldırgan güvenli bir kaynağa erişmeye çalışıyorsa, sunucu saldırgana bir WWW-Authenticate üstbilgisiyle yanıt verir. Saldırgan kimlik doğrulama bilgilerine sahip değildir, bu nedenle WWW-Authenticate üstbilgisini istemciye gönderir. İstemci, yetkilendirme üst bilgisini saldırgana gönderir ve saldırgan üst bilgiyi sunucuya gönderir ve istemcinin kimlik bilgilerini kullanarak güvenli kaynaklara erişim sağlar.  
  
 Şu anda bir istemci uygulaması HTTPS kullanarak Kerberos, Özet veya NTLM kullanan sunucuda kendi kimliğini doğruladığında, ilk olarak bir aktarım düzeyi güvenlik (TLS) kanalı oluşturulur ve kimlik doğrulaması bu kanalı kullanarak gerçekleşir. Ancak, Güvenli Yuva Katmanı (SSL) tarafından oluşturulan oturum anahtarı ile kimlik doğrulama sırasında oluşturulan oturum anahtarı arasında bir bağlama yoktur. Bu nedenle, önceki senaryoda, iletişim bir TLS (örneğin, bir HTTPS kanalı) üzerinde yer alıyorsa, iki SSL kanalı oluşturulur: biri istemci ile saldırgan arasında ve saldırgan ile sunucu arasında bir diğeri. İstemcinin kimlik bilgileri, istemci ile saldırgan arasındaki SSL kanalı üzerinden önce istemciden sunucuya, sonra da saldırgan ile sunucu arasındaki kanal üzerinden gönderilir. İstemcinin kimlik bilgileri sunucuya ulaştığında, sunucu kimlik bilgilerini bu kimlik bilgilerinin gönderildiği kanalın istemciye değil saldırgan ile geldiğini algılamadan doğrular.  
  
 Çözüm, TLS ile güvenli bir dış kanal ve istemci kimliği doğrulanmış bir iç kanal kullanmak ve bir kanal bağlama belirtecini (CBT) sunucuya geçirmek için kullanılır. CBT, TLS ile güvenli dış kanalın bir özelliğidir ve dış kanalı istemci kimliği doğrulanmış iç kanal üzerinden konuşmaya bağlamak için kullanılır.  
  
 Önceki senaryoda, istemci-saldırgan TLS kanalının CBT, sunucuya gönderilen yetkilendirme bilgileriyle birleştirilir. CBT ile uyumlu bir sunucu, istemci-saldırgan kanalına karşılık gelen istemci kimlik doğrulama bilgilerinde bulunan CBT 'yi, saldırgan-sunucu kanalına eklenen CBT 'e göre karşılaştırır. Bir CBT, bir kanalın hedefine özgüdür, bu nedenle istemci-saldırgan CBT, saldırgan-sunucu CBT ile eşleşmez. Bu, sunucunun MITK saldırısını algılamasına ve kimlik doğrulama isteğini reddetmesine olanak tanır.  
  
 İstemci tarafı herhangi bir yapılandırma ayarı gerektirmez. İstemci, CBT 'yi sunucusuna iletmek üzere güncelleştirildikten sonra her zaman bunu yapar. Sunucu da güncelleştirilmiş ise, CBT 'yi kullanacak şekilde yapılandırılabilir veya onu yoksayabilirsiniz. Güncelleştirmemişse, yok sayılır.  
  
 Sunucu aşağıdaki koruma düzeylerine sahip olabilir:  
  
- Yok. Kanal bağlama doğrulaması yapılmaz. Bu, güncelleştirilmemiş tüm sunucuların davranışıdır.  
  
- Kısmi. Güncelleştirilmiş tüm istemciler, sunucuya kanal bağlama bilgilerini sağlamalıdır. Güncelleştirilmemiş istemcilerin bunu yapması gerekmez. Bu, uygulama uyumluluğuna izin veren bir ara seçenektir.  
  
- Tam düzeyine getirir. Tüm istemcilerin kanal bağlama bilgilerini sağlaması gerekir. Sunucu, bunu yapan istemcilerden gelen kimlik doğrulama isteklerini reddeder.  
  
 Daha fazla bilgi için bkz. Win7 CBT/genişletilmiş koruma örneği.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Server App Fabric için güvenlik modeli](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))

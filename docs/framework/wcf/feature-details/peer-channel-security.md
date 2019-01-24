---
title: Eş Kanalı Güvenliği
ms.date: 03/30/2017
ms.assetid: 2c59b164-3729-44f0-a967-f247c42de662
ms.openlocfilehash: 09979cee48522355631c79e0bdf4c0fba6be782e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54541761"
---
# <a name="peer-channel-security"></a>Eş Kanalı Güvenliği
Eş kanalı, çeşitli misyonumuz mesajlaşmayı bağlı olan dağıtılmış uygulama türleri sağlar. Burada güvenilen bir kaynak içerik (örneğin, medya veya yazılım güncelleştirmeleri) dağıtır, Internet ölçekli içerik dağıtımı bazı örnekler bir arkadaş grubuyla exchange müzik ve fotoğraf veya iş arkadaşlarınız, takım işbirliği içinde bir belgeyi Düzenle. Bu senaryoların her biri, benzersiz güvenlik modeli gerektirir. Eş kanal güvenlik modeli, bu senaryoları için tasarlanan ve ilgili farklı kimlik, kimlik doğrulama ve yetkilendirme modeli ihtiyaçları için bir güvenlik modeli sağlar.  
  
## <a name="security-scenarios"></a>Güvenlik senaryoları  
 Bir içerik dağıtım senaryosu, içerik her alıcı içerik kaynağı tanımlayın gerektirir. Senaryo dağıtılmış doğası nedeniyle, her zaman biliyor ve bu işlem veya ıntercept iletileri aracıların güven mümkün değildir. Uygulamaları etkili bir şekilde, güvenilmeyen bir aracı ile iletileri değiştirmesine tehdidi azaltmak için değiştirme girişiminde herhangi bir kolayca algılanır böylece Gönderenin iletiyi güvenliğini sağlayabilirsiniz. Bu durumda, şifreleme içerik gizliliğini bağlı olarak, gerekli olabilir.  
  
 Genellikle Grup belge işbirliği gibi işbirliği senaryoları oturumda katılan her üye ayrı ayrı tanımlanan kimlik doğrulaması ve gerektirir. Bu, kullanıcı grupları tanımlayabilir ve bu gruplara karşı kimlik doğrulaması için bir mekanizma güvenli bir oturum gerekli olduğu anlamına gelir. Ayrıca, uygulamalar her ileti ileti düzeyinde kimlik doğrulaması tarafından izleme gerektirebilir. Bu tür uygulamalar için daha güçlü bir güvenlik şeması performans feda.  
  
 Sıradan bir kullanıcı grubu arasında bir iletişim oturumu bilgi grubu arasında ortak bir gizli dizi gibi resmi olmayan güvenlik modelleri gerektirebilir. Bu tür uygulamalar oluşturmak ve yapılandırmak uygun bir güvenlik modeli sahip güçlü kimlik doğrulama biçimi olması veya kabullenme ölçüler sağlayarak daha daha önemlidir. Bu senaryolar için bir parola tabanlı kimlik doğrulama mekanizması iletişim katmanı ileti kimlik doğrulaması için hala izin verirken güvenliğini korumaya yardımcı olur. Parola tabanlı güvenlik, eş kanalı için varsayılan ayardır.  
  
## <a name="token-types"></a>Belirteç türleri  
 Eş kanal güçlü tanımlama için tek bir belirteç türü uygulanabilir yetkilendirme ve kimlik doğrulaması türüne göre bir güçlü kimlik modeli sağlayan X.509 sertifikalarını tanır. Gizliliği ve bütünlüğü kolayca sertifikalar kullanılarak sağlanır. Ancak, X.509 sertifikaları kullanma ve dağıtmak zor olabilir.  
  
 Eş kanal parolaları kullanarak basit uygulamalar için de destek sağlar. Uygulamalar, hızlı ve basit eş gruplarını sağlanan parola tabanlı ayarlamayı da seçebilirsiniz. Bu durumda, bir grup sahibi karar verir ve parola üyeleri için iletişim kurar. Her üye oturum katılabilmesi için önce bu parolayı kullanarak oturum açmanız gerekir. Parolaları, yalnızca oturum girişine izin vermek için kullanılabilir; ileti kimlik doğrulaması gerçekleştirmek için kullanılamaz. Eşleri grubudur paylaştığı simetrik bir belirteç zor veya uygunsuz kaynak kimlik doğrulaması için kullanılacak olmasıdır.  
  
## <a name="security-model"></a>Güvenlik modeli  
 Eş kanal, eşler arasında bireysel bağlantıların güvenliğini sağlama becerisi sağlar. Bu, bir ileti hiçbir zaman güvenli bir bağlantı (uygulama açısından) geçen anlamına gelir. Dahili olarak, her bağlantı (iki eşler arasında taşıma kanalı) Aktarım Katmanı Güvenliği (TLS) kullanılarak korunmaktadır. Bir gönderici oluşturur ve bir ileti gönderir, yani, her ileti erişmek ve iletiyi hemen kendi eşlere güvenli bağlantılar üzerinden sırayla gönderin, anında eş, güvenli aktarım üzerinden gönderilir. Bu güvenlik yalnızca çalışır, aktarım düzeyinde ve ileti güvenlik modelleri bağımsızdır.  
  
 Eş kanal ayrıca kullanılan aktarım güvenliği bağımsız olarak iletileri güvenli hale getirmek için bir yol sağlar. Şu anda yalnızca X.509 sertifikaları desteklenir ancak bu modelde, kaynağın güvenlik belirteci kullanılarak kaynakta ileti güvenlidir. Güvenli bir ileti, ardından eş ağ üzerinden iletilir. Her alan eş kaynağı güvenilirliğini doğrulayabilirsiniz. İleti güvenlidir ve böylece aracılar ile değiştirmesine unutmayın.  
  
 Gizlilik elde etmek için uygulamaları iletiye yetkisiz erişimi önlemek için güçlü bir grup üyeliği düzenleri ile Aktarım güvenliği tercih edebilirsiniz.  
  
 Uygulama belirteci desteklenen türlerden biri seçtiği sürece eş kanallı belirli kimlik modeli gerektirmez. Uygulamalar bu kimlikler ve kimlik doğrulama kararları yaşam döngüsünü tamamen aittir.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Eş Kanalı Uygulamalarını Güvenli Hale Getirme](../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
- [Eş Kanal Kavramları](../../../../docs/framework/wcf/feature-details/peer-channel-concepts.md)
- [Eş Kanal Uygulaması Oluşturma](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)

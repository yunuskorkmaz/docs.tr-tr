---
title: Eş Kanalı Güvenliği
ms.date: 03/30/2017
ms.assetid: 2c59b164-3729-44f0-a967-f247c42de662
ms.openlocfilehash: e66c532b253c8aa53ae508a72633fa255615e80f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="peer-channel-security"></a>Eş Kanalı Güvenliği
Eş kanal çeşitli taraflı mesajlaşmayı bağımlı dağıtılmış uygulama türlerini sağlar. Burada güvenilen bir kaynak (örneğin, medya veya yazılım güncelleştirmeleri) içerik dağıtır, Internet ölçeğinde içerik dağıtımı bazı örnekler bir arkadaş grubuyla exchange müzik ve fotoğraf veya iş arkadaşlarınızı ekibi birliğine dayalı olarak bir belgeyi Düzenle. Bu senaryoların her biri benzersiz güvenlik modelini gerektirir. Eş kanal güvenlik modeli bu senaryosu için tasarlanmıştır ve farklı kimlik, kimlik doğrulama ve yetkilendirme modelleri ilgili gereksinimleriniz için bir güvenlik modeli sağlar.  
  
## <a name="security-scenarios"></a>Güvenlik senaryoları  
 İçerik dağıtım senaryosu, içerik her alıcı içerik kaynağı tanımlamak gerektirir. Senaryo dağıtılmış yapısı nedeniyle, her zaman bilmek ve bu işlem veya ıntercept iletileri aracıların güven mümkün değildir. Uygulamaları etkili bir şekilde güvenilmeyen bir aracı iletilerle değiştirmesine tehdidi azaltmak için böylece değiştirme girişimleri kolayca algılanan Gönderenin iletiyi güvenliğini sağlayabilirsiniz. Bu durumda, içerik gizliliğini bağlı olarak, şifreleme gerekli olabilir.  
  
 İşbirliği senaryoları genellikle Grup belge işbirliği gibi oturumda katılan her üye ayrı ayrı tanımlanan kimlik doğrulaması ve gerektirir. Bu, kullanıcı gruplarını tanımlar ve bu gruplara karşı kimlik doğrulaması için bir mekanizma güvenli bir oturum gerekli olduğu anlamına gelir. Ayrıca, uygulamalar her ileti kimlik doğrulama ileti düzeyinde tarafından izleme gerektirebilir. Bu tür uygulamalar için daha güçlü güvenlik şeması performans feda.  
  
 Bir kullanıcı grubuna sıradan arasında iletişim oturumu grubu arasında ortak bir gizlilik bilgisi gibi resmi olmayan güvenlik modelleri gerektirebilir. Bu tür uygulamalar oluşturmak ve yapılandırmak uygun bir güvenlik modeli sahip kimlik doğrulaması güçlü biçiminde olması veya kabullenme ölçüleri sağlayarak daha daha önemlidir. Bu senaryolarda, ileti kimlik doğrulaması için hala verirken güvenli iletişim katmanı için bir parola tabanlı kimlik doğrulama mekanizması yardımcı olur. Parola tabanlı güvenlik eş kanalı için varsayılan ayardır.  
  
## <a name="token-types"></a>Belirteç türleri  
 Eş kanal tek bir belirteç türü güçlü kimlik için kimlik doğrulama ve yetkilendirme uygulanabilir türüne göre bir güçlü kimlik modeli sağlar X.509 sertifikalarını tanır. Gizliliği ve bütünlük kolayca sertifikalar kullanılarak sağlanır. Ancak, X.509 sertifikalarını kullanın ve dağıtmak zor olabilir.  
  
 Eş kanal, parolaları ile basit uygulamalar için de destek sağlar. Sağlanan parola tabanlı hızlı ve basit eş gruplarını ayarlamak uygulamaları seçebilirsiniz. Bu durumda, bir grup sahibi karar verir ve parola üyelerine iletişim kurar. Her üye oturum katılabilmesi için önce bu parola kullanarak oturum açmanız gerekir. Parolalar, yalnızca oturum girişine izin vermek için kullanılabilir; ileti kimlik doğrulaması gerçekleştirmek için kullanılamaz. Eşleri grubudur paylaşan simetrik belirteç zor ve kaynak kimlik doğrulaması için kullanılacak uygun olmasıdır.  
  
## <a name="security-model"></a>Güvenlik modeli  
 Eş kanal tek bağlantılar eşler arasında güvenli olanağı sağlar. Bu, bir ileti hiçbir zaman güvenli bir bağlantı (uygulama açısından) üzerindeki akar olduğunu anlamına gelir. Dahili olarak, her bir bağlantının (iki eş arasında taşıma kanal) Aktarım Katmanı Güvenliği (TLS) kullanarak güvenli hale getirilir. Bir gönderici oluşturur ve bir ileti gönderir anlamına gelir, her bir iletinin erişmek ve sırayla kendi hemen eşlere güvenli bağlantıları üzerinden Gönder, ileti hemen eşlerine, onu güvenli aktarımı üzerinden gönderilir. Aktarım sırasında yalnızca works düzey ve ileti güvenlik modellerinin bağımsızdır bu güvenlik.  
  
 Eş kanal ayrıca kullanılan taşıma güvenliği bağımsız olarak iletileri güvenli hale getirmek için bir yol sağlar. Şu anda yalnızca X.509 sertifikaları desteklenir, ancak bu modelde, kaynağın güvenlik belirtecini kullanarak kaynakta ileti güvenlidir. Güvenli bir ileti sonra eş ağ üzerinden iletilir. Her alıcı eş kaynağı özgünlüğünü doğrulayabilirsiniz. İleti güvenliği ve böylece aracılar ile değiştirmesine unutmayın.  
  
 Gizliliği elde etmek için uygulamaları iletiye yetkisiz erişimi önlemek için güçlü grup üyeliği düzenleri ile taşıma güvenliği tercih edebilirsiniz.  
  
 Eş kanal uygulama desteklenen belirteç türleri birini seçer sürece belirli bir kimlik modeli gerektirmez. Uygulamalar, bu kimlikleri ve kimlik doğrulama kararları yaşam döngüsünü tamamen kendi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eş Kanalı Uygulamalarını Güvenli Hale Getirme](../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)  
 [Eş Kanal Kavramları](../../../../docs/framework/wcf/feature-details/peer-channel-concepts.md)  
 [Eş Kanal Uygulaması Oluşturma](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)

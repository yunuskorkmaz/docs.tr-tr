---
title: Eş Kanalı Güvenliği
ms.date: 03/30/2017
ms.assetid: 2c59b164-3729-44f0-a967-f247c42de662
ms.openlocfilehash: f8015f41254d17f908f3665db65af3d82eaa2b6a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84576089"
---
# <a name="peer-channel-security"></a>Eş Kanalı Güvenliği
Eş kanal, çok taraflı mesajlaşmaya bağlı olan çeşitli dağıtılmış uygulama türlerini mümkün bir şekilde sunar. Bazı örneklerde, güvenilir bir kaynağın içerik (medya veya yazılım güncelleştirmeleri gibi), bir arkadaş grubu Exchange müzik ve fotoğraflar ya da iş arkadaşları ekibi tarafından ortak olarak düzenlenerek bir belgeyi dağıttığı Internet ölçeğinde içerik dağıtımı vardır. Bu senaryoların her biri için benzersiz bir güvenlik modeli gerekir. Eş kanal güvenlik modeli, bu senaryolara yönelik olarak tasarlanmıştır ve farklı kimlik, kimlik doğrulama ve yetkilendirme modellerinin ilgili ihtiyaçları için bir ses güvenlik modeli sağlar.  
  
## <a name="security-scenarios"></a>Güvenlik senaryoları  
 İçerik dağıtım senaryosu, her içerik alıcısının içerik kaynağını belirlemesini gerektirir. Senaryonun dağıtılmış doğası nedeniyle, iletileri işleyen veya denetleyen aracıları bilmeleri ve bu aracıların güvenmesi her zaman mümkün değildir. Güvenilir olmayan bir aracı tarafından iletilerle izinsiz değişiklik oluşturabilecek tehdidi etkili bir şekilde azaltmak için, uygulamalar, her türlü değiştirme girişiminin kolayca algılanabilmesi için gönderenden iletiyi güvenli hale getirebilirsiniz. Bu durumda, içeriğin gizliliğine bağlı olarak, şifreleme gerekli olabilir.  
  
 Grup belgesi işbirliği gibi işbirliği senaryoları genellikle, oturuma katılan her üyenin ayrı ayrı tanımlanmasını ve kimlik doğrulamasından geçirilmesini gerektirir. Bu, Kullanıcı gruplarını tanımlama ve bu gruplara karşı kimlik doğrulama mekanizmalarının güvenli bir oturuma sahip olması için gerekli olduğu anlamına gelir. Üstelik, uygulamalar ileti düzeyinde kimlik doğrulamaya göre her iletiyi izlemeyi gerektirebilir. Bu tür uygulamalarda, daha güçlü bir güvenlik düzeni için performans Fede olabilir.  
  
 Bir grup sıradan kullanıcı arasındaki iletişim oturumu, grup arasında ortak bir gizli dizi bilgisi gibi, resmi olmayan güvenlik modelleri gerektirebilir. Bu tür uygulamalar için, oluşturma ve yapılandırma açısından uygun bir güvenlik modeline sahip olmak, en güçlü kimlik doğrulama biçimine veya kabul önlemleri sağlamaya göre daha önemlidir. Bu senaryolarda, parola tabanlı bir kimlik doğrulama mekanizması ileti kimlik doğrulamasına hala izin verirken iletişim katmanını güvenli hale getirmeye yardımcı olur. Parola tabanlı güvenlik, eş kanal için varsayılan ayardır.  
  
## <a name="token-types"></a>Belirteç türleri  
 Eş kanal, uygulanabilen kimlik doğrulama ve yetkilendirme türüne göre güçlü bir kimlik modeli sağlayan, güçlü tanımlama, X. 509.440 sertifikaları için tek bir belirteç türünü tanır. Gizlilik ve bütünlük, sertifikalar kullanılarak kolayca sağlanır. Ancak, X. 509.440 sertifikalarının kullanımı ve dağıtılması zor olabilir.  
  
 Eş kanal Ayrıca, parolaların kullanımı aracılığıyla basit uygulamalar için destek sağlar. Uygulamalar, sağlanan bir parolayı temel alarak hızlı ve basit eşdüzey grupları ayarlamayı seçebilir. Bu durumda, bir grup sahibi üye için parola belirler ve iletişim kurar. Oturuma katılabilmeleri için, her üyenin bu parolayı kullanarak oturum açması gerekir. Parolalar yalnızca oturum girişine izin vermek için kullanılabilir; ileti kimlik doğrulaması yapmak için kullanılamaz. Bunun nedeni, bir eş payı grubunun paylaştığı bir simetrik belirtecin zor ve kaynak kimlik doğrulaması için kullanılmak üzere uygun olmadığı bir değer.  
  
## <a name="security-model"></a>Güvenlik modeli  
 Eş kanal, eşler arasındaki tek tek bağlantıları güvenli hale getirme yeteneği sağlar. Yani, bir ileti güvenli olmayan bir bağlantıyı (uygulama perspektifinden) hiçbir şekilde hiçbir şekilde akamez. Dahili olarak, her bağlantı (iki eş arasında bir aktarım kanalı) Aktarım Katmanı Güvenliği (TLS) kullanılarak güvenli hale getirilir. Bu, bir gönderici bir ileti yazdığında ve bir ileti gönderdiğinde, bu ileti, iletinin kendisine erişen ve iletiyi güvenli bağlantılar üzerinden kendi eşlerinden en iyi şekilde Gönderen, güvenli aktarım üzerinden gönderildiği anlamına gelir. Bu güvenlik yalnızca Aktarım düzeyinde çalışarak ileti güvenliği modellerinden bağımsızdır.  
  
 Eş kanal Ayrıca, kullanılan aktarım güvenliği 'nden bağımsız olarak iletileri güvenli hale getirmek için bir yol sağlar. Bu modelde, şu anda yalnızca X. 509.440 sertifikaları desteklense de, kaynağın güvenlik belirteci kullanılarak kaynak üzerinde güvenli hale getirilir. Güvenli ileti daha sonra eş ağ üzerinden iletilir. Her alma eşi, kaynağın orijinalliğini doğrulayabilirler. Aracıların BT ile oynanabilmesi için, iletinin güvenli olduğunu unutmayın.  
  
 Uygulamalar, gizliliği sağlamak için, iletiye yetkisiz erişimi engellemek üzere güçlü grup üyeliği şemaları ile taşıma güvenliği uygulayabilir.  
  
 Uygulama desteklenen belirteç türlerinden birini seçtiği sürece eş kanal belirli bir kimlik modeli gerektirmez. Uygulamalar, bu kimliklerin ve kimlik doğrulama kararlarının yaşam döngüsüne tamamen aittir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Eş Kanalı Uygulamalarını Güvenli Hale Getirme](securing-peer-channel-applications.md)
- [Eş Kanal Kavramları](peer-channel-concepts.md)
- [Eş Kanal Uygulaması Oluşturma](building-a-peer-channel-application.md)

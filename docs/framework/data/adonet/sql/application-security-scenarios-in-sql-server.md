---
title: SQL Server'da Uygulama Güvenliği Senaryoları
ms.date: 03/30/2017
ms.assetid: 0164f3a4-406e-4693-bec3-03c8e18b46d7
ms.openlocfilehash: 2d0e65f61939312bf29111e87c49366cd9e389be
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197657"
---
# <a name="application-security-scenarios-in-sql-server"></a>SQL Server'da Uygulama Güvenliği Senaryoları

Güvenli SQL Server istemci uygulaması oluşturmanın tek doğru yolu yoktur. Her uygulama gereksinimler, dağıtım ortamı ve Kullanıcı popülasyonu içinde benzersizdir. Başlangıçta dağıtıldığında makul ölçüde güvenli bir uygulama, zaman içinde daha az güvenli hale gelebilir. Gelecekte hangi tehditlerin ortaya çıkabilecek herhangi bir doğrulukla tahmin edilmesi mümkün değildir.  
  
 Bir ürün olarak SQL Server, geliştiricilerin güvenli veritabanı uygulamaları oluşturmalarına olanak tanıyan en son güvenlik özelliklerini katmak için birçok sürümü geliştirmiştir. Ancak, güvenlik, kutuya gelmeyecektir; sürekli izleme ve güncelleştirme gerektirir.  
  
## <a name="common-threats"></a>Ortak tehditler  

 Geliştiricilerin güvenlik tehditlerini, onlara sayaç eklemek için sunulan araçları ve kendinden yetenekli güvenlik boşluklarını nasıl önleneceğini anlaması gerekir. Güvenlik en iyi şekilde düşünülebilir, ancak herhangi bir bağlantı içindeki bir kesmenin bütün kuvvetini tehlikeye atar. Aşağıdaki liste, bu bölümdeki konularda daha ayrıntılı olarak açıklanan bazı yaygın güvenlik tehditlerini içerir.  
  
### <a name="sql-injection"></a>SQL ekleme  

 SQL ekleme, kötü amaçlı bir kullanıcının geçerli giriş yerine Transact-SQL deyimlerini girdiği işlemdir. Giriş, doğrulamadan doğrudan sunucuya geçiriliyorsa ve uygulama eklenen kodu yanlışlıkla çalıştırırsa, saldırı, verileri hasar veya yok etme potansiyeli olur. Saklı yordamları ve Parametreli komutları kullanarak, dinamik SQL 'i önleyerek ve tüm kullanıcılar için izinleri kısıtlayarak SQL Server ekleme saldırıları sağlayabilirsiniz.  
  
### <a name="elevation-of-privilege"></a>Elevation of Privilege (Ayrıcalık Yükseltme)  

 Ayrıcalık yükselmesi saldırıları, bir Kullanıcı, bir sahip veya yönetici gibi güvenilir bir hesap ayrıcalıklarını varsayabiliyorsa oluşur. Her zaman en az ayrıcalıklı kullanıcı hesapları altında çalıştırın ve yalnızca gerekli izinleri atayın. Kodu yürütmek için yönetim veya sahip hesaplarını kullanmaktan kaçının. Bu, bir saldırının başarılı olması durumunda oluşabilecek hasar miktarını sınırlandırır. Ek izinler gerektiren görevleri gerçekleştirirken, yordam imzalamayı veya kimliğe bürünme özelliğini yalnızca görevin süresi boyunca kullanın. Saklı yordamları sertifikalarla imzalayabilir veya izinleri geçici olarak atamak için kimliğe bürünme özelliğini kullanabilirsiniz.  
  
### <a name="probing-and-intelligent-observation"></a>Algılama ve akıllı gözlem  

 Bir yoklama saldırısı, güvenlik açıklarını aramak için bir uygulama tarafından oluşturulan hata iletilerini kullanabilir. SQL Server hata bilgilerinin son kullanıcıya döndürülmesini engellemek için tüm yordamsal koddaki hata işlemeyi uygulayın.  
  
### <a name="authentication"></a>Kimlik Doğrulaması  

 Çalışma zamanında kullanıcı girişine dayalı bir bağlantı dizesi oluşturulursa, SQL Server oturum açma işlemleri kullanılırken bağlantı dizesi ekleme saldırısı meydana gelebilir. Bağlantı dizesi geçerli anahtar sözcük çiftleri için denetlenmediğinde, bir saldırgan çok fazla karakter ekleyebilir ve bu da sunucudaki hassas verilere veya diğer kaynaklara erişebilir. Mümkün olduğunda Windows kimlik doğrulamasını kullanın. SQL Server oturumlarını kullanmanız gerekiyorsa, <xref:System.Data.SqlClient.SqlConnectionStringBuilder> çalışma zamanında bağlantı dizelerini oluşturmak ve doğrulamak için öğesini kullanın.  
  
### <a name="passwords"></a>Parolalar  

 Bir saldırgan ayrıcalıklı kullanıcı için bir parola elde edebildiğinden veya tahmin edebildiğinden birçok saldırı başarılı olur. Parolalar, saldırganlar için ilk savunma hattınızdır, bu nedenle güçlü parolaların ayarlanması sisteminizin güvenliği için önemlidir. Karma mod kimlik doğrulaması için parola ilkeleri oluşturun ve uygulayın.  
  
 `sa`Windows kimlik doğrulaması kullanılırken bile hesaba her zaman güçlü bir parola atayın.  
  
## <a name="in-this-section"></a>Bu Bölümde  

 [SQL Server'da Saklı Yordam İzinlerini Yönetme](managing-permissions-with-stored-procedures-in-sql-server.md)  
 İzinleri yönetmek ve veri erişimini denetlemek için saklı yordamların nasıl kullanılacağını açıklar. Saklı yordamları kullanmak birçok güvenlik tehditlerine yanıt vermek için etkili bir yoldur.  
  
 [SQL Server’da Secure Dynamic SQL Yazma](writing-secure-dynamic-sql-in-sql-server.md)  
 Saklı yordamları kullanarak güvenli dinamik SQL yazma tekniklerini açıklar.  
  
 [SQL Server'da Saklı Yordam İmzalama](signing-stored-procedures-in-sql-server.md)  
 Kullanıcıların doğrudan erişimine sahip olmadıkları verilerle çalışmasını sağlamak için bir sertifikayla saklı yordamın nasıl imzalanabileceğini açıklar. Bu, saklı yordamların çağıranın doğrudan gerçekleştirme izni olmayan işlemler gerçekleştirmesine olanak sağlar.  
  
 [SQL Server'da Kimliğe Bürünme İzinlerini Özelleştirme](customizing-permissions-with-impersonation-in-sql-server.md)  
 Farklı bir kullanıcının kimliğine bürünmek için EXECUTE AS yan tümcesinin nasıl kullanılacağını açıklar. Kimliğe bürünme, yürütme bağlamını çağıranın belirtilen kullanıcıya geçirir.  
  
 [SQL Server’da Satır Düzeyinde İzinler Verme](granting-row-level-permissions-in-sql-server.md)  
 Veri erişimini kısıtlamak için satır düzeyinde izinlerin nasıl uygulanacağını açıklar.  
  
 [SQL Server’da Uygulama Rolleri Oluşturma](creating-application-roles-in-sql-server.md)  
 Uygulama rollerinin özelliklerini ve işlevlerini açıklar.  
  
 [SQL Server'da Veritabanları Arası Erişimi Etkinleştirme](enabling-cross-database-access-in-sql-server.md)  
 Güvenliği tehlikeye atamadan veritabanları arası erişimin nasıl etkinleştirileceğini açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SQL Server Güvenliği](sql-server-security.md)
- [SQL Server Güvenliğine Genel Bakış](overview-of-sql-server-security.md)
- [ADO.NET Uygulamalarının Güvenliğini Sağlama](../securing-ado-net-applications.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)

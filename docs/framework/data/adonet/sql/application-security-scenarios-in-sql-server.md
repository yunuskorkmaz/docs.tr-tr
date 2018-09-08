---
title: SQL Server'da uygulama güvenliği senaryoları
ms.date: 03/30/2017
ms.assetid: 0164f3a4-406e-4693-bec3-03c8e18b46d7
ms.openlocfilehash: bf4f4adfd5f49bd210026e40bd5fa4e67da10d75
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44180221"
---
# <a name="application-security-scenarios-in-sql-server"></a>SQL Server'da uygulama güvenliği senaryoları
Güvenli bir SQL Server istemci uygulaması oluşturmak için tek bir doğru yolu yoktur. Her uygulamanın kendi gereksinimler, dağıtım ortamı ve kullanıcı kitlesiyle benzersizdir. Başlangıçta dağıtıldığında, makul güvenli bir uygulama, zaman içinde daha az güvenli hale gelebilir. Hangi tehditleri gelecekte ortaya çıkan herhangi doğrulukla tahmin etmek mümkün değildir.  
  
 SQL Server, geliştiricilerin güvenli veritabanı uygulamaları oluşturmak en son güvenlik güncelleştirmelerini dahil etmek için birçok sürümlere göre bir ürün olarak geliştirilmiştir. Ancak, güvenlik kutuya gelmez; sürekli izleme ve güncelleştirme gerektirir.  
  
## <a name="common-threats"></a>Sık karşılaşılan tehditler  
 Geliştiriciler, güvenlik tehditlerine karşı bunları ve kendi kendine oluşan hatalardan güvenlik açıkları önlemek nasıl sayaç için sağlanan araçları anlamak gerekir. Güvenlik en iyi bir zinciri olarak burada herhangi bir bağlantı içinde bir kesme tüm gücünü etkilediğinde zorlayıcı olabilir. Aşağıdaki listede, bu bölümdeki konularda daha ayrıntılı ele alınmıştır bazı yaygın güvenlik tehditleri içerir.  
  
### <a name="sql-injection"></a>SQL ekleme  
 SQL ekleme, kötü niyetli bir kullanıcının geçerli giriş yerine Transact-SQL deyimleriyle girer işlemidir. Girişi doğrulanması gereken olmadan doğrudan sunucuya iletilmezse ve uygulama yanlışlıkla eklenen kodu yürütür, saldırı zarar verecek veya veri yok etme olanağına sahiptir. SQL ekleme saldırıları saklı yordamları kullanarak ve Parametreli Komutlar dinamik SQL önleme ve tüm kullanıcıların izinlerini kısıtlayarak Server ihlalini savuşturmanın.  
  
### <a name="elevation-of-privilege"></a>Ayrıcalık Yükseltme  
 Ayrıcalıkların yükseltilmesi saldırılarını kullanıcı ayrıcalıkları sahibi ya da yönetici gibi bir güvenilen hesap varsayar mümkün olduğunda oluşur. Her zaman en az ayrıcalıklı kullanıcı hesapları altında çalışan ve yalnızca gerekli izinleri atayın. Önlemek yönetim kullanarak veya sahibi hesapları kod yürütmek için. Bu saldırının başarılı olursa oluşabilecek zarar miktarını sınırlar. Ek izinler gerektiren görevler gerçekleştirirken, kimliğe bürünme yordam imzalama veya yalnızca görev sürekliliği için kullanın. Saklı yordamlar sertifika ile oturum açın veya geçici olarak izinler atamak için kimliğe bürünme özelliğini kullanın.  
  
### <a name="probing-and-intelligent-observation"></a>Araştırma ve akıllı gözlem  
 Bir araştırma saldırı bir uygulama tarafından oluşturulan hata iletileri, güvenlik açıklarını aramak için kullanabilirsiniz. Hata son kullanıcıya verilen SQL Server hata bilgilerinin önlemek için tüm yordam kodu işleme uygular.  
  
### <a name="authentication"></a>Kimlik doğrulaması  
 Bir bağlantı dizesi kullanıcı girişini temel alarak SQL Server oturumları kullanarak çalışma zamanında oluşturulduğunda bir bağlantı dizesi ekleme saldırısına ortaya çıkabilir. Bağlantı dizesi geçerli bir anahtar çifti işaretli değilse, bir saldırganın potansiyel olarak hassas verileri veya sunucudaki diğer kaynaklara erişme ek karakterler ekleyebilirsiniz. Windows kimlik doğrulaması, mümkün olduğunda kullanın. SQL Server oturumları kullanmanız gerekirse kullanmak <xref:System.Data.SqlClient.SqlConnectionStringBuilder> oluşturma ve bağlantı dizeleri çalışma zamanında doğrulama.  
  
### <a name="passwords"></a>Parolalar  
 Bir saldırgan edinmek ya da ayrıcalıklı bir kullanıcısı için bir parola tahmin sayıda saldırı başarılı. Parolalar, saldırganlara karşı savunma kodunuzun ilk satırını olduğundan güçlü parolalar ayarlamak sisteminizin güvenliği için önemlidir. Oluşturup karma mod kimlik doğrulaması için parola ilkelerini uygulayabilir.  
  
 Her zaman için güçlü bir parola atayın `sa` Windows kimlik doğrulaması kullanırken bile, hesap.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [SQL Server'da Saklı Yordam İzinlerini Yönetme](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)  
 Saklı yordamlar izinleri yönetmek ve veri erişimi denetlemek için nasıl kullanılacağını açıklar. Saklı yordamları kullanarak, çok sayıda güvenlik tehditleri için etkili bir yoludur.  
  
 [SQL Server’da Secure Dynamic SQL Yazma](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)  
 Saklı yordamları kullanarak güvenli dinamik SQL yazma teknikleri açıklar.  
  
 [SQL Server'da Saklı Yordam İmzalama](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md)  
 Bir saklı yordam, doğrudan erişim olmadığı verilerle çalışmak kullanıcıları etkinleştirmek için bir sertifika ile imzalamak açıklar. Bu, çağırana doğrudan gerçekleştirmek için gerekli izinlere sahip olmayan işlemler gerçekleştirmek için saklı yordamlar sağlar.  
  
 [SQL Server'da Kimliğe Bürünme İzinlerini Özelleştirme](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md)  
 Açıklar EXECUTE AS yan tümcesi başka bir kullanıcının kimliğine bürünmek için. Kimliğe bürünme arayandan yürütme bağlamı belirtilen kullanıcıya geçer.  
  
 [SQL Server’da Satır Düzeyinde İzinler Verme](../../../../../docs/framework/data/adonet/sql/granting-row-level-permissions-in-sql-server.md)  
 Veri erişimini kısıtlamak için satır düzeyinde izinler uygulamak açıklar.  
  
 [SQL Server’da Uygulama Rolleri Oluşturma](../../../../../docs/framework/data/adonet/sql/creating-application-roles-in-sql-server.md)  
 Özellikleri ve uygulama rolleri işlevselliğini açıklar.  
  
 [SQL Server'da Veritabanları Arası Erişimi Etkinleştirme](../../../../../docs/framework/data/adonet/sql/enabling-cross-database-access-in-sql-server.md)  
 Güvenliği tehlikeye atmadan veritabanları arası erişimi etkinleştirmeyi açıklar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [SQL Server Güvenliği](../../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 [SQL Server Güvenliğine Genel Bakış](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [ADO.NET Uygulamalarının Güvenliğini Sağlama](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)

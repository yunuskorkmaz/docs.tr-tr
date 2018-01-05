---
title: "SQL Server'daki uygulama güvenlik senaryoları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0164f3a4-406e-4693-bec3-03c8e18b46d7
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 8576ba3ae26788076fedf71a1f8028afbd263378
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="application-security-scenarios-in-sql-server"></a>SQL Server'daki uygulama güvenlik senaryoları
Güvenli bir SQL Server istemci uygulaması oluşturmak için tek doğru yolu yoktur. Her uygulama gereksinimleri, dağıtım ortamı ve kullanıcı nüfusu içinde benzersizdir. Başlangıçta dağıtıldığında makul güvenli bir uygulama zaman içinde daha az güvenli hale gelebilir. Hangi tehditleri gelecekte ortaya çıkan herhangi doğruluk ile tahmin etmek mümkün değildir.  
  
 SQL Server, bir ürün olarak çok sayıda sürümleri güvenli veritabanı uygulamaları oluşturmak, geliştiricilerin en son güvenlik özellikleri içerecek şekilde gelişmiştir. Ancak, güvenlik kutusuna gelmez; sürekli izleme ve güncelleştirme gerektirir.  
  
## <a name="common-threats"></a>Ortak tehditleri  
 Geliştiriciler, güvenlik tehditlerine karşı bunları ve kendi kendine inflicted güvenlik açıklarını önlemenin sayaç için sağlanan araçları anlamanız gerekir. Güvenlik en iyi, zinciri olarak burada herhangi bir bağlantı aranın tüm gücünü etkilediğinde değerlendirilebilir. Aşağıdaki listede, bu bölümdeki konularda daha ayrıntılı ele alınan bazı genel güvenlik tehditlerini içerir.  
  
### <a name="sql-injection"></a>SQL ekleme  
 SQL ekleme olarak Transact-SQL deyimi geçerli giriş yerine kötü niyetli bir kullanıcının girdiği işlemidir. Giriş doğrulamasından geçmeden doğrudan sunucuya geçirilir ve uygulama yanlışlıkla eklenen kod yürütülürse, saldırı zarar veya verilere zarar olanağına sahiptir. SQL ekleme saklı yordamları kullanarak saldırılarına ve Parametreli Komutlar dinamik SQL önleme ve tüm kullanıcıların izinlerini kısıtlayarak Server korunmanıza.  
  
### <a name="elevation-of-privilege"></a>Ayrıcalık Yükseltme  
 Ayrıcalıkların yükseltilmesi saldırılarını kullanıcı ayrıcalıklarına sahip veya yönetici gibi bir güvenilen hesabı varsayın mümkün olduğunda oluşur. Her zaman en az ayrıcalıklı kullanıcı hesapları altında çalıştırmak ve yalnızca gerekli izinleri atayın. Kaçının yönetim kullanarak veya sahibi hesapları kod yürütmek için. Bu saldırının başarılı olursa, ortaya hasar miktarını sınırlar. Ek izinleri gerektiren görevler gerçekleştirirken, yalnızca görev süresince yordamı imzalama veya kimliğe bürünme kullanın. Saklı yordamlar sertifikalarla oturum ya da geçici olarak izinler atamak için kimliğe bürünme özelliğini kullanın.  
  
### <a name="probing-and-intelligent-observation"></a>Araştırma ve akıllı gözlem  
 Bir araştırma saldırısı güvenlik açıklarını aramak için bir uygulama tarafından oluşturulan hata iletileri kullanabilirsiniz. Son kullanıcı için verilen SQL Server hata bilgilerinin önlemek için tüm yordam kodu işleme hatası uygulayın.  
  
### <a name="authentication"></a>Kimlik doğrulaması  
 Bir bağlantı dizesi kullanıcı girdisi dayalı olarak, SQL Server oturumları kullanarak çalıştırma zamanında oluşturulan bir bağlantı dizesi ekleme saldırı ortaya çıkabilir. Bağlantı dizesi için geçerli anahtar çiftleri işaretli değilse, bir saldırganın olası hassas verileri veya sunucudaki diğer kaynaklara erişme fazladan karakterler ekleyebilirsiniz. Windows kimlik doğrulaması, mümkün olduğunda kullanın. SQL Server oturumları kullanmanız gerekiyorsa kullanın <xref:System.Data.SqlClient.SqlConnectionStringBuilder> oluşturmak ve bağlantı dizeleri çalışma zamanında doğrulamak için.  
  
### <a name="passwords"></a>Parolaları  
 Bir saldırgan tarafından elde etmek veya ayrıcalıklı bir kullanıcı için bir parola tahmin etmek mümkün olduğundan çoğu saldırı başarılı. Parolaları, ilk karşı savunma hattı saldırganların, olduğundan, güçlü parolalar ayarlamak, sistem güvenliği için önemlidir. Oluşturun ve karma mod kimlik doğrulaması için parola ilkelerini zorlamak.  
  
 Her zaman güçlü bir parola atayın `sa` , Windows kimlik doğrulaması kullanırken bile hesabı.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [SQL Server'da Saklı Yordam İzinlerini Yönetme](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)  
 Saklı yordamlar izinleri yönetmek ve veri erişimi denetlemek için nasıl kullanılacağını açıklar. Saklı yordamları kullanarak, birçok güvenlik tehditlerine karşı yanıt için etkili bir yoldur.  
  
 [SQL Server’da Secure Dynamic SQL Yazma](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)  
 Güvenli dinamik SQL saklı yordamları Kullanma yazma teknikleri açıklar.  
  
 [SQL Server'da Saklı Yordam İmzalama](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md)  
 Saklı yordam, doğrudan erişim olmadığı verilerle çalışmak için kullanıcıları etkinleştirmek üzere bir sertifika ile oturum açıklar. Bu çağrıyı doğrudan gerçekleştirmek için izinlere sahip değil işlemlerini gerçekleştirmek saklı yordamlar sağlar.  
  
 [SQL Server'da Kimliğe Bürünme İzinlerini Özelleştirme](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md)  
 EXECUTE AS kullanmayı açıklar başka bir kullanıcının kimliğine bürünmesine yan tümcesi. Kimliğe bürünme çağrıyı yapandan yürütme bağlamı belirtilen kullanıcıya geçer.  
  
 [SQL Server’da Satır Düzeyinde İzinler Verme](../../../../../docs/framework/data/adonet/sql/granting-row-level-permissions-in-sql-server.md)  
 Veri erişimi kısıtlamak için satır düzeyi izinleri uygulamak açıklar.  
  
 [SQL Server’da Uygulama Rolleri Oluşturma](../../../../../docs/framework/data/adonet/sql/creating-application-roles-in-sql-server.md)  
 Özellikleri ve uygulama rolleri işlevselliğini açıklar.  
  
 [SQL Server'da Veritabanları Arası Erişimi Etkinleştirme](../../../../../docs/framework/data/adonet/sql/enabling-cross-database-access-in-sql-server.md)  
 Veritabanları arası erişim güvenliği tehlikeye atmadan etkinleştirmeyi açıklar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [SQL Server Güvenliği](../../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 [SQL Server Güvenliğine Genel Bakış](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [ADO.NET Uygulamalarının Güvenliğini Sağlama](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)

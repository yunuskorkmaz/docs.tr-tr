---
title: Yetkilendirme ve SQL Server izinleri
ms.date: 03/30/2017
ms.assetid: d340405c-91f4-4837-a3cc-a238ee89888a
ms.openlocfilehash: bdf5112e3f0e2cada4885b0b66adf248f0ffe808
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44098569"
---
# <a name="authorization-and-permissions-in-sql-server"></a>Yetkilendirme ve SQL Server izinleri
Veritabanı nesneleri oluşturma, açıkça kullanıcılar için erişilebilir hale getirmek için izinleri vermeniz gerekir. Tüm güvenli kılınabilir nesne izni deyimleri kullanarak sorumlu için verilen izinleri vardır.  
  
## <a name="the-principle-of-least-privilege"></a>En düşük öncelik ilkesini  
 En az ayrıcalıklı kullanıcı hesabı (LUA) yaklaşımı kullanarak bir uygulama geliştirmek için güvenlik tehditlerini tedarikle savunmacı, ayrıntılı bir stratejisinin önemli bir parçasıdır. LUA yaklaşım, kullanıcıların en düşük öncelik ilkesini izleyin ve her zaman sınırlı bir kullanıcı hesabıyla oturum sağlar. Yönetim görevleri ayrıştırılmış sabit sunucu rolleri ve kullanımını kullanarak `sysadmin` sabit sunucu rolünün ciddi bir şekilde kısıtlıdır.  
  
 Her zaman en az ayrıcalık ilkesini veritabanı kullanıcılarına izin verirken izleyin. Belirli bir görevi tamamlamak için en az bir kullanıcı veya rol için gerekli izinleri verin.  
  
> [!IMPORTANT]
>  Geliştirme ve test LUA yaklaşımı kullanarak bir uygulama geliştirme süreci için Zorluk derecesi ekler. Nesneleri oluşturmak ve bir sistem yöneticisi veya veritabanının sahibi olarak LUA hesabı kullandığından oturum açarken kod yazmak kolaydır. Ancak, en az ayrıcalıklı kullanıcıların düzgün çalışması için yükseltilmiş izinler gerektiren bir uygulamayı çalıştırmayı denediğinizde yüksek ayrıcalıklı bir hesap kullanarak uygulamaları geliştirme işlevsellik etkisini karartmak. İşlev kaybı yeniden almanız için kullanıcılara aşırı izinleri verme, uygulamanızı saldırılara açık bırakabilirsiniz. Tasarlama, geliştirme ve LUA hesabıyla oturum açıldığında uygulamanızı test etme, sürprizlerden ve hızlı düzeltme olarak yükseltilmiş ayrıcalıkları vermek dürtüsüne ortadan kaldıran güvenlik planlama disiplinli bir yaklaşım uygular. Uygulamanızı Windows kimlik doğrulaması kullanarak dağıtmak için hedeflenen bile test etmek için bir SQL Server oturumu kullanabilirsiniz.  
  
## <a name="role-based-permissions"></a>Role dayalı izinleri  
 Roller yerine kullanıcı izinleri verme, güvenlik yönetimini basitleştirir. Rol atanmış izin kümeleri rolünün tüm üyelerinin tarafından devralınır. Eklemek veya ayrı izni yeniden oluşturmak için kullanıcıları tek tek ayarlar olduğundan kullanıcılar bir rolden kaldırmak daha kolaydır. Rolleri yuvalanabilir; Ancak, çok fazla iç içe geçme düzeyi performansını düşürebilir. Sabit veritabanı rollerine atama izinleri kolaylaştırmak için kullanıcıları da ekleyebilirsiniz.  
  
 Şema düzeyinde izinler verebilirsiniz. Kullanıcıları otomatik olarak şemada oluşturulan tüm yeni nesneler izinlerini devralır; Yeni nesneler oluşturulurken izinler vermeniz gerekmez.  
  
## <a name="permissions-through-procedural-code"></a>Yordam kodu aracılığıyla izinler  
 Modüller aracılığıyla veri erişimi gibi şifrelenmiş saklı yordamları ve kullanıcı tanımlı işlevler, ek bir uygulama etrafında koruma katmanı sağlar. Kullanıcıların tablolar gibi temel nesneler için izinleri reddetme sırasında yalnızca saklı yordamları ve işlevleri için izinleri vererek veritabanı nesneleri ile doğrudan etkileşim öğesinden engelleyebilirsiniz. SQL Server sahiplik zinciri tarafından elde eder.  
  
## <a name="permission-statements"></a>İzni deyimleri  
 Üç Transact-SQL izni ifade aşağıdaki tabloda açıklanmıştır.  
  
|İzni deyimi|Açıklama|  
|--------------------------|-----------------|  
|VERME|Bir izin verir.|  
|İPTAL ETME|İzni iptal eder. Bu yeni nesnenin varsayılan durumudur. Bir kullanıcı ya da rol iptal izin hala diğer grupların veya rollerin asıl atandığı devralınabilir.|  
|REDDET|Böylece, devralınamaz REDDET izni iptal eder. REDDETME önceliklidir tüm izinleri REDDET nesnesine sahip veya üye için geçerli değildir dışında `sysadmin`. Reddederse, nesnenin izinlerini `public` reddedilen tüm kullanıcılar ve roller nesne sahipleri dışında rolü ve `sysadmin` üyeleri.|  
  
-   Verme deyimi, bir Grup ya da veritabanı kullanıcıları tarafından devralınan rol izinleri atayabilirsiniz. Ancak, verme deyimi, tüm diğer iznini deyimlerinden öncelik kazanır. Bu nedenle, izin verilmeyen bir kullanıcı başka bir rolden devralamaz.  
  
> [!NOTE]
>  Üyeleri `sysadmin` sabit sunucu rolü ve nesne sahipleri izinler reddedildi olamaz.  
  
## <a name="ownership-chains"></a>Sahipliği zincirleri  
 SQL Server, izin verilen sorumluları nesneleri erişebilmesini sağlar. Birden çok veritabanı nesneleri arasındaki ilişki eriştiğinizde dizisi zinciri olarak bilinir. SQL Server bağlantıları zincirindeki geçiş yapma, her öğe ayrı olarak erişimi durumunda olduğu daha da izinleri farklı değerlendirir. Bir nesne bir domainproperty'leri erişildiğinde, SQL Server ilk nesnenin sahibi çağrı nesnesi (önceki bağlantı zincirindeki) sahibine karşılaştırır. Her iki nesnenin aynı sahibi varsa, başvurulan nesnenin izinlerini denetlenmez. Nesneyi farklı bir sahibi olan başka bir nesneye eriştiğinde, sahiplik zinciri kopmuş ve SQL Server, arayanın güvenlik bağlamı denetlemeniz gerekir.  
  
## <a name="procedural-code-and-ownership-chaining"></a>Yordam kodu ve sahiplik zinciri  
 Bir kullanıcı bir tablodan veri seçen bir saklı yordam Yürütme izinleri verilir varsayalım. Saklı yordamı ve tabloyu aynı sahibi varsa, kullanıcı tablosunda herhangi bir izni verilmesi gerekmez ve izinleri engellenebilir. Ancak, saklı yordamı ve tabloyu farklı sahipleri varsa, SQL Server verileri için erişime izin vermeden önce kullanıcının izinlerini tablosunda denetlemelisiniz.  
  
> [!NOTE]
>  Sahiplik zinciri, dinamik SQL deyimleri söz konusu olduğunda geçerli değildir. SQL deyimini yürütür bir yordam çağırmak için çağırana temel alınan tablolar üzerindeki izinleri uygulamanızı SQL ekleme saldırısına karşı savunmasız bırakır verilmesi gerekir. SQL Server, kimliğe bürünme ve temel alınan tablolar izin verme gerektirmeyen sertifikaları modülleriyle imzalama gibi yeni bir mekanizma sağlar. Bunlar, CLR saklı yordamları ile de kullanılabilir.  
  
## <a name="external-resources"></a>Dış Kaynaklar  
 Daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[İzinler](/sql/relational-databases/security/permissions-database-engine)|İzinleri hiyerarşi, Katalog görünümleri ve sabit sunucu ve veritabanı rolleri, izinler açıklayan konuları içerir.|
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET Uygulamalarının Güvenliğini Sağlama](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [SQL Server'da Uygulama Güvenliği Senaryoları](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [SQL Server’da Kimlik Doğrulaması](../../../../../docs/framework/data/adonet/sql/authentication-in-sql-server.md)  
 [SQL Server’da Sunucu ve Veritabanı Rolleri](../../../../../docs/framework/data/adonet/sql/server-and-database-roles-in-sql-server.md)  
 [SQL Server'da Sahiplik ve Kullanıcı Şeması Ayrımı](../../../../../docs/framework/data/adonet/sql/ownership-and-user-schema-separation-in-sql-server.md)  
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)

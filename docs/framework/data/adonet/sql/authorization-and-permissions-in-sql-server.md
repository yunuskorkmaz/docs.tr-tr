---
title: SQL Server’da Yetkilendirme ve İzinler
ms.date: 03/30/2017
ms.assetid: d340405c-91f4-4837-a3cc-a238ee89888a
ms.openlocfilehash: c9b041a078494cd29d6cab5297728d233dafa236
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782592"
---
# <a name="authorization-and-permissions-in-sql-server"></a>SQL Server’da Yetkilendirme ve İzinler
Veritabanı nesneleri oluşturduğunuzda, kullanıcılara kullanıcıların erişimini sağlamak için açıkça izin vermeniz gerekir. Her güvenli kılınabilir nesne, izin deyimleri kullanılarak bir sorumluya verilebilecek izinlere sahiptir.  
  
## <a name="the-principle-of-least-privilege"></a>En az ayrıcalık Ilkesi  
 En az ayrıcalıklı kullanıcı hesabı (LUA) yaklaşımı kullanarak bir uygulama geliştirmek, savunma ve güvenlik tehditlerine karşı derinlemesine savunma stratejisinin önemli bir parçasıdır. LUA yaklaşımı, kullanıcıların en az ayrıcalık ilkesini izlemesini ve her zaman sınırlı kullanıcı hesaplarıyla oturum açmasını sağlar. Yönetim görevleri, sabit sunucu rolleri kullanılarak bölünür ve `sysadmin` sabit sunucu rolünün kullanımı ciddi ölçüde kısıtlıdır.  
  
 Veritabanı kullanıcılarına izin verirken en az ayrıcalık ilkesini her zaman izleyin. Belirli bir görevi gerçekleştirmek için Kullanıcı veya rol için gereken en düşük izinleri verin.  
  
> [!IMPORTANT]
> LUA yaklaşımını kullanarak bir uygulamayı geliştirmek ve test etmek, geliştirme sürecine bir zorluk derecesi ekler. Bir sistem yöneticisi veya veritabanı sahibi olarak oturum açarken, bir LUA hesabı kullandığından nesne oluşturmak ve kod yazmak daha kolay. Ancak, yüksek ayrıcalıklı bir hesap kullanan uygulamalar geliştirmek, en az ayrıcalıklı kullanıcı doğru çalışması için yükseltilmiş izinler gerektiren bir uygulamayı çalıştırmayı denediklerinde azaltılmış işlevselliğin etkisini olumsuz etkileyebilir. Kayıp işlevselliği yeniden almak için kullanıcılara aşırı izin verilmesi, uygulamanızı saldırılara karşı savunmasız bırakabilir. Bir LUA hesabıyla oturum açmış uygulamanızı tasarlamak, geliştirmek ve test etmek, önemli sürprizleri ortadan kaldıran ve hızlı bir düzeltme olarak yükseltilmiş ayrıcalıklar veren güvenlik planlamasına disiplinli bir yaklaşım uygular. Uygulamanızın Windows kimlik doğrulaması kullanılarak dağıtılması amaçlansa bile, test için SQL Server bir oturum açma kullanabilirsiniz.  
  
## <a name="role-based-permissions"></a>Rol tabanlı Izinler  
 Kullanıcılar yerine roller için izin verme güvenlik yönetimini basitleştirir. Rollere atanan izin kümeleri rolün tüm üyeleri tarafından devralınır. Bir role Kullanıcı eklemek veya bir rol kaldırmak daha kolaydır, tek tek kullanıcılar için ayrı izin kümeleri yeniden oluşturulur. Roller iç içe olabilir; Ancak, çok fazla iç içe geçme düzeyi performansı düşürebilir. Ayrıca, izin atanmasını kolaylaştırmak için, sabit veritabanı rollerine kullanıcılar ekleyebilirsiniz.  
  
 Şema düzeyinde izin verebilirsiniz. Kullanıcılar, şemada oluşturulan tüm yeni nesnelerdeki izinleri otomatik olarak devralınır; yeni nesneler oluşturulduğundan izin vermeniz gerekmez.  
  
## <a name="permissions-through-procedural-code"></a>Yordamsal kod aracılığıyla izinler  
 Saklı yordamlar ve Kullanıcı tanımlı işlevler gibi modüller aracılığıyla veri erişiminin kapsüllenmesi, uygulamanız etrafında ek bir koruma katmanı sağlar. Yalnızca, tablolar gibi temel nesnelerin izinlerini reddetirken yalnızca saklı yordamlara veya işlevlere izinler vererek kullanıcıların veritabanı nesneleriyle doğrudan etkileşimde olmasını engelleyebilirsiniz. SQL Server sahiplik zincirleyerek bunu elde eder.  
  
## <a name="permission-statements"></a>İzin deyimleri  
 Üç Transact-SQL izin deyimleri aşağıdaki tabloda açıklanmıştır.  
  
|İzin ekstresi|Açıklama|  
|--------------------------|-----------------|  
|SEMANTIĞI|İzin verir.|  
|HEDEFINI|Bir izni iptal eder. Bu, yeni bir nesnenin varsayılan durumudur. Bir kullanıcı veya rolden iptal edilen izin, hala asıl rolün atandığı diğer gruplardan veya rollerden devralınabilir.|  
|REDDEDEBILIR|REDDETME, devralınmaması için bir izni iptal eder. Reddet, ' nin nesne sahipleri veya üyeleri için uygulanmadığından, tüm izinlerin önünde `sysadmin`önceliklidir. Bir nesne üzerindeki izinleri bir `public` rol için reddetmeniz durumunda, nesne sahipleri ve `sysadmin` üyeleri hariç tüm kullanıcılar ve roller için reddedilir.|  
  
- GRANT deyimleri, veritabanı kullanıcıları tarafından devralınabilir bir gruba veya role izin atayabilir. Ancak reddetme deyimi diğer tüm izin deyimlerine göre önceliklidir. Bu nedenle, izin reddedilmiş bir Kullanıcı başka bir rolden onu alamaz.  
  
> [!NOTE]
> `sysadmin` Sabit sunucu rolü ve nesne sahiplerinin üyelerine izin verilmez.  
  
## <a name="ownership-chains"></a>Sahiplik zincirleri  
 SQL Server, yalnızca izin verilen sorumlular nesnelere erişebilmesini sağlar. Birden çok veritabanı nesnesi birbirlerine erişebildiğinde, dizi bir zincir olarak bilinir. SQL Server zincirdeki bağlantılardan geçiş yaparken, izinleri her öğeye ayrı olarak erişeceklerinden farklı şekilde değerlendirir. Bir nesne bir zincir aracılığıyla erişildiğinde, SQL Server önce nesnenin sahibini çağıran nesnenin sahibine (zincirdeki önceki bağlantı) karşılaştırır. Her iki nesne de aynı sahibe sahip ise, başvurulan nesne üzerindeki izinler denetlenmez. Bir nesne farklı bir sahibe sahip olan başka bir nesneye eriştiğinde, sahiplik zinciri bozulur ve SQL Server çağıranın güvenlik bağlamını denetlemesi gerekir.  
  
## <a name="procedural-code-and-ownership-chaining"></a>Yordamsal kod ve sahiplik zinciri  
 Bir kullanıcıya, bir tablodaki verileri seçen saklı yordamda yürütme izinleri verildiğini varsayalım. Saklı yordam ve tablo aynı sahibe sahip ise, kullanıcıya tablo üzerinde herhangi bir izin verilmesi gerekmez, hatta izin reddedilebilir. Ancak, saklı yordamın ve tablonun farklı sahipleri varsa, verilere erişim izni vermeden önce SQL Server kullanıcının tablodaki izinlerini denetlemesi gerekir.  
  
> [!NOTE]
> Dinamik SQL deyimleri söz konusu olduğunda sahiplik zinciri uygulanmaz. Bir SQL ifadesini yürüten bir yordamı çağırmak için, çağıran tablo üzerinde izin verilmelidir ve uygulamanızı SQL ekleme saldırısına karşı savunmasız bırakır. SQL Server, ilişkili tablolarda izin verilmesini gerektirmeyen sertifikalarla kimliğe bürünme ve imzalama modülleri gibi yeni mekanizmalar sağlar. Bunlar, CLR saklı yordamları ile de kullanılabilir.  
  
## <a name="external-resources"></a>Dış Kaynaklar  
 Daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[İzinler](/sql/relational-databases/security/permissions-database-engine)|İzin hiyerarşisini, katalog görünümlerini ve sabit sunucu ve veritabanı rollerinin izinlerini açıklayan konuları içerir.|
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET Uygulamalarının Güvenliğini Sağlama](../securing-ado-net-applications.md)
- [SQL Server'da Uygulama Güvenliği Senaryoları](application-security-scenarios-in-sql-server.md)
- [SQL Server’da Kimlik Doğrulaması](authentication-in-sql-server.md)
- [SQL Server’da Sunucu ve Veritabanı Rolleri](server-and-database-roles-in-sql-server.md)
- [SQL Server'da Sahiplik ve Kullanıcı Şeması Ayrımı](ownership-and-user-schema-separation-in-sql-server.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)

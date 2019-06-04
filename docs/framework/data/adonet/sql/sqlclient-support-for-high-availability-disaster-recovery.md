---
title: Yüksek Kullanılabilirlik, Olağanüstü Durum Kurtarma için SqlClient Desteği
ms.date: 03/30/2017
ms.assetid: 61e0b396-09d7-4e13-9711-7dcbcbd103a0
ms.openlocfilehash: aa4c716dc1b27d50620777613e698ca6dbab31d8
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66487642"
---
# <a name="sqlclient-support-for-high-availability-disaster-recovery"></a>Yüksek Kullanılabilirlik, Olağanüstü Durum Kurtarma için SqlClient Desteği
Bu konu, yüksek kullanılabilirlik, olağanüstü durum kurtarma--AlwaysOn Kullanılabilirlik grupları için SqlClient desteği (.NET Framework 4.5 eklenir) açıklar.  AlwaysOn Kullanılabilirlik grupları özelliği SQL Server 2012'ye eklendi. AlwaysOn Kullanılabilirlik grupları hakkında daha fazla bilgi için SQL Server Books Online'a bakın.  
  
 Şimdi, kullanılabilirlik grubu dinleyicisini belirtin bir (yüksek kullanılabilirlik, olağanüstü durum kurtarma) kullanılabilirlik grubu (ağ) veya SQL Server 2012 yük devretme kümesi örneği bağlantı özelliği. Devreder bir AlwaysOn veritabanı için SqlClient uygulama bağlıysa, özgün bağlantı bozuk ve uygulamanın yük devretme sonrasında çalışmaya devam etmek için yeni bir bağlantı açmanız gerekir.  
  
 Bir kullanılabilirlik grubu dinleyicisi veya SQL Server 2012 yük devretme kümesi örneği bağlanmıyorsanız ve bir ana bilgisayar adı ile ilişkili birden çok IP adresi varsa, SqlClient sırayla DNS girişi ile ilişkili tüm IP adresleri üzerinden yineleme. Bu zaman DNS sunucusu tarafından döndürülen ilk IP adresini bir ağ arabirim kartı (NIC) bağlı değilse alıcı olabilir. Bir kullanılabilirlik grubu dinleyicisi veya SQL Server 2012 yük devretme kümesi örneği bağlanırken SqlClient paralel olarak tüm IP adreslerinin bağlantı dener ve bağlantı denemesi başarılı olursa, sürücü bekleyen herhangi bir bağlantı atacak çalışır.  
  
> [!NOTE]
>  Bağlantı zaman aşımı süresini artırmak ve bağlantı yeniden deneme mantığını uygulayan bir uygulama bir kullanılabilirlik grubuna bağlanacak olasılığını artırır. Ayrıca, bir bağlantı nedeniyle bir yük devretme başarısız olabileceğinden, onu yeniden kadar başarısız bir bağlantıyı yeniden deneniyor. bağlantı yeniden deneme mantığı uygulamalıdır.  
  
 Aşağıdaki bağlantı özelliklerini SqlClient .NET Framework 4.5 de eklenmiştir:  
  
- `ApplicationIntent`  
  
- `MultiSubnetFailover`  
  
 Bu bağlantı dizesi anahtar sözcükler ile programlı bir şekilde değiştirebilirsiniz:  
  
1. <xref:System.Data.SqlClient.SqlConnectionStringBuilder.ApplicationIntent%2A>  
  
2. <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A>  

> [!NOTE]
>  Ayarı `MultiSubnetFailover` için `true` .NET Framework 4.6.1 veya sonraki sürümleriyle gerekli değildir.
  
## <a name="connecting-with-multisubnetfailover"></a>MultiSubnetFailover ile bağlanma  
 Her zaman belirtin `MultiSubnetFailover=True` bir kullanılabilirlik grubu dinleyicisi SQL Server 2012 veya SQL Server 2012 yük devretme kümesi örneği bağlanırken. `MultiSubnetFailover` Yük devretme kümesi örneği SQL Server 2012 ve edecek ve tüm kullanılabilirlik grupları tek ve birden çok alt ağ AlwaysOn topolojiler için yük devretme süreyi önemli ölçüde azaltmaya için daha hızlı yük devretmeyi etkinleştirir. Birden çok alt ağ bir yük devretme sırasında istemci bağlantıları paralel olarak çalışacaktır. Alt ağ bir yük devretme sırasında TCP bağlantısı agresif yeniden deneyecek.  
  
 `MultiSubnetFailover` Bağlantı özelliği, uygulama bir kullanılabilirlik grubu veya SQL Server 2012 yük devretme kümesi örneği dağıtıldığını ve SqlClient deneyerek, birincil SQL Server örneğinde veritabanına bağlanmaya çalışacaktır gösterir tüm IP adresine bağlanın. Zaman `MultiSubnetFailover=True` belirtilen bir bağlantı için istemci TCP bağlantı girişimleri işletim sisteminin varsayılan TCP yeniden aktarım aralığından daha hızlı yeniden dener. Bu yük devretme işleminden sonra daha hızlı yeniden bağlanma AlwaysOn Kullanılabilirlik grubu veya bir AlwaysOn yük devretme kümesi örneği sağlar ve hem tek ve çoklu subnet kullanılabilirlik grupları ve yük devretme kümesi örnekleri için geçerlidir.  
  
 Bağlantı dizesi anahtar sözcükler sqlclient'ta hakkında daha fazla bilgi için bkz. <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
 Belirtme `MultiSubnetFailover=True` ne zaman bir kullanılabilirlik grubu dinleyicisi veya SQL Server 2012 yük devretme kümesi örneği dışında bir şey bağlanma olumsuz bir etkisi neden olabilir ve desteklenmiyor.  
  
 Bir kullanılabilirlik grubuna bir sunucu veya SQL Server 2012 yük devretme kümesi örneği bağlanmak için aşağıdaki yönergeleri kullanın:  
  
- Kullanım `MultiSubnetFailover` bağlantı özelliği için bir tek alt ağ veya birden çok alt ağ; bağlanırken, her ikisi için de performansı iyileştirir.  
  
- Bir kullanılabilirlik grubuna bağlanmak için bağlantı dizenizi sunucusu olarak kullanılabilirlik grubunun kullanılabilirlik grubu dinleyicisini belirtin.  
  
- 64'ten fazla IP adresi ile yapılandırılmış bir SQL Server'a bağlanırken bağlantı hatası neden olur.  
  
- Kullanan bir uygulamanın davranışını `MultiSubnetFailover` bağlantı özelliği, kimlik doğrulama türüne göre değil etkilenir: SQL Server kimlik doğrulaması, Kerberos kimlik doğrulaması veya Windows kimlik doğrulaması.  
  
- Değeri Artır `Connect Timeout` için yük devretme zamanına uyum sağlayamayacak ve uygulama bağlantı yeniden deneme girişimleri azaltmak için.  
  
- Dağıtılmış işlemler desteklenmez.  
  
 Bir ikincil çoğaltma konumuna bağlanma, salt okunur yönlendirme etkin değilse, aşağıdaki durumlarda başarısız olur:  
  
1. İkincil çoğaltma konumu bağlantılarını kabul edecek şekilde yapılandırılmamışsa.  
  
2. Bir uygulama kullanıyorsa `ApplicationIntent=ReadWrite` (aşağıda açıklanmıştır) ve ikincil çoğaltma konumu salt okunur erişim için yapılandırılır.  
  
 <xref:System.Data.SqlClient.SqlDependency> salt okunur ikincil çoğaltmalarda desteklenmiyor.  
  
 Birincil kopya salt okunur iş yükleri reddedecek şekilde yapılandırılmışsa ve bağlantı dizesini içeren bir bağlantı başarısız olur `ApplicationIntent=ReadOnly`.  
  
## <a name="upgrading-to-use-multi-subnet-clusters-from-database-mirroring"></a>Birden çok alt ağ kullanmak için yükseltme kümeleri gelen veritabanı yansıtma  
 Bağlantı hatası (<xref:System.ArgumentException>) meydana gelir `MultiSubnetFailover` ve `Failover Partner` bağlantı sözcükler bağlantı dizesinde mevcut veya `MultiSubnetFailover=True` ve TCP dışındaki bir protokolü kullanılır. Hata (<xref:System.Data.SqlClient.SqlException>) da meydana gelir `MultiSubnetFailover` kullanılır ve SQL Server'ı bir veritabanı yansıtma çiftinin bir parçası olduğunu gösteren bir yük devretme iş ortağı yanıt verir.  
  
 Yükseltirseniz SqlClient uygulama şu anda birden çok alt senaryo için veritabanı yansıtma kullanır, kaldırmalısınız `Failover Partner` bağlantı özelliği değiştirin `MultiSubnetFailover` kümesine `True` ve sunucu adını değiştirin bir kullanılabilirlik grubu dinleyicisi ile bağlantı dizesi. Bir bağlantı dizesi kullanması durumunda `Failover Partner` ve `MultiSubnetFailover=True`, sürücü bir hata oluşturur. Ancak, bir bağlantı dizesi kullanması durumunda `Failover Partner` ve `MultiSubnetFailover=False` (veya `ApplicationIntent=ReadWrite`), uygulama, veritabanı yansıtma kullanır.  
  
 Sürücü AG, birincil veritabanında veritabanı yansıtma kullanılıyorsa ve bir hata döndürecektir `MultiSubnetFailover=True` bir kullanılabilirlik grubu dinleyicisi yerine birincil veritabanına bağlanacak bağlantı dizesini kullanılır.  
  
## <a name="specifying-application-intent"></a>Uygulama hedefi belirtme  
 Zaman `ApplicationIntent=ReadOnly`, istemci bir AlwaysOn etkin veritabanına bağlanırken bir okuma iş yükü ister. Sunucu bağlantısı zaman ve USE veritabanı deyimi sırasında ancak yalnızca bir Always On etkin veritabanı amaç zorlar.  
  
 `ApplicationIntent` Anahtar sözcüğü, eski, salt okunur veritabanları ile çalışmaz.  
  
 Bir veritabanı izin verebilir veya hedeflenen AlwaysOn veritabanı üzerindeki okuma iş yükleri izin vermeyin. (Bunun `ALLOW_CONNECTIONS` yan tümcesi `PRIMARY_ROLE` ve `SECONDARY_ROLE`Transact-SQL deyimleriyle.)  
  
 `ApplicationIntent` Anahtar sözcüğü, salt okunur yönlendirme etkinleştirmek için kullanılır.  
  
## <a name="read-only-routing"></a>Salt okunur yönlendirme  
 Salt okunur yönlendirme okuma yalnızca bir veritabanı çoğaltmasını kullanılabilirliğini sağlayan bir özelliktir. Salt okunur yönlendirme etkinleştirmek için:  
  
1. Bir Always On kullanılabilirlik grubu kullanılabilirlik grubu dinleyicisi için bağlanmanız gerekir.  
  
2. `ApplicationIntent` Bağlantı dizesi anahtar kelimesi ayarlanmalıdır `ReadOnly`.  
  
3. Kullanılabilirlik grubu salt okunur yönlendirme etkinleştirmek için veritabanı yöneticisi tarafından yapılandırılmış olması gerekir.  
  
 Salt okunur yönlendirme kullanarak birden çok bağlantı tümü aynı salt okunur çoğaltmaya bağlanmaya mümkündür. Salt okunur kopyaya farklı istemci bağlantıları veritabanı eşitleme değişiklikleri veya sunucunun yönlendirme yapılandırması değişiklikleri neden olabilir. Tüm salt okunur istekler aynı salt okunur kopyaya bağlanmalarını sağlamak için bir kullanılabilirlik grubu dinleyicisi için geçmeyin `Data Source` bağlantı dizesi anahtar sözcüğü. Bunun yerine, salt okunur örneğinin adını belirtin.  
  
 Salt okunur yönlendirme yalnızca Yönlendirme okuma önce birincil siteye bağlanır ve ardından en iyi kullanılabilir okunabilir ikincil için görünür olduğundan, birincil siteye bağlanan daha uzun sürebilir. Bu nedenle, oturum açma zaman aşımı artırmalısınız.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SQL Server Özellikleri ve ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-features-and-adonet.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)

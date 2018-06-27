---
title: Yüksek kullanılabilirlik, olağanüstü durum kurtarma SqlClient desteği
ms.date: 03/30/2017
ms.assetid: 61e0b396-09d7-4e13-9711-7dcbcbd103a0
ms.openlocfilehash: 001b99d7a7ec7dd7e483887ceeb0b2563a46da0a
ms.sourcegitcommit: ed7b4b9b77d35e94a35a2634e8c874f46603fb2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36948530"
---
# <a name="sqlclient-support-for-high-availability-disaster-recovery"></a>Yüksek kullanılabilirlik, olağanüstü durum kurtarma SqlClient desteği
Bu konuda ele alınmıştır SqlClient desteği (eklenen [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)]) yüksek kullanılabilirlik, olağanüstü durum kurtarma--AlwaysOn Kullanılabilirlik grupları.  AlwaysOn Kullanılabilirlik grupları özelliği SQL Server 2012'ye eklenmiştir. AlwaysOn Kullanılabilirlik grupları hakkında daha fazla bilgi için SQL Server Books Online'a bakın.  
  
 Kullanılabilirlik grubu dinleyicisi, artık belirtebilirsiniz bir (yüksek kullanılabilirlik, olağanüstü durum kurtarma) kullanılabilirlik grubu (ağ) veya SQL Server 2012 yük devretme kümesi örneği bağlantı özelliği. SqlClient uygulama yöneltilir bir AlwaysOn veritabanına bağlıysa, özgün bağlantı bozuluyor ve uygulama yük devretme sonrasında çalışmaya devam etmek için yeni bir bağlantı açmanız gerekir.  
  
 Bir kullanılabilirlik grubu dinleyicisi veya SQL Server 2012 yük devretme kümesi örneği bağlanma değil ve bir ana bilgisayar adı ile ilişkili birden çok IP adresi, SqlClient sırayla DNS girişi ile ilişkili tüm IP adreslerini yinelemek. Bu, tüm ağ arabirim kartı (NIC) DNS sunucusu tarafından döndürülen ilk IP adresine bağlı değilse zun olabilir. Bir kullanılabilirlik grubu dinleyicisi veya SQL Server 2012 yük devretme kümesi örneği bağlanırken SqlClient paralel olarak tüm IP adresleri bağlantı dener ve bağlantı denemesi başarılı olursa, sürücü herhangi bir bekleyen bağlantısı atar çalışır.  
  
> [!NOTE]
>  Bağlantı zaman aşımı süresini artırmak ve bağlantı yeniden deneme mantığı uygulamak bir uygulama bir kullanılabilirlik grubuna bağlanır olasılığı artar. Ayrıca, bir bağlantı nedeniyle yük devretme başarısız olabileceğinden onu yeniden bağlandığında kadar başarısız bağlantı yeniden deneniyor bağlantı yeniden deneme mantığı, uygulamanız gerekir.  
  
 Aşağıdaki bağlantı özelliklerini SqlClient eklenme [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)]:  
  
-   `ApplicationIntent`  
  
-   `MultiSubnetFailover`  
  
 Bu bağlantı dizesi anahtar sözcükleriyle program aracılığıyla değiştirebilirsiniz:  
  
1.  <xref:System.Data.SqlClient.SqlConnectionStringBuilder.ApplicationIntent%2A>  
  
2.  <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A>  

> [!NOTE]
>  Ayarı `MultiSubnetFailover` için `true` ile gerekli değildir [!INCLUDE[net_v461](../../../../../includes/net-v461-md.md)] veya sonraki sürümler.
  
## <a name="connecting-with-multisubnetfailover"></a>MultiSubnetFailover ile bağlanma  
 Her zaman belirtmeniz `MultiSubnetFailover=True` bir SQL Server 2012 kullanılabilirlik grubu dinleyicisi veya SQL Server 2012 yük devretme kümesi örneği bağlanırken. `MultiSubnetFailover` Yük devretme kümesi örneği SQL Server 2012 ve olacaktır ve tüm kullanılabilirlik grupları tek ve birden çok alt ağ AlwaysOn Topolojileri için yük devretme süresini önemli ölçüde azaltmak için daha hızlı yük devretmeyi etkinleştirir. Birden çok alt ağ yük devretme sırasında istemci bağlantıları paralel çalışacak. Bir alt ağ yük devretme sırasında titizlikle TCP bağlantısı yeniden deneyecek.  
  
 `MultiSubnetFailover` Bağlantı özelliği, bir kullanılabilirlik grubu ya da SQL Server 2012 yük devretme kümesi örneği uygulamanın dağıtıldığı ve SqlClient silmeyi deneyerek birincil SQL Server örneğinde veritabanına bağlanmak deneyecek gösterir tüm IP adresine bağlanın. Zaman `MultiSubnetFailover=True` belirtilen bir bağlantı için istemci TCP bağlantı denemeleri işletim sisteminin varsayılan TCP yeniden aktarım aralıklar daha hızlı yeniden dener. Bu bir AlwaysOn Kullanılabilirlik grubu veya bir AlwaysOn yük devretme kümesi örneği yük devretme işleminden sonra daha hızlı yeniden bağlanmayı sağlar ve hem tek ve birden çok subnet kullanılabilirlik grupları ve yük devretme kümesi örnekleri için geçerlidir.  
  
 SqlClient bağlantı dizesi anahtar sözcükler hakkında daha fazla bilgi için bkz: <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
 Belirtme `MultiSubnetFailover=True` ne zaman bir kullanılabilirlik grubu dinleyicisi veya SQL Server 2012 yük devretme kümesi örneği dışında bir şey bağlanma olumsuz bir etkisi neden olabilir ve desteklenmiyor.  
  
 Bir kullanılabilirlik grubundaki bir sunucuya veya SQL Server 2012 yük devretme kümesi örneği bağlanmak için aşağıdaki kılavuzları kullanın:  
  
-   Kullanım `MultiSubnetFailover` bağlantı özelliği için bir tek alt ağ veya birden çok alt ağ; bağlanırken her ikisi için de performansı iyileştirir.  
  
-   Bir kullanılabilirlik grubuna bağlanmak için kullanılabilirlik grubunun kullanılabilirlik grubu dinleyicisinin bağlantı dizenizi sunucusu olarak belirtin.  
  
-   Bir SQL Server'a bağlanırken örneği 64 taneden fazla IP adresleriyle yapılandırılmış bir bağlantı hatası neden olur.  
  
-   Kullanan bir uygulama davranışını `MultiSubnetFailover` bağlantı özelliği kimlik doğrulama türüne göre etkilenmez: SQL Server kimlik doğrulaması, Kerberos kimlik doğrulaması veya Windows kimlik doğrulaması.  
  
-   Değerini artırın `Connect Timeout` uyum sağlamak için yük devretme süresi ve uygulama bağlantı denemeleri azaltmak için.  
  
-   Dağıtılmış işlemler desteklenmiyor.  
  
 Bir ikincil çoğaltma konumuna bağlanma, salt okunur yönlendirme etkin değilse, aşağıdaki durumlarda başarısız olur:  
  
1.  İkincil çoğaltma konumun bağlantılarını kabul edecek şekilde yapılandırılmazsa.  
  
2.  Bir uygulama kullanıyorsa, `ApplicationIntent=ReadWrite` (aşağıda açıklanmıştır) ve ikincil çoğaltma konumu salt okunur erişim için yapılandırıldı.  
  
 <xref:System.Data.SqlClient.SqlDependency> salt okunur ikincil çoğaltmaların üzerine desteklenmiyor.  
  
 Bir bağlantı birincil kopya salt okunur iş yükleri reddedecek şekilde yapılandırılmış ve bağlantı dizesini içeriyorsa başarısız olur `ApplicationIntent=ReadOnly`.  
  
## <a name="upgrading-to-use-multi-subnet-clusters-from-database-mirroring"></a>Birden çok alt ağ kullanmak üzere yükseltmenin kümeleri veritabanı yansıtma  
 Bağlantı hatası (<xref:System.ArgumentException>) varsa ortaya çıkar `MultiSubnetFailover` ve `Failover Partner` bağlantı sözcükler bağlantı dizesinde mevcut veya `MultiSubnetFailover=True` ve TCP dışında bir protokolü kullanılır. Hata (<xref:System.Data.SqlClient.SqlException>) de oluşacaktır `MultiSubnetFailover` kullanılır ve SQL Server veritabanı çifti yansıtma parçası olduğunu gösteren bir yük devretme ortağı yanıt verir.  
  
 Yükseltirseniz, birden çok alt senaryo için veritabanı yansıtma SqlClient uygulama şu anda kullanır, kaldırmanız gerekir `Failover Partner` bağlantı özelliği ve bunların yerine `MultiSubnetFailover` kümesine `True` ve sunucu adını değiştirin bir kullanılabilirlik grubu dinleyicisi ile bağlantı dizesi. Bir bağlantı dizesi kullanıyorsa `Failover Partner` ve `MultiSubnetFailover=True`, sürücü bir hata oluşturur. Ancak, bir bağlantı dizesi kullanıyorsa `Failover Partner` ve `MultiSubnetFailover=False` (veya `ApplicationIntent=ReadWrite`), uygulama, veritabanı yansıtma kullanacak.  
  
 Sürücü veritabanı yansıtma AG birincil veritabanında kullanılırsa ve bir hata döndürecektir `MultiSubnetFailover=True` yerine birincil veritabanı bir kullanılabilirlik grubu dinleyicisi için bağlandığı bağlantı dizesinde kullanılır.  
  
## <a name="specifying-application-intent"></a>Uygulama hedefi belirtme  
 Zaman `ApplicationIntent=ReadOnly`, istemci bir AlwaysOn etkin veritabanına bağlanırken okuma iş yükünü ister. Sunucu bağlantısı zaman ve USE veritabanı deyimi sırasında ancak yalnızca bir Always On etkin veritabanı hedefi zorlar.  
  
 `ApplicationIntent` Anahtar sözcüğü eski, salt okunur veritabanları ile çalışmaz.  
  
 Bir veritabanı verin veya hedeflenen AlwaysOn veritabanı üzerinde okuma iş yükleri vermeyin. (Bu gerçekleştirilir `ALLOW_CONNECTIONS` yan tümcesi `PRIMARY_ROLE` ve `SECONDARY_ROLE` [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] deyimleri.)  
  
 `ApplicationIntent` Anahtar sözcüğü salt okunur yönlendirmeyi etkinleştirmek için kullanılır.  
  
## <a name="read-only-routing"></a>Salt okunur yönlendirme  
 Yönlendirme salt okunur bir veritabanının okuma yalnızca çoğaltmasını kullanılabilirliğinden emin olabilirsiniz bir özelliktir. Salt okunur yönlendirmeyi etkinleştirmek için:  
  
1.  Bir her zaman kullanılabilirlik grubu üzerinde kullanılabilirlik grubu dinleyicisi bağlanmanız gerekir.  
  
2.  `ApplicationIntent` Bağlantı dizesi anahtar sözcüğü ayarlanmalıdır `ReadOnly`.  
  
3.  Kullanılabilirlik grubu salt okunur yönlendirmeyi etkinleştirmek için veritabanı yöneticisi tarafından yapılandırılması gerekir.  
  
 Salt okunur yönlendirme kullanarak birden çok bağlantı tümü aynı salt okunur kopyaya bağlanın mümkündür. Farklı salt okunur çoğaltmaları istemci bağlantıları veritabanı eşitleme değişiklikleri veya sunucunun yönlendirme yapılandırmasındaki değişiklikler neden olabilir. Tüm salt okunur istekleri aynı salt okunur kopyaya bağlandığından emin olmak için bir kullanılabilirlik grubu dinleyicisi geçmeyin `Data Source` bağlantı dizesi anahtar sözcüğü. Bunun yerine, salt okunur örneğinin adını belirtin.  
  
 Salt okunur yönlendirme için birincil yalnızca Yönlendirme okuma ilk birincil bağlanır ve en iyi kullanılabilir okunabilir ikincil için görünür olduğundan bağlanmaktan daha uzun sürebilir. Bu nedenle, oturum açma zaman aşımı artırmanız gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [SQL Server Özellikleri ve ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-features-and-adonet.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)

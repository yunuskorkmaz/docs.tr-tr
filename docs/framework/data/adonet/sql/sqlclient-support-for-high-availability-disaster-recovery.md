---
title: Yüksek Kullanılabilirlik, Olağanüstü Durum Kurtarma için SqlClient Desteği
ms.date: 03/30/2017
ms.assetid: 61e0b396-09d7-4e13-9711-7dcbcbd103a0
ms.openlocfilehash: 104fdd78ce3f4b9c18f09fc41fddebe46815d217
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938466"
---
# <a name="sqlclient-support-for-high-availability-disaster-recovery"></a>Yüksek Kullanılabilirlik, Olağanüstü Durum Kurtarma için SqlClient Desteği
Bu konuda, yüksek kullanılabilirlik, olağanüstü durum kurtarma--AlwaysOn Kullanılabilirlik Grupları için SqlClient desteği (.NET Framework 4,5 ' de eklenmiştir) açıklanmaktadır.  AlwaysOn Kullanılabilirlik Grupları özellik SQL Server 2012 eklendi. AlwaysOn Kullanılabilirlik Grupları hakkında daha fazla bilgi için bkz. SQL Server Books Online.  
  
 Artık bağlantı özelliğinde bir (yüksek kullanılabilirlik, olağanüstü durum kurtarma) kullanılabilirlik grubu (AG) veya SQL Server 2012 yük devretme kümesi örneğinin kullanılabilirlik grubu dinleyicisini belirtebilirsiniz. Bir SqlClient uygulaması yükü devredildiği bir AlwaysOn veritabanına bağlıysa, özgün bağlantı bozulur ve uygulamanın yük devretmeden sonra çalışmaya devam etmesi için yeni bir bağlantı açması gerekir.  
  
 Bir kullanılabilirlik grubu dinleyicisine veya SQL Server 2012 yük devretme kümesi örneğine bağlandıysanız ve birden çok IP adresi bir ana bilgisayar adıyla ilişkilendirilirse, SqlClient DNS girdisiyle ilişkili tüm IP adresleri üzerinden sırayla yinelenir. Bu, DNS sunucusu tarafından döndürülen ilk IP adresi herhangi bir ağ arabirim kartına (NIC) bağlanmazsa zaman alabilir. Bir kullanılabilirlik grubu dinleyicisine veya SQL Server 2012 yük devretme kümesi örneğine bağlanırken, SqlClient tüm IP adreslerine paralel olarak bağlantı kurmaya çalışır ve bağlantı girişimi başarılı olursa sürücü bekleyen tüm bağlantıları atar denemelerini.  
  
> [!NOTE]
> Bağlantı zaman aşımını artırma ve bağlantı yeniden deneme mantığı uygulama, bir uygulamanın bir kullanılabilirlik grubuna bağlanması olasılığını artırır. Ayrıca, bir bağlantı yük devretme nedeniyle başarısız olabileceğinden, bağlantısı yeniden bağlanana kadar başarısız bağlantıyı yeniden denemeden bağlantı yeniden deneme mantığını uygulamanız gerekir.  
  
 Aşağıdaki bağlantı özellikleri .NET Framework 4,5 ' de SqlClient eklendi:  
  
- `ApplicationIntent`  
  
- `MultiSubnetFailover`  
  
 Bu bağlantı dizesi anahtar sözcüklerini programlı bir şekilde değiştirebilirsiniz:  
  
1. <xref:System.Data.SqlClient.SqlConnectionStringBuilder.ApplicationIntent%2A>  
  
2. <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A>  

> [!NOTE]
> .NET Framework 4.6.1 veya sonraki sürümlerde gerekli değildir.`true` `MultiSubnetFailover`
  
## <a name="connecting-with-multisubnetfailover"></a>MultiSubnetFailover Ile bağlanma  
 SQL Server 2012 `MultiSubnetFailover=True` kullanılabilirlik grubu dinleyicisine veya SQL Server 2012 yük devretme kümesi örneğine bağlanırken her zaman belirtin. `MultiSubnetFailover`SQL Server 2012 ' deki tüm kullanılabilirlik grupları ve yük devretme kümesi örneği için daha hızlı yük devretmeyi sağlar ve tek ve çok alt ağ AlwaysOn topolojileri için yük devretme süresini önemli ölçüde azaltır. Çoklu alt ağ yük devri sırasında, istemci bağlantıları paralel olarak dener. Alt ağ yük devretmesi sırasında TCP bağlantısını yeniden dener.  
  
 `MultiSubnetFailover` Connection özelliği, uygulamanın bir kullanılabilirlik grubuna veya SQL Server 2012 yük devretme kümesi örneğine dağıtıldığını ve bu SqlClient ' nin birincil SQL Server örneğindeki veritabanına bağlanmayı deneydiğini belirtir Tüm IP adreslerine bağlanın. `MultiSubnetFailover=True` Bir bağlantı için belirtildiğinde istemci, TCP bağlantı girişimlerini işletim sisteminin varsayılan TCP yeniden aktarım aralıklarından daha hızlı yeniden dener. Bu, bir AlwaysOn kullanılabilirlik grubunun veya bir AlwaysOn yük devretme kümesi örneğinin yük devretmesinin ardından daha hızlı yeniden bağlantı sağlar ve hem tek hem çok alt ağ kullanılabilirlik grupları ve yük devretme kümesi örnekleri için geçerlidir.  
  
 SqlClient bağlantı dizesi anahtar sözcükleri hakkında daha fazla bilgi için bkz <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
 Kullanılabilirlik `MultiSubnetFailover=True` grubu dinleyicisi veya SQL Server 2012 yük devretme kümesi örneği dışında bir şeye ne zaman bağlanıldığını belirtmek, olumsuz bir performans etkisi oluşmasına neden olabilir ve desteklenmez.  
  
 Bir kullanılabilirlik grubundaki bir sunucuya veya SQL Server 2012 yük devretme kümesi örneğine bağlanmak için aşağıdaki yönergeleri kullanın:  
  
- Tek bir alt ağa veya çok alt ağa bağlanırken bağlantıözelliğinikullanın;herikisiiçindeperformansıgeliştirir.`MultiSubnetFailover`  
  
- Bir kullanılabilirlik grubuna bağlanmak için, bağlantı dizinizdeki sunucu olarak kullanılabilirlik grubunun kullanılabilirlik grubu dinleyicisini belirtin.  
  
- 64 ' den fazla IP adresiyle yapılandırılan bir SQL Server örneğine bağlanmak bağlantı hatasına neden olur.  
  
- `MultiSubnetFailover` Bağlantı özelliğini kullanan bir uygulamanın davranışı, kimlik doğrulama türüne göre etkilenmez: SQL Server kimlik doğrulaması, Kerberos kimlik doğrulaması veya Windows kimlik doğrulaması.  
  
- Değerini yük devretme zamanına `Connect Timeout` uyacak şekilde artırın ve uygulama bağlantısı yeniden deneme girişimlerini azaltın.  
  
- Dağıtılmış işlemler desteklenmiyor.  
  
 Salt okuma yönlendirmesi etkin değilse, ikincil bir çoğaltma konumuna bağlanmak aşağıdaki durumlarda başarısız olur:  
  
1. İkincil çoğaltma konumu bağlantıları kabul edecek şekilde yapılandırılmamışsa.  
  
2. Bir uygulama (aşağıda `ApplicationIntent=ReadWrite` ele alınmıştır) kullanıyorsa ve ikincil çoğaltma konumu salt okuma erişimi için yapılandırılmışsa.  
  
 <xref:System.Data.SqlClient.SqlDependency>salt okuma ikincil çoğaltmalarda desteklenmez.  
  
 Birincil çoğaltma salt okuma iş yüklerini reddedecek şekilde yapılandırıldıysa ve bağlantı dizesi içerdiğinde `ApplicationIntent=ReadOnly`bir bağlantı başarısız olur.  
  
## <a name="upgrading-to-use-multi-subnet-clusters-from-database-mirroring"></a>Veritabanı yansıtmasında çok alt ağ kümeleri kullanmak için yükseltme  
 <xref:System.ArgumentException>Bağlantı dizesinde `MultiSubnetFailover` vebağlantı`Failover Partner` anahtar kelimeleri varsa ve TCP dışında bir protokol kullanılıyorsa bir bağlantı hatası () oluşur. `MultiSubnetFailover=True` Kullanılıyorsa bir hata<xref:System.Data.SqlClient.SqlException>() da `MultiSubnetFailover` oluşur ve SQL Server bir veritabanı yansıtma çiftinin parçası olduğunu belirten bir yük devretme ortağı yanıtı döndürür.  
  
 Şu anda veritabanı yansıtma kullanan bir SqlClient uygulamasını Çoklu alt ağ senaryosuna yükseltirseniz, `Failover Partner` bağlantı özelliğini kaldırmalı ve içindeki sunucu adını olarak `True` ayarla ve Değiştir ile `MultiSubnetFailover` değiştirmelisiniz. kullanılabilirlik grubu dinleyicisi ile bağlantı dizesi. Bir bağlantı dizesi ve `Failover Partner` `MultiSubnetFailover=True`kullanıyorsa, sürücü bir hata oluşturur. Ancak, bir bağlantı dizesi ve `Failover Partner` `MultiSubnetFailover=False` (veya `ApplicationIntent=ReadWrite`) kullanıyorsa, uygulama veritabanı yansıtmayı kullanacaktır.  
  
 Veritabanı, AG 'deki birincil veritabanında veritabanı yansıtma kullanılıyorsa ve `MultiSubnetFailover=True` bir kullanılabilirlik grubu dinleyicisi yerine birincil bir veritabanına bağlanan bağlantı dizesinde kullanılıyorsa, sürücü bir hata döndürür.  
  
## <a name="specifying-application-intent"></a>Uygulama hedefini belirtme  
 Ne `ApplicationIntent=ReadOnly`zaman, istemci AlwaysOn etkin bir veritabanına bağlanırken bir okuma iş yükü ister. Sunucu, bağlantı sırasında ve bir kullanım veritabanı bildiriminde, ancak yalnızca her zaman etkinleştirilmiş bir veritabanına yönelik amacı zorlayacaktır.  
  
 `ApplicationIntent` Anahtar sözcüğü, eski, salt okunurdur veritabanları ile çalışmaz.  
  
 Bir veritabanı hedeflenen AlwaysOn veritabanında okuma iş yüklerine izin verebilir veya bu iş yüklerini engelleyemez. (Bu, `ALLOW_CONNECTIONS` `PRIMARY_ROLE` ve `SECONDARY_ROLE`Transact-SQL deyimlerinin yan tümcesiyle yapılır.)  
  
 Anahtar `ApplicationIntent` sözcüğü, salt okunurdur yönlendirmeyi etkinleştirmek için kullanılır.  
  
## <a name="read-only-routing"></a>Salt okuma yönlendirmesi  
 Salt okuma yönlendirmesi, bir veritabanının salt okuma çoğaltması kullanılabilirliğini garanti eden bir özelliktir. Salt okuma yönlendirmeyi etkinleştirmek için:  
  
1. Her zaman açık kullanılabilirlik grubu kullanılabilirlik grubu dinleyicisine bağlanmanız gerekir.  
  
2. Bağlantı dizesi anahtar sözcüğü olarak `ReadOnly`ayarlanmalıdır. `ApplicationIntent`  
  
3. Salt okuma yönlendirmeyi etkinleştirmek için kullanılabilirlik grubunun veritabanı yöneticisi tarafından yapılandırılması gerekir.  
  
 Salt okuma yönlendirmesi kullanan birden çok bağlantı, hepsi aynı salt okuma çoğaltmasına bağlanmayacak olabilir. Veritabanı eşitlemede veya sunucu yönlendirme yapılandırmasındaki değişiklikler üzerinde yapılan değişiklikler, istemci bağlantılarının farklı salt okuma çoğaltmalarına neden olabilir. Tüm salt okuma isteklerinin aynı salt-tek çoğaltmaya bağlanmasını sağlamak için, `Data Source` bağlantı dizesi anahtar sözcüğüne bir kullanılabilirlik grubu dinleyicisi geçirmeyin. Bunun yerine, salt okunurdur örneğinin adını belirtin.  
  
 Salt okunur yönlendirme birinciye bağlanmasından sonra, salt okunur yönlendirme birinciye bağlandığından daha uzun sürebilir ve daha sonra kullanılabilir en iyi okunabilir ikincil için arama yapar. Bu nedenle, oturum açma zaman aşımını artırmanız gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SQL Server Özellikleri ve ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-features-and-adonet.md)
- [ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)

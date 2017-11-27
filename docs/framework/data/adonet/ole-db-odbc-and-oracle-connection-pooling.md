---
title: "OLE DB, ODBC ve Oracle bağlantı havuzu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2bd83b1e-3ea9-43c4-bade-d9cdb9bbbb04
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 22ef6afa36c7fc46713ec5c0940c305fc967e91b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ole-db-odbc-and-oracle-connection-pooling"></a>OLE DB, ODBC ve Oracle bağlantı havuzu
Bağlantı havuzu önemli ölçüde performans ve ölçeklenebilirlik, uygulamanızın geliştirebilirsiniz. Bu bölümde, bağlantı için OLE DB, ODBC ve Oracle için .NET Framework veri sağlayıcıları havuzu anlatılmaktadır.  
  
## <a name="connection-pooling-for-oledb"></a>Bağlantı için OleDb havuzu  
 OLE DB için .NET Framework veri sağlayıcısı kullanarak oturum havuzu OLE DB bağlantıları otomatik olarak havuza ekler. Bağlantı dizesi bağımsız değişkenleri, etkinleştirme veya devre dışı OLE DB hizmetleri havuzu dahil olmak üzere kullanılabilir. Örneğin, aşağıdaki bağlantı dizesi oturum havuzu OLE DB ve otomatik işlem kaydı devre dışı bırakır.  
  
```  
Provider=SQLOLEDB;OLE DB Services=-4;Data Source=localhost;Integrated Security=SSPI;  
```  
  
 Her zaman kapatın veya bağlantı havuza geri dönebilmek için işiniz bittiğinde bağlantı dispose öneririz. Açıkça kapatılmamış bağlantıları havuza geri. Örneğin, kapsam dışı geçti, ancak, değil açıkça kapatıldı bağlantı yalnızca bağlantı havuzu maksimum havuz boyutuna ulaştı ve bağlantı hala geçerli ise döndürülür.  
  
 OLE DB oturum veya kaynak havuzu yanı sıra OLE DB sağlayıcı hizmet varsayılanlarını geçersiz kılarak havuzu devre dışı bırakma hakkında daha fazla bilgi için bkz: [OLE DB Programcı Kılavuzu](http://go.microsoft.com/fwlink/?linkid=45232).  
  
## <a name="connection-pooling-for-odbc"></a>Bağlantı için ODBC havuzu  
 Bağlantı için .NET Framework veri sağlayıcısı için ODBC havuzu ODBC sürücüsü, bağlantı için kullanılan ve ODBC için .NET Framework veri sağlayıcısı tarafından etkilenmez Yöneticisi tarafından yönetilir.  
  
 Etkinleştirmek veya bağlantı havuzu devre dışı bırakmak için açık **ODBC Veri Kaynağı Yöneticisi** Denetim Masası'ndaki Yönetimsel Araçlar klasöründeki. **Bağlantı havuzu** sekme bağlantı yüklü her ODBC sürücüsü için parametreleri havuzu belirtmenize olanak sağlar. Bağlantı havuzu değişiklikleri belirli bir ODBC sürücü için o ODBC sürücüsü kullanan tüm uygulamalar etkileyeceğini unutmayın.  
  
 ODBC bağlantı havuzu ile ilgili daha fazla bilgi için bkz: [bilgisi: sık sorulan sorular hakkında ODBC bağlantı havuzu](http://support.microsoft.com/kb/169470).  
  
## <a name="connection-pooling-for-oracleclient"></a>Bağlantı için OracleClient havuzu  
 Oracle için .NET Framework veri sağlayıcısı ADO.NET istemci uygulamanız için otomatik olarak bağlantı havuzu sağlar. Bağlantı havuzu davranışını denetlemek için çeşitli bağlantı dizesi değiştiricileri de sağlayabilirsiniz (Bu konunun ilerleyen bölümlerinde "Denetleme bağlantı havuzu ile bağlantı dizesi anahtar sözcükler" konusuna bakın).  
  
### <a name="pool-creation-and-assignment"></a>Havuz oluşturma ve atama  
 Bağlantı açıldığında, bağlantı havuzu bağlantı dizesini içeren bağlantı havuzu ilişkilendirir tam bir eşleştirme algoritması temel alınarak oluşturulur. Her bağlantı havuzu ayrı bağlantı dizesi ile ilişkilidir. Yeni bir bağlantı açıldığında, bağlantı dizesi var olan bir havuzu için tam bir eşleşme değilse yeni bir havuz oluşturulur.  
  
 Etkin İşlem sonlanana kadar oluşturduktan sonra bağlantı havuzu yok edilmez. Etkin olmayan ya da boş havuzları bakımı çok az sistem kaynaklarını kullanır.  
  
### <a name="connection-addition"></a>Bağlantı ekleme  
 Bağlantı havuzu her benzersiz bağlantı dizesi için oluşturulur. Bir havuz oluşturduğunuzda, birden çok bağlantı nesneleri oluşturulur ve böylece en küçük havuz boyutu gereksinimini sağlanıyorsa havuzuna eklenir. Bağlantılar, en büyük havuz boyutu kadar gerektiğinde havuzuna eklenir.  
  
 Zaman bir <xref:System.Data.OracleClient.OracleConnection> nesnesi istendi, kullanılabilir bir bağlantının kullanılabilir olması durumunda havuzundan elde edilir. Kullanılabilir olması için bağlantı gerekir şu anda kullanılmayan, eşleşen bir işlem bağlamına sahip veya değil hiçbir işlem içerikle ilişkili ve sunucu için geçerli bir bağlantı vardır.  
  
 En büyük havuz boyutuna ulaştı ve kullanılabilir bağlantı yok, istek sıraya alındı. Bağlantı havuzlayıcı geri havuza en bağlantıları yeniden ayırma bu isteklerini karşılar. Kapalı veya elden bağlantıları geri havuza yayınlanır.  
  
### <a name="connection-removal"></a>Bağlantı kaldırma  
 Bağlantı havuzlayıcı uzun bir süre için boşta kaldıktan sonra ya da havuzlayıcı sunucusuyla bağlantı zarar görmesi olduğunu algılarsa havuzundan bir bağlantıyı kaldırır. Bu sunucu ile iletişim kurmak yalnızca denemeden sonra algılanabilmesi olduğunu unutmayın. Bir bağlantı, artık sunucuya bağlı bulunursa, geçersiz olarak işaretlendi. Bağlantı havuzlayıcı havuzuna serbest ve geçersiz olarak işaretlenmiş nesneler için arayan bağlantı havuzu düzenli aralıklarla tarar. Bu bağlantılar kalıcı olarak kaldırılır.  
  
 Bir bağlantı kayboldu bir sunucuya varsa, bağlantı havuzlayıcı kesilen bağlantı algıladı değil ve geçersiz olarak işaretlendi, bu bağlantı havuzundan çizilebilir. Bu durumda, bir özel durum oluşturulur. Ancak, tekrar havuza bırakın için bağlantı kapatmalısınız.  
  
 Çağırmayın `Close` veya `Dispose` üzerinde bir `Connection`, `DataReader`, veya diğer yönetilen nesne içinde `Finalize` sınıfınızın yöntemi. Bir Sonlandırıcı, yalnızca sınıfınız doğrudan sahibi yönetilmeyen kaynakları serbest bırakmak. Sınıfınıza yönetilmeyen kaynakları sahip olmadığından, içermeyen bir `Finalize` Sınıf tanımınız yöntemi. Daha fazla bilgi için bkz: [çöp toplama](../../../../docs/standard/garbage-collection/index.md).  
  
### <a name="transaction-support"></a>İşlem desteği  
 Bağlantı havuzu ve atanan göre işlem bağlamı çizilir. İstekte bulunan iş parçacığı ve atanan bağlantı bağlamında eşleşmesi gerekir. Bu nedenle, her bağlantı havuzu gerçekte bağlantıları onlarla ve içine ilişkili hiçbir işlem bağlamına sahip bölünmüştür *N* her bir özel işlem bağlamı bağlantılarla içeren alt bölüm.  
  
 Bağlantı kapalı olduğunda geri havuza ve kendi işlem bağlamına dayalı uygun alt bölümü olarak yayımlanır. Dağıtılmış işlem hala olsa bile bu nedenle, bağlantı bir hata oluşturmadan kapatabilirsiniz bekliyor. Bu, tamamlama veya sonraki bir zamanda Dağıtılmış İşlem iptal olanak sağlar.  
  
### <a name="controlling-connection-pooling-with-connection-string-keywords"></a>Bağlantı dizesi anahtar sözcükleriyle bağlantı havuzu denetleme  
 <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A> Özelliği <xref:System.Data.OracleClient.OracleConnection> nesnesi bağlantı mantığı havuzu davranışını ayarlamak için kullanılan bağlantı dizesi anahtar/değer çiftlerinin destekler.  
  
 Aşağıdaki tabloda açıklanmaktadır <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A> değerleri bağlantı davranışı havuzu ayarlamak için kullanın.  
  
|Ad|Varsayılan|Açıklama|  
|----------|-------------|-----------------|  
|`Connection Lifetime`|0|Bir bağlantı havuza geri döner, oluşturulma zamanı geçerli saati ile karşılaştırılır ve bu zaman aralığı (saniye cinsinden) tarafından belirtilen değeri aşarsa bağlantı yok `Connection Lifetime`. Bu, Yük Dengeleme server çalıştıran ve bir sunucu yalnızca çevrimiçi duruma getirilmeden arasında zorlamak için kümelenmiş yapılandırmalarında yararlıdır.<br /><br /> Sıfır (0) değeri en büyük zaman aşımı havuza alınmış bağlantılarının neden olur.|  
|`Enlist`|'true'|Zaman `true`, bir işlem bağlamı varsa havuzlayıcı otomatik olarak geçerli işlem içeriği bağlantı oluşturma iş parçacığının kaydeder.|  
|`Max Pool Size`|100|Havuzda izin verilen bağlantılarının maksimum sayısı.|  
|`Min Pool Size`|0|Havuzda tutulan bağlantıları minimum sayısı.|  
|`Pooling`|'true'|Zaman `true`, bağlantı uygun havuzundan çizilmiş veya gerekirse, oluşturulur ve uygun havuzuna eklenir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bağlantı havuzu](../../../../docs/framework/data/adonet/connection-pooling.md)  
 [Performans sayaçları](../../../../docs/framework/data/adonet/performance-counters.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)

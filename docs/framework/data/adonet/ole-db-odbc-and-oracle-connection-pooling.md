---
title: OLE DB, ODBC ve Oracle Bağlantı Havuzu
ms.date: 03/30/2017
ms.assetid: 2bd83b1e-3ea9-43c4-bade-d9cdb9bbbb04
ms.openlocfilehash: 7c17863facd962583e0da03e810c9a8150cda0a6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59208897"
---
# <a name="ole-db-odbc-and-oracle-connection-pooling"></a>OLE DB, ODBC ve Oracle Bağlantı Havuzu
Bağlantı havuzu performans ve ölçeklenebilirlik, uygulamanızın önemli ölçüde artırabilirsiniz. Bu bölümde, bağlantı için OLE DB, ODBC ve Oracle için .NET Framework veri sağlayıcıları havuzu açıklanmaktadır.  
  
## <a name="connection-pooling-for-oledb"></a>Bağlantı için OleDb havuzu  
 OLE DB için .NET Framework veri sağlayıcısı, OLE DB oturum havuzunu kullanan bağlantı otomatik olarak havuza ekler. Bağlantı dizesi bağımsız değişkenleri, etkinleştirme veya devre dışı OLE DB hizmetleri havuzu dahil olmak üzere kullanılabilir. Örneğin, aşağıdaki bağlantı dizesi OLE DB oturum havuzu ve otomatik bir işlem kaydı devre dışı bırakır.  
  
```  
Provider=SQLOLEDB;OLE DB Services=-4;Data Source=localhost;Integrated Security=SSPI;  
```  
  
 Her zaman kapatın veya havuzuna bağlantı döndürmek için kullanarak tamamladığınızda bir bağlantı dispose öneririz. Açıkça kapanmamış bağlantıları havuza geri. Örneğin, bir bağlantı, kapsam dışına geçti, ancak bu değil açıkça kapatıldı yalnızca bağlantı havuzuna maksimum havuz boyutuna ulaştı ve bağlantı hala geçerli ise döndürülür.  
  
 OLE DB oturumu veya kaynak havuzu hem de havuzu OLE DB sağlayıcı hizmet varsayılanlarını geçersiz kılma ile devre dışı bırakma hakkında daha fazla bilgi için bkz: [OLE DB Programcı Kılavuzu](https://go.microsoft.com/fwlink/?linkid=45232).  
  
## <a name="connection-pooling-for-odbc"></a>Bağlantı için ODBC havuzu  
 ODBC için .NET Framework veri sağlayıcısı için bağlantı havuzu ODBC sürücü bağlantısı için kullanılır ve ODBC için .NET Framework veri sağlayıcısı tarafından etkilenmez Yöneticisi tarafından yönetilir.  
  
 Etkinleştirmek veya devre dışı bağlantı havuzu için açık **ODBC Veri Kaynağı Yöneticisi** Yönetimsel Araçlar klasörünü Denetim Masası'nda. **Bağlantı havuzu** sekme bağlantı parametrelerini yüklü her ODBC sürücüsü havuzu belirtmenize olanak sağlar. Belirli bir ODBC sürücü için bağlantı havuzu değişiklikleri, ODBC sürücüsünü kullanan tüm uygulamalar etkileyeceğini unutmayın.  
  
## <a name="connection-pooling-for-oracleclient"></a>Bağlantı için OracleClient havuzu  
 Oracle için .NET Framework veri sağlayıcısı, bağlantı otomatik olarak ADO.NET istemci uygulamanız için havuzu sağlar. Bağlantı havuzu davranışını denetlemek için çeşitli bağlantı dizesi değiştiriciler de sağlayabilirsiniz (Bu konunun ilerleyen bölümlerinde "Denetleme bağlantı havuzu ile bağlantı dizesi anahtar sözcükler" konusuna bakın).  
  
### <a name="pool-creation-and-assignment"></a>Havuz oluşturma ve atama  
 Bağlantı açıldığında bir bağlantı havuzu bağlantı dizesiyle bağlantı havuzu ilişkilendiren tam bir eşleştirme algoritmasını temel alınarak oluşturulur. Her bağlantı havuzu bir ayrı bir bağlantı dizesi ile ilişkilidir. Yeni bir bağlantı açıldığında, bağlantı dizesi, mevcut bir havuza tam bir eşleşme değilse, yeni bir havuz oluşturulur.  
  
 Etkin İşlem sonlandırılana kadar oluşturulduktan sonra bağlantı havuzları yok edilmez. Etkin olmayan veya boş havuzu koruma çok az sayıda sistem kaynaklarını kullanır.  
  
### <a name="connection-addition"></a>Bağlantı ekleme  
 Her benzersiz bir bağlantı dizesi için bir bağlantı havuzu oluşturulur. Bir havuz oluşturulduğunda, birden çok bağlantı nesneleri oluşturulur ve böylece en az bir havuz boyutu gereksinimini memnun havuzuna eklenmiş. Bağlantılar, en büyük havuz boyutu aşmayacak şekilde gerektiğinde havuzuna eklenir.  
  
 Olduğunda bir <xref:System.Data.OracleClient.OracleConnection> istenen nesneyi, kullanılabilir bir bağlantı varsa havuzundan elde edilir. Kullanılabilir olması için bağlantı gerekir şu anda kullanılmayan, eşleşen bir işlem bağlamına sahip veya değil herhangi bir işlem bağlamı ile ilişkili ve sunucu için geçerli bir bağlantı vardır.  
  
 Maksimum havuz boyutuna ulaştı ve kullanılabilir bağlantı yok, isteği sıraya alınır. Bağlantı havuzlayıcı havuza yayınlandıkça bağlantıları tahsis Bu istekler karşılar. Kapalı veya elden bağlantıları geri havuzuna serbest bırakılır.  
  
### <a name="connection-removal"></a>Bağlantı kaldırma  
 Uzun süre boşta kaldıktan sonra ya da sunucu ile bağlantı yazıyordunuz havuzlayıcı algılarsa, bağlantı havuzlayıcı havuzdan bir bağlantıyı kaldırır. Bu sunucu ile iletişim kurmak yalnızca denemeden sonra algılanabilmesi olduğunu unutmayın. Artık sunucuya bağlı bir bağlantı bulunması durumunda geçersiz olarak işaretlendi. Bağlantı havuzlayıcı havuzuna serbest bırakılmış ve geçersiz olarak işaretlenmiş nesneler için arayan bağlantı havuzları düzenli aralıklarla tarar. Bu bağlantılar kalıcı olarak kaldırılır.  
  
 Bağlantı kayboldu bir sunucuya varsa, bu bağlantı, bağlantı havuzlayıcı değil kesilen bağlantı algıladı ve geçersiz olarak işaretlenmiş, havuzdan kurulabilir. Bu durumda, bir özel durum oluşturulur. Ancak, tekrar havuza bırakın için bağlantı kapatmalısınız.  
  
 Çağırmayın `Close` veya `Dispose` üzerinde bir `Connection`, `DataReader`, ya da diğer yönetilen nesnelere `Finalize` sınıfınızın yöntemi. İçindeki bir sonlandırıcı yalnızca sınıfınıza doğrudan sahip olduğu yönetilmeyen kaynakları serbest bırakın. Sınıfınızın herhangi bir yönetilmeyen kaynağa sahip değilse içermeyen bir `Finalize` sınıf tanımına yöntemi. Daha fazla bilgi için [çöp toplama](../../../../docs/standard/garbage-collection/index.md).  
  
### <a name="transaction-support"></a>İşlem Desteği  
 Bağlantı havuzu ve da atanan göre işlem bağlamı çizilir. İstenen iş parçacığı ve atanmış bağlantı bağlamı eşleşmesi gerekir. Bu nedenle, her bir bağlantı havuzu gerçekten bağlantıları içine ve bunlarla ilişkili hiçbir işlem bağlamı ile ayrılır *N* alt bölümleri her belirli işlem bağlamı ile bağlantılar içerir.  
  
 Bağlantı kapalı olduğunda geri havuzu ve onun işlem bağlamına dayalı uygun alt yayımlanır. Dağıtılmış işlem yine de olsa bile bu nedenle, bağlantı oluşturulurken bir hata olmadan kapatabilirsiniz bekleniyor. Bu, tamamlama veya sonraki bir zamanda Dağıtılmış işlemi iptal etmenizi sağlar.  
  
### <a name="controlling-connection-pooling-with-connection-string-keywords"></a>Bağlantı dizesi anahtar sözcüklerle bağlantı havuzu denetleme  
 <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A> Özelliği <xref:System.Data.OracleClient.OracleConnection> nesnesi için bağlantı havuzu mantıksal davranışını ayarlamak için kullanılan bağlantı dizesi anahtar/değer çiftleri destekler.  
  
 Aşağıdaki tabloda açıklanmıştır <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A> değerler bağlantı havuzu davranışı ayarlamak için kullanabilirsiniz.  
  
|Ad|Varsayılan|Açıklama|  
|----------|-------------|-----------------|  
|`Connection Lifetime`|0|Bir bağlantı, havuza geri döner, oluşturulma zamanı geçerli saati ile karşılaştırılır ve bu zaman aralığı (saniye cinsinden) tarafından belirtilen değeri aşarsa bağlantı edildiğinde `Connection Lifetime`. Bu, kümelenmiş yapılandırmalardaki çalışan bir sunucu ve yalnızca çevrimiçi bir sunucu arasında yük dengelemeyi zorlamak için kullanışlıdır.<br /><br /> Sıfır (0) değeri en büyük zaman aşımı havuza alınmış bağlantılarının kesilmesine neden olur.|  
|`Enlist`|'true'|Zaman `true`, bir işlem bağlamı varsa havuzlayıcı geçerli işlem bağlamı oluşturma iş parçacığının bağlantı otomatik olarak kaydeder.|  
|`Max Pool Size`|100|Havuzda izin verilen bağlantı sayısı.|  
|`Min Pool Size`|0|Havuzda tutulan bağlantıları en küçük sayısı.|  
|`Pooling`|'true'|Zaman `true`, bağlantı uygun havuzdan çizilmiş veya gerekirse, oluşturulan ve uygun havuzuna eklenmiş.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bağlantı Havuzu](../../../../docs/framework/data/adonet/connection-pooling.md)
- [Performans Sayaçları](../../../../docs/framework/data/adonet/performance-counters.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)

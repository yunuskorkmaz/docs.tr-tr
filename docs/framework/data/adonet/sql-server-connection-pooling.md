---
title: SQL Server Connection Pooling (ADO.NET)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e51d44e-7c4e-4040-9332-f0190fe36f07
ms.openlocfilehash: 79749f5e593fbf4ea282cc5c8000be88098b702f
ms.sourcegitcommit: 59b51cd7c95c75be85bd6ef715e9ef8c85720bac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37874601"
---
# <a name="sql-server-connection-pooling-adonet"></a>SQL Server Connection Pooling (ADO.NET)
Veritabanı sunucusuna bağlanması, zaman birkaç adımdan oluşur. Bir yuva ya da bir adlandırılmış kanal gibi fiziksel bir kanal, sunucu ile ilk el sıkışma gerçekleşmelidir, oluşturulmalıdır bağlantı dizesi bilgilerini ayrıştırıldığında, bağlantı sunucu tarafından doğrulanması, denetimleri kaydetme için çalıştırılması gerekir Geçerli işlem ve benzeri.  
  
 Uygulamada, çoğu uygulama, bağlantıları için yalnızca bir veya birkaç farklı yapılandırmaları kullanın. Bu uygulama yürütme sırasında aynı bağlantı fazla sürekli açık kapalı ve anlamına gelir. Bağlantılar, açma maliyetini en aza indirmek için [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] adında bir iyileştirme teknik kullanır *bağlantı havuzu*.  
  
 Bağlantı havuzu yeni bir bağlantı açılmalıdır sayısını azaltır. *Havuzlayıcı* fiziksel bağlantı sahipliğini tutar. Bağlantılar, bir dizi her verilen bağlantı yapılandırması etkin bağlantı etkin tutulan bağlantıyı destekliyorsa tutarak yönetir. Her bir kullanıcı çağırır `Open` bir bağlantıda kullanılabilir bir bağlantı havuzundaki havuzlayıcı arar. Havuza alınmış bir bağlantı varsa, bunu yeni bir bağlantı açmak yerine çağırana döndürür. Uygulama çağırdığında `Close` bağlantıda havuzlayıcı kapatma yerine etkin bağlantılar havuza alınmış kümesini döndürür. Bağlantı havuza döndüğünde, sonraki yüklenmek hazır olduğunda `Open` çağırın.  
  
 Yalnızca bağlantıları aynı yapılandırmaya sahip bir havuzda toplanabilir mi. [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] aynı zamanda, her yapılandırma için birkaç havuzu tutar. Tümleşik güvenlik kullanıldığında bağlantıları bağlantı dizesi ve Windows Identity havuzlarına ayrılır. Bağlantılar, ayrıca tabanlı olup, bir kayıtlı üzerinde havuza eklenir. Kullanırken <xref:System.Data.SqlClient.SqlConnection.ChangePassword%2A>, <xref:System.Data.SqlClient.SqlCredential> örneği bağlantı havuzunu etkiler. Farklı örnekleri <xref:System.Data.SqlClient.SqlCredential> kullanıcı kimliği ve parola aynı olsa bile, farklı bağlantı havuzları kullanır.  
  
 Bağlantı havuzu performans ve ölçeklenebilirlik, uygulamanızın önemli ölçüde artırabilirsiniz. Varsayılan olarak, bağlantı havuzu etkin [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]. Açıkça devre dışı sürece açılır ve uygulamanızda kapalı havuzlayıcı bağlantıları iyileştirir. Ayrıca, bağlantı havuzu davranışını denetlemek için çeşitli bağlantı dizesi değiştiriciler sağlayabilirsiniz. Daha fazla bilgi için bu konunun ilerleyen bölümlerinde "Denetleme bağlantı havuzu ile bağlantı dizesi anahtar sözcükler" konusuna bakın.  
  
> [!NOTE]
>  Bağlantı havuzu etkin olduğunda ve bir zaman aşımı hatası veya başka bir oturum açma hata oluşursa bir özel durum ve sonraki bağlantı denemelerinde sonraki beş saniye boyunca "engelleme süresi" başarısız olur. Uygulama engelleme süresi içinde bağlanmaya çalışırsa, ilk özel durum yeniden oluşturulur. Bir engelleme süresi sona erdikten sonra sonraki hatalar iki kez önceki engelleme süresi en fazla bir dakika kadar sürece yeni bir engelleme nokta olarak mı neden olur.  
  
## <a name="pool-creation-and-assignment"></a>Havuz oluşturma ve atama  
 Bir bağlantı ilk kez açıldığında bir bağlantı havuzu bağlantı dizesiyle bağlantı havuzu ilişkilendiren tam bir eşleştirme algoritmasını temel alınarak oluşturulur. Her bağlantı havuzu bir ayrı bir bağlantı dizesi ile ilişkilidir. Yeni bir bağlantı açıldığında, bağlantı dizesi, mevcut bir havuza tam bir eşleşme değilse, yeni bir havuz oluşturulur. Her uygulama etki alanı, bağlantı dizesi başına ve tümleşik güvenlik kullanıldığında Windows kimlik, işlem başına bağlantılar havuza. Bağlantı dizelerini, ayrıca bir tam eşleşme olmalıdır; aynı bağlantı için farklı bir düzende sağlanan anahtar sözcükleri ayrı olarak havuza.  
  
 Aşağıdaki örnekte C#, üç yeni <xref:System.Data.SqlClient.SqlConnection> nesneleri oluşturulur, ancak yalnızca iki bağlantı havuzları yönetmek için gereklidir. Birinci ve ikinci bağlantı dizeleri için atanan değer tarafından farklı olduğunu unutmayın `Initial Catalog`.  
  
```  
using (SqlConnection connection = new SqlConnection(  
  "Integrated Security=SSPI;Initial Catalog=Northwind"))  
    {  
        connection.Open();        
        // Pool A is created.  
    }  
  
using (SqlConnection connection = new SqlConnection(  
  "Integrated Security=SSPI;Initial Catalog=pubs"))  
    {  
        connection.Open();        
        // Pool B is created because the connection strings differ.  
    }  
  
using (SqlConnection connection = new SqlConnection(  
  "Integrated Security=SSPI;Initial Catalog=Northwind"))  
    {  
        connection.Open();        
        // The connection string matches pool A.  
    }  
```  
  
 Varsa `MinPoolSize` ya da bağlantı dizesinde belirtilmedi veya belirtilen olarak sıfır, bir süre işlem yapılmadığında havuzundaki bağlantı kapatılacak. Ancak, belirtilen `MinPoolSize` , sıfırdan büyük bağlantı havuzu kadar yok edilmez `AppDomain` kaldırılır ve işlem sona erer. Etkin olmayan veya boş havuzları bakım minimum sistem ek okumalar içerir.  
  
> [!NOTE]
>  Önemli bir hata oluştuğunda bir yük devretme gibi havuzu otomatik olarak temizlenir.  
  
## <a name="adding-connections"></a>Bağlantılar ekleme  
 Her benzersiz bir bağlantı dizesi için bir bağlantı havuzu oluşturulur. Bir havuz oluşturulduğunda, birden çok bağlantı nesneleri oluşturulur ve böylece en az bir havuz boyutu gereksinimini memnun havuzuna eklenmiş. Bağlantılar, havuza eklenir, gerektiğinde, belirtilen en büyük havuz boyutu aşmayacak şekilde (varsayılan değer 100'dür). Kapalı veya elden bağlantıları geri havuzuna serbest bırakılır.  
  
 Olduğunda bir <xref:System.Data.SqlClient.SqlConnection> istenen nesneyi, kullanılabilir bir bağlantı varsa havuzundan elde edilir. Kullanılabilir olması için bir bağlantı gerekir kullanılmayan, eşleşen bir işlem bağlamına sahip veya herhangi bir işlem bağlamı ile ilişkilendirilmemiş ve sunucu için geçerli bir bağlantı vardır.  
  
 Bağlantı havuzlayıcı havuza yayınlandıkça bağlantıları tahsis bağlantı isteklerini karşılar. Maksimum havuz boyutuna ulaştı ve kullanılabilir bağlantı yok, isteği sıraya alınır. Havuzlayıcı sonra herhangi bir bağlantı zaman aşımı ulaşılana kadar geri kazanmak çalışır (varsayılan değer 15 saniyedir). Bağlantı zaman aşımına uğramadan önce havuzlayıcı isteği gerçekleştiremiyor ise bir özel durum oluşturulur.  
  
> [!CAUTION]
>  Böylece bağlantı havuzuna döndürülür, işiniz bittiğinde, her zaman bağlantı kapatmanızı öneririz. Kullanarak bunu yapabilirsiniz `Close` veya `Dispose` yöntemlerinin `Connection` nesne veya tüm bağlantıları içinde açarak bir `using` C# ' ta, ifade veya `Using` Visual Basic'te deyimi. Açıkça kapanmamış bağlantıları eklenemez veya havuza geri döner. Daha fazla bilgi için [using deyimi](~/docs/csharp/language-reference/keywords/using-statement.md) veya [nasıl yapılır: bir sistem kaynağını atma](~/docs/visual-basic/programming-guide/language-features/control-flow/how-to-dispose-of-a-system-resource.md) Visual Basic için.  
  
> [!NOTE]
>  Çağırmayın `Close` veya `Dispose` üzerinde bir `Connection`, `DataReader`, ya da diğer yönetilen nesnelere `Finalize` sınıfınızın yöntemi. İçindeki bir sonlandırıcı yalnızca sınıfınıza doğrudan sahip olduğu yönetilmeyen kaynakları serbest bırakın. Sınıfınızın herhangi bir yönetilmeyen kaynağa sahip değilse içermeyen bir `Finalize` sınıf tanımına yöntemi. Daha fazla bilgi için [çöp toplama](../../../../docs/standard/garbage-collection/index.md).  
  
Bağlantı kapatma ve açma ile ilgili olaylar hakkında daha fazla bilgi için bkz. [denetim oturum açma olay sınıfı](/sql/relational-databases/event-classes/audit-login-event-class) ve [denetim oturum kapatma olay sınıfı](/sql/relational-databases/event-classes/audit-logout-event-class) SQL Server belgelerindeki.  
  
## <a name="removing-connections"></a>Bağlantılarını kaldırma  
 Bağlantı havuzlayıcı yaklaşık 4-8 dakika boşta kaldıktan sonra veya havuzlayıcı sunucusuyla bağlantı yazıyordunuz algılarsa havuzdan bir bağlantıyı kaldırır. Kesilen bağlantı sunucusuyla iletişim kurmak yalnızca denemeden sonra algılanabilmesi unutmayın. Artık sunucuya bağlı bir bağlantı bulunması durumunda geçersiz olarak işaretlendi. Yalnızca bunlar iadesi ya da kapatıldığında, geçersiz bağlantılar bağlantı havuzundan kaldırılır.  
  
 Bağlantı kayboldu bir sunucuya varsa, bu bağlantı, bağlantı havuzlayıcı değil kesilen bağlantı algıladı ve geçersiz olarak işaretlenmiş olsa bile havuzdan kurulabilir. Bağlantı hala geçerli olup olmadığını denetleyerek ek yükü ortadan kaldırır gerçekleşmesi için sunucuya başka bir gidiş dönüş neden olarak bir havuzlayıcı sahip avantajları olduğundan durum budur. Bu durumda, bağlantıyı kullanmak için yapılan ilk girişim bağlantı yazıyordunuz ve bir özel durum algılar.  
  
## <a name="clearing-the-pool"></a>Havuz temizleme  
 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 2.0 kullanılmaya havuzu temizlemek için iki yeni yöntem: <xref:System.Data.SqlClient.SqlConnection.ClearAllPools%2A> ve <xref:System.Data.SqlClient.SqlConnection.ClearPool%2A>. `ClearAllPools` bağlantı havuzları için belirli bir sağlayıcı, temizler ve `ClearPool` belirli bir bağlantı ile ilişkili bağlantı havuzu temizler. Çağrı zamanında kullanılan bağlantılar varsa, uygun şekilde işaretlenir. Kapatıldığında, havuza geri döner yerine atılır.  
  
## <a name="transaction-support"></a>İşlem desteği  
 Bağlantı havuzu ve da atanan göre işlem bağlamı çizilir. Sürece `Enlist=false` belirtilen bağlantı dizesinde bağlantı havuzu sağlar bağlantı kayıtlı olduğundan emin olarak <xref:System.Transactions.Transaction.Current%2A> bağlamı. Ne zaman bir bağlantı kapatıldı ve kayıtlı bir havuzla döndürülen `System.Transactions` işlem, bu kenara sonraki Bu bağlantı havuzunun aynı istek şekilde `System.Transactions` işlem varsa aynı bağlantıyı döndürür. Böyle bir talep verilir ve havuza alınmış bağlantı kullanılabilir bir bağlantı havuzunun işlem temelli olmayan bölümünden çizilmiş ve kayıtlı. Bağlantı yok ya da havuzun alanında bulunan kullanılabilir değilse yeni bir bağlantı oluşturulur ve kayıtlı.  
  
 Bağlantı kapalı olduğunda geri havuzu ve onun işlem bağlamına dayalı uygun alt yayımlanır. Dağıtılmış işlem yine de olsa bile bu nedenle, bağlantı oluşturulurken bir hata olmadan kapatabilirsiniz bekleniyor. Bu, tamamlama veya dağıtılmış işlem daha sonra iptal etmenizi sağlar.  
  
## <a name="controlling-connection-pooling-with-connection-string-keywords"></a>Bağlantı dizesi anahtar sözcüklerle bağlantı havuzu denetleme  
 `ConnectionString` Özelliği <xref:System.Data.SqlClient.SqlConnection> nesnesi için bağlantı havuzu mantıksal davranışını ayarlamak için kullanılan bağlantı dizesi anahtar/değer çiftleri destekler. Daha fazla bilgi için bkz. <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
## <a name="pool-fragmentation"></a>Havuzu parçalanması  
 Uygulama çok sayıda işlem çıkana kadar serbest bırakılmaz havuzları burada oluşturabilirsiniz birçok Web uygulamalarında ortak bir sorunu havuzu parçalanması var. Bu, performansın düşmesine neden olur, açık ve alıcı bellek çok sayıda bağlantılarını bırakır.  
  
### <a name="pool-fragmentation-due-to-integrated-security"></a>Tümleşik güvenlik nedeniyle havuzu parçalanması  
 Bağlantı, bağlantı dizesini ve kullanıcı kimliğini göre havuza eklenir. Bu nedenle, Web sitesi ve bir tümleşik güvenlik oturumu temel kimlik doğrulaması veya Windows kimlik doğrulamasını kullanıyorsanız kullanıcı başına bir havuz olursunuz. Bu tek bir kullanıcı isteklerini izleyen veritabanı performansını artırmamasına karşın, bu kullanıcının diğer kullanıcılar tarafından yapılan bağlantılar yararlanamaz. Ayrıca veritabanı sunucusu için kullanıcı başına en az bir bağlantı ile sonuçlanır. Geliştiriciler, güvenlik ve denetim gereksinimlerini karşı yaratmasını önlemelidir belirli bir Web uygulaması mimarisi bir yan etkisi budur.  
  
### <a name="pool-fragmentation-due-to-many-databases"></a>Havuzu parçalanması nedeniyle çok sayıda veritabanı  
 Çoğu Internet hizmet sağlayıcıları, çeşitli Web sitelerini tek bir sunucu üzerinde barındırın. Bunlar, Forms kimlik doğrulaması oturum açma onaylayın ve ardından bu kullanıcı veya kullanıcı grubu için belirli bir veritabanına bir bağlantı açmak için tek bir veritabanı kullanabilir. Kimlik doğrulama veritabanı bağlantısı havuza ve herkes tarafından kullanılır. Ancak, ayrı bir havuz sunucuya bağlantı sayısını artırmak her veritabanı için bağlantı yoktur.  
  
 Uygulama tasarımı, yan etkisi de budur. SQL sunucusuna bağlandığınızda, güvenliği tehlikeye atmadan bu yan etkiyi önlemek için görece basit bir yolu yoktur. Her bir kullanıcı veya grup için ayrı bir veritabanına bağlanma, yerine sunucuda aynı veritabanına bağlanmak ve yürüten [!INCLUDE[tsql](../../../../includes/tsql-md.md)] istenen veritabanına değiştirmek için deyimi kullanın. Aşağıdaki kod parçası, bir ilk bağlantı oluşturma gösterilmektedir `master` veritabanını ve ardından belirtilen istenen veritabanı derlemesine geçme `databaseName` string değişkeni.  
  
```vb  
' Assumes that command is a valid SqlCommand object and that  
' connectionString connects to master.  
    command.Text = "USE DatabaseName"  
Using connection As New SqlConnection(connectionString)  
    connection.Open()  
    command.ExecuteNonQuery()  
End Using  
```  
  
```csharp  
// Assumes that command is a SqlCommand object and that  
// connectionString connects to master.  
command.Text = "USE DatabaseName";  
using (SqlConnection connection = new SqlConnection(  
  connectionString))  
  {  
    connection.Open();  
    command.ExecuteNonQuery();  
  }  
```  
  
## <a name="application-roles-and-connection-pooling"></a>Uygulama rolleri ve bağlantı havuzu  
 Sonra bir SQL Server uygulama rolü çağırarak etkinleştirildi `sp_setapprole` sistem saklı yordam, bu bağlantının güvenlik bağlamı olarak ayarlanamaz. Ancak, havuzu etkinse, bağlantı havuzuna döndürülür ve havuza alınmış bağlantı yeniden denediğinizde hata oluşur. Daha fazla bilgi için bkz. Bilgi Bankası makalesi, "[SQL OLE DB kaynak havuzu ile uygulama rolü hataları](http://support.microsoft.com/default.aspx?scid=KB;EN-US;Q229564)."  
  
### <a name="application-role-alternatives"></a>Uygulama rolü alternatifleri  
 Uygulama rolleri yerine kullanabileceğiniz güvenlik mekanizmaları avantajlarından almanızı öneririz. Daha fazla bilgi için [SQL Server'da uygulama rolleri oluşturma](../../../../docs/framework/data/adonet/sql/creating-application-roles-in-sql-server.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bağlantı Havuzu](../../../../docs/framework/data/adonet/connection-pooling.md)  
 [SQL Server ve ADO.NET](../../../../docs/framework/data/adonet/sql/index.md)  
 [Performans Sayaçları](../../../../docs/framework/data/adonet/performance-counters.md)  
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)

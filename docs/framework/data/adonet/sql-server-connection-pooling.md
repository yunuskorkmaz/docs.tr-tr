---
title: SQL Server Bağlantı Havuzu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e51d44e-7c4e-4040-9332-f0190fe36f07
ms.openlocfilehash: 149511bd4e84baabf11eca014257127b587830df
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149004"
---
# <a name="sql-server-connection-pooling-adonet"></a>SQL Server Bağlantı Havuzu (ADO.NET)
Bir veritabanı sunucusuna bağlanmak genellikle birkaç zaman alıcı adımdan oluşur. Soket veya adlandırılmış bir boru gibi fiziksel bir kanal kurulmalı, sunucuile ilk el sıkışma yapılmalı, bağlantı dize bilgileri ayrıştırılmalı, bağlantı sunucu tarafından doğrulanmalıdır, denetimler geçerli işlem ve benzeri.  
  
 Uygulamada, çoğu uygulama bağlantılar için yalnızca bir veya birkaç farklı yapılandırma kullanır. Bu, uygulama yürütme sırasında birçok aynı bağlantının art arda açılıp kapatılacağı anlamına gelir. Bağlantıları açma maliyetini en aza indirmek için, ADO.NET *bağlantı havuzu*adı verilen bir optimizasyon tekniği kullanır.  
  
 Bağlantı havuzu, yeni bağlantıların kaç kez açılması gerektiğini azaltır. *Havuzcu* fiziksel bağlantının sahipliğini korur. Verilen her bağlantı yapılandırması için bir dizi etkin bağlantıyı canlı tutarak bağlantıları yönetir. Bir kullanıcı bir `Open` bağlantıyı aradığında, havuzcu havuzda kullanılabilir bir bağlantı arar. Birleştirilmiş bir bağlantı varsa, yeni bir bağlantı açmak yerine arayanın döndürür. Uygulama bağlantıyı `Close` aradığında, havuzlayıcı bağlantıyı kapatmak yerine havuzlu etkin bağlantı kümesine döndürür. Bağlantı havuza döndürüldükten sonra, bir sonraki `Open` çağrıda yeniden kullanılmaya hazırdır.  
  
 Yalnızca aynı yapılandırmaya sahip bağlantılar bir araya alınabilir. ADO.NET aynı anda, her yapılandırma için bir tane olmak üzere birden fazla havuz tutar. Bağlantılar bağlantı dizesi ve tümleşik güvenlik kullanıldığında Windows kimliği tarafından havuzlara ayrılır. Bağlantılar, bir işlemde kaydolup olmadıklarına bağlı olarak da biraraya alınır. Kullanırken, <xref:System.Data.SqlClient.SqlConnection.ChangePassword%2A> <xref:System.Data.SqlClient.SqlCredential> örnek bağlantı havuzunu etkiler. <xref:System.Data.SqlClient.SqlCredential> Kullanıcı kimliği ve parola aynı olsa bile, farklı bağlantı havuzları kullanır.  
  
 Bağlantıları birleştirme, uygulamanızın performansını ve ölçeklenebilirliğini önemli ölçüde artırabilir. Varsayılan olarak, bağlantı havuzu ADO.NET etkinleştirilir. Açıkça devre dışı kaldığınız sürece, havuzsahibi uygulamalarınızda açılıp kapandıkları için bağlantıları optimize eder. Bağlantı birleştirme davranışını denetlemek için birkaç bağlantı dizesi değiştirici de sağlayabilirsiniz. Daha fazla bilgi için daha sonra bu konuyla "Bağlantı Dizeanahtarlarıyla Bağlantı Havuzu'nun Denetleilmesi" konusuna bakın.  
  
> [!NOTE]
> Bağlantı havuzu etkinleştirildiğinde ve bir zaman arası hatası veya başka bir oturum açma hatası oluşursa, bir özel durum atılır ve sonraki bağlantı denemeleri sonraki beş saniye boyunca "engelleme süresi" başarısız olur. Uygulama engelleme süresi içinde bağlanmaya çalışırsa, ilk özel durum yeniden atılır. Engelleme dönemi sona erdikten sonraki hatalar, bir önceki engelleme dönemine göre iki kat daha uzun olan yeni bir engelleme dönemine ve en fazla bir dakikaya kadar sonuçlanacaktır.  
  
## <a name="pool-creation-and-assignment"></a>Havuz Oluşturma ve Atama  
 Bir bağlantı ilk açıldığında, bağlantı havuzubağlantıdaki bağlantı dizesiyle ilişkilendiren tam eşleşen algoritmayı temel alan bir bağlantı havuzu oluşturulur. Her bağlantı havuzu farklı bir bağlantı dizesi ile ilişkilidir. Yeni bir bağlantı açıldığında, bağlantı dizesi varolan bir havuzla tam eşleşme değilse, yeni bir havuz oluşturulur. Bağlantılar, işlem başına, uygulama etki alanı başına, bağlantı dizesi başına ve tümleşik güvenlik kullanıldığında, Windows kimliği başına birleştirilir. Bağlantı dizeleri de tam bir eşleşme olmalıdır; aynı bağlantı için farklı bir sırada sağlanan anahtar kelimeler ayrı ayrı biraraya gelecektir.  
  
 Aşağıdaki C# örneğinde, <xref:System.Data.SqlClient.SqlConnection> üç yeni nesne oluşturulur, ancak bunları yönetmek için yalnızca iki bağlantı havuzu gerekir. Birinci ve ikinci bağlantı dizeleri için `Initial Catalog`atanan değere göre farklılık gösterir.  
  
```csharp
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
  
 `MinPoolSize` Bağlantı dizesinde belirtilmemişse veya sıfır olarak belirtilmişse, havuzdaki bağlantılar bir hareketsizlik döneminden sonra kapatılır. Ancak, belirtilen `MinPoolSize` sıfırdan büyükse, bağlantı havuzu boşaltılına `AppDomain` ve işlem sona erene kadar yok edilmez. Etkin olmayan veya boş havuzların bakımı, en az sistem ek yükü içerir.  
  
> [!NOTE]
> Önemli bir hata olduğunda havuz otomatik olarak temizlenir( örneğin, bir hata.  
  
## <a name="adding-connections"></a>Bağlantı Ekleme  
 Her benzersiz bağlantı dizesi için bir bağlantı havuzu oluşturulur. Bir havuz oluşturulduğunda, en az havuz boyutu gereksiniminin karşılanması için birden çok bağlantı nesnesi oluşturulur ve havuza eklenir. Bağlantılar gerektiğinde havuza, belirtilen maksimum havuz boyutuna kadar eklenir (100 varsayılandır). Bağlantılar kapatıldıklarında veya imha edildiklerinde havuza geri salınır.  
  
 Bir <xref:System.Data.SqlClient.SqlConnection> nesne istendiğinde, kullanılabilir bir bağlantı varsa havuzdan elde edilir. Kullanılabilir olması için bağlantının kullanılmaması, eşleşen bir işlem bağlamı olması veya herhangi bir işlem bağlamıyla ilişkisinin kullanılmaması ve sunucuya geçerli bir bağlantısı olması gerekir.  
  
 Bağlantı havuzu, bağlantıları havuza geri salınan bağlantıları yeniden tahsis ederek bağlantı isteklerini karşılar. En büyük havuz boyutuna ulaşıldıysa ve kullanılabilir bağlantı yoksa, istek sıraya alınır. Havuzcu daha sonra zaman ayarı ulaşılana kadar (varsayılan 15 saniyedir) bağlantıları geri almaya çalışır. Havuzcu bağlantı süreleri dolmadan önce isteği karşılayamıyorsa, bir özel durum atılır.  
  
> [!CAUTION]
> Bağlantının havuza döndürülebilmeleri için bağlantıyı kullanmayı bitirdiğinizde bağlantıyı her zaman kapatmanızı öneririz. Bunu `Close` nesnenin `Dispose` yöntemlerini `Connection` kullanarak veya C#'daki bir `using` deyimin içindeki tüm bağlantıları `Using` açarak veya Visual Basic'teki bir ifadeyi kullanarak yapabilirsiniz. Açıkça kapatılmayan bağlantılar eklenmeyebilir veya havuza döndürülebilir. Daha fazla bilgi [için, Bildirim'i veya](../../../csharp/language-reference/keywords/using-statement.md) Nasıl Olur: Visual Basic için [Bir Sistem Kaynağından Nasıl Atınır'a](../../../visual-basic/programming-guide/language-features/control-flow/how-to-dispose-of-a-system-resource.md) bakın.  
  
> [!NOTE]
> Sınıfınızın `Close` yönteminde `Finalize` `Connection`bir `DataReader`, a veya başka bir yönetilen nesneyi aramayın. `Dispose` Sonlandırıcıda, yalnızca sınıfınızın doğrudan sahip olduğu yönetilmeyen kaynakları serbest bırakın. Sınıfınız yönetilmeyen kaynaklara sahip değilse, sınıf `Finalize` tanımınıza bir yöntem eklemeyin. Daha fazla bilgi için [Çöp Toplama'ya](../../../standard/garbage-collection/index.md)bakın.  
  
Bağlantıları açma ve kapatmayla ilgili olaylar hakkında daha fazla bilgi için SQL Server belgelerinde [Denetim Giriş Etkinlik Sınıfı](/sql/relational-databases/event-classes/audit-login-event-class) ve Denetim Giriş Etkinlik [Sınıfı'na](/sql/relational-databases/event-classes/audit-logout-event-class) bakın.  
  
## <a name="removing-connections"></a>Bağlantıları Kaldırma  
 Bağlantı havuzu, yaklaşık 4-8 dakika boşta kaldıktan sonra veya havuzlayıcı sunucuyla bağlantının kesildiğini algılarsa havuzdan bir bağlantı kaldırır. Kopmuş bir bağlantının ancak sunucuyla iletişim kurmaya çalıştıktan sonra algılanabileceğini unutmayın. Artık sunucuya bağlı olmayan bir bağlantı bulunursa, geçersiz olarak işaretlenir. Geçersiz bağlantılar yalnızca kapatıldığında veya geri alındıklarında bağlantı havuzundan kaldırılır.  
  
 Kaybolan bir sunucuya bağlantı varsa, bağlantı havuzcu kopan bağlantıyı algılayıp geçersiz olarak işaretlemiş olsa bile bu bağlantı havuzdan çekilebilir. Bu durum, bağlantının hala geçerli olup olmadığını denetleme nin ek yükü, sunucuya başka bir gidiş-dönüş yolculuğun oluşmasına neden olarak bir havuz sahibine sahip olmanın avantajlarını ortadan kaldıracağı için durum böyledir. Bu durumda, bağlantıyı kullanmak için ilk girişimi bağlantı kesilmiş olduğunu algılar ve bir özel durum atılır.  
  
## <a name="clearing-the-pool"></a>Havuzu Temizleme  
 ADO.NET 2.0 havuzu temizlemek için iki <xref:System.Data.SqlClient.SqlConnection.ClearAllPools%2A> yeni <xref:System.Data.SqlClient.SqlConnection.ClearPool%2A>yöntem tanıttı: ve . `ClearAllPools`Belirli bir sağlayıcının bağlantı havuzlarını `ClearPool` temizler ve belirli bir bağlantıyla ilişkili bağlantı havuzunu temizler. Arama sırasında kullanılan bağlantılar varsa, bunlar uygun şekilde işaretlenir. Kapatıldıklarında, havuza döndürülmek yerine atılırlar.  
  
## <a name="transaction-support"></a>İşlem Desteği  
 Bağlantılar havuzdan çizilir ve hareket bağlamına göre atanır. Bağlantı `Enlist=false` dizesinde belirtilmediği sürece, bağlantı havuzu bağlantının <xref:System.Transactions.Transaction.Current%2A> bağlam içinde kaydolduğundan emin olmasını sağlar. Bir bağlantı kapatıldığında ve kayıtlı `System.Transactions` bir işlemle havuza döndürüldüğünde, aynı `System.Transactions` işlemle bu bağlantı havuzu için bir sonraki istek varsa aynı bağlantıyı döndürecek şekilde bir kenara bırakılır. Böyle bir istek verilirse ve havuzlu bağlantı yoksa, havuzun işlenmemiş kısmından bir bağlantı çizilir ve kaydolur. Havuzun her iki alanında da bağlantı yoksa, yeni bir bağlantı oluşturulur ve kaydolur.  
  
 Bir bağlantı kapatıldığında, işlem bağlamına göre havuza ve uygun alt bölüme geri bırakılır. Bu nedenle, dağıtılmış bir hareket beklemede olsa bile, hata oluşturmadan bağlantıyı kapatabilirsiniz. Bu, dağıtılmış hareketi daha sonra gerçekleştirmenize veya iptal etmenizi sağlar.  
  
## <a name="controlling-connection-pooling-with-connection-string-keywords"></a>Bağlantı Dize anahtar kelimeleri ile Bağlantı Havuzu denetleme  
 Nesnenin `ConnectionString` <xref:System.Data.SqlClient.SqlConnection> özelliği, bağlantı birleştirme mantığının davranışını ayarlamak için kullanılabilecek bağlantı dize anahtarlarını/değer çiftlerini destekler. Daha fazla bilgi için bkz. <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
## <a name="pool-fragmentation"></a>Havuz Parçalanması  
 Havuz parçalanması, uygulamanın işlem çıkana kadar serbest bırakılmayan çok sayıda havuz oluşturabileceği birçok Web uygulamasında yaygın bir sorundur. Bu, çok sayıda bağlantıyı açık ve bellek tüketen bırakır ve bu da düşük performansa neden olabilir.  
  
### <a name="pool-fragmentation-due-to-integrated-security"></a>Entegre Güvenlik Nedeniyle Havuz Parçalanma  
 Bağlantılar, bağlantı dizesine ve kullanıcı kimliğine göre biraraya getirilmiştir. Bu nedenle, Web sitesinde Temel kimlik doğrulama veya Windows Kimlik Doğrulama ve tümleşik bir güvenlik girişi kullanırsanız, kullanıcı başına bir havuz elde elabilirsiniz. Bu, tek bir kullanıcı için sonraki veritabanı isteklerinin performansını artırsa da, bu kullanıcı diğer kullanıcılar tarafından yapılan bağlantılardan yararlanamaz. Ayrıca, kullanıcı başına veritabanı sunucusuna en az bir bağlantı sağlar. Bu, geliştiricilerin güvenlik ve denetim gereksinimlerine karşı tartmak gerekir belirli bir Web uygulaması mimarisinin bir yan etkisidir.  
  
### <a name="pool-fragmentation-due-to-many-databases"></a>Birçok Veritabanına Bağlı Havuz Parçalanma  
 Birçok Internet servis sağlayıcısı, tek bir sunucuda birden fazla Web sitesi barındırz. Formlar kimlik doğrulama oturumunu onaylamak ve ardından söz konusu kullanıcı veya kullanıcı grubu için belirli bir veritabanına bağlantı açmak için tek bir veritabanı kullanabilirler. Kimlik doğrulama veritabanına bağlantı bir araya ve herkes tarafından kullanılır. Ancak, her veritabanına sunucuya bağlantı sayısını artıran ayrı bir bağlantı havuzu vardır.  
  
 Bu aynı zamanda uygulama tasarımının bir yan etkisidir. SQL Server'a bağlandığınızda güvenlikten ödün vermeden bu yan etkiyi önlemenin nispeten basit bir yolu vardır. Her kullanıcı veya grup için ayrı bir veritabanına bağlanmak yerine, sunucudaki aynı veritabanına bağlanın ve ardından istenen veritabanına değişmek için Transact-SQL USE deyimini çalıştırın. Aşağıdaki kod parçası `master` veritabanına bir ilk bağlantı oluşturma ve daha sonra `databaseName` dize değişkeninde belirtilen istenen veritabanına geçiş gösterir.  
  
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
  
## <a name="application-roles-and-connection-pooling"></a>Uygulama Rolleri ve Bağlantı Havuzu  
 Bir SQL Server uygulama rolü `sp_setapprole` sistem depolanan yordamı çağırarak etkinleştirildikten sonra, bu bağlantının güvenlik bağlamı sıfırlanamaz. Ancak, havuzlama etkinse, bağlantı havuza döndürülür ve havuzdaki bağlantı yeniden kullanıldığında bir hata oluşur. Daha fazla bilgi için Bilgi Bankası makalesine bakın, "[OLE DB kaynak havuzu ile SQL uygulama rol hataları."](https://support.microsoft.com/default.aspx?scid=KB;EN-US;Q229564)  
  
### <a name="application-role-alternatives"></a>Uygulama Rolü Alternatifleri  
 Uygulama rolleri yerine kullanabileceğiniz güvenlik mekanizmalarından yararlanmanızı öneririz. Daha fazla bilgi için [bkz.](./sql/creating-application-roles-in-sql-server.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bağlantı Havuzu](connection-pooling.md)
- [SQL Server ve ADO.NET](./sql/index.md)
- [Performans Sayaçları](performance-counters.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)

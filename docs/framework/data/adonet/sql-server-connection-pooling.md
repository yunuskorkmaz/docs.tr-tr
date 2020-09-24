---
title: SQL Server bağlantı havuzu
description: Yeni bağlantıların yükünü azaltan SQL Server bağlantı havuzu kullanarak bağlantıların ADO.NET nasıl en aza indirecek hakkında bilgi edinin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e51d44e-7c4e-4040-9332-f0190fe36f07
ms.openlocfilehash: 96d9e9a7e43f71dc30bd2d7a7f1902238941d471
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156361"
---
# <a name="sql-server-connection-pooling-adonet"></a>SQL Server Bağlantı Havuzu (ADO.NET)

Bir veritabanı sunucusuna bağlanmak genellikle birkaç zaman alan adımdan oluşur. Yuva veya adlandırılmış kanal gibi bir fiziksel kanal oluşturulması gerekir, sunucu ile ilk el sıkışma gerçekleşmelidir, bağlantı dizesi bilgileri ayrıştırılmalıdır, bağlantının sunucu tarafından doğrulanması gerekir, bu, geçerli işlemde son listeye alındı ve bu şekilde devam eder.  
  
 Uygulamada çoğu uygulama, bağlantılar için yalnızca bir veya birkaç farklı yapılandırma kullanır. Yani, uygulama yürütme sırasında birçok özdeş bağlantı tekrar tekrar açılıp kapatılacaktır. ADO.NET bağlantıları açma maliyetini en aza indirmek için, *bağlantı havuzu*adlı bir iyileştirme tekniği kullanır.  
  
 Bağlantı havuzu yeni bağlantıların kaç kez açılması gerektiğini azaltır. *Havuzlayıcı* fiziksel bağlantının sahipliğini tutar. Belirli bir bağlantı yapılandırması için etkin bir etkin bağlantı kümesi tutarak bağlantıları yönetir. Kullanıcı `Open` bir bağlantı üzerinde her çağırdığında havuzlayıcı havuzda kullanılabilir bir bağlantı arar. Havuza alınmış bir bağlantı varsa, yeni bir bağlantı açmak yerine bunu çağırana döndürür. Uygulama, bağlantıda çağrı yaparken `Close` , havuzlayıcı onu kapatmak yerine havuza alınmış etkin bağlantılar kümesine geri döndürür. Bağlantı havuza döndürüldüğünde, sonraki çağrıda yeniden kullanılmak üzere kullanılabilir `Open` .  
  
 Yalnızca aynı yapılandırmaya sahip bağlantılar havuza alınabilir. ADO.NET, her yapılandırma için bir tane olmak üzere birkaç havuzu aynı anda tutar. Bağlantılar, tümleşik güvenlik kullanıldığında bağlantı dizesine ve Windows kimliğine göre havuzlara ayrılır. Bağlantılar Ayrıca, bir işlemde kayıtlı olup olmadıkları temel alınarak da havuza alınır. Kullanırken <xref:System.Data.SqlClient.SqlConnection.ChangePassword%2A> , <xref:System.Data.SqlClient.SqlCredential> örnek bağlantı havuzunu etkiler. Farklı örnekleri <xref:System.Data.SqlClient.SqlCredential> , Kullanıcı kimliği ve parola aynı olsa bile farklı bağlantı havuzları kullanacaktır.  
  
 Havuzlama bağlantıları, uygulamanızın performansını ve ölçeklenebilirliğini önemli ölçüde geliştirebilir. Varsayılan olarak, ADO.NET ' de bağlantı havuzu etkindir. Açıkça devre dışı bırakılmadığınız sürece havuzlayıcı, uygulamanızda açılıp kapandıkça bağlantıları en iyi duruma getirir. Ayrıca, bağlantı havuzu davranışlarını denetlemek için çeşitli bağlantı dizesi değiştiricileri sağlayabilirsiniz. Daha fazla bilgi için bu konunun devamındaki "bağlantı dizesi anahtar sözcükleriyle bağlantı havuzunu denetleme" bölümüne bakın.  
  
> [!NOTE]
> Bağlantı havuzu etkinleştirildiğinde ve bir zaman aşımı hatası ya da başka bir oturum açma hatası oluşursa, bir özel durum oluşturulur ve sonraki bağlantı denemeleri sonraki beş saniye boyunca başarısız olur ve "engelleme dönemi". Uygulama engelleme süresi içinde bağlanmaya çalışırsa, ilk özel durum yeniden oluşturulur. Bir engelleme süresi sona erdikten sonraki hatalar, önceki engelleme süresi kadar iki kez bir dakika kadar olan yeni bir engelleme dönemi oluşmasına neden olur.  
  
## <a name="pool-creation-and-assignment"></a>Havuz oluşturma ve atama  

 Bir bağlantı ilk kez açıldığında, havuzu bağlantıdaki bağlantı dizesiyle ilişkilendiren tam bir eşleşen algoritmaya göre bir bağlantı havuzu oluşturulur. Her bağlantı havuzu ayrı bir bağlantı dizesiyle ilişkilendirilir. Yeni bir bağlantı açıldığında, bağlantı dizesi var olan bir havuza tam eşleşme değilse yeni bir havuz oluşturulur. Bağlantılar işlem başına, her uygulama etki alanı, bağlantı dizesi başına ve tümleşik güvenlik kullanıldığında Windows kimliği başına havuza alınır. Bağlantı dizeleri de tam eşleşme olmalıdır; aynı bağlantı için farklı bir sırada sağlanan anahtar sözcükler ayrı olarak havuza alınır.  
  
 Aşağıdaki C# örneğinde, üç yeni <xref:System.Data.SqlClient.SqlConnection> nesne oluşturulur, ancak bunları yönetmek için yalnızca iki bağlantı havuzu gerekir. Birinci ve ikinci bağlantı dizelerinin, için atanan değerle farklı olduğunu unutmayın `Initial Catalog` .  
  
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
  
 `MinPoolSize`Bağlantı dizesinde belirtilmemişse veya sıfır olarak belirtilmişse, havuzdaki bağlantılar bir süre etkinlik dışı kaldıktan sonra kapatılacaktır. Ancak, belirtilen değer `MinPoolSize` sıfırdan büyükse bağlantı havuzu, `AppDomain` kaldırılana ve işlem sona erene kadar yok edilmez. Etkin olmayan veya boş havuzların bakımı en düşük sistem yükünü içerir.  
  
> [!NOTE]
> Havuz, yük devretme gibi önemli bir hata oluştuğunda otomatik olarak temizlenir.  
  
## <a name="adding-connections"></a>Bağlantı ekleme  

 Her benzersiz bağlantı dizesi için bir bağlantı havuzu oluşturulur. Bir havuz oluşturulduğunda, en düşük havuz boyutu gereksiniminin karşılanması için birden fazla bağlantı nesnesi oluşturulur ve havuza eklenir. Bağlantılar, belirtilen en büyük havuz boyutuna kadar (varsayılan olarak 100), havuza gerektiği şekilde eklenir. Bağlantılar, kapalı veya atılmış olmaları durumunda havuza geri yayımlanır.  
  
 Bir <xref:System.Data.SqlClient.SqlConnection> nesne istendiğinde, kullanılabilir bir bağlantı varsa havuzdan alınır. Kullanılabilir olması için bir bağlantının kullanılmamış olması, eşleşen bir işlem bağlamına sahip olması veya herhangi bir işlem bağlamı ile ilişkilendirilmemiş olması ve sunucuya geçerli bir bağlantısı olması gerekir.  
  
 Bağlantı havuzlayıcı, havuza geri yayımlandıklarında bağlantıları yeniden bulmaya göre bağlantı isteklerini karşılar. En büyük havuz boyutuna ulaşılmışsa ve kullanılabilir bir bağlantı yoksa, istek sıraya alınır. Havuzlayıcı daha sonra zaman aşımına ulaşılana kadar tüm bağlantıları geri almaya çalışır (varsayılan değer 15 saniyedir). Bağlantı zaman aşımına uğramadan havuzlayıcı isteği karşılayamaz, bir özel durum oluşturulur.  
  
> [!CAUTION]
> Bağlantının havuza döndürülabilmesi için, kullanmayı bitirdiğinizde bağlantıyı her zaman kapatmanızı öneririz. Bunu, nesnesinin ya da yöntemlerinden birini ya da `Close` `Dispose` `Connection` C# içindeki bir deyimin içindeki tüm bağlantıları `using` ya da `Using` Visual Basic bir ifadesini kullanarak yapabilirsiniz. Açıkça kapatılmayan bağlantılar, havuza eklenmeyebilir veya havuza döndürülemez. Daha fazla bilgi için bkz. [using deyimleri](../../../csharp/language-reference/keywords/using-statement.md) veya [nasıl yapılır: Visual Basic Için sistem kaynağını atma](../../../visual-basic/programming-guide/language-features/control-flow/how-to-dispose-of-a-system-resource.md) .  
  
> [!NOTE]
> `Close` `Dispose` Sınıfınızın yönteminde bir, veya `Connection` ya da başka bir `DataReader` yönetilen nesneyi `Finalize` çağırmayın. Sonlandırıcıda yalnızca, sınıfınızın doğrudan sahip olduğu yönetilmeyen kaynakları serbest bırakın. Sınıfınız hiçbir yönetilmeyen kaynağa sahip değilse, `Finalize` sınıf tanımınıza bir yöntem eklemeyin. Daha fazla bilgi için bkz. [çöp toplama](../../../standard/garbage-collection/index.md).  
  
Açma ve kapatma bağlantılarıyla ilişkili olaylar hakkında daha fazla bilgi için, SQL Server belgelerinde [oturum açma olay sınıfını denetleme ve oturum](/sql/relational-databases/event-classes/audit-login-event-class) [kapatma olayı sınıfını](/sql/relational-databases/event-classes/audit-logout-event-class) denetleme bölümüne bakın.  
  
## <a name="removing-connections"></a>Bağlantılar kaldırılıyor  

 Bağlantı havuzlayıcı yaklaşık 4-8 dakika boyunca boşta kaldıktan sonra havuzdan bir bağlantıyı kaldırır veya havuzlayıcı sunucuyla bağlantının bozulmuş olduğunu algılarsa. Bir bağlantı kurulan bağlantının yalnızca sunucuyla iletişim kurmaya çalıştıktan sonra algılanabileceğini unutmayın. Artık sunucuya bağlı olmayan bir bağlantı bulunursa, geçersiz olarak işaretlenir. Geçersiz bağlantılar, bağlantı havuzundan yalnızca kapalı veya geri kazanılanlar sırasında kaldırılır.  
  
 Kaybolan bir sunucuya bağlantı varsa, bağlantı havuzlayıcı bağlantıyı algılamamış ve geçersiz olarak işaretlediği halde bu bağlantı havuzdan çizilebilirler. Bu durum, bağlantının hala geçerli olduğunu denetleme yükünün, sunucu üzerinde başka bir gidiş dönüş olmasına neden olarak bir Havuzluğa sahip olmanın avantajlarından ortadan kaldırılmasına neden olur. Bu gerçekleştiğinde, bağlantıyı ilk kez kullanma denemesi bağlantının bozulmuş olduğunu algılar ve bir özel durum oluşturulur.  
  
## <a name="clearing-the-pool"></a>Havuz temizleniyor  

 ADO.NET 2,0, havuzu temizlemek için iki yeni yöntem sunmuştur: <xref:System.Data.SqlClient.SqlConnection.ClearAllPools%2A> ve <xref:System.Data.SqlClient.SqlConnection.ClearPool%2A> . `ClearAllPools` belirli bir sağlayıcı için bağlantı havuzlarını temizler ve `ClearPool` belirli bir bağlantıyla ilişkili bağlantı havuzunu temizler. Çağrı sırasında kullanılan bağlantılar varsa, bunlar uygun şekilde işaretlenir. Kapatıldığında, havuza döndürülmek yerine atılır.  
  
## <a name="transaction-support"></a>İşlem Desteği  

 Bağlantılar havuzdan çizilir ve işlem bağlamına göre atanır. `Enlist=false`Bağlantı dizesinde belirtilmedikçe, bağlantı havuzu bağlantının bağlamda kayıtlı olduğundan emin olur <xref:System.Transactions.Transaction.Current%2A> . Bir bağlantı kapatılıp, kayıtlı bir işlemle havuza döndürüldüğünde `System.Transactions` , bu bağlantı havuzu için bir sonraki isteğin, varsa aynı işlemle aynı bağlantıyı döndürmesi için bu şekilde ayarlanır `System.Transactions` . Bu tür bir istek verildiyse ve havuza alınmış bağlantı yoksa, havuzun işlem temelli olmayan kısmından bir bağlantı çizilir ve listeye kaydedilir. Havuzun herhangi bir alanında hiçbir bağlantı yoksa, yeni bir bağlantı oluşturulur ve listeye kaydedilir.  
  
 Bir bağlantı kapatıldığında, havuza ve işlem bağlamına göre uygun alt bölüme geri gönderilir. Bu nedenle, dağıtılmış bir işlem hala beklense de bir hata oluşturmadan bağlantıyı kapatabilirsiniz. Bu, dağıtılmış işlemi daha sonra yürütmeniz veya iptal etmenizi sağlar.  
  
## <a name="controlling-connection-pooling-with-connection-string-keywords"></a>Bağlantı havuzu bağlantı dizesi anahtar sözcükleriyle denetleniyor  

 `ConnectionString`Nesnesinin özelliği, <xref:System.Data.SqlClient.SqlConnection> bağlantı havuzu mantığının davranışını ayarlamak için kullanılabilen bağlantı dizesi anahtar/değer çiftlerini destekler. Daha fazla bilgi için bkz. <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
## <a name="pool-fragmentation"></a>Havuz parçalanması  

 Havuz parçalanması, uygulamanın, işlem bitene kadar serbest bırakılmamış çok sayıda havuz oluşturbildiği birçok Web uygulamasında yaygın bir sorundur. Bu, bellek açma ve tüketme gibi çok sayıda bağlantı bırakır ve bu da performansı düşük bir performansla sonuçlanır.  
  
### <a name="pool-fragmentation-due-to-integrated-security"></a>Tümleşik güvenlik nedeniyle havuz parçalanması  

 Bağlantılar bağlantı dizesine ve kullanıcı kimliğine göre havuza alınır. Bu nedenle, Web sitesinde ve tümleşik güvenlik oturumunda temel kimlik doğrulaması veya Windows kimlik doğrulaması kullanıyorsanız, Kullanıcı başına bir havuz alırsınız. Bu, tek bir kullanıcı için sonraki veritabanı isteklerinin performansını artırsa da, bu kullanıcı diğer kullanıcılar tarafından yapılan bağlantılardan yararlanamaz. Ayrıca veritabanı sunucusuna Kullanıcı başına en az bir bağlantıya neden olur. Bu, geliştiricilerin güvenlik ve denetim gereksinimlerine göre karşılaştırmasını gerektiren belirli bir Web uygulaması mimarisinin yan etkisidir.  
  
### <a name="pool-fragmentation-due-to-many-databases"></a>Birçok veritabanı nedeniyle havuz parçalanması  

 Birçok Internet hizmet sağlayıcısı tek bir sunucuda birçok Web sitesini barındırır. Bir form kimlik doğrulaması oturum açma bilgilerini doğrulamak ve bu kullanıcı veya Kullanıcı grubu için belirli bir veritabanına bağlantı açmak için tek bir veritabanı kullanabilirler. Kimlik doğrulama veritabanına olan bağlantı havuza alınmış ve herkes tarafından kullanılır. Ancak, her bir veritabanına yönelik bağlantı sayısını artıran ayrı bir bağlantı havuzu vardır.  
  
 Bu, Uygulama tasarımının de yan etkıdır. SQL Server bağlandığınızda güvenliği tehlikeye atmadan bu yan etkilerden kaçınmak için görece basit bir yol vardır. Her Kullanıcı veya grup için ayrı bir veritabanına bağlanmak yerine, sunucuda aynı veritabanına bağlanın ve ardından Transact-SQL USE ifadesini çalıştırıp istenen veritabanına geçin. Aşağıdaki kod parçası, veritabanına bir ilk bağlantı oluşturulmasını `master` ve sonra dize değişkeninde belirtilen istenen veritabanına geçmeyi gösterir `databaseName` .  
  
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

 Bir SQL Server uygulama rolü `sp_setapprole` sistem saklı yordamı çağırarak etkinleştirildikten sonra, bu bağlantının güvenlik bağlamı sıfırlanamaz. Ancak, Havuzlama etkinse bağlantı havuza döndürülür ve havuza alınmış bağlantı yeniden kullanıldığında bir hata oluşur. Daha fazla bilgi için bkz. Bilgi Bankası makalesi, "[OLE DB kaynak havuzlama Ile SQL uygulama rolü hataları](https://support.microsoft.com/default.aspx?scid=KB;EN-US;Q229564)".  
  
### <a name="application-role-alternatives"></a>Uygulama rolü alternatifleri  

 Uygulama rolleri yerine kullanabileceğiniz güvenlik mekanizmalarının avantajlarından yararlanmanızı öneririz. Daha fazla bilgi için bkz. [SQL Server uygulama rolleri oluşturma](./sql/creating-application-roles-in-sql-server.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bağlantı Havuzu](connection-pooling.md)
- [SQL Server ve ADO.NET](./sql/index.md)
- [Performans sayaçları](performance-counters.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)

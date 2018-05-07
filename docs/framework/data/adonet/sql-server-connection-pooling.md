---
title: SQL Server bağlantı (ADO.NET) havuzu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e51d44e-7c4e-4040-9332-f0190fe36f07
ms.openlocfilehash: 78e852e2f1894f92e5b43228faedfad0d78981fa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="sql-server-connection-pooling-adonet"></a>SQL Server bağlantı (ADO.NET) havuzu
Genellikle bir veritabanı sunucusuna bağlanmayı zaman birkaç adımdan oluşur. Bir yuva veya bir adlandırılmış kanal gibi fiziksel bir kanal, sunucu ile ilk el sıkışma olmalıdır, kurulmalıdır bağlantı dizesi bilgilerini ayrıştırılır, bağlantı sunucu tarafından doğrulanması gerekir, denetimleri içinde kaydetme için çalıştırılması gerekir Geçerli hareket ve benzeri.  
  
 Uygulamada, çoğu uygulamayı bağlantıları için yalnızca bir veya birkaç farklı yapılandırmaları kullanın. Bu uygulama yürütmesi sırasında birçok aynı bağlantıları art arda açılan kapalı anlamına gelir. Bağlantılar, açma maliyetini en aza indirmek için [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] adında bir en iyi duruma getirme teknik kullanır *bağlantı havuzu*.  
  
 Bağlantı havuzu yeni bağlantıları açılmalıdır sayısını azaltır. *Havuzlayıcı* fiziksel bağlantı sahipliğini korur. Etkin bağlantılar her verilen bağlantı yapılandırması için bir dizi canlı tutma tarafından bağlantılarını yönetir. Her bir kullanıcı çağırır `Open` bir bağlantıda bir bağlantı havuzundaki havuzlayıcı arar. Havuza alınmış bir bağlantının kullanılabilir olması durumunda, bunu yeni bir bağlantı açarak yerine çağırana döndürür. Uygulama çağırdığında `Close` bağlantıda havuzlayıcı, kapatma yerine etkin bağlantıları havuza alınmış kümesini döndürür. Bağlantı havuza geri döndüğünde, sonraki yüklenmek için hazır `Open` çağırın.  
  
 Yalnızca aynı yapılandırmaya sahip bağlantılar havuza. [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] aynı zamanda, her yapılandırma için bir tane birkaç havuzu tutar. Tümleşik güvenlik kullanıldığında bağlantıları bağlantı dizesi ve Windows Identity havuzlara ayrılır. Bağlantılar olup bunlar işlemde kayıtlıdır üzerinde temel da verebilir. Kullanırken <xref:System.Data.SqlClient.SqlConnection.ChangePassword%2A>, <xref:System.Data.SqlClient.SqlCredential> örneği bağlantı havuzu etkiler. Farklı örnekleri <xref:System.Data.SqlClient.SqlCredential> kullanıcı kimliği ve parola aynı olsa bile farklı bağlantı havuzu kullanır.  
  
 Bağlantı havuzu önemli ölçüde performans ve ölçeklenebilirlik, uygulamanızın geliştirebilirsiniz. Varsayılan olarak, bağlantı havuzu etkin [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]. Açıkça devre dışı sürece açılır ve uygulamanızda kapalı olarak havuzlayıcı bağlantıları en iyi duruma getirir. Bağlantı havuzu oluşturma davranışını denetlemek için çeşitli bağlantı dizesi değiştiricileri de sağlayabilir. Daha fazla bilgi için bu konunun ilerleyen bölümlerinde "Denetleme bağlantı havuzu ile bağlantı dizesi anahtar sözcükler" konusuna bakın.  
  
> [!NOTE]
>  Bağlantı havuzu etkin olduğunda ve bir zaman aşımı hatası veya başka bir oturum açma hata oluşursa, bir özel durum ve sonraki beş için "engelleme süresini saniye" sonraki bağlantı girişimleri başarısız olur. Uygulama engelleme süresi içinde bağlanmaya çalışırsa, ilk özel durum yeniden oluşturulur. Engelleme süresi sona erdikten sonra sonraki hataları iki kez önceki engelleme süresi en fazla bir dakika sürece yeni bir engelleme nokta sonuçlanır.  
  
## <a name="pool-creation-and-assignment"></a>Havuz oluşturma ve atama  
 Bir bağlantı ilk kez açıldığında, bağlantı havuzu bağlantı dizesini içeren bağlantı havuzu ilişkilendirir tam bir eşleştirme algoritması temel alınarak oluşturulur. Her bağlantı havuzu ayrı bağlantı dizesi ile ilişkilidir. Yeni bir bağlantı açıldığında, bağlantı dizesi var olan bir havuzu için tam bir eşleşme değilse yeni bir havuz oluşturulur. Uygulama etki alanı, bağlantı dizesi başına ve tümleşik güvenlik kullanıldığında, Windows kimlik her işlem başına bağlantılar havuza. Bağlantı dizeleri de tam eşleşme olmalıdır; anahtar sözcükler, aynı bağlantı için farklı bir sırayla sağlanan ayrı olarak havuza.  
  
 Aşağıdaki örnekte C#, yeni üç <xref:System.Data.SqlClient.SqlConnection> nesneler oluşturulur, ancak yalnızca iki bağlantı havuzu bunları yönetmek için gereklidir. Birinci ve ikinci bağlantı dizeleri için atanan değer tarafından farklı Not `Initial Catalog`.  
  
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
  
 Varsa `MinPoolSize` ya da bağlantı dizesinde belirtilmedi veya belirtilen sıfır olarak bağlantıları havuzundaki bir süre işlem yapılmadığında kapatılacak. Ancak, belirtilen `MinPoolSize` , sıfırdan büyük bağlantı havuzu kadar yok edilmez `AppDomain` kaldırılır ve işlem sona erer. Etkin olmayan ya da boş havuzlarının bakım minimum sistem yükünü içerir.  
  
> [!NOTE]
>  Önemli bir hata oluştuğunda bir yük devretme gibi havuzu otomatik olarak temizlenir.  
  
## <a name="adding-connections"></a>Bağlantıları ekleme  
 Bağlantı havuzu her benzersiz bağlantı dizesi için oluşturulur. Bir havuz oluşturduğunuzda, birden çok bağlantı nesneleri oluşturulur ve böylece en küçük havuz boyutu gereksinimini sağlanıyorsa havuzuna eklenir. Bağlantılar, havuza eklendiğinde, gerektiğinde, belirtilen en büyük havuz boyutu kadar (varsayılan değer 100'dır). Kapalı veya elden bağlantıları geri havuza yayınlanır.  
  
 Zaman bir <xref:System.Data.SqlClient.SqlConnection> nesnesi istendi, kullanılabilir bir bağlantının kullanılabilir olması durumunda havuzundan elde edilir. Kullanılabilmesi için bir bağlantı gerekir kullanılmayan, eşleşen bir işlem bağlamına sahip veya hiçbir işlem içerikle ilişkilendirilmemiş ve sunucu için geçerli bir bağlantı vardır.  
  
 Bağlantı havuzlayıcı geri havuza en bağlantıları yeniden ayırma bağlantıları isteklerini karşılar. En büyük havuz boyutuna ulaştı ve kullanılabilir bağlantı yok, istek sıraya alındı. Zaman aşımı ulaşılana kadar tüm bağlantılar geri kazanmak daha sonra havuzlayıcı çalışır (varsayılan değer 15 saniyedir). Bağlantı zaman aşımına uğramadan önce havuzlayıcı isteği gerçekleştiremiyor, özel durum oluşur.  
  
> [!CAUTION]
>  Böylece bağlantı havuza geri döner işiniz bittiğinde, her zaman bağlantı kapatmanızı öneririz. Kullanarak bunu yapabilirsiniz `Close` veya `Dispose` yöntemlerinin `Connection` nesne veya göre içindeki tüm bağlantılar'ı açma bir `using` C# ' ta, deyimi veya `Using` Visual Basic'de deyimini. Açıkça kapatılmamış bağlantıları eklenemez veya havuza geri döner. Daha fazla bilgi için bkz: [deyimiyle](~/docs/csharp/language-reference/keywords/using-statement.md) veya [nasıl yapılır: bir sistem kaynağını atma](~/docs/visual-basic/programming-guide/language-features/control-flow/how-to-dispose-of-a-system-resource.md) Visual Basic.  
  
> [!NOTE]
>  Çağırmayın `Close` veya `Dispose` üzerinde bir `Connection`, `DataReader`, veya diğer yönetilen nesne içinde `Finalize` sınıfınızın yöntemi. Bir Sonlandırıcı, yalnızca sınıfınız doğrudan sahibi yönetilmeyen kaynakları serbest bırakmak. Sınıfınıza yönetilmeyen kaynakları sahip olmadığından, içermeyen bir `Finalize` Sınıf tanımınız yöntemi. Daha fazla bilgi için bkz: [çöp toplama](../../../../docs/standard/garbage-collection/index.md).  
  
> [!NOTE]
>  Bir bağlantı öğesinden alınan ya da bağlantı havuza geri döner sunucuda oturum açma ve kapatma olayları oluşturulmaz. Bağlantı havuzu döndürüldüğünde bağlantı gerçekte kapalı olmasıdır. Daha fazla bilgi için bkz: [denetim oturum açma olay sınıfı](http://msdn2.microsoft.com/library/ms190260.aspx) ve [denetim oturum kapatma olay sınıfı](http://msdn2.microsoft.com/library/ms175827.aspx) SQL Server Books Online.  
  
## <a name="removing-connections"></a>Bağlantıları kaldırma  
 Bağlantı havuzlayıcı yaklaşık 4-8 dakika boşta kaldıktan sonra ya da havuzlayıcı sunucusuyla bağlantı zarar görmesi olduğunu algılarsa havuzundan bir bağlantıyı kaldırır. Kesilen bağlantı yalnızca sunucusuyla iletişim kurmaya sonra algılanabilmesi unutmayın. Bir bağlantı, artık sunucuya bağlı bulunursa, geçersiz olarak işaretlendi. Yalnızca bunlar iadesi ya da kapatıldığında geçersiz bağlantıları bağlantı havuzundan kaldırılır.  
  
 Bir bağlantı kayboldu bir sunucuya varsa, bağlantı havuzlayıcı kesilen bağlantı algıladı değil ve geçersiz olarak işaretlenmiş olsa bile bu bağlantı havuzundan çizilebilir. Başka bir gidiş dönüş gerçekleşmesi için sunucuya neden olan bir havuzlayıcı sahip avantajlarını bağlantı hala geçerli olduğunu denetleme yükünü ortadan kaldırır çünkü bu durumdur. Bu durumda, ilk bağlantı kullanma girişimi bağlantı zarar görmesi ve bir özel durum algılar.  
  
## <a name="clearing-the-pool"></a>Havuz temizleme  
 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 2.0 sunulan havuzu temizlemek için iki yeni yöntemleri: <xref:System.Data.SqlClient.SqlConnection.ClearAllPools%2A> ve <xref:System.Data.SqlClient.SqlConnection.ClearPool%2A>. `ClearAllPools` bağlantı havuzu için belirli bir sağlayıcı, temizler ve `ClearPool` belirli bir bağlantı ile ilişkili bağlantı havuzu temizler. Çağrı aynı anda kullanılan bağlantılarının varsa, bunlar uygun şekilde işaretlenir. Kapatıldığında, havuza geri döner yerine atılır.  
  
## <a name="transaction-support"></a>İşlem desteği  
 Bağlantı havuzu ve atanan göre işlem bağlamı çizilir. Sürece `Enlist=false` belirtilen bağlantı dizesinde bağlantı havuzu yapar bağlantı kayıtlı emin olarak <xref:System.Transactions.Transaction.Current%2A> bağlamı. Ne zaman bir bağlantı kapatılır ve bir kayıtlı havuzuyla döndürülen `System.Transactions` işlem, bu ayarlanmış kenara sonraki aynı o bağlantı havuzu için istek şekilde `System.Transactions` işlem varsa aynı bağlantıyı döndürür. Böyle bir istek verilir ve havuza alınan bağlantı kullanılabilir değilse, bir bağlantı havuzu işlem temelli olmayan bölümünden çizilmiş ve kayıtlı. Bağlantı havuzu ya da alanında varsa, yeni bir bağlantı oluşturulur ve kayıtlı.  
  
 Bağlantı kapalı olduğunda geri havuza ve kendi işlem bağlamına dayalı uygun alt bölümü olarak yayımlanır. Dağıtılmış işlem hala olsa bile bu nedenle, bağlantı bir hata oluşturmadan kapatabilirsiniz bekliyor. Bu, tamamlama veya dağıtılmış işlem daha sonra iptal olanak sağlar.  
  
## <a name="controlling-connection-pooling-with-connection-string-keywords"></a>Bağlantı dizesi anahtar sözcükleriyle bağlantı havuzu denetleme  
 `ConnectionString` Özelliği <xref:System.Data.SqlClient.SqlConnection> nesnesi bağlantı mantığı havuzu davranışını ayarlamak için kullanılan bağlantı dizesi anahtar/değer çiftlerinin destekler. Daha fazla bilgi için bkz. <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
## <a name="pool-fragmentation"></a>Havuzu parçalanması  
 Havuzu parçalanması ortak birçok Web uygulamaları burada uygulama çok sayıda işlem çıkar kadar serbest bırakılmaz havuzları oluşturabilirsiniz sorunudur. Bu, çok sayıda bağlantıları performansın düşmesine neden olur, açık ve alan bellek bırakır.  
  
### <a name="pool-fragmentation-due-to-integrated-security"></a>Tümleşik güvenlik nedeniyle havuzu parçalanması  
 Bağlantılar bağlantı dizesini ve kullanıcı kimliği göre havuza. Bu nedenle, Web sitesi ve bir tümleşik güvenlik oturumu temel kimlik doğrulaması veya Windows kimlik doğrulaması kullanıyorsanız, kullanıcı başına bir havuzu alın. Bu tek bir kullanıcı için sonraki veritabanı isteklerinin performansını iyileştirir karşın, bu kullanıcının diğer kullanıcılar tarafından yapılan bağlantılarının yararlanamaz. Veritabanı sunucusu için kullanıcı başına en az bir bağlantı da sonuçlanır. Geliştiriciler, güvenlik ve denetim gereksinimlerini karşı tartmanız gerekir belirli bir Web uygulama mimarinin bir yan etkisi budur.  
  
### <a name="pool-fragmentation-due-to-many-databases"></a>Birçok veritabanı nedeniyle havuzu parçalanması  
 Çoğu Internet hizmet sağlayıcıları tek bir sunucu üzerinde çeşitli Web sitelerini barındırır. Tek bir veritabanı Forms kimlik doğrulaması oturum açma onaylayın ve ardından kullanıcı veya kullanıcı grubu için belirli bir veritabanına bir bağlantı açmak için kullandıkları. Kimlik doğrulama veritabanı bağlantısı havuza ve herkes tarafından kullanılır. Ancak, sunucuya bağlantı sayısını artıracak bağlantıları her veritabanı için ayrı bir havuz yoktur.  
  
 Bu uygulama tasarımının bir yan etkisi de geçerlidir. SQL sunucusuna bağlandığında, güvenliği tehlikeye atmadan bu yan etkiyi önlemek için oldukça basit bir yolu yoktur. Her kullanıcı veya grup için ayrı bir veritabanına bağlanmak, yerine sunucuda aynı veritabanına bağlanın ve sonra yürütün [!INCLUDE[tsql](../../../../includes/tsql-md.md)] istenilen veritabanına değiştirmek için deyimi kullanın. Aşağıdaki kod parçası ilk bağlantınız oluşturmayı gösterir `master` veritabanı ve belirtilen istenen veritabanına geçiş `databaseName` dize değişkeni.  
  
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
 Bir SQL Server sonra çağırarak uygulama rolü etkinleştirildi `sp_setapprole` sistem saklı yordamı, bu bağlantının güvenlik bağlamı sıfırlayamazsınız. Ancak, havuzu etkinleştirilirse bağlantı havuza geri döner ve havuza alınan bağlantı yeniden denediğinizde hata oluşur. Daha fazla bilgi için bkz. Bilgi Bankası makalesi, "[OLE DB kaynak havuzu ile SQL uygulama rolü hataları](http://support.microsoft.com/default.aspx?scid=KB;EN-US;Q229564)."  
  
### <a name="application-role-alternatives"></a>Uygulama rolü alternatifleri  
 Uygulama rolleri yerine kullanabileceğiniz güvenlik mekanizmaları avantajlarından yararlanmak öneririz. Daha fazla bilgi için bkz: [SQL Server'daki uygulama rolleri oluşturma](../../../../docs/framework/data/adonet/sql/creating-application-roles-in-sql-server.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bağlantı Havuzu](../../../../docs/framework/data/adonet/connection-pooling.md)  
 [SQL Server ve ADO.NET](../../../../docs/framework/data/adonet/sql/index.md)  
 [Performans Sayaçları](../../../../docs/framework/data/adonet/performance-counters.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)

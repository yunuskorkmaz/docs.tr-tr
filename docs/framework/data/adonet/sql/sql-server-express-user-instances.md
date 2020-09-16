---
title: SQL Server Express Kullanıcı Örnekleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 00c12376-cb26-4317-86ad-e6e9c089be57
ms.openlocfilehash: 71f42cb2707c27be6c1a761d09d3a2dae1791680
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90552680"
---
# <a name="sql-server-express-user-instances"></a>SQL Server Express Kullanıcı Örnekleri
Microsoft SQL Server Express Edition (SQL Server Express), yalnızca SQL Server () için .NET Framework Veri Sağlayıcısı kullanılırken kullanılabilen Kullanıcı örneği özelliğini destekler `SqlClient` . Bir kullanıcı örneği, bir üst örnek tarafından oluşturulan SQL Server Express veritabanı altyapısının ayrı bir örneğidir. Kullanıcı örnekleri, yerel bilgisayarlarında yönetici olmayan kullanıcıların SQL Server Express veritabanlarına ekler ve bunlara bağlanmasına izin verir. Her örnek, bireysel kullanıcının güvenlik bağlamı altında, tek örnekli Kullanıcı bazında çalışır.  
  
## <a name="user-instance-capabilities"></a>Kullanıcı örneği özellikleri  
 Kullanıcı örnekleri, en az ayrıcalıklı kullanıcı hesabı (LUA) altında Windows çalıştıran kullanıcılar için yararlıdır. Her kullanıcının, `sysadmin` bilgisayarında çalışan örnek üzerinde Windows Yöneticisi olarak çalışmasına gerek kalmadan SQL Server Sistem Yöneticisi () ayrıcalıkları vardır. Bir Kullanıcı örneğinde sınırlı izinlerle yürütülen yazılım, SQL Server Express örneği kullanıcının yönetici olmayan Windows hesabı altında, hizmet olarak değil, sistem genelinde değişiklik yapamaz. Her kullanıcı örneği, üst örneğinden ve aynı bilgisayarda çalışan diğer kullanıcı örneklerinden yalıtılmıştır. Bir Kullanıcı örneğinde çalışan veritabanları yalnızca tek kullanıcı modunda açılır ve birden çok kullanıcının bir kullanıcı örneği üzerinde çalışan veritabanlarına bağlanması mümkün değildir. Çoğaltma ve dağıtılmış sorgular da Kullanıcı örnekleri için devre dışıdır.
  
> [!NOTE]
> Kullanıcı örnekleri, kendi bilgisayarlarında zaten yönetici olan kullanıcılar veya birden çok veritabanı kullanıcısı içeren senaryolar için gerekli değildir.  
  
## <a name="enabling-user-instances"></a>Kullanıcı örneklerini etkinleştirme  
 Kullanıcı örnekleri oluşturmak için bir SQL Server Express üst örneğinin çalışıyor olması gerekir. SQL Server Express yüklendiğinde Kullanıcı örnekleri varsayılan olarak etkindir ve üst örnekte **sp_configure** sistem saklı yordamını yürüten bir sistem yöneticisi tarafından açıkça etkinleştirilebilir veya devre dışı bırakılabilir.  
  
```sql  
-- Enable user instances.  
sp_configure 'user instances enabled','1'
  
-- Disable user instances.  
sp_configure 'user instances enabled','0'  
```  
  
 Kullanıcı örnekleri için ağ protokolünün yerel adlandırılmış kanallar olması gerekir. Bir kullanıcı örneği SQL Server uzak bir örneğinde başlatılamaz ve SQL Server oturum açma işlemlerine izin verilmez.  
  
## <a name="connecting-to-a-user-instance"></a>Kullanıcı örneğine bağlanma  
 `User Instance`Ve `AttachDBFilename` <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> anahtar sözcükleri bir <xref:System.Data.SqlClient.SqlConnection> Kullanıcı örneğine bağlanmasına izin verir. Kullanıcı örnekleri ve özellikleri tarafından da desteklenir <xref:System.Data.SqlClient.SqlConnectionStringBuilder> `UserInstance` `AttachDBFilename` .  
  
 Aşağıda gösterilen örnek bağlantı dizesi hakkında aşağıdakileri göz önünde edin:  
  
- `Data Source`Anahtar sözcüğü, Kullanıcı örneğini oluşturan SQL Server Express üst örneğine başvurur. Varsayılan örnek .\SQLEXPRESS.  
  
- `Integrated Security` , olarak ayarlanır `true` . Bir kullanıcı örneğine bağlanmak için Windows kimlik doğrulaması gerekir; SQL Server oturum açma işlemleri desteklenmez.  
  
- , `User Instance` `true` Bir kullanıcı örneği çağıran olarak ayarlanır. (Varsayılan değer `false` .)  
  
- `AttachDbFileName`Bağlantı dizesi anahtar sözcüğü, tam yol adını içermesi gereken birincil veritabanı dosyasını (. mdf) eklemek için kullanılır. `AttachDbFileName` Ayrıca bir bağlantı dizesi içindeki "Genişletilmiş Özellikler" ve "ilk dosya adı" anahtarlarına karşılık gelir <xref:System.Data.SqlClient.SqlConnection> .  
  
- `|DataDirectory|`Kanal simgelerine eklenen dize, bağlantıyı açan uygulamanın veri dizinine başvurur ve. mdf ve. ldf veritabanının ve günlük dosyalarının konumunu gösteren göreli bir yol sağlar. Bu dosyaları başka bir yerde bulmak istiyorsanız dosyaların tam yolunu sağlamanız gerekir.  
  
```text
Data Source=.\\SQLExpress;Integrated Security=true;  
User Instance=true;AttachDBFilename=|DataDirectory|\InstanceDB.mdf;  
Initial Catalog=InstanceDB;  
```  
  
> [!NOTE]
> Ayrıca, <xref:System.Data.SqlClient.SqlConnectionStringBuilder> <xref:System.Data.SqlClient.SqlConnectionStringBuilder.UserInstance%2A> <xref:System.Data.SqlClient.SqlConnectionStringBuilder.AttachDBFilename%2A> çalışma zamanında bir bağlantı dizesi oluşturmak için ve özelliklerini de kullanabilirsiniz.  
  
### <a name="using-the-124datadirectory124-substitution-string"></a>&#124;DataDirectory&#124; değiştirme dizesi kullanma  
 `AttachDbFileName` , ADO.NET 2,0 ' de `|DataDirectory|` (kanal sembolleri içine alınmış) değiştirme dizesinin tanıtılmasıyla genişletildi. `DataDirectory``AttachDbFileName`, bir veri dosyasının göreli yolunu belirtmek için ile birlikte kullanıldığında, geliştiricilerin tam yol belirtmek yerine veri kaynağına göre göreli bir yolu temel alan bağlantı dizeleri oluşturmalarına olanak tanır.  
  
 Öğesinin işaret ettiği fiziksel konum `DataDirectory` , uygulamanın türüne bağlıdır. Bu örnekte, eklenecek Northwind. mdf dosyası uygulamanın \ app_data klasöründe bulunur.  
  
```text
Data Source=.\\SQLExpress;Integrated Security=true;  
User Instance=true;  
AttachDBFilename=|DataDirectory|\app_data\Northwind.mdf;  
Initial Catalog=Northwind;  
```  
  
 `DataDirectory`Kullanıldığında, ortaya çıkan dosya yolu, dizin yapısında değiştirme dizesi tarafından işaret edilen dizinden daha yüksek olamaz. Örneğin, tam genişletilmiş `DataDirectory` C:\AppDirectory\ App_Data ise, yukarıda gösterilen örnek bağlantı dizesi c:\appdirectoryaltında olduğundan geçerlidir. Bununla birlikte, olarak belirtilmeye çalışılması `DataDirectory` `|DataDirectory|\..\data` bir hata oluşmasına neden olur çünkü \Data bir \Appdirectoryalt dizini değildir.  
  
 Bağlantı dizesinde hatalı biçimli bir değiştirme dizesi varsa, bir <xref:System.ArgumentException> oluşturulur.  
  
> [!NOTE]
> <xref:System.Data.SqlClient> değiştirme dizelerini yerel bilgisayar dosya sistemine karşı tam yollarla çözer. Bu nedenle, uzak sunucu, HTTP ve UNC yol adları desteklenmez. Sunucu yerel bilgisayarda bulunmuyorsa bağlantı açıldığında bir özel durum oluşur.  
  
 <xref:System.Data.SqlClient.SqlConnection>Açıldığında, varsayılan SQL Server Express örneğinden, çağıranın hesabı altında çalışan bir çalışma zamanı başlatılmış örneğe yönlendirilir.  
  
> [!NOTE]
> <xref:System.Data.SqlClient.SqlConnection.ConnectionTimeout%2A>Kullanıcı örneklerinin normal örneklere göre yüklenmeye daha uzun sürebileceğinden, değeri artırmak gerekebilir.  
  
 Aşağıdaki kod parçası yeni bir açar `SqlConnection` , bağlantı dizesini konsol penceresinde görüntüler ve ardından kod bloğundan çıkarken bağlantıyı kapatır `using` .  
  
```vb  
Private Sub OpenSqlConnection()  
    ' Retrieve the connection string.  
    Dim connectionString As String = GetConnectionString()  
  
    Using connection As New SqlConnection(connectionString)  
        connection.Open()  
        Console.WriteLine("ConnectionString: {0}", _  
           connection.ConnectionString)  
    End Using  
End Sub  
```  
  
```csharp  
private static void OpenSqlConnection()  
{  
    // Retrieve the connection string.  
    string connectionString = GetConnectionString();  
  
    using (SqlConnection connection =
        new SqlConnection(connectionString))  
    {  
        connection.Open();  
        Console.WriteLine("ConnectionString: {0}",
             connection.ConnectionString);  
    }  
}  
```  
  
> [!NOTE]
> SQL Server içinde çalışan ortak dil çalışma zamanı (CLR) kodunda Kullanıcı örnekleri desteklenmez. , <xref:System.InvalidOperationException> `Open` Bağlantı dizesinde bulunan bir üzerinde çağrılırsa oluşturulur <xref:System.Data.SqlClient.SqlConnection> `User Instance=true` .  
  
## <a name="lifetime-of-a-user-instance-connection"></a>Kullanıcı örneği bağlantısının ömrü  
 Hizmet olarak çalışan SQL Server sürümlerinden farklı olarak, SQL Server Express örneklerinin el ile başlatılması ve durdurulması gerekmez. Kullanıcı oturum açtığında ve bir kullanıcı örneğine her bağlanışında, Kullanıcı örneği zaten çalışmıyorsa başlatılır. Kullanıcı örneği veritabanlarının, `AutoClose` bir süre işlem yapılmadan sonra veritabanını otomatik olarak kapatması için seçenek kümesi vardır. Başlatılan sqlservr.exe işlem, örneğe son bağlantı kapatıldıktan sonra sınırlı bir zaman aşımı süresi boyunca çalışır, bu nedenle zaman aşımı süresi dolmadan önce başka bir bağlantı açılırsa yeniden başlatılması gerekmez. Bu zaman aşımı süresi dolmadan önce yeni bir bağlantı açılmamışsa Kullanıcı örneği otomatik olarak kapanır. Üst örnekteki Sistem Yöneticisi, Kullanıcı örneği **zaman aşımı** seçeneğini değiştirmek için **sp_configure** kullanarak bir kullanıcı örneği için zaman aşımı süresi süresini ayarlayabilir. Varsayılan değer 60 dakikadır.  
  
> [!NOTE]
> `Min Pool Size`Bağlantı dizesinde sıfırdan büyük bir değere sahip ise, bağlantı havuzlayıcı her zaman açılmış birkaç bağlantıyı korur ve Kullanıcı örneği otomatik olarak kapatılmaz.  
  
## <a name="how-user-instances-work"></a>Kullanıcı örnekleri nasıl çalışır?  
 Her Kullanıcı için bir kullanıcı örneği ilk kez oluşturulduğunda, **ana** ve **msdb** sistem veritabanları, Kullanıcı örneği tarafından özel kullanım için, şablon verileri klasöründen kullanıcının yerel uygulama veri deposu dizini altındaki bir yola kopyalanır. Bu yol genellikle olur `C:\Documents and Settings\<UserName>\Local Settings\Application Data\Microsoft\Microsoft SQL Server Data\SQLEXPRESS` . Bir kullanıcı örneği başlatıldığında, **tempdb**, log ve Trace dosyaları da bu dizine yazılır. Örnek için, her kullanıcı için benzersiz olması garanti edilen bir ad oluşturulur.  
  
 Varsayılan olarak, Windows buıltın\users grubunun tüm üyelerine, SQL Server ikili dosyalarında okuma ve yürütme izinlerinin yanı sıra yerel örneğe bağlanma izinleri verilir. Kullanıcı örneğini barındıran çağıran kullanıcının kimlik bilgileri doğrulandıktan sonra, bu kullanıcı `sysadmin` o örnekte olur. Yalnızca paylaşılan bellek Kullanıcı örnekleri için etkindir, yani yalnızca yerel makinedeki işlemler mümkündür.  
  
 Kullanıcılara bağlantı dizesinde belirtilen. mdf ve. ldf dosyalarında hem okuma hem de yazma izinleri verilmelidir.  
  
> [!NOTE]
> . Mdf ve. ldf dosyaları sırasıyla veritabanı ve günlük dosyalarını temsil eder. Bu iki dosya eşleşen bir küme olduğundan yedekleme ve geri yükleme işlemleri sırasında dikkatli olunmalıdır. Veritabanı dosyası, günlük dosyasının tam sürümü hakkında bilgi içerir ve yanlış bir günlük dosyasıyla birleştirildiğinde veritabanı açılmaz.  
  
 Verilerin bozulmasını önlemek için, Kullanıcı örneğindeki bir veritabanı özel erişimle açılır. Aynı bilgisayarda iki farklı kullanıcı örneği aynı veritabanını paylaşıyorsa, ikinci bir örnekte açılmadan önce ilk örnekteki kullanıcının veritabanını kapatması gerekir.  
  
## <a name="user-instance-scenarios"></a>Kullanıcı örneği senaryoları  
 Kullanıcı örnekleri, geliştirme bilgisayarlarında yönetim hesapları olan geliştiricilere bağlı olmayan bir SQL Server veri deposu ile veritabanı uygulamalarına yönelik geliştiriciler sağlar. Kullanıcı örnekleri, veritabanı uygulamasının bir dosyaya bağlandığı erişim/Jet modeline dayalıdır ve Kullanıcı, bir sistem yöneticisinin izin vermesini gerektirmeden tüm veritabanı nesneleri üzerinde otomatik olarak tam izinlere sahip olur. Kullanıcının en az ayrıcalıklı kullanıcı hesabı (LUA) altında çalıştığı ve sunucuda veya yerel makinede yönetici ayrıcalıklarına sahip olmadığı durumlarda, ancak veritabanı nesneleri ve uygulamalar oluşturmanız gerekir. Kullanıcı örnekleri, kullanıcıların, daha ayrıcalıklı bir sistem hizmetinin güvenlik bağlamında değil, kullanıcının kendi güvenlik bağlamı altında çalışan çalışma zamanında örnekler oluşturmalarına olanak tanır.  
  
> [!IMPORTANT]
> Kullanıcı örnekleri yalnızca, kullanan tüm uygulamaların tam olarak güvendiği senaryolarda kullanılmalıdır.  
  
 Kullanıcı örneği senaryoları şunları içerir:  
  
- Verilerin paylaşılabileceği tek kullanıcılı uygulamalar gerekli değildir.  
  
- ClickOnce dağıtımı. .NET Framework 2,0 (veya üzeri) ve SQL Server Express zaten hedef bilgisayarda yüklüyse, bir ClickOnce eyleminin sonucu olarak indirilen yükleme paketi yönetici olmayan kullanıcılar tarafından yüklenebilir ve kullanılabilir. Kurulumun bir parçası olan bir yöneticinin SQL Server Express yüklemesi gerektiğini unutmayın. Daha fazla bilgi için bkz. [Windows Forms Için ClickOnce dağıtımı](/dotnet/desktop/winforms/clickonce-deployment-for-windows-forms).
  
- Windows kimlik doğrulamasını kullanarak adanmış ASP.NET barındırma. Tek bir SQL Server Express örneği, intranette barındırılabilir. Uygulama, kimliğe bürünme özelliğini kullanarak değil, ASPNET Windows hesabını kullanarak bağlanır. Kullanıcı örnekleri, tüm uygulamaların aynı Kullanıcı örneğini paylaştığı ve artık birbirinden yalıtılmış kalmayacak olan üçüncü taraf veya paylaşılan barındırma senaryolarında kullanılmamalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SQL Server ve ADO.NET](index.md)
- [Bağlantı dizeleri](../connection-strings.md)
- [Bir veri kaynağına bağlanma](../connecting-to-a-data-source.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)

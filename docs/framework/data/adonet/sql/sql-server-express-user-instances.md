---
title: SQL Server Express Kullanıcı Örnekleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 00c12376-cb26-4317-86ad-e6e9c089be57
ms.openlocfilehash: f76b1f0a09be2f745156437919f43ebaa8840519
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938490"
---
# <a name="sql-server-express-user-instances"></a>SQL Server Express Kullanıcı Örnekleri
Microsoft SQL Server Express Edition (SQL Server Express), yalnızca SQL Server (`SqlClient`) için .NET Framework veri sağlayıcısı kullanılırken kullanılabilen Kullanıcı örneği özelliğini destekler. Bir kullanıcı örneği, bir üst örnek tarafından oluşturulan SQL Server Express veritabanı altyapısının ayrı bir örneğidir. Kullanıcı örnekleri, yerel bilgisayarlarında yönetici olmayan kullanıcıların SQL Server Express veritabanlarına ekler ve bunlara bağlanmasına izin verir. Her örnek, bireysel kullanıcının güvenlik bağlamı altında, tek örnekli Kullanıcı bazında çalışır.  
  
## <a name="user-instance-capabilities"></a>Kullanıcı örneği özellikleri  
 Kullanıcı örnekleri, her kullanıcının bilgisayarında çalışan örnek üzerinde Windows olarak çalıştırılması gerekmeden SQL Server Sistem Yöneticisi (`sysadmin`) ayrıcalıklarına sahip olduğundan, en az ayrıcalıklı kullanıcı hesabı (LUA) altında Windows çalıştıran kullanıcılar için yararlıdır. Yönetici de. Bir Kullanıcı örneğinde sınırlı izinlerle yürütülen yazılım, SQL Server Express örneği kullanıcının yönetici olmayan Windows hesabı altında, hizmet olarak değil, sistem genelinde değişiklik yapamaz. Her kullanıcı örneği, üst örneğinden ve aynı bilgisayarda çalışan diğer kullanıcı örneklerinden yalıtılmıştır. Bir Kullanıcı örneğinde çalışan veritabanları yalnızca tek kullanıcı modunda açılır ve birden çok kullanıcının bir kullanıcı örneği üzerinde çalışan veritabanlarına bağlanması mümkün değildir. Çoğaltma ve dağıtılmış sorgular da Kullanıcı örnekleri için devre dışıdır.  
  
 Daha fazla bilgi için SQL Server Books Online 'daki "Kullanıcı örnekleri" başlığına bakın.  
  
> [!NOTE]
> Kullanıcı örnekleri, kendi bilgisayarlarında zaten yönetici olan kullanıcılar veya birden çok veritabanı kullanıcısı içeren senaryolar için gerekli değildir.  
  
## <a name="enabling-user-instances"></a>Kullanıcı örneklerini etkinleştirme  
 Kullanıcı örnekleri oluşturmak için bir SQL Server Express üst örneğinin çalışıyor olması gerekir. SQL Server Express yüklendiğinde Kullanıcı örnekleri varsayılan olarak etkindir ve üst örnekte **sp_configure** sistem saklı yordamını yürüten bir sistem yöneticisi tarafından açıkça etkinleştirilebilir veya devre dışı bırakılabilir.  
  
```  
-- Enable user instances.  
sp_configure 'user instances enabled','1'   
  
-- Disable user instances.  
sp_configure 'user instances enabled','0'  
```  
  
 Kullanıcı örnekleri için ağ protokolünün yerel adlandırılmış kanallar olması gerekir. Bir kullanıcı örneği SQL Server uzak bir örneğinde başlatılamaz ve SQL Server oturum açma işlemlerine izin verilmez.  
  
## <a name="connecting-to-a-user-instance"></a>Kullanıcı örneğine bağlanma  
 `User Instance` Ve `AttachDBFilename` anahtarsözcükleri<xref:System.Data.SqlClient.SqlConnection> bir kullanıcı örneğine bağlanmasına izin verir. <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> Kullanıcı örnekleri <xref:System.Data.SqlClient.SqlConnectionStringBuilder> `UserInstance` ve özellikleritarafındandadesteklenir.`AttachDBFilename`  
  
 Aşağıda gösterilen örnek bağlantı dizesi hakkında aşağıdakileri göz önünde edin:  
  
- `Data Source` Anahtar sözcüğü, Kullanıcı örneğini oluşturan SQL Server Express üst örneğine başvurur. Varsayılan örnek .\SQLEXPRESS.  
  
- `Integrated Security`, olarak `true`ayarlanır. Bir kullanıcı örneğine bağlanmak için Windows kimlik doğrulaması gerekir; SQL Server oturum açma işlemleri desteklenmez.  
  
- , Bir kullanıcı örneği `true`çağıran olarak ayarlanır. `User Instance` (Varsayılan `false`değer.)  
  
- `AttachDbFileName` Bağlantı dizesi anahtar sözcüğü, tam yol adını içermesi gereken birincil veritabanı dosyasını (. mdf) eklemek için kullanılır. `AttachDbFileName`Ayrıca bir <xref:System.Data.SqlClient.SqlConnection> bağlantı dizesi içindeki "Genişletilmiş Özellikler" ve "ilk dosya adı" anahtarlarına karşılık gelir.  
  
- `|DataDirectory|` Kanal simgelerine eklenen dize, bağlantıyı açan uygulamanın veri dizinine başvurur ve. mdf ve. ldf veritabanının ve günlük dosyalarının konumunu gösteren göreli bir yol sağlar. Bu dosyaları başka bir yerde bulmak istiyorsanız dosyaların tam yolunu sağlamanız gerekir.  
  
```  
Data Source=.\\SQLExpress;Integrated Security=true;  
User Instance=true;AttachDBFilename=|DataDirectory|\InstanceDB.mdf;  
Initial Catalog=InstanceDB;  
```  
  
> [!NOTE]
> Ayrıca, <xref:System.Data.SqlClient.SqlConnectionStringBuilder> <xref:System.Data.SqlClient.SqlConnectionStringBuilder.UserInstance%2A> çalışma zamanında bir bağlantı <xref:System.Data.SqlClient.SqlConnectionStringBuilder.AttachDBFilename%2A> dizesi oluşturmak için ve özelliklerini de kullanabilirsiniz.  
  
### <a name="using-the-124datadirectory124-substitution-string"></a>&#124;DataDirectory&#124; değiştirme dizesini kullanma  
 `AttachDbFileName`, `|DataDirectory|` ADO.NET 2,0 ' de (kanal sembolleri içine alınmış) değiştirme dizesinin tanıtılmasıyla genişletildi. `DataDirectory`, bir veri dosyasının göreli `AttachDbFileName` yolunu belirtmek için ile birlikte kullanıldığında, geliştiricilerin tam yol belirtmek yerine veri kaynağına göre göreli bir yolu temel alan bağlantı dizeleri oluşturmalarına olanak tanır.  
  
 Öğesinin `DataDirectory` işaret ettiği fiziksel konum, uygulamanın türüne bağlıdır. Bu örnekte, eklenecek Northwind. mdf dosyası uygulamanın \app_data klasöründe bulunur.  
  
```  
Data Source=.\\SQLExpress;Integrated Security=true;  
User Instance=true;  
AttachDBFilename=|DataDirectory|\app_data\Northwind.mdf;  
Initial Catalog=Northwind;  
```  
  
 `DataDirectory` Kullanıldığında, ortaya çıkan dosya yolu, dizin yapısında değiştirme dizesi tarafından işaret edilen dizinden daha yüksek olamaz. Örneğin, tam genişletilmiş `DataDirectory` C:\AppDirectory\app_data ise, yukarıda gösterilen örnek bağlantı dizesi c:\appdirectoryaltında olduğundan geçerlidir. Bununla birlikte, olarak `DataDirectory` `|DataDirectory|\..\data` belirtilmeye çalışılması bir hata oluşmasına neden olur çünkü \Data bir \appdirectoryalt dizini değildir.  
  
 Bağlantı dizesinde hatalı biçimli bir değiştirme dizesi varsa, bir <xref:System.ArgumentException> oluşturulur.  
  
> [!NOTE]
> <xref:System.Data.SqlClient>değiştirme dizelerini yerel bilgisayar dosya sistemine karşı tam yollarla çözer. Bu nedenle, uzak sunucu, HTTP ve UNC yol adları desteklenmez. Sunucu yerel bilgisayarda bulunmuyorsa bağlantı açıldığında bir özel durum oluşur.  
  
 <xref:System.Data.SqlClient.SqlConnection> Açıldığında, varsayılan SQL Server Express örneğinden, çağıranın hesabı altında çalışan bir çalışma zamanı başlatılmış örneğe yönlendirilir.  
  
> [!NOTE]
> Kullanıcı örneklerinin normal örneklere göre yüklenmeye daha <xref:System.Data.SqlClient.SqlConnection.ConnectionTimeout%2A> uzun sürebileceğinden, değeri artırmak gerekebilir.  
  
 Aşağıdaki kod parçası yeni `SqlConnection`bir açar, bağlantı dizesini konsol penceresinde görüntüler ve ardından `using` kod bloğundan çıkarken bağlantıyı kapatır.  
  
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
> SQL Server içinde çalışan ortak dil çalışma zamanı (CLR) kodunda Kullanıcı örnekleri desteklenmez. , Bağlantı dizesinde bulunan `Open` <xref:System.Data.SqlClient.SqlConnection> bir üzerinde`User Instance=true` çağrılırsa oluşturulur. <xref:System.InvalidOperationException>  
  
## <a name="lifetime-of-a-user-instance-connection"></a>Kullanıcı örneği bağlantısının ömrü  
 Hizmet olarak çalışan SQL Server sürümlerinden farklı olarak, SQL Server Express örneklerinin el ile başlatılması ve durdurulması gerekmez. Kullanıcı oturum açtığında ve bir kullanıcı örneğine her bağlanışında, Kullanıcı örneği zaten çalışmıyorsa başlatılır. Kullanıcı örneği veritabanlarının, `AutoClose` bir süre işlem yapılmadan sonra veritabanını otomatik olarak kapatması için seçenek kümesi vardır. Başlatılan sqlservr. exe işlemi, örneğe son bağlantı kapatıldıktan sonra sınırlı bir zaman aşımı süresi boyunca çalışır durumda tutulur, bu nedenle zaman aşımı süresi dolmadan önce başka bir bağlantı açılırsa yeniden başlatılması gerekmez. Bu zaman aşımı süresi dolmadan önce yeni bir bağlantı açılmamışsa Kullanıcı örneği otomatik olarak kapanır. Üst örnekteki Sistem Yöneticisi, Kullanıcı örneği **zaman aşımı** seçeneğini değiştirmek için **sp_configure** kullanarak bir kullanıcı örneği için zaman aşımı süresi süresini ayarlayabilir. Varsayılan değer 60 dakikadır.  
  
> [!NOTE]
> Bağlantı `Min Pool Size` dizesinde sıfırdan büyük bir değere sahip ise, bağlantı havuzlayıcı her zaman açılmış birkaç bağlantıyı korur ve Kullanıcı örneği otomatik olarak kapatılmaz.  
  
## <a name="how-user-instances-work"></a>Kullanıcı örnekleri nasıl çalışır?  
 Her Kullanıcı için bir kullanıcı örneği ilk kez oluşturulduğunda, **ana** ve **msdb** sistem veritabanları, Kullanıcı örneği tarafından özel kullanım için, şablon verileri klasöründen kullanıcının yerel uygulama veri deposu dizini altındaki bir yola kopyalanır. Bu yol genellikle `C:\Documents and Settings\<UserName>\Local Settings\Application Data\Microsoft\Microsoft SQL Server Data\SQLEXPRESS`olur. Bir kullanıcı örneği başlatıldığında, **tempdb**, log ve Trace dosyaları da bu dizine yazılır. Örnek için, her kullanıcı için benzersiz olması garanti edilen bir ad oluşturulur.  
  
 Varsayılan olarak, Windows buıltın\users grubunun tüm üyelerine, SQL Server ikili dosyalarında okuma ve yürütme izinlerinin yanı sıra yerel örneğe bağlanma izinleri verilir. Kullanıcı örneğini barındıran çağıran kullanıcının kimlik bilgileri doğrulandıktan sonra, bu kullanıcı o örnekte olur `sysadmin` . Yalnızca paylaşılan bellek Kullanıcı örnekleri için etkindir, yani yalnızca yerel makinedeki işlemler mümkündür.  
  
 Kullanıcılara bağlantı dizesinde belirtilen. mdf ve. ldf dosyalarında hem okuma hem de yazma izinleri verilmelidir.  
  
> [!NOTE]
> . Mdf ve. ldf dosyaları sırasıyla veritabanı ve günlük dosyalarını temsil eder. Bu iki dosya eşleşen bir küme olduğundan yedekleme ve geri yükleme işlemleri sırasında dikkatli olunmalıdır. Veritabanı dosyası, günlük dosyasının tam sürümü hakkında bilgi içerir ve yanlış bir günlük dosyasıyla birleştirildiğinde veritabanı açılmaz.  
  
 Verilerin bozulmasını önlemek için, Kullanıcı örneğindeki bir veritabanı özel erişimle açılır. Aynı bilgisayarda iki farklı kullanıcı örneği aynı veritabanını paylaşıyorsa, ikinci bir örnekte açılmadan önce ilk örnekteki kullanıcının veritabanını kapatması gerekir.  
  
## <a name="user-instance-scenarios"></a>Kullanıcı örneği senaryoları  
 Kullanıcı örnekleri, geliştirme bilgisayarlarında yönetim hesapları olan geliştiricilere bağlı olmayan bir SQL Server veri deposu ile veritabanı uygulamalarına yönelik geliştiriciler sağlar. Kullanıcı örnekleri, veritabanı uygulamasının bir dosyaya bağlandığı erişim/Jet modeline dayalıdır ve Kullanıcı, bir sistem yöneticisinin izin vermesi gerekmeden tüm veritabanı nesneleri üzerinde otomatik olarak tam izinlere sahip olur izinleri. Kullanıcının en az ayrıcalıklı kullanıcı hesabı (LUA) altında çalıştığı ve sunucuda veya yerel makinede yönetici ayrıcalıklarına sahip olmadığı durumlarda, ancak veritabanı nesneleri ve uygulamalar oluşturmanız gerekir. Kullanıcı örnekleri, kullanıcıların, daha ayrıcalıklı bir sistem hizmetinin güvenlik bağlamında değil, kullanıcının kendi güvenlik bağlamı altında çalışan çalışma zamanında örnekler oluşturmalarına olanak tanır.  
  
> [!IMPORTANT]
> Kullanıcı örnekleri yalnızca, kullanan tüm uygulamaların tam olarak güvendiği senaryolarda kullanılmalıdır.  
  
 Kullanıcı örneği senaryoları şunları içerir:  
  
- Verilerin paylaşılabileceği tek kullanıcılı uygulamalar gerekli değildir.  
  
- ClickOnce dağıtımı. .NET Framework 2,0 (veya üzeri) ve SQL Server Express zaten hedef bilgisayarda yüklüyse, bir ClickOnce eyleminin sonucu olarak indirilen yükleme paketi yönetici olmayan kullanıcılar tarafından yüklenebilir ve kullanılabilir. Kurulumun bir parçası olan bir yöneticinin SQL Server Express yüklemesi gerektiğini unutmayın. Daha fazla bilgi için bkz. [Windows Forms Için ClickOnce dağıtımı](../../../winforms/clickonce-deployment-for-windows-forms.md).
  
- Windows kimlik doğrulamasını kullanarak adanmış ASP.NET barındırma. Tek bir SQL Server Express örneği, intranette barındırılabilir. Uygulama, kimliğe bürünme özelliğini kullanarak değil, ASPNET Windows hesabını kullanarak bağlanır. Kullanıcı örnekleri, tüm uygulamaların aynı Kullanıcı örneğini paylaştığı ve artık birbirinden yalıtılmış kalmayacak olan üçüncü taraf veya paylaşılan barındırma senaryolarında kullanılmamalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SQL Server ve ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)
- [Bağlantı Dizeleri](../../../../../docs/framework/data/adonet/connection-strings.md)
- [Veri Kaynağına Bağlanma](../../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)
- [ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)

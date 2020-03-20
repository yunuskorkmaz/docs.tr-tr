---
title: SQL Server Express Kullanıcı Örnekleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 00c12376-cb26-4317-86ad-e6e9c089be57
ms.openlocfilehash: 2bd67a9315eda4161d4b76e1638f5c08f9598a52
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174491"
---
# <a name="sql-server-express-user-instances"></a>SQL Server Express Kullanıcı Örnekleri
Microsoft SQL Server Express Edition (SQL Server Express), yalnızca SQL Server için .NET Framework Data`SqlClient`Provider () kullanılırken kullanılabilen kullanıcı örneği özelliğini destekler. Kullanıcı örneği, bir üst örnek tarafından oluşturulan SQL Server Express Veritabanı Altyapısının ayrı bir örneğidir. Kullanıcı örnekleri, yerel bilgisayarlarında yönetici olmayan kullanıcıların SQL Server Express veritabanlarına eklemesine ve bunlara bağlanmasına olanak tanır. Her örnek, kullanıcı başına bir örnek bazında, tek tek kullanıcının güvenlik bağlamı altında çalışır.  
  
## <a name="user-instance-capabilities"></a>Kullanıcı Örneği Özellikleri  
 Kullanıcı örnekleri, Windows'u en az ayrıcalıklı bir kullanıcı hesabı (LUA) altında çalıştıran kullanıcılar için yararlıdır. Her kullanıcı, Windows yöneticisi`sysadmin`olarak çalışmaya gerek kalmadan bilgisayarında çalışan örnek üzerinde SQL Server sistem yöneticisi ( ) ayrıcalıkları vardır. Sınırlı izinlere sahip bir kullanıcı örneğinde çalıştırılan yazılım, SQL Server Express örneği hizmet olarak değil, kullanıcının yönetici olmayan Windows hesabı altında çalıştığı için sistem genelinde değişiklik yapamaz. Her kullanıcı örneği, üst örneğinden ve aynı bilgisayarda çalışan diğer kullanıcı örneklerinden yalıtılır. Kullanıcı örneğinde çalışan veritabanları yalnızca tek kullanıcı modunda açılır ve birden çok kullanıcının bir kullanıcı örneğinde çalışan veritabanlarına bağlanması mümkün değildir. Çoğaltma ve dağıtılmış sorgular da kullanıcı örnekleri için devre dışı bırakılır.
  
> [!NOTE]
> Kullanıcı örnekleri, kendi bilgisayarlarında zaten yönetici olan kullanıcılar veya birden çok veritabanı kullanıcılarını içeren senaryolar için gerekli değildir.  
  
## <a name="enabling-user-instances"></a>Kullanıcı Örneklerini Etkinleştirme  
 Kullanıcı örnekleri oluşturmak için, SQL Server Express'in bir üst örneğinin çalışıyor olması gerekir. SQL Server Express yüklendiğinde kullanıcı örnekleri varsayılan olarak etkinleştirilir ve üst örnekte **sp_configure** sistem depolanan yordamı yürüten bir sistem yöneticisi tarafından açıkça etkinleştirilebilir veya devre dışı bırakılır.  
  
```sql  
-- Enable user instances.  
sp_configure 'user instances enabled','1'
  
-- Disable user instances.  
sp_configure 'user instances enabled','0'  
```  
  
 Kullanıcı örnekleri için ağ protokolü yerel Adlandırılmış Borular olmalıdır. Bir kullanıcı örneği SQL Server'ın uzak bir örneğinde başlatılamaz ve SQL Server girişlerine izin verilmez.  
  
## <a name="connecting-to-a-user-instance"></a>Kullanıcı Örneğine Bağlanma  
 Anahtar `User Instance` `AttachDBFilename` <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> kelimeler ve <xref:System.Data.SqlClient.SqlConnection> anahtar kelimeler, a'nın bir kullanıcı örneğine bağlanmasını sağlar. Kullanıcı örnekleri de ve <xref:System.Data.SqlClient.SqlConnectionStringBuilder> `UserInstance` `AttachDBFilename` özellikleri tarafından desteklenir.  
  
 Aşağıda gösterilen örnek bağlantı dizesi hakkında aşağıdakileri not edin:  
  
- Anahtar `Data Source` kelime, kullanıcı örneğini oluşturan SQL Server Express'in üst örneğine başvurur. Varsayılan örnek .\sqlexpress'tir.  
  
- `Integrated Security`olarak `true`ayarlanır. Bir kullanıcı örneğine bağlanmak için Windows Kimlik Doğrulama'sı gereklidir; SQL Server girişleri desteklenmez.  
  
- Kullanıcı `User Instance` örneğini `true`çağıran , olarak ayarlanır. (Varsayılan dır `false`.)  
  
- `AttachDbFileName` Bağlantı dizesi anahtar kelimesi, tam yol adını içermesi gereken birincil veritabanı dosyasını (.mdf) eklemek için kullanılır. `AttachDbFileName`ayrıca bağlantı <xref:System.Data.SqlClient.SqlConnection> dizesi içindeki "genişletilmiş özellikler" ve "ilk dosya adı" tuşlarına karşılık gelir.  
  
- Boru `|DataDirectory|` sembollerine ekteki ikame dizesi, bağlantıyı açan uygulamanın veri dizinini ifade eder ve .mdf ve .ldf veritabanı ve günlük dosyalarının konumunu gösteren göreli bir yol sağlar. Bu dosyaları başka bir yerde bulmak istiyorsanız, dosyalara tam yol sağlamanız gerekir.  
  
```text
Data Source=.\\SQLExpress;Integrated Security=true;  
User Instance=true;AttachDBFilename=|DataDirectory|\InstanceDB.mdf;  
Initial Catalog=InstanceDB;  
```  
  
> [!NOTE]
> Çalışma zamanında bir <xref:System.Data.SqlClient.SqlConnectionStringBuilder> <xref:System.Data.SqlClient.SqlConnectionStringBuilder.UserInstance%2A> <xref:System.Data.SqlClient.SqlConnectionStringBuilder.AttachDBFilename%2A> bağlantı dizesi oluşturmak için ve özellikleri de kullanabilirsiniz.  
  
### <a name="using-the-124datadirectory124-substitution-string"></a>&#124;DataDirectory&#124; Değiştirme Dizesini Kullanma  
 `AttachDbFileName`(boru sembolleriyle içlenmiş) ikame `|DataDirectory|` dizesi girişi ile 2.0 ADO.NET uzatıldı. `DataDirectory`bir veri dosyasına göreli bir yol belirtmek `AttachDbFileName` için birlikte kullanılır, geliştiricilerin tam bir yol belirtmek için gerekli olmak yerine veri kaynağına göreli bir yolu temel alan bağlantı dizeleri oluşturmak için izin.  
  
 Noktayı işaret `DataDirectory` eden fiziksel konum, uygulamanın türüne bağlıdır. Bu örnekte, eklenecek Northwind.mdf dosyası uygulamanın \app_data klasöründe yer alır.  
  
```text
Data Source=.\\SQLExpress;Integrated Security=true;  
User Instance=true;  
AttachDBFilename=|DataDirectory|\app_data\Northwind.mdf;  
Initial Catalog=Northwind;  
```  
  
 Kullanıldığında, `DataDirectory` elde edilen dosya yolu dizin yapısında ikame dizesinin işaret ettiğinden daha yüksek olamaz. Örneğin, tamamen genişletilmiş `DataDirectory` C:\AppDirectory\app_data ise, yukarıda gösterilen örnek bağlantı dizesi çalışır çünkü c:\AppDirectory'nin altındadır. Ancak, \veri `DataDirectory` \AppDirectory bir alt dizini olmadığından bir hata neden olur olarak `|DataDirectory|\..\data` belirtmeye çalışır.  
  
 Bağlantı dizesi yanlış biçimlendirilmiş bir değiştirme dizesi varsa, bir <xref:System.ArgumentException> atılmalıdır.  
  
> [!NOTE]
> <xref:System.Data.SqlClient>ikame dizelerini yerel bilgisayar dosya sistemine karşı tam yollara giderir. Bu nedenle, uzak sunucu, HTTP ve UNC yol adları desteklenmez. Sunucu yerel bilgisayarda bulunmuyorsa bağlantı açıldığında bir özel durum atılır.  
  
 <xref:System.Data.SqlClient.SqlConnection> Açıldığında, varsayılan SQL Server Express örneğinden, arayanın hesabı altında çalışan bir çalışma zamanı başlatılan örneğe yönlendirilir.  
  
> [!NOTE]
> Kullanıcı örneklerinin <xref:System.Data.SqlClient.SqlConnection.ConnectionTimeout%2A> yüklenmesi normal örneklerden daha uzun sürebilir.  
  
 Aşağıdaki kod parçası yeni `SqlConnection`bir açılır, konsol penceresinde bağlantı dizesini görüntüler ve `using` kod bloğundan çıkarken bağlantıyı kapatır.  
  
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
> Kullanıcı örnekleri, SQL Server'ın içinde çalışan ortak dil çalışma süresi (CLR) kodunda desteklenmez. Bağlantı <xref:System.InvalidOperationException> dizesinde bulunan `Open` <xref:System.Data.SqlClient.SqlConnection> `User Instance=true` bir a'ya çağrılırsa bir atılır.  
  
## <a name="lifetime-of-a-user-instance-connection"></a>Kullanıcı Örneği Bağlantısının Kullanım Ömrü  
 Hizmet olarak çalışan SQL Server sürümlerinin aksine, SQL Server Express örneklerinin el ile başlatılması ve durdurulması gerekmez. Bir kullanıcı oturum açıp bir kullanıcı örneğine her bağkuruca, zaten çalışmıyorsa kullanıcı örneği başlatılır. Kullanıcı örneği veritabanları, `AutoClose` veritabanının bir hareketsizlik döneminden sonra otomatik olarak kapatılması için seçenek kümesine sahiptir. Başlatılan sqlservr.exe işlemi, örneğe son bağlantı kapatıldıktan sonra sınırlı bir zaman aşımı süresi boyunca çalışmaya devam eder, bu nedenle zaman aşımı süresi dolmadan başka bir bağlantı açılırsa yeniden başlatılması gerekmez. Bu zaman aşımı süresi dolmadan önce yeni bir bağlantı açılmazsa kullanıcı örneği otomatik olarak kapanır. Üst örnekteki bir sistem yöneticisi, **kullanıcı örneğinin zaman ayarı** seçeneğini değiştirmek için **sp_configure** kullanarak bir kullanıcı örneğinin zaman ödeme süresinin süresini ayarlayabilir. Varsayılan değer 60 dakikadır.  
  
> [!NOTE]
> `Min Pool Size` Sıfırdan büyük bir değere sahip bağlantı dizesinde kullanılırsa, bağlantı havuzu her zaman birkaç açık bağlantı tutar ve kullanıcı örneği otomatik olarak kapanmaz.  
  
## <a name="how-user-instances-work"></a>Kullanıcı Örnekleri Nasıl Çalışır?  
 Her kullanıcı için ilk kez bir kullanıcı örneği oluşturulduğunda, **ana** ve **msdb** sistem veritabanları Şablon Veri klasöründen kullanıcı örneğinin özel kullanımı için kullanıcının yerel uygulama veri deposu dizininin altındaki bir yola kopyalanır. Bu yol genellikle `C:\Documents and Settings\<UserName>\Local Settings\Application Data\Microsoft\Microsoft SQL Server Data\SQLEXPRESS`. Bir kullanıcı örneği başlatıldığında, **tempdb,** günlük ve izleme dosyaları da bu dizine yazılır. Örnek için bir ad oluşturulur ve bu ad her kullanıcı için benzersiz olduğu garanti edilir.  
  
 Varsayılan olarak, Windows Builtin\Users grubunun tüm üyelerine yerel örnekte bağlanma ve SQL Server ikililerinde okuma ve yürütme izinleri verilir. Kullanıcı örneğini barındıran arama yapan kullanıcının kimlik bilgileri doğrulandıktan sonra, bu kullanıcı bu `sysadmin` örnekte olur. Yalnızca paylaşılan bellek, kullanıcı örnekleri için etkinleştirilir, bu da yalnızca yerel makinedeki işlemlerin mümkün olduğu anlamına gelir.  
  
 Kullanıcılara bağlantı dizesinde belirtilen .mdf ve .ldf dosyalarında okuma ve yazma izinleri verilmelidir.  
  
> [!NOTE]
> .mdf ve .ldf dosyaları sırasıyla veritabanını ve günlük dosyalarını temsil eder. Bu iki dosya eşleşen bir kümedir, bu nedenle yedekleme ve geri yükleme işlemleri sırasında dikkatli olunmalıdır. Veritabanı dosyası günlük dosyasının tam sürümü hakkında bilgi içerir ve yanlış günlük dosyası ile birleştiğinde veritabanı açılmaz.  
  
 Veri bozulmasını önlemek için, kullanıcı örneğinde özel erişimle bir veritabanı açılır. İki farklı kullanıcı örneği aynı bilgisayarda aynı veritabanını paylaşıyorsa, ikinci örnekte açılabilmesi için ilk örnekteki kullanıcının veritabanını kapatması gerekir.  
  
## <a name="user-instance-scenarios"></a>Kullanıcı Örneği Senaryoları  
 Kullanıcı örnekleri, veritabanı uygulamalarının geliştiricileringeliştirme bilgisayarlarında yönetim hesapları olmasına bağlı olmayan bir SQL Server veri deposu sağlar. Kullanıcı örnekleri, veritabanı uygulamasının yalnızca bir dosyaya bağlandığı Access/Jet modeline dayanır ve kullanıcı, izin vermek için bir sistem yöneticisinin müdahalesine gerek kalmadan tüm veritabanı nesnelerinde otomatik olarak tam izinlere sahiptir. Kullanıcının en az ayrıcalıklı bir kullanıcı hesabı (LUA) altında çalıştığı ve sunucu veya yerel makinede yönetim ayrıcalıkları olmadığı, ancak veritabanı nesneleri ve uygulamaları oluşturması gereken durumlarda çalışması amaçlanmıştır. Kullanıcı örnekleri, kullanıcıların daha ayrıcalıklı bir sistem hizmetinin güvenlik bağlamında değil, kullanıcının kendi güvenlik bağlamı altında çalışan çalışma zamanında örnekler oluşturmasına olanak sağlar.  
  
> [!IMPORTANT]
> Kullanıcı örnekleri yalnızca onu kullanan tüm uygulamaların tam olarak güvenildiği senaryolarda kullanılmalıdır.  
  
 Kullanıcı örneği senaryoları şunlardır:  
  
- Veri paylaşımının gerekli olmadığı tek kullanıcılı uygulamalar.  
  
- ClickOnce dağıtım. Hedef bilgisayara .NET Framework 2.0 (veya daha sonra) ve SQL Server Express zaten yüklüyse, ClickOnce işlemi sonucunda indirilen yükleme paketi yönetici olmayan kullanıcılar tarafından yüklenebilir ve kullanılabilir. Kurulumun bir parçası ysa, bir yöneticinin SQL Server Express'i yüklemesi gerektiğini unutmayın. Daha fazla bilgi [için Windows Formlar için ClickOnce Dağıtım'a](../../../winforms/clickonce-deployment-for-windows-forms.md)bakın.
  
- Windows Kimlik Doğrulaması kullanarak barındırmaya adanmış ASP.NET. Tek bir SQL Server Express örneği bir intranet üzerinde barındırılabilir. Uygulama, kimliğe bürünme kullanarak değil, ASPNET Windows hesabını kullanarak bağlanır. Kullanıcı örnekleri, tüm uygulamaların aynı kullanıcı örneğini paylaşacağı ve artık birbirinden izole edilmeyeceğini niçin üçüncü taraf veya paylaşılan barındırma senaryoları için kullanılmamalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SQL Server ve ADO.NET](index.md)
- [Bağlantı Dizeleri](../connection-strings.md)
- [Veri Kaynağına Bağlanma](../connecting-to-a-data-source.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)

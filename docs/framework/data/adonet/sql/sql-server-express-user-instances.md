---
title: SQL Server Express kullanıcı örnekleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 00c12376-cb26-4317-86ad-e6e9c089be57
ms.openlocfilehash: 4546ce2a08fc2ac20717bbaa55d4688b43d34b47
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56093820"
---
# <a name="sql-server-express-user-instances"></a>SQL Server Express kullanıcı örnekleri
Microsoft SQL Server Express Edition (SQL Server Express) .NET Framework veri sağlayıcısı için SQL Server kullanırken yalnızca kullanılabilir kullanıcı örneği özelliğini destekler (`SqlClient`). Bir kullanıcı örneği, SQL Server Express Veritabanı Altyapısı'nın üst örneği tarafından oluşturulan ayrı bir örneğidir. Kullanıcı örnekleri eklemek ve SQL Server Express veritabanlarına bağlanmak için kendi yerel bilgisayarlarında yönetici olmayan kullanıcılar izin verin. Her örneği, tek kullanıcı, kullanıcı başına tek örnek güvenlik bağlamı altında çalışır.  
  
## <a name="user-instance-capabilities"></a>Kullanıcı örneği özellikleri  
 Kullanıcı örnekleri her bir kullanıcı SQL Server Sistem Yöneticisi olduğundan Windows (LUA) en az ayrıcalıklı kullanıcı hesabı altında çalışan kullanıcılar için kullanışlıdır (`sysadmin`) bir Windows çalıştırmak zorunda kalmadan her bilgisayar üzerinde çalışan örnek üzerindeki ayrıcalıkları yönetici de. SQL Server Express örneği bir hizmet olarak değil bir kullanıcının yönetici olmayan Windows hesabı altında çalıştığı için yazılım sınırlı izinlere sahip bir kullanıcı örneği üzerinde yürütülen sistem genelinde değişiklik yapamaz. Her bir kullanıcı örneği, kendi üst örneğini ve aynı bilgisayarda çalışan diğer kullanıcı örnekleri yalıtılır. Bir kullanıcı örneği üzerinde çalışan veritabanları yalnızca tek kullanıcı modunda açılır ve bir kullanıcı örneği üzerinde çalışan veritabanlarına bağlanmak birden çok kullanıcı için mümkün değildir. Çoğaltma ve dağıtılmış sorgular, ayrıca kullanıcı örnekleri için devre dışıdır.  
  
 Daha fazla bilgi için SQL Server Books Online'da "kullanıcı örnekleri" konusuna bakın.  
  
> [!NOTE]
>  Kullanıcı örnekleri kendi bilgisayarlarında yönetici olan kullanıcılar için veya birden çok veritabanı kullanıcıları içeren senaryolar için gerekli değildir.  
  
## <a name="enabling-user-instances"></a>Kullanıcı örnekleri etkinleştirme  
 Kullanıcı örnekleri oluşturmak için bir üst SQL Server Express örneğini çalıştırılması gerekir. Kullanıcı örnekleri, varsayılan olarak etkinleştirilir, SQL Server Express yüklenir ve bunlar açıkça etkinleştirilebilir veya yürütülürken bir sistem yöneticisi tarafından devre dışı olduğunda **sp_configure** üst örneğinde sistem saklı yordamı.  
  
```  
-- Enable user instances.  
sp_configure 'user instances enabled','1'   
  
-- Disable user instances.  
sp_configure 'user instances enabled','0'  
```  
  
 Ağ Protokolü kullanıcı örnekleri için adlandırılmış kanallar yerel olması gerekir. Bir kullanıcı örneği bir SQL Server'ın uzak örneğinde başlatılamıyor ve SQL Server oturumları izin verilmez.  
  
## <a name="connecting-to-a-user-instance"></a>Bir kullanıcı örneğine bağlanma  
 `User Instance` Ve `AttachDBFilename` <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> anahtar sözcüklere izin bir <xref:System.Data.SqlClient.SqlConnection> bir kullanıcı örneğine bağlanmak için. Kullanıcı örnekleri tarafından da desteklenir <xref:System.Data.SqlClient.SqlConnectionStringBuilder> `UserInstance` ve `AttachDBFilename` özellikleri.  
  
 Aşağıda gösterilen örnek bağlantı dizesi hakkında aşağıdakileri unutmayın:  
  
-   `Data Source` Anahtar sözcüğü üst SQL Server'ın kullanıcı örneği oluşturan Express örneğine başvurur. The default instance is .\sqlexpress.  
  
-   `Integrated Security` ayarlanır `true`. Bir kullanıcı örneğine bağlanmak için Windows kimlik doğrulaması gereklidir; SQL Server oturumları desteklenmez.  
  
-   `User Instance` Ayarlanır `true`, bir kullanıcı örneği başlatır. (Varsayılan değer `false`.)  
  
-   `AttachDbFileName` Bağlantı dizesi anahtar kelimesi, tam yol adını içermelidir birincil veritabanı dosyasını (.mdf) eklemek için kullanılır. `AttachDbFileName` Ayrıca, "genişletilmiş özellikler" ve "başlangıç dosyası adı" anahtarları içinde karşılık gelen bir <xref:System.Data.SqlClient.SqlConnection> bağlantı dizesi.  
  
-   `|DataDirectory|` Kanal sembolleri içine değiştirme dizesi bağlantısı açılıyor uygulamanın veri dizini gösterir ve .mdf ve .ldf veritabanı ve günlük dosyalarının konumunu belirten göreli bir yol sağlar. Bu dosyaları başka bir yerde bulmak isterseniz, dosyaların tam yolunu sağlamanız gerekir.  
  
```  
Data Source=.\\SQLExpress;Integrated Security=true;  
User Instance=true;AttachDBFilename=|DataDirectory|\InstanceDB.mdf;  
Initial Catalog=InstanceDB;  
```  
  
> [!NOTE]
>  Ayrıca <xref:System.Data.SqlClient.SqlConnectionStringBuilder> <xref:System.Data.SqlClient.SqlConnectionStringBuilder.UserInstance%2A> ve <xref:System.Data.SqlClient.SqlConnectionStringBuilder.AttachDBFilename%2A> özellikler zamanında bağlantı dizenizi oluşturmak için çalışma zamanında.  
  
### <a name="using-the-124datadirectory124-substitution-string"></a>Kullanarak &#124;DataDirectory&#124; değiştirme dizesi  
 `AttachDbFileName` ADO.NET 2. 0'sunulmasıyla birlikte genişletilmişse `|DataDirectory|` (kanal sembolleri alınmış) değiştirme dizesi. `DataDirectory` ile birlikte kullanılan `AttachDbFileName` bir veri dosyası için göreli bir yol belirtmek için göreli bir yol olan yerine veri kaynağına dayalı bağlantı dizesi oluşturmak, geliştiricilerin tam yolunu belirtmeniz gerekir.  
  
 Fiziksel konum, `DataDirectory` bağlı olan uygulama türüne işaret eder. Bu örnekte, eklenmiş Northwind.mdf dosya uygulamanın \app_data klasöründe bulunur.  
  
```  
Data Source=.\\SQLExpress;Integrated Security=true;  
User Instance=true;  
AttachDBFilename=|DataDirectory|\app_data\Northwind.mdf;  
Initial Catalog=Northwind;  
```  
  
 Zaman `DataDirectory` olan kullanıldığında, sonuçta elde edilen dosya yolu dizin yapısında değiştirme dizesi tarafından belirtilen dizin daha yüksek olamaz. Örneğin, tam olarak Genişletilmiş `DataDirectory` C:\AppDirectory\app_data sonra c:\AppDirectory olduğundan works gösterilen örnek bağlantı dizesi. Ancak, denemek `DataDirectory` olarak `|DataDirectory|\..\data` \data \AppDirectory dizininin bir alt olmadığından bir hataya neden olur.  
  
 Bağlantı dizesi bir Düzensiz biçimlendirilmiş bir değiştirme dizesi varsa bir <xref:System.ArgumentException> oluşturulur.  
  
> [!NOTE]
>  <xref:System.Data.SqlClient> Yerel bilgisayar dosya sistemine karşı tam yollarını içine değiştirme dizelerini çözümler. Bu nedenle, uzak sunucu, HTTP ve UNC yolu adları desteklenmemektedir. Bağlantı açıldığında sunucunun yerel bilgisayarda bulunmuyorsa, bir özel durum oluşturulur.  
  
 Zaman <xref:System.Data.SqlClient.SqlConnection> olan açıldı, onu varsayılan SQL Server Express örneğinden çağıranın hesabı altında çalıştırma başlatılan örneği çalışan bir yönlendirilir.  
  
> [!NOTE]
>  Artırmak gerekli olabilir <xref:System.Data.SqlClient.SqlConnection.ConnectionTimeout%2A> kullanıcı örnekleri, normal örneklerden yüklenmesi daha uzun sürebilir değeri.  
  
 Aşağıdaki kod parçası, yeni bir açılır `SqlConnection`, bağlantı dizesini konsol penceresinde görüntüler ve ardından çıkarken bağlantıyı kapatır `using` kod bloğu.  
  
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
>  Kullanıcı örnekleri içinde SQL Server çalıştıran ortak dil çalışma zamanı (CLR) kodu desteklenmez. Bir <xref:System.InvalidOperationException> oluşturulur `Open` üzerinde çağrılır bir <xref:System.Data.SqlClient.SqlConnection> olan `User Instance=true` bağlantı dizesindeki.  
  
## <a name="lifetime-of-a-user-instance-connection"></a>Bir kullanıcı örneği bağlantı ömrü  
 SQL Server sürümlerinden farklı olarak bir hizmet olarak çalıştırın, SQL Server Express örneklerini el ile yapmanız gerekmez, kullanmaya ve durduruldu. Zaten çalışmıyorsa, bir kullanıcı oturum açtığında ve bir kullanıcı örneğine bağlanan her zaman kullanıcı örneği başlatıldı. Kullanıcı örneği veritabanlarının `AutoClose` seçenek kümesi böylece veritabanı bir süre işlem yapılmadığında otomatik olarak kapatılır. Başlatılan sqlservr.exe işlem tutulur çalıştıran bir sınırlı bir zaman aşımı süresini örneği son bağlantı kapatıldıktan sonra zaman aşımına uğramadan önce başka bir bağlantı açıldıysa yeniden başlatılması gerekmez. Bu zaman aşımı süresi sona ermeden önce yeni bağlantı açarsa, kullanıcı örneği otomatik olarak kapanır. Üst örneğinde Sistem Yöneticisi kullanarak bir kullanıcı örneği için zaman aşımı süresini süresini ayarlayabilirsiniz **sp_configure** değiştirmek için **kullanıcı örneği zaman aşımı** seçeneği. Varsayılan değer 60 dakikadır.  
  
> [!NOTE]
>  Varsa `Min Pool Size` kullanılan bağlantı dizesinde, sıfırdan büyük bir değere sahip birkaç açık bağlantıları her zaman bağlantı havuzlayıcı korur ve kullanıcı örneği otomatik olarak kapatılacak değil.  
  
## <a name="how-user-instances-work"></a>Kullanıcı iş nasıl örnekleri  
 Bir kullanıcı örneği her bir kullanıcı için oluşturulan ilk kez **ana** ve **msdb** sistem veritabanları kopyalanır şablon veri klasöründen kullanıcının yerel uygulama veri deposu altındaki yol kullanıcı örneği tarafından kullanılacak dizin. Bu yol genellikle `C:\Documents and Settings\<UserName>\Local Settings\Application Data\Microsoft\Microsoft SQL Server Data\SQLEXPRESS`. Bir kullanıcı örneği başlatıldığında **tempdb**, günlük ve izleme dosyaları da bu dizine yazılır. Örneğin, her kullanıcı için benzersiz olması garanti bir ad oluşturulur.  
  
 Varsayılan olarak Windows BUILTIN\USERS grubunun tüm üyeleri üzerinde yerel bağlanın yanı sıra okuma ve Yürütme izinleri SQL Server ikili dosyalarını izinleri verilir. Kullanıcı örneği barındıran çağıran kullanıcının kimlik bilgileri doğruladıktan sonra o kullanıcı olur `sysadmin` örneğine. Yalnızca paylaşılan bellek, yalnızca yerel makine üzerinde işlemler mümkün olmadığı anlamına gelir, kullanıcı örnekleri için etkinleştirilir.  
  
 Kullanıcılar hem okuma hem bağlantı dizesinde belirtilen .mdf ve .ldf dosyalarda izinleri verilmelidir.  
  
> [!NOTE]
>  .Mdf ve .ldf dosyaları veritabanı ve günlük dosyalarının sırasıyla temsil eder. Bu iki dosyayı özen yedekleme sırasında düşünülmesi gereken ve geri yükleme işlemleri eşlenmiş bir küme olduğundan. Veritabanı dosyası günlük dosyasının tam sürümünü ilgili bilgiler içerir ve yanlış günlük dosyası ile sıkı bağlı, veritabanı açılır değil.  
  
 Veri bozulmasını önlemek için kullanıcı örneğinde bir veritabanı ile özel erişim açılır. İki farklı bir kullanıcı örneği aynı bilgisayarda aynı veritabanını paylaşıyorsanız, ikinci bir örneğinde açılmadan önce ilk örnek kullanıcı veritabanı kapatmanız gerekir.  
  
## <a name="user-instance-scenarios"></a>Kullanıcı örneği senaryoları  
 Kullanıcı örnekleri, veritabanı uygulamalarının geliştiriciler, geliştirme bilgisayarlarını üzerindeki yönetim hesaplarına sahip bağlı olmayan bir SQL Server veri deposu ile geliştiriciler sağlar. Kullanıcı örnekleri burada veritabanı uygulaması yalnızca bir dosyaya bağlar ve otomatik olarak tam izinleri tüm veritabanı nesnelerinin vermek için bir sistem yöneticisinin bir müdahalesi olmadan kullanıcının erişim/Jet modeline dayanır izinler. Burada kullanıcı (LUA) en az ayrıcalıklı kullanıcı hesabı altında çalıştığından ve sunucu veya yerel makine üzerinde yönetimsel yetkilere sahip değil, ancak veritabanı nesneleri ve uygulamaları oluşturmak için gereken durumlarda çalışacak şekilde tasarlanmıştır. Kullanıcı örnekleri, kullanıcının kendi güvenlik bağlamı altında ve değil daha ayrıcalıklı sistem hizmeti güvenlik bağlamında çalışan çalışma zamanında oluşumlarının izin ver.  
  
> [!IMPORTANT]
>  Kullanıcı örnekleri yalnızca onu kullanan tüm uygulamaları tam güvenilir olduğu senaryolarda kullanılmalıdır.  
  
 Kullanıcı örneği senaryoları şunları içerir:  
  
-   Herhangi bir tek kullanıcı uygulama burada veri paylaşımı gerekli değildir.  
  
-   ClickOnce dağıtımı. .NET Framework 2.0 (veya üzeri) ve SQL Server Express hedef bilgisayarda zaten yüklüyse, bir ClickOnce eylem sonucu olarak karşıdan yükleme paketini yüklenebilir ve yönetici olmayan kullanıcılar tarafından kullanılabilir. Bu kurulumun bir parçası olduğu yönetici SQL Server Express yüklemeniz gerektiğini unutmayın. Daha fazla bilgi için [Windows Forms için ClickOnce dağıtımı](../../../winforms/clickonce-deployment-for-windows-forms.md).
  
-   Özel ASP.NET, Windows kimlik doğrulaması kullanarak barındırma. Tek bir SQL Server Express örneği intranet üzerinde barındırılabilir. Uygulamayı, kimliğe bürünme kullanılmadığında ASPNET Windows hesabı kullanarak bağlanır. Kullanıcı örnekleri, üçüncü taraf veya paylaşılan barındırma burada tüm uygulamalar aynı kullanıcı örneği paylaşımında yapabileceği ve artık birbirinden yalıtılmış kalır senaryoları için kullanılmamalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [SQL Server ve ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)
- [Bağlantı Dizeleri](../../../../../docs/framework/data/adonet/connection-strings.md)
- [Veri Kaynağına Bağlanma](../../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)

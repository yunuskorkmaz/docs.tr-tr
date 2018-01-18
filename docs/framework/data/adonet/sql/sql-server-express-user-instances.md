---
title: "SQL Server Express kullanıcı örnekleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 00c12376-cb26-4317-86ad-e6e9c089be57
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 55f3393c84ec08d3c3944552ac2bed7d15dd025f
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="sql-server-express-user-instances"></a>SQL Server Express kullanıcı örnekleri
Microsoft SQL Server Express Edition (SQL Server Express) yalnızca SQL Server için .NET Framework veri sağlayıcısı kullanarak olduğunda kullanıcı örneği özelliğini destekler (`SqlClient`). Bir kullanıcı örneği, SQL Server Express Veritabanı Altyapısı'nın üst örneği tarafından oluşturulan ayrı bir örneğidir. Kullanıcı örnekleri ekleyin ve SQL Server Express veritabanlarına bağlanmak için yerel bilgisayarlarında yönetici olmayan kullanıcıların verin. Her bir örnek tek kullanıcı, kullanıcı başına tek örnek olarak, güvenlik bağlamı altında çalışır.  
  
## <a name="user-instance-capabilities"></a>Kullanıcı örneği özellikleri  
 Kullanıcı örnekleri SQL Server Sistem Yöneticisi her kullanıcının sahip olduğu en az ayrıcalıklı kullanıcı hesabı (LUA) altında Windows çalıştıran kullanıcılar için yararlı (`sysadmin`) Windows çalıştıran gerek kalmadan her bilgisayar üzerinde çalışan örnek üzerinden ayrıcalıkları de yönetici. SQL Server Express örneği bir hizmet olarak değil kullanıcının yönetici olmayan Windows hesabı altında çalışıyor olduğundan sınırlı izinlere sahip bir kullanıcı örneği üzerinde yazılım yürütülürken sistem genelinde değişiklik yapamazsınız. Her bir kullanıcı örneği, kendi üst örneği ve aynı bilgisayarda çalışan başka bir kullanıcı örnekleri'ndan yalıtılır. Bir kullanıcı örneği üzerinde çalışan veritabanları yalnızca tek kullanıcı modunda açılır ve bir kullanıcı örneği üzerinde çalışan veritabanlarına bağlanmak birden çok kullanıcı için kullanılamaz. Çoğaltma ve dağıtılmış sorgular Ayrıca kullanıcı örnekleri için devre dışıdır.  
  
 Daha fazla bilgi için SQL Server Books Online'da "kullanıcı örnekleri" konusuna bakın.  
  
> [!NOTE]
>  Kullanıcı örnekleri zaten kendi bilgisayarlarındaki yöneticisi olan kullanıcılar için veya birden çok veritabanı kullanıcıları içeren senaryoları için gerekli değildir.  
  
## <a name="enabling-user-instances"></a>Kullanıcı örnekleri etkinleştirme  
 Kullanıcı örnekleri oluşturmak için bir üst SQL Server Express örneğini çalıştırması gerekir. Kullanıcı örnekleri, varsayılan olarak etkinleştirilir, SQL Server Express yüklendi ve bunlar açıkça etkinleştirilebilir veya yürütülürken bir sistem yöneticisi tarafından devre dışı olduğunda **sp_configure** sistem saklı yordamı üst örneğinde.  
  
```  
-- Enable user instances.  
sp_configure 'user instances enabled','1'   
  
-- Disable user instances.  
sp_configure 'user instances enabled','0'  
```  
  
 Ağ Protokolü kullanıcı örnekleri için adlandırılmış kanallar yerel olması gerekir. Bir kullanıcı örneği SQL Server'ın uzak örneğinde başlatılamıyor ve SQL Server oturumları izin verilmez.  
  
## <a name="connecting-to-a-user-instance"></a>Bir kullanıcı örneğine bağlanma  
 `User Instance` Ve `AttachDBFilename` <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> anahtar sözcüklere izin bir <xref:System.Data.SqlClient.SqlConnection> bir kullanıcı örneğine bağlanmak için. Kullanıcı örnekleri tarafından da desteklenir <xref:System.Data.SqlClient.SqlConnectionStringBuilder> `UserInstance` ve `AttachDBFilename` özellikleri.  
  
 Aşağıda gösterilen örnek bağlantı dizesi hakkında aşağıdakileri unutmayın:  
  
-   `Data Source` Anahtar sözcüğü'nın kullanıcı örneği oluşturma SQL Server Express'in üst örneğine başvurur. Varsayılan örneğidir. \sqlexpress.  
  
-   `Integrated Security`ayarlanmış `true`. Bir kullanıcı örneğine bağlanmak için Windows kimlik doğrulaması gereklidir; SQL Server oturumları desteklenmez.  
  
-   `User Instance` Ayarlanır `true`, bir kullanıcı örneği çağırır. (Varsayılan `false`.)  
  
-   `AttachDbFileName` Bağlantı dizesi anahtar sözcüğü tam yol adını içermelidir birincil veritabanı dosyası (.mdf) eklemek için kullanılır. `AttachDbFileName`Ayrıca "genişletilmiş özellikler" ve "ilk dosya adı" anahtarları içinde karşılık gelen bir <xref:System.Data.SqlClient.SqlConnection> bağlantı dizesi.  
  
-   `|DataDirectory|` Değiştirme dizesi kanal sembolleri arasına bağlantı açarak uygulamayı veri dizinine gösterir ve .mdf ve .ldf veritabanı ve günlük dosyalarının konumunu belirten göreli bir yol sağlar. Bu dosyaları başka bir yerde bulmak isterseniz, dosyalara tam yolunu belirtmeniz gerekir.  
  
```  
Data Source=.\\SQLExpress;Integrated Security=true;  
User Instance=true;AttachDBFilename=|DataDirectory|\InstanceDB.mdf;  
Initial Catalog=InstanceDB;  
```  
  
> [!NOTE]
>  Aynı zamanda <xref:System.Data.SqlClient.SqlConnectionStringBuilder> <xref:System.Data.SqlClient.SqlConnectionStringBuilder.UserInstance%2A> ve <xref:System.Data.SqlClient.SqlConnectionStringBuilder.AttachDBFilename%2A> özellikleri bir bağlantı dizesi, yapı çalışma zamanında.  
  
### <a name="using-the-124datadirectory124-substitution-string"></a>Kullanarak &#124; DataDirectory &#124; Değiştirme dizesi  
 `AttachDbFileName`ADO.NET 2.0 başlanmasıyla Genişletilmiş `|DataDirectory|` (kanal sembolleri alınmış) değiştirme dizesi. `DataDirectory`ile birlikte kullanılan `AttachDbFileName` bir veri dosyası için göreli bir yol belirtmek için göreli bir yol olmak yerine veri kaynağına dayalı bağlantı dizesi oluşturmak geliştiriciler izin vererek tam yolunu belirtmeniz gerekir.  
  
 Fiziksel konum, `DataDirectory` bağımlı olan uygulama türüne işaret eder. Bu örnekte, eklenecek Northwind.mdf dosyası uygulamanın \app_data klasöründe bulunur.  
  
```  
Data Source=.\\SQLExpress;Integrated Security=true;  
User Instance=true;  
AttachDBFilename=|DataDirectory|\app_data\Northwind.mdf;  
Initial Catalog=Northwind;  
```  
  
 Zaman `DataDirectory` olan kullanıldığında, sonuçta elde edilen dosya yolu dizin yapısında değiştirme dizesi tarafından işaret dizin daha yüksek olamaz. Örneğin, varsa tam olarak Genişletilmiş `DataDirectory` C:\AppDirectory\app_data sonra c:\AppDirectory olduğundan works gösterilen örnek bağlantı dizesi değil. Ancak, belirleme girişimi `DataDirectory` olarak `|DataDirectory|\..\data` \data \AppDirectory alt olmadığından bir hatayla sonuçlanır.  
  
 Bağlantı dizesi bir düzgün biçimlendirilmemiş değiştirme dizesi varsa bir <xref:System.ArgumentException> oluşturulur.  
  
> [!NOTE]
>  <xref:System.Data.SqlClient>Yerel bilgisayar dosya sistemine karşı tam yollarını içine değiştirme dizelerini çözümler. Bu nedenle, uzak sunucu, HTTP ve UNC yolu adları desteklenmez. Sunucu yerel bilgisayarda bulunmuyorsa, bağlantı açıldığında bir özel durum oluşur.  
  
 Zaman <xref:System.Data.SqlClient.SqlConnection> olan açıldı, onu varsayılan SQL Server Express örneğinden Arayanın hesabı altında çalışan bir çalışma zamanı başlatılan örneği yeniden yönlendirilir.  
  
> [!NOTE]
>  Artırmak gerekli olabilir <xref:System.Data.SqlClient.SqlConnection.ConnectionTimeout%2A> kullanıcı örnekleri normal örnekleri yüklenmesi daha uzun sürebilir değeri.  
  
 Aşağıdaki kod parçası yeni bir açılır `SqlConnection`, bağlantı dizesi konsol penceresinde görüntüler ve ardından çıkarken bağlantıyı kapatır `using` kod bloğu.  
  
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
>  Kullanıcı örnekleri içinde SQL Server çalıştıran ortak dil çalışma zamanı (CLR) kodda desteklenmez. Bir <xref:System.InvalidOperationException> erişilirse durum `Open` üzerinde adlı bir <xref:System.Data.SqlClient.SqlConnection> olan `User Instance=true` bağlantı dizesinde.  
  
## <a name="lifetime-of-a-user-instance-connection"></a>Bir kullanıcı örneği bağlantı ömrü  
 SQL Server sürümlerinden farklı olarak bir hizmet olarak çalıştırmak, SQL Server Express örneği el ile yapmanız gerekmez, başlatılan ve durduruldu. Zaten çalışmıyorsa, bir kullanıcı oturum açtığında ve bir kullanıcı örneğine bağlanan her zaman kullanıcı örneği başlatıldı. Kullanıcı örneği veritabanlarına sahip `AutoClose` seçenek kümesi böylece veritabanını bir süre işlem yapılmadığında otomatik olarak kapatılır. Başlatılan sqlservr.exe işlem tutulur örneği son bağlantı kapatıldıktan sonra bir sınırlı için zaman aşımı süresini çalıştıran başka bir bağlantı zaman aşımı süresi doldu önce açarsa yeniden başlatılması gerekmez. O zaman aşımı süresi sona ermeden önce yeni bir bağlantı açar, kullanıcı örneği otomatik olarak kapanır. Üst örneğinde Sistem Yöneticisi kullanılarak bir kullanıcı örneği için zaman aşımı süresini süresini ayarlayabilirsiniz **sp_configure** değiştirmek için **kullanıcı örneği zaman aşımı** seçeneği. Varsayılan değer 60 dakikadır.  
  
> [!NOTE]
>  Varsa `Min Pool Size` kullanılan sıfırdan büyük bir değer ile bağlantı dizesinde bağlantı havuzlayıcı her zaman birkaç açık bağlantıları korur ve kullanıcı örneği otomatik olarak kapatılacak değil.  
  
## <a name="how-user-instances-work"></a>Kullanıcı iş nasıl örnekleri  
 Bir kullanıcı örneği her bir kullanıcı için oluşturulan ilk kez **ana** ve **msdb** sistem veritabanları kopyalanır şablon verileri klasöründen kullanıcının yerel uygulama veri deposu altındaki yol kullanıcı örneği tarafından özel kullanım için dizini. Bu genellikle yoludur `C:\Documents and Settings\<UserName>\Local Settings\Application Data\Microsoft\Microsoft SQL Server Data\SQLEXPRESS`. Bir kullanıcı örneği başlatıldığında **tempdb**, günlük ve izleme dosyaları de bu dizine yazılır. Her kullanıcı için benzersiz olması garanti örneği için bir ad oluşturulur.  
  
 Varsayılan olarak Windows BUILTIN\USERS grubunun tüm üyeleri yerel örneğinde bağlanmak yanı sıra okuma ve Yürütme izinleri SQL Server ikili dosyaları izinleri verilir. Kullanıcı örneği barındırma arayan kullanıcının kimlik bilgileri doğruladıktan sonra o kullanıcı olur `sysadmin` , örnekteki. Yalnızca paylaşılan bellek, yalnızca yerel makine üzerindeki işlemleri mümkün olduğu anlamına gelir kullanıcı örnekleri için etkinleştirilir.  
  
 Kullanıcılar, hem okuma hem bağlantı dizesinde belirtilen .mdf ve .ldf dosyalarının izinleri verilmelidir.  
  
> [!NOTE]
>  .Mdf ve .ldf dosyalarının veritabanı ve günlük dosyalarının sırasıyla temsil eder. Dikkatli yedekleme sırasında düşünülmesi gereken ve geri yükleme işlemleri için bu iki eşlenmiş bir küme dosyalarıdır. Veritabanı dosyası günlük dosyasının tam sürümü hakkında bilgiler içerir ve yanlış günlük dosyasıyla birlikte, veritabanı açılmaz.  
  
 Veri bozulmasını önlemek için bir kullanıcı örneği veritabanında özel kullanım erişimi ile açılır. İki farklı kullanıcı örnekleri aynı bilgisayarda aynı veritabanını paylaşıyorsanız, ikinci bir örneğinde açılmadan önce kullanıcının ilk örneği üzerinde veritabanı kapatmanız gerekir.  
  
## <a name="user-instance-scenarios"></a>Kullanıcı örnek senaryolar  
 Kullanıcı örnekleri geliştiriciler geliştirme bilgisayarlarında yönetici hesaplarına sahip geliştiriciler bağlı olmayan bir SQL Server veri deposu veritabanı uygulamaları sağlar. Kullanıcı örnekleri burada veritabanı uygulama yalnızca bir dosyaya bağlanır ve kullanıcı otomatik olarak tam tüm veritabanı nesnelerinin vermek için bir Sistem Yöneticisi müdahalesine gerek kalmadan izinleri erişim/Jet modelini temel alan izinler. Burada kullanıcının en az ayrıcalıklı kullanıcı hesabı (LUA) altında çalışan ve sunucu veya yerel makine üzerinde yönetimsel ayrıcalıklara sahip değil, ancak veritabanı nesneleri ve uygulamaları oluşturmak için gereken durumlarda çalışmak üzere tasarlanmıştır. Kullanıcı örnekleri kullanıcının kendi güvenlik bağlamı altında ve değil daha ayrıcalıklı bir sistem hizmeti güvenlik bağlamında çalıştırma zamanında örnekleri oluşturmak kullanıcıların izin verin.  
  
> [!IMPORTANT]
>  Kullanıcı örnekleri yalnızca onu kullanan tüm uygulamaları tam güvenilir olduğu senaryolarda kullanılmalıdır.  
  
 Kullanıcı örnek senaryolar şunlardır:  
  
-   Herhangi bir tek kullanıcı uygulama burada veri paylaşımı gerekli değildir.  
  
-   ClickOnce dağıtımı. .NET Framework 2.0 (veya üstü) ve SQL Server Express hedef bilgisayarda zaten yüklü değilse, bir ClickOnce eylem sonucu olarak karşıdan yükleme paketi yüklü ve yönetici olmayan kullanıcılar tarafından kullanılır. Kurulumun bir parçası ise, yönetici SQL Server Express yüklemeniz gerektiğini unutmayın. Daha fazla bilgi için bkz: [Windows Forms uygulamaları için ClickOnce dağıtım](http://msdn.microsoft.com/en-us/34d8c770-48f2-460c-8d67-4ea5684511df).  
  
-   Windows kimlik doğrulaması kullanarak ASP.NET barındıran ayrılmış. Tek bir SQL Server Express örneği intranet üzerinde barındırılabilir. Uygulama, kimliğe bürünme kullanmayan ASPNET Windows hesabını kullanarak bağlanır. Kullanıcı örnekleri, üçüncü taraf veya paylaşılan barındırma burada tüm uygulamalar aynı kullanıcı örneği paylaştığınız ve artık birbirinden yalıtılmış kalarak senaryolarında için kullanılmamalıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [SQL Server ve ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)  
 [Bağlantı Dizeleri](../../../../../docs/framework/data/adonet/connection-strings.md)  
 [Veri Kaynağına Bağlanma](../../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)

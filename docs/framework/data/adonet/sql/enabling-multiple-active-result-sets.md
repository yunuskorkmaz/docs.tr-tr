---
title: Birden Çok Etkin Sonuç Kümesini Etkinleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 576079e4-debe-4ab5-9204-fcbe2ca7a5e2
ms.openlocfilehash: 633aaa4a9540d0895252e56dbeabd97200081fc9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59304408"
---
# <a name="enabling-multiple-active-result-sets"></a>Birden Çok Etkin Sonuç Kümesini Etkinleştirme
Birden çok etkin sonuç kümesi (MARS) tek bir bağlantı üzerinde birden çok toplu iş yürütme izin vermek için SQL Server ile birlikte çalışan bir özelliktir. SQL Server ile kullanmak için MARS etkinleştirilmişse kullanılan her komut nesnesi bir oturum bağlantı ekler.  
  
> [!NOTE]
>  MARS kullanmak için bir mantıksal bağlantısını ve ardından bir mantıksal bağlantı etkin her komut için tek bir MARS oturum açar.  
  
## <a name="enabling-and-disabling-mars-in-the-connection-string"></a>Bağlantı dizesindeki MARS devre dışı bırakma ve etkinleştirme  
  
> [!NOTE]
>  Aşağıdaki bağlantı dizelerini örneği kullanmak **AdventureWorks** veritabanını SQL Server'a dahildir. Sağlanan bağlantı dizeleri, veritabanı MSSQL1 adlı bir sunucu üzerinde yüklü olduğu varsayılmaktadır. Bağlantı dizesi, ortamınız için gerektiği gibi değiştirin.  
  
 MARS özelliği varsayılan olarak devre dışıdır. Ekleyerek etkinleştirilebilir "MultipleActiveResultSets = True" bağlantı dizenizi için anahtar çifti. "True" MARS etkinleştirmek için geçerli tek değerdir. Aşağıdaki örnek, bir SQL Server örneğine bağlanmayı ve MARS etkin olduğunu belirtmek nasıl gösterir.  
  
```vb  
Dim connectionString As String = "Data Source=MSSQL1;" & _  
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" & _  
    "MultipleActiveResultSets=True"  
```  
  
```csharp  
string connectionString = "Data Source=MSSQL1;" +   
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" +  
    "MultipleActiveResultSets=True";  
```  
  
 Ekleyerek MARS devre dışı bırakabilirsiniz "MultipleActiveResultSets = False" bağlantı dizenizi için anahtar çifti. "False" MARS devre dışı bırakmak için geçerli tek değerdir. Aşağıdaki bağlantı dizesi MARS devre dışı bırakma gösterir.  
  
```vb  
Dim connectionString As String = "Data Source=MSSQL1;" & _  
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" & _  
    "MultipleActiveResultSets=False"  
```  
  
```csharp  
string connectionString = "Data Source=MSSQL1;" +   
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" +  
    "MultipleActiveResultSets=False";  
```  
  
## <a name="special-considerations-when-using-mars"></a>MARS kullanırken özel durumları  
 Genel olarak, mevcut uygulamaları MARS özellikli bir bağlantı kullanmak için değiştirilmesi gerekir. Ancak, uygulamalarınızda MARS özelliklerini kullanmak istiyorsanız, aşağıdaki özel konular anlamanız gerekir.  
  
### <a name="statement-interleaving"></a>Deyimi Aralama  
 MARS operations sunucuda zaman uyumlu olarak yürütülür. Deyimi seçin ve BULK INSERT deyimleri Interleaving izin verilir. Ancak, veri işleme dili (DML) ve veri tanımlama dili (DDL) deyimleri atomik olarak yürütür. Atomik bir toplu iş yürütülürken yürütülmeye çalışılırken herhangi bir deyim engellenir. Paralel yürütme sunucuda MARS özelliği değil.  
  
 İki toplu bir MARS bağlantısı altında bunlardan birini içeren bir SELECT deyimi gönderdiyseniz diğer bir DML deyimi içeren DML SELECT deyiminin yürütülmesini içinde yürütme başlayabilirsiniz. Ancak, SELECT deyiminde ilerleme yapabilmeniz için önce DML deyimi tamamlanana kadar çalışması gerekir. Her iki deyimleri aynı işlem altında çalışıyorsa, SELECT deyimi yürütme başlatıldıktan sonra bir DML deyimi tarafından yapılan değişiklikler için okuma işlemi görünmez.  
  
 İlk satırın üretilene kadar diğer bir deyişle, bekliyor ancak bir SELECT deyimi WAITFOR ifadeye işlem vermez. WAITFOR deyimi beklerken diğer bir toplu aynı bağlantı içinde yürütebilir anlamına gelir.  
  
### <a name="mars-session-cache"></a>MARS oturum önbelleği  
 Bir bağlantı ile etkin MARS açık olduğunda, ek yükü ekler mantıksal bir oturum oluşturulur. Ek yükü en aza indirmek ve performansı artırmak için **SqlClient** bağlantı MARS oturumunda önbelleğe alır. Önbelleği, en fazla 10 MARS oturumu içerir. Bu değer, ayarlanabilir bir kullanıcı değil. Oturum sınırına ulaşıldığında, yeni bir oturum oluşturulur; bir hata değil oluşturulur. Bağlantı başına önbellek ve içerdiği oturumları olan; bağlantıları arasında paylaşılan değil. Oturumu serbest bırakıldığında, havuzun üst sınırına ulaşıldı sürece havuza döndürülür. Önbellek havuzu dolu ise, oturumu kapatılır. MARS oturumları süresi dolmaz. Bağlantı nesnesi çıkarıldığından, yalnızca temizlenir. MARS oturum önbelleği önceden yüklü değil. Daha fazla oturumları uygulamanın gerektirdiği yüklenir.  
  
### <a name="thread-safety"></a>İş Parçacığı Güvenliği  
 MARS işlemleri, iş parçacığı açısından güvenli değildir.  
  
### <a name="connection-pooling"></a>Bağlantı Havuzu  
 MARS etkin bağlantı, herhangi bir bağlantı gibi havuza eklenir. Uygulama etkin MARS biri diğeri devre dışı MARS ile iki bağlantı açarsa, iki ayrı havuzlarında bağlantılardır. Daha fazla bilgi için [SQL Server Connection Pooling (ADO.NET)](../../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).  
  
### <a name="sql-server-batch-execution-environment"></a>SQL Server toplu yürütme ortamı  
 Bağlantı açıldığında, varsayılan bir ortama tanımlanır. Bu ortam, ardından bir mantıksal MARS oturuma kopyalanır.  
  
 Toplu yürütme ortamını aşağıdaki bileşenleri içerir:  
  
-   (Örneğin, ANSI_NULLS, DATE_FORMAT, dil, TEXTSIZE) seçeneklerini ayarlama  
  
-   Güvenlik bağlamı (kullanıcı/uygulama rolü)  
  
-   Veritabanı bağlamı (geçerli veritabanı)  
  
-   Yürütme durumu değişkenleri (örneğin, @@ERROR, @@ROWCOUNT, @@FETCH_STATUS @@IDENTITY)  
  
-   Üst düzey geçici tablolar  
  
 MARS ile bir varsayılan yürütme ortamı için bir bağlantı ilişkilidir. Belirli bir bağlantı altında çalıştırmaya başlar her yeni batch varsayılan ortamın bir kopyasını alır. Belirtilen bir toplu iş altında kod yürütüldüğünde, ortama yapılan tüm değişiklikler belirli toplu belirlenir. Bir kez yürütme tamamlandığında, yürütme ayarları varsayılan ortama kopyalanır. Aynı işlemde sıralı olarak yürütülecek birkaç komut veren tek bir toplu iş söz konusu olduğunda, semantiği eski istemciler veya sunucular içeren bağlantılar tarafından kullanıma sunulan aynıdır.  
  
### <a name="parallel-execution"></a>Paralel Yürütme  
 MARS bir uygulamada birden fazla bağlantı için tüm gereksinimleri kaldırmak için tasarlanmamıştır. Bir uygulamanın doğru Paralel yürütme komutlarının bir sunucuya karşı gerekiyorsa, birden çok bağlantı kullanılmalıdır.  
  
 Örneğin, aşağıdaki senaryoyu göz önünde bulundurun. İki komut nesneleri, bir sonuç kümesi ve verilerini güncelleştirmek için başka bir işlem için bir tane oluşturulur; MARS aracılığıyla ortak bağlantı paylaşırlar. Bu senaryoda, `Transaction`.`Commit` Tüm sonuçları şu özel durum oluşturan ilk command nesnesinde okunana kadar güncelleştirme başarısız olur:  
  
 İleti: İşlem bağlamı başka bir oturum tarafından kullanılıyor.  
  
 Kaynak: .NET SqlClient veri sağlayıcısı  
  
 Beklenen: (null)  
  
 Alınan: System.Data.SqlClient.SqlException  
  
 Bu senaryoyu gerçekleştirmek için üç seçenek vardır:  
  
1. Okuyucu oluşturulduktan sonra işlem başlatın ve böylece işlemin bir parçası değil. Her güncelleştirme, böylece kendi işlem olur.  
  
2. Tüm iş okuyucu kapatıldıktan sonra işleyin. Bu, önemli toplu güncelleştirmeler için olasılığına sahiptir.  
  
3. MARS kullanmayın; Bunun yerine MARS önce yaptığınız gibi her komut nesnesi için ayrı bir bağlantı kullanın.  
  
### <a name="detecting-mars-support"></a>MARS destek algılama  
 MARS okuyarak desteği için bir uygulama denetleyebilirsiniz `SqlConnection.ServerVersion` değeri. Birincil numara 9 için SQL Server 2005 ve SQL Server 2008 için 10 olması gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Birden Çok Etkin Sonuç Kümesi (MARS)](../../../../../docs/framework/data/adonet/sql/multiple-active-result-sets-mars.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)

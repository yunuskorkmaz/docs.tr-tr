---
title: Birden Çok Etkin Sonuç Kümesini Etkinleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 576079e4-debe-4ab5-9204-fcbe2ca7a5e2
ms.openlocfilehash: 1f8cb573d051970414f3962057f6329683eea5bd
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782401"
---
# <a name="enabling-multiple-active-result-sets"></a>Birden Çok Etkin Sonuç Kümesini Etkinleştirme
Birden çok etkin sonuç kümesi (MARS), tek bir bağlantıda birden çok toplu işi yürütmeye izin vermek için SQL Server ile birlikte çalışarak bir özelliktir. MARS, SQL Server ile kullanım için etkinleştirildiğinde, kullanılan her komut nesnesi bağlantıya bir oturum ekler.  
  
> [!NOTE]
> Tek bir MARS oturumu, MARS için bir mantıksal bağlantı ve her etkin komut için bir mantıksal bağlantı açar.  
  
## <a name="enabling-and-disabling-mars-in-the-connection-string"></a>Bağlantı dizesinde MARS 'ı etkinleştirme ve devre dışı bırakma  
  
> [!NOTE]
> Aşağıdaki bağlantı dizeleri SQL Server bulunan örnek **AdventureWorks** veritabanını kullanır. Belirtilen bağlantı dizeleri, veritabanının MSSQL1 adlı bir sunucuda yüklü olduğunu varsayar. Bağlantı dizesini ortamınız için gereken şekilde değiştirin.  
  
 MARS özelliği varsayılan olarak devre dışıdır. Bağlantı dizenizi "MultipleActiveResultSets = true" anahtar sözcüğü çifti eklenerek etkinleştirilebilir. MARS 'ı etkinleştirmek için geçerli olan tek değer "true" değeridir. Aşağıdaki örnek, bir SQL Server örneğine nasıl bağlanabileceğinizi ve bu MARS 'ın etkinleştirilmesi gerektiğini belirtir.  
  
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
  
 Bağlantı dizenizi "MultipleActiveResultSets = false" anahtar sözcük çiftini ekleyerek MARS 'ı devre dışı bırakabilirsiniz. MARS devre dışı bırakmak için geçerli olan tek değer "false" değeridir. Aşağıdaki bağlantı dizesi, MARS 'ın nasıl devre dışı bırakılacağını gösterir.  
  
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
  
## <a name="special-considerations-when-using-mars"></a>MARS kullanırken özel konular  
 Genel olarak, mevcut uygulamaların MARS özellikli bir bağlantı kullanması için değişiklik yapması gerekmez. Ancak, uygulamalarınızda MARS özelliklerini kullanmak istiyorsanız, aşağıdaki özel konuları anlamanız gerekir.  
  
### <a name="statement-interleaving"></a>İfade araya ekleme  
 MARS işlemleri sunucuda zaman uyumlu olarak yürütülür. SELECT ve BULK INSERT deyimlerinin deyim araya ekleme değerlerine izin verilir. Ancak, veri işleme dili (DML) ve veri tanımlama dili (DDL) deyimleri otomatik olarak yürütülür. Atomik bir toplu iş yürütülürken yürütülmeye çalışan tüm deyimler engellenir. Sunucudaki paralel yürütme bir MARS özelliği değildir.  
  
 Bir MARS bağlantısı altında iki toplu işlem gönderilirse, bunlardan biri DML ifadesini içeren bir SELECT ifadesini içeriyorsa, DML SELECT ifadesinin yürütülmesi içinde yürütmeye başlayabilir. Ancak, SELECT ifadesinin ilerleme yapabilmesi için DML bildiriminin tamamlanmasını çalıştırması gerekir. Her iki deyim de aynı işlem altında çalışıyorsa, SELECT deyimi başladıktan sonra bir DML deyimi tarafından yapılan tüm değişiklikler okuma işlemine görünmez.  
  
 SELECT ifadesinin içindeki bir WAITFOR deyimleri, beklerken, ilk satır üretilene kadar işlem yapmaz. Bu, bir WAITFOR bildirisi beklerken aynı bağlantı içinde başka hiçbir toplu iş yürütülemmeyeceğini gösterir.  
  
### <a name="mars-session-cache"></a>MARS oturum önbelleği  
 Bir bağlantı MARS etkinken açıldığında, ek yük ekleyen bir mantıksal oturum oluşturulur. Ek yükü en aza indirmek ve performansı artırmak için, **SQLCLIENT** Mars oturumunu bir bağlantı içinde önbelleğe alır. Önbellekte en fazla 10 MARS oturumu bulunur. Bu değer Kullanıcı tarafından ayarlanamaz. Oturum sınırına ulaşıldığında, yeni bir oturum oluşturulur; bir hata oluşturulmaz. İçinde bulunan önbellek ve oturumlar bağlantı başına olur; bağlantılar arasında paylaşılmaz. Bir oturum bırakıldığında, havuzun üst sınırına ulaşılmadığı takdirde havuza döndürülür. Önbellek havuzu doluysa, oturum kapalıdır. MARS oturumlarının süreleri dolmaz. Bunlar yalnızca bağlantı nesnesi atıldığı zaman temizlenir. MARS oturum önbelleği önceden yüklenmedi. Uygulama daha fazla oturum gerektirdiğinden yüklenir.  
  
### <a name="thread-safety"></a>İş Parçacığı Güvenliği  
 MARS işlemleri iş parçacığı açısından güvenli değildir.  
  
### <a name="connection-pooling"></a>Bağlantı Havuzu  
 MARS etkin bağlantıları, diğer tüm bağlantılar gibi havuza alınır. Bir uygulama iki bağlantı açarsa, MARS ve diğeri de MARS devre dışı bırakıldığında iki bağlantı ayrı havuzlardır. Daha fazla bilgi için bkz. [SQL Server bağlantı havuzu (ADO.net)](../sql-server-connection-pooling.md).  
  
### <a name="sql-server-batch-execution-environment"></a>Toplu yürütme ortamı SQL Server  
 Bir bağlantı açıldığında, varsayılan bir ortam tanımlanmıştır. Bu ortam daha sonra bir mantıksal MARS oturumuna kopyalanır.  
  
 Toplu yürütme ortamı aşağıdaki bileşenleri içerir:  
  
- Seçenekleri ayarla (örneğin, ANSI_NULLS, DATE_FORMAT, LANGUAGE, TEXTSIZE)  
  
- Güvenlik bağlamı (Kullanıcı/uygulama rolü)  
  
- Veritabanı bağlamı (geçerli veritabanı)  
  
- Yürütme durumu değişkenleri (@ERRORÖrneğin, @, @@ROWCOUNT, @@FETCH_STATUS @@IDENTITY)  
  
- Üst düzey geçici tablolar  
  
 MARS ile, varsayılan bir yürütme ortamı bir bağlantıyla ilişkilendirilir. Belirli bir bağlantı altında yürütmeye başlayan her yeni toplu işlem, varsayılan ortamın bir kopyasını alır. Belirli bir toplu iş altında kod yürütüldüğünde, ortamda yapılan tüm değişiklikler belirli bir toplu işe göre kapsamlandırılır. Yürütme tamamlandıktan sonra, yürütme ayarları varsayılan ortama kopyalanır. Tek bir toplu iş, aynı işlem kapsamında sırayla yürütülmesi için birkaç komut veren bir toplu işlem söz konusu olduğunda, semantik, önceki istemci veya sunucuları içeren bağlantılar tarafından açığa çıkarılan olanlarla aynıdır.  
  
### <a name="parallel-execution"></a>Paralel Yürütme  
 MARS, bir uygulamadaki birden çok bağlantı için tüm gereksinimleri kaldırmak üzere tasarlanmamıştır. Bir uygulamanın bir sunucuya karşı doğru paralel yürütülmesi gerekiyorsa, birden çok bağlantı kullanılmalıdır.  
  
 Örneğin, aşağıdaki senaryoyu göz önünde bulundurun. Bir sonuç kümesini işlemek için biri ve verileri güncelleştirmek için bir tane olmak üzere iki komut nesnesi oluşturulur; MARS aracılığıyla ortak bir bağlantı paylaşır. Bu senaryoda, `Transaction`.`Commit` İlk komut nesnesinde tüm sonuçlar okunana kadar güncelleştirmede başarısız olur ve aşağıdaki özel durum ortaya çıkarsa:  
  
 İleti: İşlem bağlamı başka bir oturum tarafından kullanılıyor.  
  
 Kaynak: .NET SqlClient Veri Sağlayıcısı  
  
 Beklenen: (null)  
  
 Aldığınızı System. Data. SqlClient. SqlException  
  
 Bu senaryoyu işlemek için üç seçenek vardır:  
  
1. İşlemin bir parçası olmaması için okuyucu oluşturulduktan sonra işlemi başlatın. Her güncelleştirme, kendi işlemi olur.  
  
2. Okuyucu kapatıldıktan sonra tüm işleri yürütün. Bu, önemli miktarda güncelleştirme için olası bir işlem içerir.  
  
3. MARS kullanmayın; Bunun yerine, MARS 'tan önce yaptığınız gibi her bir komut nesnesi için ayrı bir bağlantı kullanın.  
  
### <a name="detecting-mars-support"></a>MARS desteğini algılama  
 Bir uygulama, `SqlConnection.ServerVersion` değeri okuyarak Mars desteğini denetleyebilir. Ana sayı SQL Server 2005 için 9 ve SQL Server 2008 için 10 olmalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Birden Çok Etkin Sonuç Kümesi (MARS)](multiple-active-result-sets-mars.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)

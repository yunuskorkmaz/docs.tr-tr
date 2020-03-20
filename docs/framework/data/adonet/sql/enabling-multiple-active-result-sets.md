---
title: Birden Çok Etkin Sonuç Kümesini Etkinleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 576079e4-debe-4ab5-9204-fcbe2ca7a5e2
ms.openlocfilehash: 72125be835298218e5445fe1915d6a17f5008bb2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148731"
---
# <a name="enabling-multiple-active-result-sets"></a>Birden Çok Etkin Sonuç Kümesini Etkinleştirme
Çoklu Etkin Sonuç Kümeleri (MARS), sql server ile çalışan ve tek bir bağlantıda birden çok toplu iş yürütmeye izin veren bir özelliktir. MARS SQL Server ile kullanım için etkinleştirildiğinde, kullanılan her komut nesnesi bağlantıya bir oturum ekler.  
  
> [!NOTE]
> Tek bir MARS oturumu MARS'ın kullanması için bir mantıksal bağlantı ve ardından her etkin komut için bir mantıksal bağlantı açar.  
  
## <a name="enabling-and-disabling-mars-in-the-connection-string"></a>Bağlantı Dizesinde MARS'ı Etkinleştirme ve Devre Dışı Bırakma  
  
> [!NOTE]
> Aşağıdaki bağlantı dizeleri, SQL Server ile birlikte örnek **AdventureWorks** veritabanını kullanır. Sağlanan bağlantı dizeleri veritabanı MSSQL1 adlı bir sunucuda yüklü olduğunu varsayar. Bağlantı dizesini ortamınız için gerektiği gibi değiştirin.  
  
 MARS özelliği varsayılan olarak devre dışı bırakılır. Bağlantı dizenize "MultipleActiveResultSets=True" anahtar kelime çiftini ekleyerek etkinleştirilebilir. "True" MARS'ı etkinleştirmek için tek geçerli değerdir. Aşağıdaki örnek, SQL Server'ın bir örneğine nasıl bağlanılabildiğini ve MARS'ın etkinleştirilmesi gerektiğini nasıl belirteceğini göstermektedir.  
  
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
  
 Bağlantı dizenize "MultipleActiveResultSets=False" anahtar kelime çiftini ekleyerek MARS'ı devre dışı bırakabilirsiniz. "False" MARS devre dışı bırakmak için tek geçerli değerdir. Aşağıdaki bağlantı dizesi MARS'ı nasıl devre dışı kkarşılayabildiğini gösterir.  
  
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
  
## <a name="special-considerations-when-using-mars"></a>MARS Kullanırken Dikkat Edilmesi Gereken Özel Noktalar  
 Genel olarak, varolan uygulamaların MARS özellikli bir bağlantı kullanmak için değiştirilmesi gerekmez. Ancak, uygulamalarınızda MARS özelliklerini kullanmak istiyorsanız, aşağıdaki özel hususları anlamanız gerekir.  
  
### <a name="statement-interleaving"></a>Bildirim Ara  
 MARS işlemleri sunucuda eşzamanlı olarak yürütülür. SELECT ve BULK INSERT ifadelerinin deyiminin ayrılmasına izin verilir. Ancak, veri işleme dili (DML) ve veri tanım dili (DDL) deyimleri atomik olarak yürütülür. Atomik bir toplu iş yürütülürken yürütmeye çalışan tüm ifadeler engellenir. Sunucudaki paralel yürütme bir MARS özelliği değildir.  
  
 Mars bağlantısı altında iki toplu iş gönderilirse, bunlardan biri SELECT deyimi, diğeri DML deyimi içeren, DML SELECT deyiminin yürütülmesi nde yürütmeye başlayabilir. Ancak, SELECT deyiminin ilerleme kaydedilemeden önce DML deyiminin tamamlanması gerekir. Her iki deyim de aynı işlem altında çalışıyorsa, SELECT deyimi yürütmeye başladıktan sonra Bir DML deyimi tarafından yapılan değişiklikler okundu işlemi için görünmez.  
  
 SELECT deyiminin içindeki WAITFOR deyimi, ilk satır üretilene kadar işlemi beklerken vermez. Bu, WAITFOR deyimi beklerken aynı bağlantı içinde başka hiçbir toplu işlemin yürütülamayacağı anlamına gelir.  
  
### <a name="mars-session-cache"></a>MARS Oturum Önbelleği  
 When a connection is opened with MARS enabled, a logical session is created, which adds additional overhead. Genel yükü en aza indirmek ve performansı artırmak için **SqlClient,** mars oturumunu bir bağlantı içinde önbelleğe alıyor. Önbellek en fazla 10 MARS oturumu içerir. Bu değer kullanıcı tarafından ayarlanılamaz. Oturum sınırına ulaşılırsa, yeni bir oturum oluşturulur-bir hata oluşturulmaz. Önbellek ve içerdiği oturumlar bağlantı başına; bağlantılar arasında paylaşılmaz. Oturum serbest bırakıldığında, havuzun üst sınırına ulaşılmadığı sürece havuza döndürülür. Önbellek havuzu doluysa, oturum kapatılır. MARS oturumlarının süresi dolmaz. Yalnızca bağlantı nesnesi imha edildiğinde temizlenirler. MARS oturum önbelleği önceden yüklenmedi. Uygulama daha fazla oturum gerektirdiğinden yüklenir.  
  
### <a name="thread-safety"></a>İş Parçacığı Güvenliği  
 MARS işlemleri iş parçacığı için güvenli değildir.  
  
### <a name="connection-pooling"></a>Bağlantı Havuzu  
 MARS özellikli bağlantılar, diğer bağlantılar gibi bir araya toplandı. Bir uygulama, biri MARS etkin, diğeri MARS devre dışı bırakılmış iki bağlantı açarsa, iki bağlantı ayrı havuzlarda dır. Daha fazla bilgi için [SQL Server Connection Pooling (ADO.NET)](../sql-server-connection-pooling.md)adresine bakın.  
  
### <a name="sql-server-batch-execution-environment"></a>SQL Server Toplu Yürütme Ortamı  
 Bir bağlantı açıldığında, varsayılan bir ortam tanımlanır. Bu ortam daha sonra mantıksal bir MARS oturumuna kopyalanır.  
  
 Toplu yürütme ortamı aşağıdaki bileşenleri içerir:  
  
- Seçenekleri ayarlama (örneğin, ANSI_NULLS, DATE_FORMAT, Dİl, TEXTSIZE)  
  
- Güvenlik bağlamı (kullanıcı/uygulama rolü)  
  
- Veritabanı bağlamı (geçerli veritabanı)  
  
- Yürütme durumu değişkenleri@ERROR(örneğin,@ROWCOUNT@@FETCH_STATUS ,@IDENTITY@ , @ @ )  
  
- Üst düzey geçici tablolar  
  
 MARS ile varsayılan yürütme ortamı bir bağlantıyla ilişkilidir. Belirli bir bağlantı altında yürütmeye başlayan her yeni toplu iş, varsayılan ortamın bir kopyasını alır. Kod belirli bir toplu iş altında yürütüldüğünde, ortamda yapılan tüm değişiklikler belirli toplu iş kapsamına alınır. Yürütme tamamlandığında, yürütme ayarları varsayılan ortama kopyalanır. Tek bir toplu işlemin aynı işlem altında sırayla yürütülmesi için birkaç komut vermesi durumunda, anlamsal işlemler önceki istemcileri veya sunucuları içeren bağlantılar tarafından açığa çıkarılanlarla aynıdır.  
  
### <a name="parallel-execution"></a>Paralel Yürütme  
 MARS, bir uygulamadaki birden çok bağlantı için tüm gereksinimleri kaldırmak için tasarlanmaz. Bir uygulama nın bir sunucuya karşı komutların gerçek paralel yürütülmesi ne gerekiyorsa, birden çok bağlantı kullanılmalıdır.  
  
 Örneğin aşağıdaki senaryoları düşünün. İki komut nesnesi oluşturulur, biri sonuç kümesini işlemek için diğeri verileri güncelleştirmek için; MARS üzerinden ortak bir bağlantıyı paylaşırlar. Bu senaryoda, `Transaction`.`Commit` tüm sonuçlar ilk komut nesnesi üzerinde okunana kadar güncelleştirmede başarısız olur ve aşağıdaki özel durum verir:  
  
 İleti: Başka bir oturum tarafından kullanılan hareket bağlamı.  
  
 Kaynak: .NET SqlClient Veri Sağlayıcısı  
  
 Beklenen: (null)  
  
 Alınan: System.Data.sqlclient.sqlException  
  
 Bu senaryoyu işlemek için üç seçenek vardır:  
  
1. Okuyucu oluşturulduktan sonra hareketi başlatın, böylece işlemin bir parçası olmaz. Her güncelleştirme daha sonra kendi işlem olur.  
  
2. Okuyucu kapandıktan sonra tüm işi gerçekleştirin. Bu, önemli bir güncelleştirme grubu için potansiyele sahiptir.  
  
3. MARS kullanmayın; bunun yerine MARS'dan önce yaptığınız gibi her komut nesnesi için ayrı bir bağlantı kullanın.  
  
### <a name="detecting-mars-support"></a>MARS Desteğini Algılama  
 Bir uygulama değeri okuyarak MARS `SqlConnection.ServerVersion` desteği için kontrol edebilirsiniz. Sql Server 2005 için en büyük sayı 9, SQL Server 2008 için 10 olmalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Birden Çok Etkin Sonuç Kümesi (MARS)](multiple-active-result-sets-mars.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)

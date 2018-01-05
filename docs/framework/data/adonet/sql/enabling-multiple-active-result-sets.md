---
title: "Birden fazla etkin sonuç kümesi etkinleştirme"
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
ms.assetid: 576079e4-debe-4ab5-9204-fcbe2ca7a5e2
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 0235a63a24f81968718d526ff676b023c060b9a6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="enabling-multiple-active-result-sets"></a>Birden fazla etkin sonuç kümesi etkinleştirme
Birden fazla etkin sonuç kümeleri (MARS) birden çok toplu işlem yürütme üzerinde tek bir bağlantıya izin vermek için SQL Server ile çalışan bir özelliktir. MARS, SQL Server ile kullanmak için etkinleştirildiğinde, kullanılan her komut nesnesi bir oturum bağlantısı ekler.  
  
> [!NOTE]
>  Tek bir MARS oturumu MARS kullanmak için bir mantıksal bağlantı ve ardından her etkin komutu için bir mantıksal bağlantı açar.  
  
## <a name="enabling-and-disabling-mars-in-the-connection-string"></a>Etkinleştirme ve bağlantı dizesindeki MARS devre dışı bırakma  
  
> [!NOTE]
>  Aşağıdaki bağlantı dizeleri örneği kullanmak **AdventureWorks** SQL Server'da bulunan veritabanı. Sağlanan bağlantı dizeleri, veritabanı MSSQL1 adlı bir sunucuda yüklü olduğunu varsayar. Bağlantı dizesi, ortamınız için gerektiği gibi değiştirin.  
  
 MARS özelliği varsayılan olarak devre dışıdır. Ekleyerek etkinleştirilebilir "MultipleActiveResultSets = True", bağlantı dizesi için anahtar çifti. MARS etkinleştirmek için tek geçerli değer "True" dır. Aşağıdaki örnek, SQL Server örneğine bağlanma ve MARS etkin olduğunu belirtmek nasıl gösterilir.  
  
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
  
 Ekleyerek MARS devre dışı bırakabilirsiniz "MultipleActiveResultSets = False" bağlantı dizenizi için anahtar çifti. MARS devre dışı bırakmak için tek geçerli değer "False" dır. Aşağıdaki bağlantı dizesi MARS devre dışı bırakma gösterir.  
  
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
 Genel olarak, var olan uygulamaları MARS etkin bir bağlantı kullanmak için değiştirilmesi gerekir. Ancak, uygulamalarınızda MARS özelliklerini kullanmak isterseniz, aşağıdaki özel hususlar anlamanız gerekir.  
  
### <a name="statement-interleaving"></a>Deyimi Interleaving  
 MARS işlemleri zaman uyumlu olarak sunucuda yürütün. Deyimi seçin ve BULK INSERT deyimleri Interleaving izin verilir. Ancak, veri işleme dili (DML) ve veri tanımlama dili (DDL) deyimleri otomatik olarak çalışır. Atomik bir toplu iş yürütülürken yürütme girişimi deyimleri engellenir. Paralel yürütme sunucuda bir MARS özelliği değil.  
  
 Bir MARS bağlantısı altında biri bir SELECT deyimi içeren iki toplu gönderdiyseniz diğer bir DML deyimi içeren DML yürütme SELECT deyiminin içinde yürütme başlayabilirsiniz. Ancak, SELECT deyiminde ilerleme yapabilmeniz için önce DML deyimi tamamlanıncaya kadar çalıştırmanız gerekir. Her iki deyimleri aynı işlemde çalıştırıyorsanız, SELECT deyimi yürütme başlatıldıktan sonra bir DML deyimi tarafından yapılan değişiklikler okuma işlemi için görünür değildir.  
  
 İlk satırın üretilene kadar diğer bir deyişle, bekliyor ancak bir SELECT deyimi WAITFOR ifadeye işlem vermez. Bu, bir WAITFOR ifadesi bekliyor. sırada başka bir toplu aynı bağlantı içinde yürütebilir anlamına gelir.  
  
### <a name="mars-session-cache"></a>MARS oturumu önbelleği  
 Bağlantı etkin MARS ile açıldığında, ek yükü ekler mantıksal bir oturum oluşturulur. Ek yükü en aza indirmek ve performansı geliştirmek için **SqlClient** bağlantı MARS oturumunda önbelleğe alır. Önbelleği en fazla 10 MARS oturumu içerir. Bu değer ayarlanabilir kullanıcı değil. Oturum sınırına ulaşıldığında, yeni bir oturum oluşturulur — bir hata değildir oluşturulur. Bağlantı başına önbellek ve içerdiği oturumları olan; bağlantılarında paylaşılmaz. Oturumu serbest bırakıldığında havuzun üst sınırına ulaşıldı sürece havuzuna döndürülür. Önbellek havuzun doluysa oturumu kapatılır. MARS oturumları dolmaz. Bağlantı nesnesi çıkarıldığından bunlar yalnızca temizlenmesini. MARS oturumu önbelleği önceden yüklü değil. Daha fazla oturumları uygulamanın gerektirdiği şekilde yüklenir.  
  
### <a name="thread-safety"></a>İş Parçacığı Güvenliği  
 MARS işlem iş parçacığı açısından güvenli değildir.  
  
### <a name="connection-pooling"></a>Bağlantı havuzu  
 MARS etkin bağlantılar gibi başka bir bağlantı havuza. Bir uygulama biri etkin MARS diğeri devre dışı MARS ile iki bağlantı açılırsa, iki ayrı havuzlarında bağlantılardır. Daha fazla bilgi için bkz: [SQL Server bağlantı havuzu (ADO.NET)](../../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).  
  
### <a name="sql-server-batch-execution-environment"></a>SQL Server toplu iş yürütme ortamı  
 Bağlantı açıldığında, varsayılan ortam tanımlanır. Bu ortam sonra mantıksal MARS oturuma kopyalanır.  
  
 Toplu iş yürütme ortamı aşağıdaki bileşenleri içerir:  
  
-   SET seçenekleri (örneğin, ANSI_NULLS DATE_FORMAT, dil, TEXTSIZE)  
  
-   Güvenlik bağlamı (kullanıcı/uygulama rolü)  
  
-   Veritabanı bağlamı (geçerli veritabanı)  
  
-   Yürütme durumu değişkenleri (örneğin, @@ERROR, @@ROWCOUNT, @@FETCH_STATUS @@IDENTITY)  
  
-   Üst düzey geçici tabloları  
  
 MARS ile bir varsayılan yürütme ortamı bağlantı ilişkilidir. Verilen bağlantı altında yürütülmeye başlamadan her yeni toplu varsayılan ortamın kopyasını alır. Her kod altında belirtilen bir toplu iş yürütüldüğünde, ortama yapılan tüm değişiklikler için belirli toplu kapsamlıdır. Bir kez yürütme tamamlandığında, yürütme ayarları varsayılan ortamına kopyalanır. Aynı işlemde sıralı olarak yürütülecek birkaç komutların veren tek bir toplu iş söz konusu olduğunda, semantiği önceki istemciler veya sunucular içeren bağlantılar tarafından kullanıma sunulan aynıdır.  
  
### <a name="parallel-execution"></a>Paralel Yürütme  
 MARS bir uygulamada birden çok bağlantı için tüm gereksinimleri kaldırmak için tasarlanmamıştır. Bir uygulama bir sunucuya karşı komutların true Paralel yürütme gerekiyorsa, birden çok bağlantı kullanılmalıdır.  
  
 Örneğin, aşağıdaki senaryoyu göz önünde bulundurun. İki komut nesneleri, bir sonuç kümesi ve verilerini güncelleştirmek için başka bir işleme için bir tane oluşturulur; MARS aracılığıyla ortak bağlantı paylaştıkları. Bu senaryoda, `Transaction`.`Commit` Tüm sonuçlar şu özel durum oluşturan ilk command nesnesinde okunan kadar güncelleştirme başarısız olur:  
  
 İleti: İşlem bağlamı başka bir oturum tarafından kullanılıyor.  
  
 Kaynak: .net SqlClient veri sağlayıcısı  
  
 Beklenen: (boş)  
  
 Alınan: System.Data.SqlClient.SqlException  
  
 Bu senaryo işlemek için üç seçenek vardır:  
  
1.  Okuyucu oluşturulduktan sonra işlemin bir parçası değil işlem başlatın. Her güncelleştirmeyi daha sonra kendi işlem olur.  
  
2.  Okuyucu kapatıldıktan sonra tüm iş uygulayın. Bu güncelleştirmeler önemli toplu için olasılığı vardır.  
  
3.  MARS kullanmayın; Bunun yerine önce MARS yaptığınız gibi her komut nesnesi için ayrı bir bağlantı kullanın.  
  
### <a name="detecting-mars-support"></a>MARS destek algılama  
 MARS okuyarak desteği için bir uygulama denetleyebilirsiniz `SqlConnection.ServerVersion` değeri. Ana 9 SQL Server 2005 ve SQL Server 2008 için 10 olmalıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Birden Çok Etkin Sonuç Kümesi (MARS)](../../../../../docs/framework/data/adonet/sql/multiple-active-result-sets-mars.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)

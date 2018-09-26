---
title: SQL Server'da anlık görüntü yalıtımı
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 43ae5dd3-50f5-43a8-8d01-e37a61664176
ms.openlocfilehash: 52c5dba1a21b0e8d8e5af1dc159941e5f4b4aa5f
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45970079"
---
# <a name="snapshot-isolation-in-sql-server"></a>SQL Server'da anlık görüntü yalıtımı
Anlık görüntü yalıtımı OLTP uygulamalar için eşzamanlılık geliştirir.  
  
## <a name="understanding-snapshot-isolation-and-row-versioning"></a>Anlık görüntü yalıtımı ve satır sürüm anlama  
 Anlık görüntü yalıtımı etkinleştirildikten sonra her işlem için güncelleştirilmiş satır sürümleri de korunur **tempdb**. Her işlemin benzersiz işlem sıra numarası tanımlar ve bu benzersiz sayı her satır sürümü için kaydedilir. İşlem, bir sıra numarası işlem sırası sayısını önce sahip en son satır sürümleri ile birlikte çalışır. İşlem başladıktan sonra oluşturulan yeni satır sürümleri işlem tarafından göz ardı edilir.  
  
 "Snapshot" terimi, işlem sorguların tümünün aynı sürümü veya zamanlı işlemin başladığı anda veritabanının durumuna göre veritabanının anlık görüntü gördüğünüzü olgu yansıtır. Önceki tamamlanmamış bir işlem tarafından engellenme olmadan yürütmek için diğer işlemleri izin veren bir anlık görüntü işlemi, veri sayfaları ve temel alınan veri satırları üzerinde kilit elde edilen. Verileri okuyan işlemleri verileri değiştirme işlemleri engellemez ve SQL Server'daki varsayılan READ COMMITTED yalıtım düzeyi altında normalde yaptığınız gibi verileri okuyan işlemleri verileri yazma işlemleri engellemez. Engelleyici olmayan bu davranışı, ayrıca önemli ölçüde karmaşık işlemleri için kilitlenmeleri olasılığını azaltır.  
  
 Anlık görüntü yalıtımı iyimser eşzamanlılık modeli kullanır. Anlık görüntü işlemi işlemin başlamasından bu yana değişmiş olan verileri değişiklikleri kaydetmeye çalışırsa, işlem geri alma ve bir hata oluşacaktır. Bu, değiştirilecek verilere erişen SELECT deyimleri için UPDLOCK ipuçlarını kullanarak önleyebilirsiniz. SQL Server Books Online'da "kilitleme ipuçları" daha fazla bilgi için bkz.  
  
 Anlık görüntü yalıtımı işlemlerde kullanılmadan önce allow_snapshot_ısolatıon açık veritabanı seçeneğini ayarlayarak etkinleştirilmesi gerekir. Bu geçici bir veritabanında satır sürümlerini depolamak için bir mekanizma etkinleştirir (**tempdb**). İle Transact-SQL ALTER DATABASE deyimini kullanan her veritabanında anlık görüntü yalıtımını etkinleştirmeniz gerekir. Bu bakımdan, anlık görüntü yalıtımı READ COMMITTED, TEKRARLANABİLİR okuma, seri hale GETİRİLEBİLİR ve READ UNCOMMITTED hiçbir yapılandırma gerektiren geleneksel yalıtım düzeylerinden farklıdır. Aşağıdaki deyimleri, anlık görüntü yalıtımını etkinleştirmeniz ve varsayılan davranışını READ COMMITTED SNAPSHOT ile değiştirin:  
  
```  
ALTER DATABASE MyDatabase  
SET ALLOW_SNAPSHOT_ISOLATION ON  
  
ALTER DATABASE MyDatabase  
SET READ_COMMITTED_SNAPSHOT ON  
```  
  
 Sürümü tutulan satırlara erişimi, read_commıtted_snapshot ON seçeneği ayarlama varsayılan READ COMMITTED yalıtım düzeyi altında sağlar. Read_commıtted_snapshot seçeneği OFF olarak ayarlanmışsa, sürümü tutulan satırlara erişimi için açıkça her oturum için anlık görüntü yalıtım düzeyini ayarlamanız gerekir.  
  
## <a name="managing-concurrency-with-isolation-levels"></a>Yalıtım düzeyleri ile eşzamanlılığı yönetme  
 Transact-SQL deyimini yürütür yalıtım düzeyi kilitleme ve satır sürüm davranışını belirler. Bağlantı geniş kapsamı bir yalıtım düzeyi vardır ve işlem YALITIM düzeyi AYARLANAN deyimi ile bağlantı için bir kez ayarlanırsa, bu bağlantı kapalı veya başka bir yalıtım düzeyi kadar devam eder. Bağlantı kapalı olduğunda ve havuza geri döner son işlem YALITIM düzeyi AYARLANAN deyimden yalıtım düzeyi korunur. Sonraki bağlantıları yeniden anda yürürlükte olan bağlantısı yalıtım düzeyi havuza bir havuza alınmış bir bağlantı kullanın.  
  
 Bir bağlantıda verilen her sorgu, tek bir deyim veya işlem yalıtım değiştirir, ancak bağlantı yalıtım düzeyini etkilemez kilit ipuçlarına içerebilir. Yalıtım düzeyleri veya kilit ipuçlarına, saklı yordamların ayarlayın veya İşlevler, onları çağıran bağlantının yalıtım düzeyi değiştirmeyin ve yalnızca saklı yordam veya işlev çağrı süresi boyunca geçerli olur.  
  
 SQL Server'ın önceki sürümlerinde desteklenen SQL 92 standartlarındaki dört yalıtım düzeyi:  
  
-   Diğer işlemler tarafından yerleştirilen kilit yoksayar READ UNCOMMITTED yalıtım düzeyi en az kısıtlayıcı olmasıdır. READ UNCOMMITTED altında çalıştırma işlemleri henüz diğer işlemler tarafından taahhüt değil değiştirilen veri değerlerini okuyabilirsiniz. Bunlar, "kirli" okuma olarak adlandırılır.  
  
-   READ COMMITTED SQL Server için varsayılan yalıtım düzeyi var. Kirli okuma, deyimleri değiştirilmiş, ancak diğer işlemler tarafından henüz uygulanmamış veri değerleri okunamıyor belirterek engeller. Yine de diğer işlemleri değiştirmek, Ekle veya geçerli işlem tekrarlanabilir olmayan okuma veya "hayalet" veri içinde ayrı deyimler yürütmeleri arasında verileri silin.  
  
-   REPEATABLE READ READ COMMITTED daha kısıtlayıcı bir yalıtım düzeyi var. Okuma KAYDEDİLEN kapsar ve başka bir işlem değiştirmek veya geçerli işlem yürütmeleri kadar geçerli işlem tarafından Okunmuş verilerini silmek ayrıca belirtir. Salt okunur veri çubuğunda paylaşılan kilit her deyim sonunda yayımlanan yerine işlem süresince tutulur çünkü eşzamanlılık okuma KAYDEDİLEN için daha düşük maliyetlidir.  
  
-   Tüm aralıkları anahtarların kilitler ve işlem tamamlanana kadar Kilit tutan çünkü en kısıtlayıcı bir yalıtım düzeyi seri hale GETİRİLEBİLİR. Bu, TEKRARLANABİLİR okuma kapsayan ve diğer işlemlerin işlem tamamlanana kadar bu işlem tarafından okunana aralıkları yeni satır eklenemiyor kısıtlama ekler.  
  
 Daha fazla bilgi için SQL Server Books Online'da "yalıtım düzeyleri" konusuna bakın.  
  
### <a name="snapshot-isolation-level-extensions"></a>Anlık görüntü yalıtım düzeyi uzantıları  
 SQL Server uzantılarını anlık görüntü yalıtım düzeyi giriş ve ek READ COMMITTED uygulaması ile SQL 92 yalıtım düzeyleri kullanıma sunmuştu. Read_commıtted_snapshot yalıtım düzeyi şeffaf bir şekilde READ COMMITTED tüm işlemler için değiştirebilirsiniz.  
  
-   Anlık görüntü yalıtımı, bir işlem içinde okunan veriler hiçbir zaman eş zamanlı diğer işlemler tarafından yapılan değişiklikleri yansıtacak belirtir. İşlem, işlem başladığında mevcut veri satır sürümleri kullanır. Okunduğunda, anlık görüntü işlemleri diğer işlemleri veri yazmasını engellemez için veriler üzerinde kilit yerleştirilir. Veri yazma işlemleri, verileri okuma anlık görüntü hareketlerin engellemez. Anlık görüntü yalıtımı kullanmak için allow_snapshot_ısolatıon veritabanı seçeneği etkinleştirmeniz gerekir.  
  
-   Bir veritabanında anlık görüntü yalıtımı etkinleştirildiğinde veritabanı seçeneği read_commıtted_snapshot varsayılan READ COMMITTED yalıtım düzeyi davranışını belirler. READ COMMITTED read_commıtted_snapshot ON açıkça belirtmezseniz, tüm örtük işlemleri için uygulanır. Bu ayarı read_commıtted_snapshot devre dışı (varsayılan) olarak aynı davranışı üretir. Veritabanı altyapısı, paylaşılan kilit read_commıtted_snapshot kapalı etkin olduğunda, varsayılan yalıtım düzeyi zorlamak için kullanır. Veritabanı altyapısı veritabanı seçeneği read_commıtted_snapshot ON olarak ayarlarsanız, satır sürüm oluşturma ve anlık görüntü yalıtımı kilitleri verileri korumak için kullanmak yerine varsayılan olarak kullanır.  
  
## <a name="how-snapshot-isolation-and-row-versioning-work"></a>Nasıl anlık görüntü yalıtımı ve satır sürüm oluşturma iş  
 Anlık görüntü yalıtım düzeyi, bir satır güncelleştirildiğinde, her zaman etkin olduğunda, SQL Server veritabanı altyapısı özgün satırda kopyasını depoladığından **tempdb**ve işlem sırası birkaç satır ekler. Gerçekleşen olayların sırasını verilmiştir:  
  
-   Yeni bir işlem tarafından başlatılan ve bir işlem sıra numarası atanır.  
  
-   Veritabanı altyapısı işlem içinde bir satır okur ve bir satır sürümündeki alır **tempdb** en yakın ve işlem sırası sayı daha düşük olan sıra numarası.  
  
-   Veritabanı altyapısı, anlık görüntü işlem başlatıldığında işlem sıra numarası kaydedilmemiş işlemleri etkin işlem sırası sayıda listesinde değilse görmek için denetler.  
  
-   İşlem satırdan sürümünü okur **tempdb** , hareketin başlangıcını itibarıyla geçerli. Bu sıra sayı değerlerini işlem sıra numarası değerinden daha yüksek olacağı için işlem başlatıldıktan sonra eklenen yeni satırlar görmezsiniz.  
  
-   Geçerli işlem, işlem başladıktan sonra bir satır sürümde olacağından silinen satırlar göreceksiniz **tempdb** daha düşük bir sıra numarası değere sahip.  
  
 Anlık görüntü yalıtım net etkisiyle, DSR'nin veya bağlantılı tablolarda kilitleri yerleştirme olmadan işlem başlangıcında bulunduğu gibi işlem tüm verileri dilediği zaman isteyebilmesi ' dir. Bu gibi durumlarda performans geliştirmeleri sonuçlanabilir Çekişme olduğunda.  
  
 Her zaman bir anlık görüntü işlemi, iyimser eşzamanlılık denetimi, satırları güncelleştirme diğer hareketlerin önleyen kilitleri stopaj kullanır. Anlık görüntü işlemi işlem başladıktan sonra değişen bir satır için bir güncelleştirme kaydetmeye çalışırsa, işlem geri alındı ve bir hata ortaya çıkar.  
  
## <a name="working-with-snapshot-isolation-in-adonet"></a>ADO.NET'te anlık görüntü yalıtımı ile çalışma  
 ADO.NET'te tarafından desteklenen anlık görüntü yalıtımı <xref:System.Data.SqlClient.SqlTransaction> sınıfı. Bir veritabanı için anlık görüntü yalıtımı etkinleştirilmiş, ancak için read_commıtted_snapshot ON yapılandırılmamış başlatmalıdır bir <xref:System.Data.SqlClient.SqlTransaction> kullanarak **IsolationLevel.Snapshot** çağırırken numaralandırma değeri <xref:System.Data.SqlClient.SqlConnection.BeginTransaction%2A> yöntem. Bu kod parçasını bağlantının açık olduğunu varsayar <xref:System.Data.SqlClient.SqlConnection> nesne.  
  
```vb  
Dim sqlTran As SqlTransaction = _  
  connection.BeginTransaction(IsolationLevel.Snapshot)  
```  
  
```csharp  
SqlTransaction sqlTran =   
  connection.BeginTransaction(IsolationLevel.Snapshot);  
```  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, kilitli verilerinize erişmeye çalışan tarafından farklı yalıtım düzeyleri nasıl davranacağını gösterir ve üretim kodunda kullanılmak üzere tasarlanmamıştır.  
  
 Kod bağlandığı **AdventureWorks** adlı bir tablo oluşturur ve örnek SQL Server veritabanında **TestSnapshot** ve verilerin bir satır ekler. Kod, veritabanı için anlık görüntü yalıtımı etkinleştirmek için ALTER DATABASE Transact-SQL deyimini kullanır, ancak varsayılan READ COMMITTED yalıtım düzeyi davranışı etkin bırakılması read_commıtted_snapshot seçeneğini ayarlamaz. Kod aşağıdaki eylemleri gerçekleştirir:  
  
-   Başlar, ancak tamamlamaz, bir güncelleştirme işlemini başlatmaya SERIALIZABLE yalıtım düzeyi kullanan sqlTransaction1. Bu tabloda kilitleme etkisi vardır.  
  
-   İkinci bir bağlantı açar ve verileri okumak için anlık görüntü yalıtım düzeyi kullanılarak ikinci bir hareket başlatır **TestSnapshot** tablo. Anlık görüntü yalıtımı etkinleştirilmiş olduğundan, bu işlem sqlTransaction1 başlatmadan önce var olan verileri okuyabilir.  
  
-   Bu, üçüncü bir bağlantı açar ve tablodaki verileri okuma girişimi için READ yalıtım düzeyi kullanılarak bir işlem başlatır. Bu durumda, zaman aşımına ve ilk işlem bir tabloda yerleştirilen kilit geçmiş okunamıyor çünkü kod veri okunamıyor. Bu yalıtım düzeyleri de ilk işlemde yerleştirilen kilit geçmiş okunamıyor çünkü TEKRARLANABİLİR okuma ve SERIALIZABLE yalıtım düzeyleri kullanıldıysa aynı sonucu oluşacak.  
  
-   Dördüncü bir bağlantı açar ve kaydedilmemiş değerin kirli okuma içinde sqlTransaction1 gerçekleştirir READ UNCOMMITTED yalıtım düzeyi kullanılarak bir işlem başlatır. İlk işlem kaydedilmiş değilse, bu değeri hiçbir zaman gerçekten veritabanında var olabilir.  
  
-   İlk işlem geri alınır ve silerek temizler **TestSnapshot** tablo ve kapatma anlık görüntü yalıtımı için **AdventureWorks** veritabanı.  
  
> [!NOTE]
>  Aşağıdaki örnekler aynı bağlantı dizesine bağlantı havuzu ile kapalı kullanın. Bağlantı bir havuzda toplanır, yalıtım düzeyiyle sıfırlama yalıtım düzeyi sunucuda sıfırlanmaz. Sonuç olarak, kendi yalıtım düzeyleri, havuza alınmış bağlantı kümesi ile aynı havuza alınmış iç bağlantısı kullanmak daha sonraki bağlantılar başlatın. Bağlantı havuzu kapalı kapatma açıkça her bağlantı için yalıtım düzeyini ayarlamak için alternatiftir.  
  
 [!code-csharp[DataWorks SnapshotIsolation.Demo#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.Demo/CS/source.cs#1)]
 [!code-vb[DataWorks SnapshotIsolation.Demo#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.Demo/VB/source.vb#1)]  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, veri değiştirildiğinde anlık görüntü yalıtımı davranışını gösterir. Kod, aşağıdaki eylemleri gerçekleştirir:  
  
-   Bağlandığı **AdventureWorks** örnek anlık görüntü yalıtımı veritabanı ve etkinleştirir.  
  
-   Adlı bir tablo oluşturur **TestSnapshotUpdate** ve örnek verileri üç satırı ekler.  
  
-   Başlar, ancak tamamlamaz, sqlTransaction1 anlık görüntü yalıtımı kullanma. Üç veri satırı, işlem sırasında seçilir.  
  
-   İkinci oluşturur **SqlConnection** için **AdventureWorks** ve güncelleştiren bir değer sqlTransaction1 Seçili satırlardan birinin READ COMMITTED yalıtım düzeyi kullanılarak ikinci bir işlem oluşturur.  
  
-   SqlTransaction2 kaydeder.  
  
-   Zaten bu sqlTransaction1 sqlTransaction1 ve aynı satırda güncelleştirme denemeleri döndürür. Hata 3960 tetiklenir ve sqlTransaction1 otomatik olarak geri alınır. **SqlException.Number** ve **SqlException.Message** konsol penceresinde görüntülenir.  
  
-   Anlık görüntü yalıtımı devre dışı bırakmak için temizleme kodu yürütür **AdventureWorks** ve silme **TestSnapshotUpdate** tablo.  
  
 [!code-csharp[DataWorks SnapshotIsolation.DemoUpdate#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.DemoUpdate/CS/source.cs#1)]
 [!code-vb[DataWorks SnapshotIsolation.DemoUpdate#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.DemoUpdate/VB/source.vb#1)]  
  
### <a name="using-lock-hints-with-snapshot-isolation"></a>Anlık görüntü yalıtımıyla kilit ipuçlarına kullanma  
 Önceki örnekte, ilk işlem, verileri seçer ve ilk işlemin tamamlanması açmadan önce ikinci bir hareket verileri ilk işlem aynı satırda güncelleştirmeye çalıştığında bir güncelleme çakışması neden güncelleştirir. İşlem başına kilit ipuçlarına sağlayarak uzun süre çalışan anlık işlemleri güncelleştirme çakışması olasılığını azaltabilirsiniz. Aşağıdaki SELECT deyimi, seçili satırları kilitlemek için UPDLOCK ipucu kullanır:  
  
```  
SELECT * FROM TestSnapshotUpdate WITH (UPDLOCK)   
  WHERE PriKey BETWEEN 1 AND 3  
```  
  
 İlk işlem tamamlanmadan önce satır güncelleştirilmeye çalışılıyor herhangi bir satır UPDLOCK kilit ipucuna bloğu kullanma. Bu işlem sırasında güncelleştirildiğinde seçilen satırları yok çakışması olmadığını güvence altına alır. "Kilit ipuçlarına" SQL Server Books Online'a bakın.  
  
 Uygulamanız çok sayıda çakışma varsa, anlık görüntü yalıtımı en iyi seçim olmayabilir. İpuçları, yalnızca gerçekten gerekli olduğunda kullanılmalıdır. Böylece kendi işlem için kilit ipuçlarına sürekli kullanır, uygulamanızın tasarlanmalıdır değil.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [SQL Server ve ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)  
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)

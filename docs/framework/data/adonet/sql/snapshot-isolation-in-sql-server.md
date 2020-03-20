---
title: SQL Server'da Anlık Görüntü Yalıtımı
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 43ae5dd3-50f5-43a8-8d01-e37a61664176
ms.openlocfilehash: 8313ffc8eef70c1e5efc24b09a160edb7cec1595
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174270"
---
# <a name="snapshot-isolation-in-sql-server"></a>SQL Server'da Anlık Görüntü Yalıtımı
Anlık görüntü yalıtımı OLTP uygulamaları için eşzamanlılığı artırır.  
  
## <a name="understanding-snapshot-isolation-and-row-versioning"></a>Anlık Görüntü Yalıtımı ve Satır Sürümünü Anlama  
 Anlık görüntü yalıtımı etkinleştirildikten sonra, her işlem için güncelleştirilmiş satır sürümleri korunmalıdır.  SQL Server 2019'dan önce bu sürümler **tempdb'de**depolandı. SQL Server 2019, kendi satır sürümlerini gerektiren hızlandırılmış Veritabanı Kurtarma (ADR) adlı yeni bir özelliği tanıttı.  Bu nedenle, SQL Server 2019 itibariyle, ADR etkin değilse, satır sürümleri her zaman olduğu gibi **tempdb** tutulur.  ADR etkinse, her ikisi de anlık görüntü yalıtımı ve ADR ile ilgili tüm satır sürümleri, kullanıcının belirttiği bir dosya grubunda kullanıcı veritabanında bulunan ADR'nin Kalıcı Sürüm Deposu'nda (PVS) tutulur. Benzersiz bir işlem sırası numarası her hareketi tanımlar ve bu benzersiz sayılar her satır sürümü için kaydedilir. Hareket, hareketin sıra numarasından önce sıra numarasına sahip en son satır sürümleriyle çalışır. Hareket başladıktan sonra oluşturulan yeni satır sürümleri hareket tarafından yoksayılır.  
  
 "Anlık görüntü" terimi, işlemdeki tüm sorguların, işlemin başladığı anda veritabanının durumuna bağlı olarak veritabanının aynı sürümünü veya anlık görüntüsünü gördüğü gerçeğini yansıtır. Anlık görüntü hareketindeki temel veri satırlarında veya veri sayfalarında kilit alınmaz ve bu da diğer işlemlerin daha önce tamamlanmamış bir işlem tarafından engellenmeden yürütülmesine izin verir. Verileri değiştiren hareketler, verileri okuyan hareketleri engellemez ve verileri okuyan hareketler, normalde SQL Server'da varsayılan READ COMMITTED yalıtım düzeyi altında olacağı için veri yazan hareketleri engellemez. Bu engellemeolmayan davranış, karmaşık hareketler için kilitlenme olasılığını da önemli ölçüde azaltır.  
  
 Anlık görüntü yalıtımı iyimser bir eşzamanlılık modeli kullanır. Anlık görüntü hareketi, işlem başladığından beri değişen verilerde değişiklik yapmaya çalışırsa, hareket geri döner ve bir hata yükselir. Verilere erişim sağlayan SELECT ifadeleri için UPDLOCK ipuçlarını kullanarak bunu önleyebilirsiniz. Daha fazla bilgi için SQL Server Books Online'da "İpuçlarını Kilitleme" başlıklı bilgi için bkz.  
  
 Anlık görüntü yalıtımı, işlemlerde kullanılmadan önce ALLOW_SNAPSHOT_ISOLATION ON veritabanı seçeneği ayarlayarak etkinleştirilmelidir. Bu, satır sürümlerini geçici veritabanında depolama mekanizmasını etkinleştirir **(tempdb).** Transact-SQL ALTER DATABASE deyimiyle kullanan her veritabanında anlık görüntü yalıtımını etkinleştirmeniz gerekir. Bu bağlamda, anlık görüntü yalıtımı, yapılandırma gerektirmeyen READ COMMITTED, REPEATABLE READ, SERIALIZABLE ve READ UNCOMMITTED'un geleneksel yalıtım düzeylerinden farklıdır. Aşağıdaki ifadeler anlık görüntü yalıtımını etkinleştirir ve varsayılan READ COMMITTED davranışını SNAPSHOT ile değiştirir:  
  
```sql  
ALTER DATABASE MyDatabase  
SET ALLOW_SNAPSHOT_ISOLATION ON  
  
ALTER DATABASE MyDatabase  
SET READ_COMMITTED_SNAPSHOT ON  
```  
  
 READ_COMMITTED_SNAPSHOT ON seçeneğinin ayarlanması, varsayılan READ COMMITTED yalıtım düzeyi altında sürümlenmiş satırlara erişim sağlar. READ_COMMITTED_SNAPSHOT seçeneği KAPALI olarak ayarlanmışsa, sürümlü satırlara erişmek için her oturum için Anlık Görüntü yalıtım düzeyini açıkça ayarlamanız gerekir.  
  
## <a name="managing-concurrency-with-isolation-levels"></a>Yalıtım Düzeyleri ile Eşzamanlılık Yönetimi  
 Transact-SQL deyiminin yürütüldettiği yalıtım düzeyi, kilitleme ve satır sürüm davranışını belirler. İzolasyon düzeyi bağlantı geniş bir kapsama sahiptir ve SET Hareket İzOLASYON DÜZEYİ deyimiyle bağlantı için ayarlandıktan sonra, bağlantı kapanana veya başka bir yalıtım düzeyi ayarlanana kadar etkin kalır. Bir bağlantı kapatıldığında ve havuza döndürüldüğünde, son SET İşlem İzOLASYON DÜZEYİ deyiminden yalıtım düzeyi korunur. Birleştirilmiş bağlantıyı yeniden kullanan sonraki bağlantılar, bağlantının biraraya bağlandığının etkisinde olan yalıtım düzeyini kullanır.  
  
 Bağlantı içinde verilen tek tek sorgular, tek bir deyim veya hareket için yalıtımı değiştiren ancak bağlantının yalıtım düzeyini etkilemeyen kilit ipuçları içerebilir. Depolanan yordamlar veya işlevlerde ayarlanan yalıtım düzeyleri veya kilit ipuçları, onları çağıran bağlantının yalıtım düzeyini değiştirmez ve yalnızca depolanan yordam veya işlev çağrısı süresince etkindir.  
  
 SQL-92 standardında tanımlanan dört yalıtım düzeyi, SQL Server'ın ilk sürümlerinde desteklenmiştir:  
  
- READ UNCOMMITTED, diğer hareketler tarafından yerleştirilen kilitleri yoksaydığından en az kısıtlayıcı yalıtım düzeyidir. READ UNCOMMITTED altında gerçekleştirilen işlemler, henüz diğer işlemler tarafından işlenmemiş değiştirilmiş veri değerlerini okuyabilir; bunlara "kirli" okur denir.  
  
- READ COMMITTED, SQL Server için varsayılan yalıtım düzeyidir. Deyimlerin değiştirilen ancak diğer işlemler tarafından henüz işlenemeyen veri değerlerini okuyamadığını belirterek kirli okumaları önler. Diğer işlemler, geçerli hareket içindeki tek tek ifadelerin yürütülmesi arasındaki verileri değiştirmeye, eklemeye veya silmeye devam ederek yinelenemeyen okumalarla veya "hayali" verilerle sonuçlanabilir.  
  
- TEKRAR EDIleBilen OKUMA, READ COMMITTED'dan daha kısıtlayıcı bir izolasyon düzeyidir. READ COMMITTED'ı kapsar ve ayrıca geçerli işlem işleyene kadar geçerli hareket tarafından okunan verileri değiştiremez veya silemez. Her bildirimin sonunda yayımlanacak işlem süresi boyunca paylaşılan kilitler tutulduğundan, eşzamanlılık READ COMMITTED'a göre daha düşüktür.  
  
- SERIALIZABLE en kısıtlayıcı yalıtım düzeyidir, çünkü tüm anahtar aralıklarını kilitler ve işlem tamamlanana kadar kilitleri tutar. TEKRARLANABILIR OKUMA'yı kapsar ve hareket tamamlanana kadar diğer işlemlerin hareket tarafından okunan aralıklara yeni satırlar ekleyememesi kısıtlamasını ekler.  
  
 Daha fazla bilgi için [İşlem Kilitleme ve Satır Sürüm Kılavuzu'na](/sql/relational-databases/sql-server-transaction-locking-and-row-versioning-guide)bakın.  
  
### <a name="snapshot-isolation-level-extensions"></a>Anlık Görüntü Yalıtım Düzey Uzantıları  
 SQL Server, SNAPSHOT yalıtım düzeyinin getirilmesi ve READ COMMITTED'ın ek bir uygulaması ile SQL-92 yalıtım düzeylerine uzantılar getirmiştir. READ_COMMITTED_SNAPSHOT yalıtım düzeyi, tüm işlemler için READ COMMITTED'ın yerini saydam olarak alabilir.  
  
- SNAPSHOT yalıtımı, bir hareket içinde okunan verilerin diğer eşzamanlı hareketler tarafından yapılan değişiklikleri asla yansıtmayacağını belirtir. Hareket, hareket başladığında var olan veri satırı sürümlerini kullanır. Okunduğunda verilere kilit yerleştirilmez, bu nedenle SNAPSHOT hareketleri diğer işlemlerin veri yazılmasına engel olmaz. Veri yazan hareketler anlık görüntü hareketlerinin veri okumalarını engellemez. Kullanmak için ALLOW_SNAPSHOT_ISOLATION veritabanı seçeneğini ayarlayarak anlık görüntü yalıtımını etkinleştirmeniz gerekir.  
  
- VeritabanıREAD_COMMITTED_SNAPSHOT seçeneği, veritabanında anlık görüntü yalıtımı etkinleştirildiğinde varsayılan READ COMMITTED yalıtım düzeyinin davranışını belirler. READ_COMMITTED_SNAPSHOT A'yı açıkça belirtmezseniz, READ COMMITTED tüm örtülü işlemlere uygulanır. Bu, READ_COMMITTED_SNAPSHOT OFF (varsayılan) olarak aynı davranışı üretir. READ_COMMITTED_SNAPSHOT KAPAİn yürürlüğe girdiğinde, Veritabanı Altyapısı varsayılan yalıtım düzeyini zorlamak için paylaşılan kilitleri kullanır. READ_COMMITTED_SNAPSHOT veritabanı seçeneğini ON olarak ayarlarsanız, veritabanı altyapısı verileri korumak için kilitkullanmak yerine satır sürüm ve anlık görüntü yalıtımını varsayılan olarak kullanır.  
  
## <a name="how-snapshot-isolation-and-row-versioning-work"></a>Anlık Görüntü Yalıtımı ve Satır Sürümleme Nasıl Çalışır?  
 Anlık görüntü yalıtım düzeyi etkinleştirildiğinde, her satır güncelleştirildiğinde, SQL Server Database Engine orijinal satırın bir kopyasını **tempdb'de**depolar ve satıra bir işlem sıra numarası ekler. Aşağıdaki olaylar dizisi oluşur:  
  
- Yeni bir işlem başlatıldı ve bir hareket sıra numarası atanır.  
  
- Veritabanı Altyapısı hareket içindeki bir satırı okur ve sıra numarası işlem sıra numarasına en yakın ve daha düşük olan **tempdb'den** satır sürümünü alır.  
  
- Veritabanı Altyapısı, anlık görüntü hareketi başlatıldığında, işlem sırası numarasının, anlık görüntü hareketi başlatıldığında etkin olan işlem sıra numaraları listesinde olup olmadığını denetler.  
  
- Hareket, hareketin başlangıcında geçerli olan **tempdb'den** satırın sürümünü okur. Bu sıra numarası değerleri hareket sıra numarasıdeğerinden daha yüksek olacağından, işlem başlatıldıktan sonra eklenen yeni satırları görmez.  
  
- **Tempdb'de** daha düşük sıra numarası değerine sahip bir satır sürümü olacağından, geçerli hareket, hareket başladıktan sonra silinen satırları görür.  
  
 Anlık görüntü yalıtımının net etkisi, işlemin tüm verileri işlemin başlangıcında var olduğu gibi, temel tablolara herhangi bir kilit koymadan görmesidir. Bu, çekişmenin olduğu durumlarda performans iyileştirmelerine neden olabilir.  
  
 Anlık görüntü hareketi her zaman iyimser eşzamanlılık denetimini kullanır ve diğer hareketlerin satırları güncelleştirmesini engelleyecek kilitleri stopajlar. Anlık görüntü hareketi, işlem başladıktan sonra değiştirilen bir satıra güncelleştirme ayırmaya çalışırsa, hareket geri alınır ve bir hata yükseltilir.  
  
## <a name="working-with-snapshot-isolation-in-adonet"></a>ADO.NET'da Anlık Görüntü Yalıtımı ile Çalışma  
 Anlık görüntü yalıtımı <xref:System.Data.SqlClient.SqlTransaction> sınıf tarafından ADO.NET olarak desteklenir. Anlık görüntü yalıtımı için bir veritabanı etkinleştirildiyse ancak READ_COMMITTED_SNAPSHOT A <xref:System.Data.SqlClient.SqlTransaction> için yapılandırılmamışsa, <xref:System.Data.SqlClient.SqlConnection.BeginTransaction%2A> yöntemi ararken **İzolasyon Düzeyi.Anlık Görüntü** numaralandırma değerini kullanarak başlatmanız gerekir. Bu kod parçası, bağlantının <xref:System.Data.SqlClient.SqlConnection> açık bir nesne olduğunu varsayar.  
  
```vb  
Dim sqlTran As SqlTransaction = _  
  connection.BeginTransaction(IsolationLevel.Snapshot)  
```  
  
```csharp  
SqlTransaction sqlTran =
  connection.BeginTransaction(IsolationLevel.Snapshot);  
```  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, kilitli verilere erişmeye çalışarak farklı yalıtım düzeylerinin nasıl çalıştığını gösterir ve üretim kodunda kullanılmak üzere tasarlanmamıştır.  
  
 Kod, SQL Server'daki **AdventureWorks** örnek veritabanına bağlanır ve **TestSnapshot** adında bir tablo oluşturur ve bir veri satırı ekler. Kod, veritabanı için anlık görüntü yalıtımını açmak için ALTER DATABASE Transact-SQL deyimini kullanır, ancak varsayılan READ COMMITTED yalıtım düzeyi davranışını etkin bırakarak READ_COMMITTED_SNAPSHOT seçeneğini ayarlamaz. Kod daha sonra aşağıdaki eylemleri gerçekleştirir:  
  
- Bir güncelleştirme hareketi başlatmak için SERIALIZABLE yalıtım düzeyini kullanan sqlTransaction1 başlar, ancak tamamlanmaz. Bu, tabloyu kilitleme etkisine sahiptir.  
  
- İkinci bir bağlantı açar ve **TestSnapshot** tablosundaki verileri okumak için SNAPSHOT yalıtım düzeyini kullanarak ikinci bir işlem başlatır. Anlık görüntü yalıtımı etkin olduğundan, bu işlem sqlTransaction1 başlamadan önce var olan verileri okuyabilir.  
  
- Üçüncü bir bağlantı açar ve tablodaki verileri okumaya çalışmak için READ COMMITTED yalıtım düzeyini kullanarak bir işlem başlatır. Bu durumda, ilk işlemde tabloya yerleştirilen kilitleri ve saatleri okuyamadığı için kod verileri okuyamaz. Bu yalıtım düzeyleri de ilk işlemde yerleştirilen kilitleri geçmiş okuyamaz çünkü TEKRAREDİlEBILEN READ ve SERIALIZABLE izolasyon düzeyleri kullanılırsa aynı sonuç oluşur.  
  
- Dördüncü bir bağlantı açar ve sqlTransaction1'de işlenmemiş değerin kirli bir okumasını gerçekleştiren READ UNCOMMITTED yalıtım düzeyini kullanarak bir işlem başlatır. İlk işlem taahhüt edilmezse, bu değer veritabanında hiçbir zaman var olmayabilir.  
  
- İlk işlemi geri alır ve **TestSnapshot** tablosunu silerek ve **AdventureWorks** veritabanı için anlık görüntü yalıtımını kapatarak temizler.  
  
> [!NOTE]
> Aşağıdaki örneklerde bağlantı havuzu kapalı aynı bağlantı dizesini kullanın. Bir bağlantı birleştirilmişse, yalıtım düzeyini sıfırlamak sunucudaki yalıtım düzeyini sıfırlamaz. Sonuç olarak, aynı havuzlu iç bağlantıyı kullanan sonraki bağlantılar, yalıtım düzeylerinin birleştirilmiş bağlantınınkine göre ayarlanmasıyla başlar. Bağlantı birleştirmeyi kapatmanın alternatifi, her bağlantı için yalıtım düzeyini açıkça ayarlamaktır.  
  
 [!code-csharp[DataWorks SnapshotIsolation.Demo#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.Demo/CS/source.cs#1)]
 [!code-vb[DataWorks SnapshotIsolation.Demo#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.Demo/VB/source.vb#1)]  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, veriler değiştirilirken anlık görüntü yalıtımı davranışını gösterir. Kod aşağıdaki eylemleri gerçekleştirir:  
  
- **AdventureWorks** örnek veritabanına bağlanır ve SNAPSHOT yalıtımı sağlar.  
  
- **TestSnapshotUpdate** adında bir tablo oluşturur ve üç örnek veri satırı ekler.  
  
- Snapshot yalıtımı kullanarak sqlTransaction1 başlar, ancak tamamlanmaz. Harekette üç veri satırı seçilir.  
  
- **AdventureWorks'e** ikinci bir **SqlConnection** oluşturur ve sqlTransaction1'de seçilen satırlardan birinde bir değeri güncelleştiren READ COMMITTED yalıtım düzeyini kullanarak ikinci bir işlem oluşturur.  
  
- sqlTransaction2'yi işler.  
  
- sqlTransaction1'e döner ve sqlTransaction1'in zaten işlediği aynı satırı güncelleştirmeye çalışır. Hata 3960 yükseltilir ve sqlTransaction1 otomatik olarak geri alınır. **SqlException.Number** ve **SqlException.Message** Konsol penceresinde görüntülenir.  
  
- **AdventureWorks'te** anlık görüntü yalıtımını kapatmak ve **TestSnapshotUpdate** tablosunu silmek için temizleme kodunu yürütür.  
  
 [!code-csharp[DataWorks SnapshotIsolation.DemoUpdate#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.DemoUpdate/CS/source.cs#1)]
 [!code-vb[DataWorks SnapshotIsolation.DemoUpdate#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.DemoUpdate/VB/source.vb#1)]  
  
### <a name="using-lock-hints-with-snapshot-isolation"></a>Anlık Görüntü Yalıtımı ile Kilit İpuçları kullanma  
 Önceki örnekte, ilk işlem verileri seçer ve ilk işlem tamamlanmadan önce ikinci bir işlem verileri güncelleştirir ve ilk işlem aynı satırı güncelleştirmeye çalıştığında güncelleştirme çakışmasına neden olur. İşlemin başında kilit ipuçları sağlayarak uzun süren anlık görüntü işlemlerinde çakışmaları güncelleştirme olasılığını azaltabilirsiniz. Aşağıdaki SELECT deyimi, seçili satırları kilitlemek için UPDLOCK ipucunu kullanır:  
  
```sql  
SELECT * FROM TestSnapshotUpdate WITH (UPDLOCK)
  WHERE PriKey BETWEEN 1 AND 3  
```  
  
 UPDLOCK kilit ipucunu kullanarak, ilk işlem tamamlanmadan önce satırları güncelleştirmeye çalışan satırları engeller. Bu, seçili satırların daha sonra işlemde güncelleştirildiğinde çakışma olmamasını garanti eder. SQL Server Books Online'da "İpuçlarını Kilitleme" başlıklı bünyeye bakın.  
  
 Uygulamanızda çok sayıda çakışma varsa, anlık görüntü yalıtımı en iyi seçim olmayabilir. İpuçları sadece gerçekten gerektiğinde kullanılmalıdır. Uygulamanız, sürekli olarak çalışması için kilit ipuçlarına dayanacak şekilde tasarlanmamalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SQL Server ve ADO.NET](index.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
- [İşlem Kilitleme ve Satır Sürüm Kılavuzu](/sql/relational-databases/sql-server-transaction-locking-and-row-versioning-guide)

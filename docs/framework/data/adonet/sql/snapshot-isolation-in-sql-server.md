---
title: SQL Server'da Anlık Görüntü Yalıtımı
description: SQL Server ' de anlık görüntü yalıtımı ve satır sürümü oluşturma hakkında bir genel bakış okuyun ve yalıtım düzeyleriyle eşzamanlılık yönetimi hakkında bilgi edinin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 43ae5dd3-50f5-43a8-8d01-e37a61664176
ms.openlocfilehash: 4934c031eb9dfb26d60c5233937cbc65ca60d4f7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183084"
---
# <a name="snapshot-isolation-in-sql-server"></a>SQL Server'da Anlık Görüntü Yalıtımı

Anlık görüntü yalıtımı OLTP uygulamaları için eşzamanlılık geliştirir.  
  
## <a name="understanding-snapshot-isolation-and-row-versioning"></a>Anlık görüntü yalıtımını ve satır sürüm oluşturmayı anlama  

 Anlık görüntü yalıtımı etkinleştirildikten sonra, her bir işlem için güncelleştirilmiş satır sürümlerinin tutulması gerekir.  SQL Server 2019 ' dan önce bu sürümler **tempdb**'de depolandı. SQL Server 2019, kendi satır sürümleri kümesini gerektiren hızlandırılmış veritabanı kurtarma (ADR) özelliğine sahip yeni bir özellik sunar.  Bu nedenle, SQL Server 2019 itibariyle, ADR etkinleştirilmemişse, satır sürümleri **tempdb** 'de her zaman olarak tutulur.  ADR etkinse, hem anlık görüntü yalıtımı hem de ADR ile ilgili tüm satır sürümleri, kullanıcının belirttiği bir dosya grubunda bulunan Kullanıcı veritabanında bulunan ADR 'nin kalıcı sürüm deposunda (PVS) tutulur. Benzersiz bir işlem sıra numarası her bir işlemi tanımlar ve bu benzersiz numaralar her bir satır sürümü için kaydedilir. İşlem, işlemin sıra numarasından önce sıra numarası olan en son satır sürümleriyle birlikte kullanılabilir. İşlem başladıktan sonra oluşturulan daha yeni satır sürümleri işlem tarafından yok sayılır.  
  
 "Snapshot" terimi, işlemdeki tüm sorguların, işlem başladığında veritabanının durumuna bağlı olarak veritabanının aynı sürümünü veya anlık görüntüsünü görmesinin gerçeğini yansıtır. Bir anlık görüntü işleminde temel alınan veri satırlarında veya veri sayfalarında hiçbir kilit alınmadı. Bu, diğer işlemlerin önceki bir tamamlanmamış işlem tarafından engellenmeden yürütülmesine izin verir. Verileri değiştiren işlemler, verileri okuyan işlemleri engellemez ve verileri okuyan işlemler, normalde SQL Server ' de varsayılan okuma olarak KAYDEDILMIŞ yalıtım düzeyi altında olacak şekilde veri yazan işlemleri engellemez. Bu engelleyici olmayan davranış, karmaşık işlemler için kilitlenmeleri olasılığını önemli ölçüde azaltır.  
  
 Anlık görüntü yalıtımı bir iyimser eşzamanlılık modeli kullanır. Anlık görüntü işlemi, işlem başlangıcından bu yana değiştirilen verilerde yapılan değişiklikleri kaydetmeye çalışırsa, işlem geri alınacaktır ve bir hata oluşur. Bu, değiştirilecek verilere erişen SELECT deyimleri için UPDLOCK ipuçlarını kullanarak bunu önleyebilirsiniz. Daha fazla bilgi için SQL Server Books Online 'da "kilitleme Ipuçları" bölümüne bakın.  
  
 İşlem sırasında kullanılmadan önce veritabanı seçeneği ALLOW_SNAPSHOT_ISOLATION ayarlanarak anlık görüntü yalıtımının etkinleştirilmesi gerekir. Bu, satır sürümlerini geçici veritabanında (**tempdb**) depolamaya yönelik mekanizmayı etkinleştirir. Transact-SQL ALTER DATABASE ifadesiyle kullanan her veritabanında anlık görüntü yalıtımını etkinleştirmeniz gerekir. Bu şekilde, anlık görüntü yalıtımı, hiçbir yapılandırma gerektirmeyen READ COMMITTED, YINELENEBILIR READ, SERIALIZABLE ve READ UNCOMMıTTED olan geleneksel yalıtım düzeylerinden farklıdır. Aşağıdaki deyimler anlık görüntü yalıtımını etkinleştirir ve varsayılan okuma KAYDEDILMIŞ davranışını anlık GÖRÜNTÜYLE değiştirir:  
  
```sql  
ALTER DATABASE MyDatabase  
SET ALLOW_SNAPSHOT_ISOLATION ON  
  
ALTER DATABASE MyDatabase  
SET READ_COMMITTED_SNAPSHOT ON  
```  
  
 READ_COMMITTED_SNAPSHOT ON seçeneğinin ayarlanması, varsayılan olarak KAYDEDILMIŞ yalıtım düzeyi altında sürümlü satırlara erişim sağlar. READ_COMMITTED_SNAPSHOT seçeneği kapalı olarak ayarlanırsa, sürümlü satırlara erişebilmek için her oturum için anlık görüntü yalıtımı düzeyini açıkça ayarlamanız gerekir.  
  
## <a name="managing-concurrency-with-isolation-levels"></a>Yalıtım düzeyleriyle eşzamanlılık yönetimi  

 Bir Transact-SQL ifadesinin çalıştırıldığı yalıtım düzeyi, kilitleme ve satır sürümü oluşturma davranışını belirler. Yalıtım düzeyi, bağlantı genelinde kapsama sahiptir ve Işlem yalıtım DÜZEYI ayarla ifadesiyle bir bağlantı için ayarlandıktan sonra bağlantı kapatılana veya başka bir yalıtım düzeyi ayarlanana kadar etkin kalır. Bir bağlantı kapatılıp havuza döndürüldüğünde, son ayarlanan Işlem yalıtım DÜZEYI deyimindeki yalıtım düzeyi korunur. Havuza alınmış bir bağlantıyı yeniden kullanan sonraki bağlantılar, bağlantı havuza alındığı sırada geçerli olan yalıtım düzeyini kullanır.  
  
 Bir bağlantı içinde verilen tekil sorgular, tek bir deyimin veya işlemin yalıtımını değiştiren ancak bağlantının yalıtım düzeyini etkilemeyen kilit ipuçları içerebilir. Saklı yordamlarda veya işlevlerde ayarlanan yalıtım düzeyleri veya kilit ipuçları, bunları çağıran bağlantının yalıtım düzeyini değiştirmez ve yalnızca saklı yordamın veya işlev çağrısının süresi boyunca geçerli olur.  
  
 SQL Server önceki sürümlerinde SQL-92 standardında tanımlanan dört yalıtım düzeyi desteklenmekteydi:  
  
- Diğer işlemler tarafından verilen kilitleri yoksaydığından, READ UNCOMMıTTED, en az kısıtlayıcı yalıtım düzeyidir. READ UNCOMMıTTED altında yürütülen işlemler, başka işlemler tarafından henüz kaydedilmemiş olan değiştirilmiş veri değerlerini okuyabilir; Bunlar "kirli" okumalar olarak adlandırılır.  
  
- OKUMA IŞLENDI, SQL Server için varsayılan yalıtım düzeyidir. Bu ifadeler, değiştirilmiş ancak başka işlemler tarafından henüz kaydedilmemiş olan veri değerlerini okuyamayacağını belirterek kirli okumaları önler. Diğer işlemler, geçerli işlem içindeki tek tek deyimlerin yürütmeleri arasında verileri değiştirebilir, ekleyebilir veya silebilir, bu da yinelenmemiş okuma veya "hayalet" verileri elde eder.  
  
- YINELENEBILIR okuma, okuma IŞLENDI öğesinden daha kısıtlayıcı bir yalıtım düzeyidir. Bu, okumayı taahhüt eder ve ayrıca, geçerli işlem tamamlanana kadar geçerli işlem tarafından okunan verileri başka hiçbir işlem tarafından değişiklik veya silme işlemini belirtir. Okuma verilerinde paylaşılan kilitler, her deyimin sonunda yayınlanmak yerine işlem süresince tutulduğundan eşzamanlılık, okuma için daha düşüktür.  
  
- SERI hale GETIRILEBILIR, tüm anahtar aralıklarını kilitlediği ve işlem tamamlanana kadar kilitleri tutan için en kısıtlayıcı yalıtım düzeyidir. YINELENEBILIR okumayı kapsar ve diğer işlemlerin işlem tamamlanana kadar işlem tarafından okunan aralıklara yeni satırlar Ekleyememe kısıtlaması ekler.  
  
 Daha fazla bilgi için, [Işlem kilitleme ve satır sürümü oluşturma kılavuzuna](/sql/relational-databases/sql-server-transaction-locking-and-row-versioning-guide)bakın.  
  
### <a name="snapshot-isolation-level-extensions"></a>Anlık görüntü yalıtım düzeyi uzantıları  

 SQL Server, SQL-92 yalıtım düzeylerine, anlık görüntü yalıtım düzeyi ve daha fazla READ COMMıTTED bir uygulama ile sunulan uzantıları sunmuştur. READ_COMMITTED_SNAPSHOT yalıtım düzeyi, tüm işlemler için OKUNABILIR olarak IŞLENMIŞ şekilde değiştirebilir.  
  
- ANLıK görüntü yalıtımı, bir işlem içinde okunan verilerin diğer eşzamanlı işlemler tarafından yapılan değişiklikleri hiçbir şekilde yansıtmayacağını belirtir. İşlem başladığında mevcut olan veri satırı sürümlerini kullanır. Okuma sırasında verileri hiçbir kilit yerleştirmez, bu nedenle anlık görüntü işlemleri diğer işlemlerin veri yazmasını engellemez. Veri yazan işlemler, anlık görüntü işlemlerini veri okumaktan engellemez. ALLOW_SNAPSHOT_ISOLATION veritabanı seçeneğini kullanmak için ayarlayarak anlık görüntü yalıtımını etkinleştirmeniz gerekir.  
  
- READ_COMMITTED_SNAPSHOT veritabanı seçeneği, anlık görüntü yalıtımı bir veritabanında etkinleştirildiğinde varsayılan okuma tarafından KAYDEDILMIŞ yalıtım düzeyinin davranışını belirler. Açık olarak READ_COMMITTED_SNAPSHOT açık bir şekilde belirtmezseniz, tüm örtük işlemlere okuma işlemi uygulanır. Bu, READ_COMMITTED_SNAPSHOT OFF (varsayılan) ayarıyla aynı davranışı üretir. READ_COMMITTED_SNAPSHOT OFF etkin olduğunda, veritabanı altyapısı varsayılan yalıtım düzeyini zorlamak için paylaşılan kilitler kullanır. READ_COMMITTED_SNAPSHOT veritabanı seçeneğini açık olarak ayarlarsanız, veritabanı altyapısı, verileri korumak için kilitler kullanmak yerine varsayılan olarak satır sürümü oluşturma ve anlık görüntü yalıtımı kullanır.  
  
## <a name="how-snapshot-isolation-and-row-versioning-work"></a>Anlık görüntü yalıtımı ve satır sürümü oluşturma nasıl çalışır?  

 ANLıK görüntü yalıtım düzeyi etkinleştirildiğinde, bir satır her güncelleştirildiği zaman, SQL Server veritabanı altyapısı **tempdb**'de orijinal satırın bir kopyasını depolar ve satıra bir işlem sıra numarası ekler. Oluşan olayların sırası aşağıda verilmiştir:  
  
- Yeni bir işlem başlatılır ve bir işlem sıra numarası atanır.  
  
- Veritabanı altyapısı, işlem içindeki bir satırı okur ve sıra numarası en yakın, işlem sırası numarasından daha düşük olan **tempdb** 'den satır sürümünü alır.  
  
- Veritabanı altyapısı, işlem sırası numarasının, anlık görüntü işlemi başlatıldığında etkin olan kaydedilmemiş işlemlerin işlem sırası numaraları listesinde olup olmadığını denetler.  
  
- İşlem, işlemin başlangıcı itibariyle geçerli olan **tempdb** 'den satır sürümünü okur. İşlem başlatıldıktan sonra yeni satırları, bu sıra numarası değerleri işlem sırası numarası değerinden yüksek olacak şekilde görmez.  
  
- Geçerli işlem, **tempdb** 'de daha düşük bir sıra numarası değeri olan bir satır sürümü olacağı için, işlem başladıktan sonra silinen satırları görür.  
  
 Anlık görüntü yalıtımının net etkisi, işlemin başlangıcında olduğu gibi, temel alınan tablolara herhangi bir kilit oluşturmadan veya yerleştirmeksizin tüm verileri görür. Bu durum, çekişme durumunda performans iyileştirmelerine yol açabilir.  
  
 Anlık görüntü işlemi her zaman iyimser eşzamanlılık denetimini kullanır ve diğer işlemlerin satırları güncelleştirmesini engelleyecek herhangi bir kilidi stopajın. Anlık görüntü işlemi, işlem başladıktan sonra değiştirilen bir satıra bir güncelleştirmeyi kaydetmeye çalışırsa, işlem geri alınır ve bir hata oluşur.  
  
## <a name="working-with-snapshot-isolation-in-adonet"></a>ADO.NET içinde anlık görüntü yalıtımıyla çalışma  

 Anlık görüntü yalıtımı, ADO.NET tarafından sınıfı tarafından desteklenir <xref:System.Data.SqlClient.SqlTransaction> . Bir veritabanı, anlık görüntü yalıtımı için etkinleştirildiyse, ancak ÜZERINDE READ_COMMITTED_SNAPSHOT için yapılandırılmamışsa, <xref:System.Data.SqlClient.SqlTransaction> yöntemi çağırırken **IsolationLevel. Snapshot** numaralandırma değerini kullanarak bir ' u başlatmanız gerekir <xref:System.Data.SqlClient.SqlConnection.BeginTransaction%2A> . Bu kod parçası, bağlantının açık bir nesne olduğunu varsayar <xref:System.Data.SqlClient.SqlConnection> .  
  
```vb  
Dim sqlTran As SqlTransaction = _  
  connection.BeginTransaction(IsolationLevel.Snapshot)  
```  
  
```csharp  
SqlTransaction sqlTran =
  connection.BeginTransaction(IsolationLevel.Snapshot);  
```  
  
### <a name="example"></a>Örnek  

 Aşağıdaki örnek, kilitli verilere erişmeye çalışan farklı yalıtım düzeylerinin nasıl davrandığını gösterir ve üretim kodunda kullanılmak üzere tasarlanmamıştır.  
  
 Kod, SQL Server **AdventureWorks** örnek veritabanına bağlanır ve **TestSnapshot** adlı bir tablo oluşturur ve bir veri satırı ekler. Kod ALTER DATABASE Transact-SQL deyimini kullanarak veritabanı için anlık görüntü yalıtımını açabilir, ancak READ_COMMITTED_SNAPSHOT seçeneğini ayarlayıp varsayılan olarak KAYDEDILMIŞ yalıtım düzeyi davranışını etkin halde bırakır. Kod daha sonra aşağıdaki eylemleri gerçekleştirir:  
  
- Bir güncelleştirme işlemini başlatmak için, SERI hale GETIRILEBILIR yalıtım düzeyini kullanan, ancak tamamlanmayan, sqlTransaction1. Bu, tabloyu kilitleme etkisine sahiptir.  
  
- İkinci bir bağlantı açar ve **TestSnapshot** tablosu içindeki verileri okumak IÇIN anlık görüntü yalıtımı düzeyini kullanarak ikinci bir işlem başlatır. Anlık görüntü yalıtımı etkinleştirildiğinden, bu işlem sqlTransaction1 başlamadan önce var olan verileri okuyabilir.  
  
- Üçüncü bir bağlantı açar ve tablodaki verileri okumayı denemek için READ COMMıTTED yalıtım düzeyini kullanarak bir işlem başlatır. Bu durumda, kod ilk işlem içindeki tabloya yerleştirilmiş kilitleri okuyamadığından ve zaman aşımına uğradığından verileri okuyamıyor. Aynı sonuç, YINELENEBILIR okuma ve SERI hale GETIRILEBILIR yalıtım düzeyleri kullanılmışsa meydana gelir çünkü bu yalıtım düzeyleri ilk işleme yerleştirilmiş kilitleri daha fazla okuyamaz.  
  
- Dördüncü bir bağlantı açar ve sqlTransaction1 içinde işlenmemiş değerin kirli okunduğunu gerçekleştiren READ UNCOMMıTTED yalıtım düzeyini kullanarak bir işlem başlatır. İlk işlem yürütülmüyorsa, bu değer veritabanında hiçbir şekilde yok olabilir.  
  
- İlk işlemi geri alır ve **TestSnapshot** tablosunu silerek ve **AdventureWorks** veritabanı için anlık görüntü yalıtımını kapatarak temizler.  
  
> [!NOTE]
> Aşağıdaki örnekler, bağlantı havuzu kapalıyken aynı bağlantı dizesini kullanır. Bir bağlantı havuza alınmış ise, yalıtım düzeyini sıfırlamak sunucudaki yalıtım düzeyini sıfırlamaz. Sonuç olarak, aynı havuza alınmış iç bağlantıyı kullanan sonraki bağlantılar, havuza alınmış bağlantının kendilerine ayarlanan yalıtım düzeyleriyle başlar. Bağlantı havuzunu kapatmak için bir alternatif, yalıtım düzeyini her bağlantı için açıkça ayarlamaya yöneliktir.  
  
 [!code-csharp[DataWorks SnapshotIsolation.Demo#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.Demo/CS/source.cs#1)]
 [!code-vb[DataWorks SnapshotIsolation.Demo#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.Demo/VB/source.vb#1)]  
  
### <a name="example"></a>Örnek  

 Aşağıdaki örnek, veri değiştirilirken anlık görüntü yalıtımının davranışını gösterir. Kod aşağıdaki eylemleri gerçekleştirir:  
  
- **AdventureWorks** örnek veritabanına BAĞLANıR ve anlık görüntü yalıtımına olanak sağlar.  
  
- **TestSnapshotUpdate** adlı bir tablo oluşturur ve üç satır örnek veri ekler.  
  
- ANLıK görüntü yalıtımı kullanarak sqlTransaction1 başlar ancak tamamlanmaz. İşlemde üç satır veri seçilir.  
  
- **AdventureWorks** 'e Ikinci bir **SqlConnection** oluşturur ve sqlTransaction1 içinde seçilen satırlardan BIRINDEKI BIR değeri güncelleştiren Read commıtted yalıtım düzeyini kullanarak ikinci bir işlem oluşturur.  
  
- Yürütmeler sqlTransaction2.  
  
- SqlTransaction1 ' e döner ve sqlTransaction1 'in zaten yürütüldüğü satırı güncelleştirme girişiminde bulunur. Hata 3960 tetiklenir ve sqlTransaction1 otomatik olarak geri alınır. **SqlException. Number** ve **SqlException. Message** konsol penceresinde görüntülenir.  
  
- **AdventureWorks** 'te anlık görüntü yalıtımını devre dışı bırakmak ve **TestSnapshotUpdate** tablosunu silmek için Temizleme kodunu yürütür.  
  
 [!code-csharp[DataWorks SnapshotIsolation.DemoUpdate#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.DemoUpdate/CS/source.cs#1)]
 [!code-vb[DataWorks SnapshotIsolation.DemoUpdate#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.DemoUpdate/VB/source.vb#1)]  
  
### <a name="using-lock-hints-with-snapshot-isolation"></a>Anlık görüntü yalıtımıyla kilit Ipuçlarını kullanma  

 Önceki örnekte, ilk işlem verileri seçer ve ikinci bir işlem ilk işlem tamamlanmadan önce verileri güncelleştirir, ilk işlem aynı satırı güncelleştirmeye çalıştığında güncelleştirme çakışmasına neden olur. İşlemin başlangıcında kilit ipuçları sağlayarak uzun süre çalışan anlık görüntü işlemlerinde güncelleştirme çakışmalarının olasılığını azaltabilirsiniz. Aşağıdaki SELECT deyimleri, seçili satırları kilitlemek için UPDLOCK ipucunu kullanır:  
  
```sql  
SELECT * FROM TestSnapshotUpdate WITH (UPDLOCK)
  WHERE PriKey BETWEEN 1 AND 3  
```  
  
 UPDLOCK kilit ipucu kullanımı, ilk işlem tamamlanmadan önce satırları güncelleştirmeye çalışan tüm satırları engeller. Bu, seçili satırların işlemde daha sonra güncellendiklerinde hiçbir çakışma olmadığından emin olmasını sağlar. SQL Server Books Online 'da "kilitleme Ipuçları" bölümüne bakın.  
  
 Uygulamanızda çok fazla çakışma varsa, anlık görüntü yalıtımı en iyi seçim olmayabilir. İpuçları yalnızca gerçekten gerektiğinde kullanılmalıdır. Uygulamanız, işlem için kilit ipuçlarına sürekli olarak dayanmasını sağlayacak şekilde tasarlanmamalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SQL Server ve ADO.NET](index.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
- [İşlem kilitleme ve satır sürümü oluşturma kılavuzu](/sql/relational-databases/sql-server-transaction-locking-and-row-versioning-guide)

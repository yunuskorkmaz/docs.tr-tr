---
title: "SQL Server'da anlık görüntü yalıtımı"
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
ms.assetid: 43ae5dd3-50f5-43a8-8d01-e37a61664176
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: f7353ecd6f4e2db60db1c77c7771af43d68be760
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="snapshot-isolation-in-sql-server"></a>SQL Server'da anlık görüntü yalıtımı
Anlık görüntü yalıtımı OLTP uygulamalar için eşzamanlılık geliştirir.  
  
## <a name="understanding-snapshot-isolation-and-row-versioning"></a>Anlık görüntü yalıtımı ve satır sürüm anlama  
 Anlık görüntü yalıtımı etkinleştirildiğinde, her işlem için güncelleştirilmiş satır sürümleri içinde korunur **tempdb**. Her işlem benzersiz işlem sırası numarası tanımlar ve bu benzersiz numaraları her satır sürümü için kaydedilir. İşlem, işlem sırası sayısı önce sıra numarasına sahip en son satır sürümleri ile çalışır. İşlem başladıktan sonra oluşturulan yeni satır sürümleri işlem tarafından göz ardı edilir.  
  
 "Anlık görüntü" terimi işlemdeki tüm sorgular aynı sürüm veya anda işlem başladığı veritabanının durumuna bağlı veritabanının anlık görüntü bakın olgu yansıtır. Temel alınan veri satırları veya veri sayfaları önceki tamamlanmamış bir işlem tarafından engellenen olmadan yürütmek için diğer işlemleri izin veren bir anlık görüntü işlemde alınan kilit yok. Verileri değiştirme işlemleri veri okuma işlemleri engellemez ve bunlar varsayılan READ COMMITTED yalıtım düzeyi SQL Server'ın altında normalde yaptığınız gibi veri okuma işlemleri veri yazma işlemleri engellemez. Engelleyici olmayan bu davranış, ayrıca önemli ölçüde kilitlenmeleri karmaşık işlemleri için olasılığını azaltır.  
  
 Anlık görüntü yalıtımı iyimser eşzamanlılık modeli kullanır. İşlemin başlamasından bu yana değişti veri değişiklikleri gerçekleştirmek bir anlık görüntü işlemi çalışırsa, işlem döndürülmesine neden olur ve bir hata oluşur. Bu, değiştirilecek verilere erişmek için SELECT deyimleri UPDLOCK ipuçlarını kullanarak önleyebilirsiniz. SQL Server Books Online'da "kilitleme ipuçları" daha fazla bilgi için bkz.  
  
 Anlık görüntü yalıtımı işlemlerinde kullanılmadan önce allow_snapshot_ısolatıon açık veritabanı seçeneğini ayarlayarak etkinleştirilmesi gerekir. Bu geçici bir veritabanında satır sürümlerini depolamak için mekanizması etkinleştirir (**tempdb**). İle Transact-SQL ALTER DATABASE deyimini kullanan her veritabanında anlık görüntü yalıtımını etkinleştirmeniz gerekir. Bu bakımdan, anlık görüntü yalıtımı READ COMMITTED, REPEATABLE READ, seri hale GETİRİLEBİLİR ve READ UNCOMMITTED yapılandırma gerektiren geleneksel yalıtım düzeyi arasından farklıdır. Aşağıdaki deyimleri anlık görüntü yalıtımını etkinleştirmeniz ve READ COMMITTED varsayılan davranışı anlık görüntü ile değiştirin:  
  
```  
ALTER DATABASE MyDatabase  
SET ALLOW_SNAPSHOT_ISOLATION ON  
  
ALTER DATABASE MyDatabase  
SET READ_COMMITTED_SNAPSHOT ON  
```  
  
 Read_commıtted_snapshot ON seçeneği varsayılan READ COMMITTED yalıtım düzeyi altında sürümlü satır erişmesini sağlar. Read_commıtted_snapshot seçeneği OFF olarak ayarlarsanız, her oturum için anlık görüntü yalıtım düzeyi sürümlü satır erişmek için açıkça ayarlamanız gerekir.  
  
## <a name="managing-concurrency-with-isolation-levels"></a>Eşzamanlılık yalıtım düzeyi ile yönetme  
 Altında bir Transact-SQL deyimini yürütür yalıtım düzeyi kilitleme ve satır sürüm davranışını belirler. Bir yalıtım düzeyi bağlantı genelinde kapsama sahip ve işlem YALITIM düzeyi AYARLANAN ifadesiyle bağlantı ayarlandıktan etkin bağlantı kapalı veya başka bir yalıtım düzeyi kadar kalır. Bir bağlantı kapatılır ve havuza geri döner etkinleştirildiğinde, son işlem YALITIM düzeyi AYARLANAN deyimden yalıtım düzeyi korunur. Sonraki bağlantılar yürürlükte olan zaman bağlantısı yalıtım düzeyi havuza alınmış bir havuza alınan bağlantı kullanımı yeniden kullanma.  
  
 İçinde bir bağlantı verilen tek tek sorguları, tek bir deyimde veya işlem yalıtımını değiştirir, ancak bağlantı yalıtım düzeyini etkilemez kilit ipuçlarına içerebilir. Yalıtım düzeylerinde veya kilit ipuçlarına saklı yordamlarda ayarlayın veya İşlevler onları çağıran bağlantının yalıtım düzeyi değiştirmeyin ve yalnızca saklı yordam veya işlev çağrısı süresince etkindir.  
  
 SQL-92 standardında tanımlanan dört yalıtım düzeyi erken SQL Server'ın sürümlerinde desteklenen:  
  
-   Diğer işlemler tarafından yerleştirilen kilitleri yok sayar READ UNCOMMITTED yalıtım düzeyini en az kısıtlayıcı olmasıdır. READ UNCOMMITTED altında yürütülen işlemler henüz diğer işlemler tarafından taahhüt değil değiştirilmiş veri değerleri okuyabilirsiniz. Bunlar, "kirli" okuma olarak adlandırılır.  
  
-   READ COMMITTED SQL Server için varsayılan yalıtım düzeyi olur. Kirli okuma deyimleri değiştirildi, ancak henüz diğer işlemler tarafından yürütülen veri değerleri okunamıyor belirterek engeller. Hala diğer işlemleri değiştirmek, eklemek veya tek tek deyimleri geçerli işlem tekrarlanabilir olmayan okuma veya "hayalet" veri kaynaklanan içinde yürütmeleri arasında verileri silme.  
  
-   REPEATABLE READ READ COMMITTED daha daha kısıtlayıcı bir yalıtım düzeyi değil. READ COMMITTED kapsar ve ayrıca başka bir işlem değiştirin veya geçerli işlem tamamlandıktan kadar geçerli hareket tarafından okunur verilerini silmek belirtir. Eşzamanlılık okuma KAYDEDİLEN değerinden daha düşük olduğundan veri okuma paylaşılan kilit her deyimi sonunda yayımlanan yerine işlem boyunca tutulur.  
  
-   Anahtarların tüm aralıkları kilitler ve işlem tamamlanana kadar kilitler tutan en kısıtlayıcı yalıtım düzeyi seri hale GETİRİLEBİLİR olmasıdır. YİNELENEBİLİR okuma kapsar ve diğer işlemleri yeni satırlar işlem tamamlanana kadar işlem tarafından okuma aralıkları INSERT yapılamıyor kısıtlama ekler.  
  
 Daha fazla bilgi için SQL Server Books Online'da "yalıtım düzeyi" konusuna bakın.  
  
### <a name="snapshot-isolation-level-extensions"></a>Anlık görüntü yalıtım düzeyi uzantıları  
 SQL Server Uzantıları anlık görüntü yalıtım düzeyi giriş ve ek READ COMMITTED uygulaması ile SQL 92 yalıtım düzeyi kullanıma sunuldu. Read_commıtted_snapshot yalıtım düzeyi saydam READ COMMITTED tüm işlemler için değiştirebilirsiniz.  
  
-   Anlık görüntü yalıtımı, bir işlem içinde okunan veriler hiçbir zaman eş zamanlı başka işlemler tarafından yapılan değişiklikleri yansıtacak belirtir. İşlem, işlem başladığında, mevcut veri satır sürümleri kullanır. Okunduğunda, anlık işlemleri verileri yazmasını diğer işlemleri engellemez şekilde kilit yok verileri yerleştirilir. Veri yazma işlemleri verileri okuma anlık görüntü hareketlerin engellemez. Bunu kullanmak için allow_snapshot_ısolatıon veritabanı seçeneği ayarlayarak anlık görüntü yalıtımını etkinleştirmeniz gerekir.  
  
-   Bir veritabanında anlık görüntü yalıtımı etkinleştirildiğinde read_commıtted_snapshot veritabanı seçeneği varsayılan READ COMMITTED yalıtım düzeyi davranışını belirler. READ COMMITTED read_commıtted_snapshot ON açıkça belirtmezseniz, tüm örtük işlemlere uygulanır. Bu read_commıtted_snapshot devre dışı (varsayılan) ayarı olarak aynı davranışı oluşturur. Veritabanı altyapısı paylaşılan kilit read_commıtted_snapshot kapalı etkin olduğunda, varsayılan yalıtım düzeyi zorlamak için kullanır. Veritabanı altyapısı satır sürüm oluşturma ve anlık görüntü yalıtım read_commıtted_snapshot veritabanı seçeneği ON olarak ayarlarsanız, verileri korumak için kilitler kullanmak yerine varsayılan olarak kullanır.  
  
## <a name="how-snapshot-isolation-and-row-versioning-work"></a>Nasıl anlık görüntü yalıtımı ve satır sürüm oluşturma çalışma  
 Anlık görüntü yalıtım düzeyi, bir satır güncelleştirilir, her zaman etkin olduğunda ilk satırda bir kopyasını SQL Server veritabanı altyapısı depolar **tempdb**ve satır için bir işlem sıra numarası ekler. Ortaya çıkan olayların sırası verilmiştir:  
  
-   Yeni bir işlemi başlatılır ve bir işlem sıra numarası atanır.  
  
-   Veritabanı altyapısı işlem içinde bir satır okur ve satır sürümünden alır **tempdb** , sıra numarası en yakın ve işlem sırası numarası değerinden daha düşük.  
  
-   Veritabanı altyapısı işlem sıra numarası kaydedilmemiş işlemleri etkin işlem sırası numaralarını listesinde değil anlık görüntü işlemi başlatıldığında olup olmadığını denetler.  
  
-   İşlem satırdaki sürümü okur **tempdb** , işlem başlangıç itibariyle geçerli. Bu sıra numarası değerleri işlem sırası numarası değerinden yüksek olduğundan işlem başlatıldıktan sonra eklenen yeni satırlar görmezsiniz.  
  
-   Geçerli işlem işlemin başlamasından sonra bir satır sürümü olacağından silinen satır görürsünüz **tempdb** daha düşük bir sıra numarası değere sahip.  
  
 Net anlık görüntü yalıtım uygularken veya kilitleri temel tabloya yerleştirmek olmadan işlem başlangıcında var gibi işlem tüm verileri görmemesini etkisidir. Bu durumlarda performans geliştirmeleri sonuçlanabilir Çekişme olduğunda.  
  
 Her zaman bir anlık görüntü işlemi satırları güncelleştirme diğer hareketlerin önleyen kilitleri tutma iyimser eşzamanlılık denetimini kullanır. Bir anlık görüntü işlemi işlemin başlamasından sonra değiştirildi bir satır için bir güncelleştirme yürütme kullanmaya çalışırsa, işlem geri alındı ve bir hata oluşur.  
  
## <a name="working-with-snapshot-isolation-in-adonet"></a>Anlık görüntü yalıtımı ADO.NET ile çalışma  
 Anlık görüntü yalıtımı ADO.NET tarafından desteklenir <xref:System.Data.SqlClient.SqlTransaction> sınıfı. Bir veritabanı için anlık görüntü yalıtım etkin, ancak read_commıtted_snapshot ON için yapılandırılmamış başlatmalıdır bir <xref:System.Data.SqlClient.SqlTransaction> kullanarak **IsolationLevel.Snapshot** çağrılırken numaralandırma değeri <xref:System.Data.SqlClient.SqlConnection.BeginTransaction%2A> yöntem. Bu kod parçası bağlantı açık olduğunu varsayar <xref:System.Data.SqlClient.SqlConnection> nesnesi.  
  
```vb  
Dim sqlTran As SqlTransaction = _  
  connection.BeginTransaction(IsolationLevel.Snapshot)  
```  
  
```csharp  
SqlTransaction sqlTran =   
  connection.BeginTransaction(IsolationLevel.Snapshot);  
```  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, farklı yalıtım düzeylerinde kilitli verilerinize erişmeye çalışan tarafından nasıl davranacağını gösterir ve üretim kodunda kullanılmak üzere tasarlanmamıştır.  
  
 Kod bağlandığı **AdventureWorks** adlı bir tablo oluşturur ve örnek SQL Server veritabanında **TestSnapshot** ve verilerin bir satır ekler. Veritabanı için anlık görüntü yalıtımını açmak için ALTER DATABASE Transact-SQL deyimi kod kullanır, ancak varsayılan READ COMMITTED yalıtım düzeyi davranışını yürürlükte bırakarak read_commıtted_snapshot seçeneği ayarlı değil. Kod, ardından aşağıdaki eylemleri gerçekleştirir:  
  
-   Başlar, ancak tamamlamaz, bir güncelleştirme işlemi başlatmak için SERIALIZABLE yalıtım düzeyi kullandığı sqlTransaction1. Bu tablo kilitleme etkisi vardır.  
  
-   İkinci bir bağlantı açar ve verileri okumak için anlık görüntü yalıtım düzeyi kullanılarak ikinci bir işlem başlatır **TestSnapshot** tablo. Anlık görüntü yalıtımı etkin olmadığından bu işlem sqlTransaction1 başlatmadan önce var olan verileri okuyabilir.  
  
-   Üçüncü bir bağlantı açar ve tablosunda veri okuma girişimi için READ COMMITTED yalıtım düzeyi kullanılarak bir işlem başlatır. Bu durumda, ilk işlem ve zaman aşımına tabloda getirilen kilitler geçti okunamıyor çünkü kod veri okunamıyor. YİNELENEBİLİR okuma ve SERIALIZABLE yalıtım düzeylerinde bu yalıtım düzeylerinde de ilk işlemde yerleşen kilitler geçti okunamıyor çünkü kullandıysanız aynı sonucu oluşacak.  
  
-   Dördüncü bir bağlantı açar ve kaydedilmemiş değerinin kirli okuma sqlTransaction1 içinde gerçekleştirir READ UNCOMMITTED yalıtım düzeyi kullanılarak bir işlem başlatır. Birinci işlem taahhüt değilse bu değeri aslında hiç veritabanında mevcut olabilir.  
  
-   Birinci işlem geri alınır ve silerek temizler **TestSnapshot** tablo ve kapatma anlık görüntü yalıtımı için **AdventureWorks** veritabanı.  
  
> [!NOTE]
>  Aşağıdaki örnekler aynı bağlantı dizesini bağlantı havuzu ile kapalı kullanın. Bir bağlantı havuza, yalıtım düzeyi sıfırlama sunucu yalıtım düzeyinde sıfırlamaz. Sonuç olarak, aynı havuza alınmış iç bağlantı kullanan sonraki bağlantılar, havuza alınan bağlantı düzeylerini ayarlamak kullanıcıların yalıtım başlayın. Bağlantı havuzu devre dışı kapatma açıkça her bağlantı için yalıtım düzeyini ayarlamak için alternatiftir.  
  
 [!code-csharp[DataWorks SnapshotIsolation.Demo#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.Demo/CS/source.cs#1)]
 [!code-vb[DataWorks SnapshotIsolation.Demo#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.Demo/VB/source.vb#1)]  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, veri değiştirildiğinde anlık görüntü yalıtım davranışını gösterir. Kod aşağıdaki eylemleri gerçekleştirir:  
  
-   Bağlandığı **AdventureWorks** örnek anlık görüntü yalıtımı veritabanı ve etkinleştirir.  
  
-   Adlı bir tablo oluşturur **TestSnapshotUpdate** ve üç örnek veri satırı ekler.  
  
-   Başlar, ancak tamamlamaz, sqlTransaction1 anlık görüntü yalıtımını kullanarak. Üç veri satırı işlemde seçilir.  
  
-   İkinci bir oluşturur **SqlConnection** için **AdventureWorks** ve sqlTransaction1 içinde seçilen satır birindeki bir değer güncelleştirmeleri READ COMMITTED yalıtım düzeyi kullanılarak ikinci bir hareket oluşturur.  
  
-   SqlTransaction2 kaydeder.  
  
-   SqlTransaction1 ve aynı satır güncelleştirme denemeleri zaten kaydedilmiş bu sqlTransaction1 döndürür. Hata 3960 tetiklenir ve sqlTransaction1 geri otomatik olarak alınır. **SqlException.Number** ve **SqlException.Message** konsol penceresinde görüntülenir.  
  
-   Anlık görüntü yalıtım modunda devre dışı bırakmak için temizleme kodu yürütür **AdventureWorks** ve silme **TestSnapshotUpdate** tablo.  
  
 [!code-csharp[DataWorks SnapshotIsolation.DemoUpdate#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.DemoUpdate/CS/source.cs#1)]
 [!code-vb[DataWorks SnapshotIsolation.DemoUpdate#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.DemoUpdate/VB/source.vb#1)]  
  
### <a name="using-lock-hints-with-snapshot-isolation"></a>Anlık görüntü yalıtımıyla kilit ipuçlarına kullanma  
 Önceki örnekte, birinci işlem verileri seçer ve birinci işlem tamamlamak açmadan önce ikinci bir hareket verileri birinci işlem aynı satır güncelleştirmeye çalıştığında bir güncelleme çakışması neden güncelleştirir. İşlem başına kilit ipuçlarına sağlayarak uzun süre çalışan anlık işlemleri güncelleştirme çakışma olasılığı azaltabilir. Aşağıdaki SELECT deyimi UPDLOCK ipucu seçili satırları kilitlemek için kullanır:  
  
```  
SELECT * FROM TestSnapshotUpdate WITH (UPDLOCK)   
  WHERE PriKey BETWEEN 1 AND 3  
```  
  
 UPDLOCK kilit ipucuna bloğu birinci işlem tamamlanmadan önce satırları güncelleştirme girişimi herhangi bir satır kullanma. Bu işlem içinde güncelleştirildiği seçili satırları çakışmalar olmasını güvence altına alır. SQL Server Books Online içindeki "kilitleme ipuçları" konusuna bakın.  
  
 Uygulamanız çok fazla çakışma varsa, anlık görüntü yalıtımı en iyi seçenek olmayabilir. İpuçları yalnızca gerçekten gerekli olduğunda kullanılmalıdır. Sürekli olarak çalışması için kilit ipuçlarına kullanır. böylece uygulamanız tasarlanmalıdır değil.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [SQL Server ve ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)

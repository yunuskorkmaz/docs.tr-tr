---
title: LINQ ve ADO.NET
ms.date: 03/30/2017
ms.assetid: bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec
ms.openlocfilehash: f57d50e6c76b3d95c1d87b6beafe345f9a251e04
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54714821"
---
# <a name="linq-and-adonet"></a>LINQ ve ADO.NET
Günümüzde, birçok iş Geliştirici iki (veya daha fazla) programlama dilleri kullanmanız gerekir: iş mantığı ve bir sunu katmanı (örneğin, Visual C# veya Visual Basic) için yüksek düzey bir dil ve veritabanıyla etkileşime girmek için bir sorgu dili (gibi [!INCLUDE[tsql](../../../../includes/tsql-md.md)]). Bu Geliştirici etkili olması için çeşitli dillerde usta olmasını gerektirir ve aynı zamanda geliştirme ortamında dil uyuşmazlığı neden olur. Örneğin, bir veritabanında bir sorgu yürütmek için veri erişimi API'si kullanan bir uygulamayı tırnak işaretleri'ni kullanarak sorgu dize sabit değeri olarak belirtir. Bu sorgu dizesi derleyiciye beklemediğiniz okunabilir ve geçersiz sözdizimi veya başvurduğu satırları veya sütunları olup gerçekten var gibi hatalara alınmamış. Sorgu parametreleri ve Hayır denetimi türü yoktur `IntelliSense` ya da destekler.  
  
 [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] geliştiricilerin ayrı sorgu dili kullanmak zorunda kalmadan, uygulama kodunda kümesi tabanlı sorgular oluşturmasını sağlar. Yazabileceğiniz [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] çeşitli numaralandırılabilir veri kaynaklarına karşı sorgular (diğer bir deyişle, uygulayan bir veri kaynağı <xref:System.Collections.IEnumerable> arabirimi) gibi bellek içi veri yapıları, XML belgeleri, SQL veritabanları ve <xref:System.Data.DataSet> nesneleri. Bu numaralandırılabilir veri kaynaklarının çeşitli şekillerde uygulanan olsa da, bunların tümü aynı söz dizimi ve dil yapıları kullanıma sunar. Sorguları programlama dilinde oluşturulmuş olması nedeniyle dize değişmez değerleri anladım veya derleyici tarafından doğrulanmış olarak katıştırılır başka bir sorgu dili kullanmak zorunda değil. Programlama diline sorguları tümleştirmek ayrıca Visual Studio programcıların derleme zamanı tür ve söz dizimi denetimini, sunarak daha üretken olmanıza olanak sağlar ve `IntelliSense`. Bu özellikler için sorgu hata ayıklama ve hata düzeltme ihtiyacınızı azaltır.  
  
 Nesnelere bellekteki SQL tablolarından veri aktarımı genellikle sıkıcı ve hataya açık olur. [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] Sağlayıcısı uygulanmış olarak [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] ve [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] kaynak verileri dönüştürür <xref:System.Collections.IEnumerable>-nesne koleksiyonları bağlı. Programcı her zaman verileri görüntüleyen bir <xref:System.Collections.IEnumerable> koleksiyon, hem sorguladığınızda ve güncelleştirdiğinizde. Tam `IntelliSense` desteği, bu koleksiyonlarla karşı sorgular yazmak için sağlanır.  
  
 Üç ayrı ADO.NET vardır [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] teknolojileri: [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)], ve [!INCLUDE[linq_entities](../../../../includes/linq-entities-md.md)]. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] daha zengin, en iyi duruma getirilmiş üzerinde sorgulama sağlar <xref:System.Data.DataSet> ve [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] veritabanı şemalarını SQL Server, doğrudan sorgu sağlar ve [!INCLUDE[linq_entities](../../../../includes/linq-entities-md.md)] sorgu sağlar bir [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)].  
  
 Aşağıdaki diyagramda, üst düzey programlama dilleri ve LINQ özellikli veri kaynakları için ADO.NET LINQ teknolojilerden nasıl ilişki kuracağını genel bir bakış sağlar.  
  
 ![LINQ to ADO.NET genel bakış](../../../../docs/framework/data/adonet/media/dpue-linqtoadonetoverview-bpuedev11.gif "DPUE_LinqToAdoNetOverview_bpuedev11")  
  
 LINQ hakkında daha fazla bilgi için bkz: [dil tümleşik sorgu (LINQ)](../../../csharp/programming-guide/concepts/linq/index.md).
  
 Aşağıdaki bölümler, hakkında daha fazla bilgi sağlar. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)], ve [!INCLUDE[linq_entities](../../../../includes/linq-entities-md.md)].  
  
## <a name="linq-to-dataset"></a>LINQ - DataSet  
 <xref:System.Data.DataSet> Olan bağlantısı kesilmiş programlama anahtar öğesi modeli [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] üzerine kurulmuştur ve yaygın olarak kullanılır. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] geliştiricilerin daha zengin sorgu özellikleri oluşturmanızı sağlayan <xref:System.Data.DataSet> diğer birçok veri kaynakları için kullanılabilir sorgu oluşumunu mekanizmasını kullanarak. Daha fazla bilgi için [LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset.md).  
  
## <a name="linq-to-sql"></a>LINQ - SQL  
 [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] yararlı bir araçtır, kavramsal model eşlemesi gerektirmeyen geliştiriciler içindir. Kullanarak [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)], kullanabileceğiniz [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] mevcut veritabanı şemasını doğrudan üzerinden programlama modeli. [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] Oluşturulacak geliştiricilerinin [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] verileri temsil eden sınıf. Kavramsal veri modeline eşleme yerine, bu veritabanı tabloları, görünümleri, saklı yordamlar ve kullanıcı tanımlı işlevleri için doğrudan sınıfları eşleme oluşturulur.  
  
 İle [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)], geliştiriciler kod şemaya aynı kullanarak doğrudan depolama yazabilirsiniz [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] programlama modeli olarak bellek içi koleksiyonlarda ve <xref:System.Data.DataSet>, XML gibi diğer veri kaynaklarına ek olarak. Daha fazla bilgi için [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md).  
  
## <a name="linq-to-entities"></a>LINQ - Varlıklar  
 Çoğu uygulama, şu anda ilişkisel veritabanlarının üzerine yazılır. Belirli bir noktada, ilişkisel bir biçimde temsil verilerle etkileşim kurmak bu uygulamaları gerekir. Veritabanı şemalarını her zaman uygulamalar oluşturmak için ideal değildir ve kavramsal modeller uygulamanızın mantıksal modellerini veritabanları ile aynı değildir. [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] Uygulamalar verileri nesne gibi etkileşim kurabilir, verileri belirli bir etki alanı model oluşturmak için kullanılan bir kavramsal bir veri modelidir. Bkz: [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) daha fazla bilgi için.  
  
 Aracılığıyla [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)], ilişkisel veri, .NET ortamını nesneler olarak gösterilir. Bu nesne için ideal bir hedef katman sağlar [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] geliştiriciler, iş mantığı oluşturmak için kullanılan dil veritabanından karşı sorgular formüle etmek destek. Bu özellik olarak da bilinen [!INCLUDE[linq_entities](../../../../includes/linq-entities-md.md)]. Bkz: [LINQ to Entities](../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md) daha fazla bilgi için.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset.md)
- [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md)
- [LINQ to Entities](../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)
- [Dil ile Tümleşik Sorgu (LINQ)](../../../csharp/programming-guide/concepts/linq/index.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)

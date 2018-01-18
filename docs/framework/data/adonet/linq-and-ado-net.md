---
title: LINQ ve ADO.NET
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec
caps.latest.revision: "8"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: d55185153e3d03ddb2b1726ed25566d6b5f396ae
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="linq-and-adonet"></a>LINQ ve ADO.NET
Bugün, birçok iş geliştiriciler iki (veya daha fazla) programlama dilleri kullanmanız gerekir: iş mantığı ve sunu katmanı için yüksek düzey bir dil (gibi [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] veya [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)]) ve veritabanıyla etkileşim için bir sorgu dili ( gibi[!INCLUDE[tsql](../../../../includes/tsql-md.md)]). Bu Geliştirici etkili olması için çeşitli dillerde bilgisi olmasını gerektirir ve aynı zamanda dil uyuşmazlıkları geliştirme ortamında neden olur. Örneğin, bir veritabanında bir sorgu yürütmek için veri erişim API'sini kullanan bir uygulamayı tırnak işaretleri kullanarak sorgu bir dize belirtir. Bu sorgu dizesi derleyiciye beklemediğiniz okunabilir durumdadır ve geçersiz sözdizimi veya olup sütunlara veya satırlara başvurduğu gerçekten var gibi hataları kontrol edilmez. Sorgu parametrelerini ve Hayır denetimi türü yok `IntelliSense` ya da destekler.  
  
 [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)]ayrı bir sorgu dili kullanmak zorunda kalmadan kendi uygulama kodunda kümesini temel alan sorgular oluşturmak geliştiriciler sağlar. Yazabileceğiniz [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] sorguları çeşitli numaralandırılabilir veri kaynakları (diğer bir deyişle, uygulayan bir veri kaynağı <xref:System.Collections.IEnumerable> arabirimi), bellek içi veri yapılarını, XML belgeleri, SQL veritabanları gibi ve <xref:System.Data.DataSet> nesneleri. Bu numaralandırılabilir veri kaynaklarının çeşitli şekillerde uygulanan karşın, bunların tümü aynı sözdizimi ve dil yapıları kullanıma sunar. Sorguları programlama dilinde kendisini oluşturulmuş olması nedeniyle dize değişmez değerleri anladım veya derleyici tarafından doğrulanmış olarak katıştırılır başka bir sorgu dili kullanmak zorunda değil. Programlama diline sorguları tümleştirme ayrıca sağlar [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] derleme zamanı tür ve sözdizimi denetimi, sağlayarak daha üretken olmak için programcıları ve `IntelliSense`. Bu özellikler sorgu hata ayıklama ve hata düzeltme gereksinimini azaltır.  
  
 Bellekte nesneleri içine SQL tablolarından veri aktarma yorucu ve hataya yatkın görülür. [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] Sağlayıcı tarafından uygulanan [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] ve [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] kaynak verisine dönüştürür <xref:System.Collections.IEnumerable>-nesne koleksiyonları tabanlı. Programcı her zaman olarak veri görünümleri bir <xref:System.Collections.IEnumerable> koleksiyonu sorguladığınızda hem güncelleştirdiğinizde. Tam `IntelliSense` desteği, bu koleksiyonlarla sorguları yazmak için sağlanır.  
  
 Üç ayrı ADO.NET vardır [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] teknolojileri: [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)], ve [!INCLUDE[linq_entities](../../../../includes/linq-entities-md.md)]. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]daha zengin, en iyi duruma getirilmiş üzerinden sorgulama sağlar <xref:System.Data.DataSet> ve [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] doğrudan sorgu olanak tanır [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] veritabanı şemalarını ve [!INCLUDE[linq_entities](../../../../includes/linq-entities-md.md)] sorgu sayesinde bir [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)].  
  
 Aşağıdaki diyagramda, nasıl ADO.NET LINQ teknolojileri üst düzey programlama dilleri ve LINQ özellikli veri kaynakları ile ilgili genel bir bakış sağlar.  
  
 ![LINQ-ADO.NET genel bakış](../../../../docs/framework/data/adonet/media/dpue-linqtoadonetoverview-bpuedev11.gif "DPUE_LinqToAdoNetOverview_bpuedev11")  
  
 LINQ dil özellikleri hakkında genel bilgi için bkz: [Lınq'ye](http://msdn.microsoft.com/library/24dddf19-12a0-4707-a4bc-eba4fa7f219e). LINQ uygulamalarınızda kullanma hakkında daha fazla bilgi için bkz: [NOT ın yapı: LINQ genel programlama kılavuzu](http://msdn.microsoft.com/en-us/609c7a6b-cbdd-429d-99f3-78d13d3bc049), ayrıntılı LINQ teknolojileri kullanma hakkında bilgi içerir.  
  
 Aşağıdaki bölümler, hakkında daha fazla bilgi sağlar. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)], ve [!INCLUDE[linq_entities](../../../../includes/linq-entities-md.md)].  
  
## <a name="linq-to-dataset"></a>LINQ - DataSet  
 <xref:System.Data.DataSet> Olan bağlantısı kesilmiş programlama anahtar öğesi modeli [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] üzerine kurulmuştur ve yaygın olarak kullanılır. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]içine daha zengin sorgu özellikleri geliştiricilerin oluşturmalarını sağlar <xref:System.Data.DataSet> diğer birçok veri kaynakları için kullanılabilir sorgu formülasyonu mekanizmasını kullanarak. Daha fazla bilgi için bkz: [LINQ-DataSet](../../../../docs/framework/data/adonet/linq-to-dataset.md).  
  
## <a name="linq-to-sql"></a>LINQ - SQL  
 [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)]eşleme için kavramsal model gerektirmeyen geliştiriciler için kullanışlı bir aracı değil. Kullanarak [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)], kullanabileceğiniz [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] varolan veritabanı şeması üzerinden doğrudan programlama modeli. [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)]Oluşturulacak geliştiricilerinin [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] verilerini temsil eden sınıf. Kavramsal veri modeli eşleme yerine, bu veritabanı tabloları, görünümleri, saklı yordamları ve kullanıcı tanımlı işlevler doğrudan sınıfları eşlemesine oluşturulur.  
  
 İle [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)], geliştiricilerin şemaya aynı kullanarak doğrudan depolama kod yazma [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] programlama deseni bellek içi koleksiyonları olarak ve <xref:System.Data.DataSet>, XML gibi diğer veri kaynaklarına ek olarak. Daha fazla bilgi için bkz: [LINQ-SQL](../../../../docs/framework/data/adonet/sql/linq/index.md).  
  
## <a name="linq-to-entities"></a>LINQ - Varlıklar  
 Çoğu uygulama şu anda ilişkisel veritabanları üzerine yazılır. Belirli bir noktada, ilişkisel bir biçimde gösterilen veriler ile etkileşim kurmak bu uygulamaları gerekir. Veritabanı şemalarını her zaman uygulamaları oluşturmak için ideal olmayan ve uygulamanın kavramsal modeller veritabanlarının mantıksal modelleri ile aynı değildir. [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] Uygulamalar nesneler olarak verilerle etkileşim kurabilir, belirli bir etki alanı veri modeli için kullanılan bir kavramsal bir veri modelidir. Bkz: [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) daha fazla bilgi için.  
  
 Aracılığıyla [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)], ilişkisel veri .NET ortamı nesneler olarak gösterilir. Bu katman için ideal bir hedef nesnesi haline getirir [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] desteği, iş mantığı oluşturmak için kullanılan dil veritabanından sorguları formüle yayınlamasına izin verme. Bu özellik olarak bilinen [!INCLUDE[linq_entities](../../../../includes/linq-entities-md.md)]. Bkz: [LINQ to Entities](../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md) daha fazla bilgi için.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset.md)  
 [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md)  
 [LINQ to Entities](../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)  
 [LINQ (dil ile tümleşik sorgu)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)

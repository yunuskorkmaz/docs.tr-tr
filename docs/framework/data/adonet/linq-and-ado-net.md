---
title: LINQ ve ADO.NET
ms.date: 03/30/2017
ms.assetid: bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec
ms.openlocfilehash: d354e2e7f2696e90845edf0348340986fd7bb83c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795191"
---
# <a name="linq-and-adonet"></a>LINQ ve ADO.NET
Günümüzde, birçok iş geliştiricisi iki (veya daha fazla) programlama dili kullanmalıdır: iş mantığı ve sunum katmanları (görsel C# veya Visual Basic gibi) için üst düzey bir dil ve veritabanıyla etkileşime geçmek için bir sorgu dili (Transact-SQL gibi) . Bunun yapılması, geliştiricinin birkaç dilde etkili olması için yeterlilisi olmasını ve ayrıca geliştirme ortamında dil uyuşmazlıklarını da sağlar. Örneğin, bir veritabanına karşı sorgu yürütmek için bir veri erişim API 'SI kullanan bir uygulama, tırnak işaretleri kullanarak sorguyu dize sabit değeri olarak belirtir. Bu sorgu dizesi derleyiciye okunabilir değil ve hatalı söz dizimi ya da başvurduğu sütunlarda veya satırlarda hata olup olmadığını denetmedi. Sorgu parametrelerinin `IntelliSense` hiçbir tür denetlemesi yoktur, ya da desteklemez.  
  
 [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)]geliştiricilerin ayrı bir sorgu dili kullanmak zorunda kalmadan kendi uygulama kodlarında küme tabanlı sorgular oluşturmasına olanak sağlar. Bellek içi veri [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] yapıları, XML belgeleri, SQL veritabanları ve <xref:System.Data.DataSet> nesneler gibi çeşitli sıralanabilir veri kaynaklarına ( <xref:System.Collections.IEnumerable> arabirimi uygulayan bir veri kaynağı) karşı sorgular yazabilirsiniz. Bu sıralanabilir veri kaynakları çeşitli yollarla uygulansa da, hepsi aynı söz dizimini ve dil yapılarını kullanıma sunar. Sorgular programlama dilinde biçimlendirilbildiğinden, derleyici tarafından anlaşılmayan veya doğrulanamayan dize sabit değerleri olarak katıştırılmış başka bir sorgu dili kullanmak zorunda değilsiniz. Sorguları programlama diliyle tümleştirmek, `IntelliSense`Visual Studio programcılarının derleme zamanı türü ve sözdizimi denetimi sağlayarak daha üretken olmasını da sağlar. Bu özellikler sorgu hata ayıklaması ve hata düzeltme ihtiyacını azaltır.  
  
 Verileri SQL tablolarından bellekteki nesnelere aktarmak genellikle sıkıcı ve hataya açıktır. Sağlayıcı LINQ to DataSet tarafından uygulanır ve [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] kaynak verileri <xref:System.Collections.IEnumerable>tabanlı nesne koleksiyonlarına dönüştürür. [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] Programcılar her zaman verileri bir <xref:System.Collections.IEnumerable> koleksiyon olarak görüntüler, her ikisi de ve güncelleştirdiğinizde. Bu `IntelliSense` koleksiyonlara karşı sorgu yazmak için tam destek sağlanır.  
  
 Üç ayrı ADO.net [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] teknolojisi vardır: LINQ to DataSet, [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)]ve LINQ to Entities. LINQ to DataSet, <xref:System.Data.DataSet> üzerinde daha zengin, iyileştirilmiş sorgulama sağlar [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] ve SQL Server veritabanı şemalarını doğrudan sorgulayabilir ve LINQ to Entities varlık veri modeli sorgulamanızı sağlar.  
  
 Aşağıdaki diyagramda, ADO.NET LINQ teknolojilerinin üst düzey programlama dilleri ve LINQ özellikli veri kaynaklarıyla nasıl ilişkilendirileceğiyle bir genel bakış sunulmaktadır.  
  
 ![LINQ to ADO.NET genel bakış](./media/dpue-linqtoadonetoverview-bpuedev11.gif "DPUE_LinqToAdoNetOverview_bpuedev11")  
  
 LINQ hakkında daha fazla bilgi için bkz. [dil Ile tümleşik sorgu (LINQ)](../../../csharp/programming-guide/concepts/linq/index.md).
  
 Aşağıdaki bölümlerde LINQ to DataSet, [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)]ve LINQ to Entities hakkında daha fazla bilgi sağlanmaktadır.  
  
## <a name="linq-to-dataset"></a>LINQ - DataSet  
 , <xref:System.Data.DataSet> ADO.net 'in oluşturulduğu ve yaygın olarak kullanıldığı, bağlantısı kesilen programlama modelinin anahtar öğesidir. LINQ to DataSet, geliştiricilerin ' de diğer birçok veri kaynağı <xref:System.Data.DataSet> için kullanılabilen aynı sorgu formül mekanizmasını kullanarak daha zengin sorgu özellikleri oluşturmalarına olanak sağlar. Daha fazla bilgi için [LINQ to DataSet](linq-to-dataset.md).  
  
## <a name="linq-to-sql"></a>LINQ - SQL  
 [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)], kavramsal bir modelle eşleme gerektirmeyen geliştiriciler için yararlı bir araçtır. Kullanarak [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)], [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] programlama modelini doğrudan mevcut veritabanı şemasının üzerinde kullanabilirsiniz. [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)]geliştiricilerin verileri temsil eden .NET Framework sınıfları oluşturmasını sağlar. Kavramsal veri modeliyle eşleme yerine, bu oluşturulan sınıflar doğrudan veritabanı tabloları, görünümler, saklı yordamlar ve Kullanıcı tanımlı işlevlerle eşlenir.  
  
 Sayesinde [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)]geliştiriciler, bellek içi koleksiyonlarla aynı [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] programlama düzenini ve <xref:System.Data.DataSet>XML gibi diğer veri kaynaklarına ek olarak, doğrudan depolama şemasına kod yazabilir. Daha fazla bilgi için bkz. [LINQ to SQL](./sql/linq/index.md).  
  
## <a name="linq-to-entities"></a>LINQ - Varlıklar  
 Çoğu uygulama şu anda ilişkisel veritabanlarının üzerine yazılmıştır. Bu uygulamaların bir noktada, ilişkisel bir formda temsil edilen verilerle etkileşim kurması gerekir. Veritabanı şemaları, uygulama oluşturmak için her zaman ideal değildir ve uygulamanın kavramsal modelleri, veritabanlarının mantıksal modelleriyle aynı değildir. Varlık Veri Modeli, uygulamaların nesneler olarak verilerle etkileşime girebilmesi için belirli bir etki alanının verilerini modellemek üzere kullanılabilen kavramsal bir veri modelidir. Daha fazla bilgi için bkz. [ADO.NET Entity Framework](./ef/index.md) .  
  
 Varlık Veri Modeli, ilişkisel veriler .NET ortamında nesneler olarak sunulur. Bu, nesne katmanını destek için [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] ideal bir hedef haline getirir ve geliştiricilerin iş mantığını oluşturmak için kullanılan dilden sorguları veritabanına göre formüllemesini sağlar. Bu yetenek LINQ to Entities olarak bilinir. Daha fazla bilgi için bkz. [LINQ to Entities](./ef/language-reference/linq-to-entities.md) .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to DataSet](linq-to-dataset.md)
- [LINQ to SQL](./sql/linq/index.md)
- [LINQ to Entities](./ef/language-reference/linq-to-entities.md)
- [Dil ile Tümleşik Sorgu (LINQ)](../../../csharp/programming-guide/concepts/linq/index.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)

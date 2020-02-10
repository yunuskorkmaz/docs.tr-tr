---
title: LINQ ve ADO.NET
titleSuffix: ''
ms.date: 03/30/2017
ms.assetid: bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec
ms.openlocfilehash: c5b56fa78ce0276953597d63b3d6e2f45d88c8ab
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094442"
---
# <a name="linq-and-adonet"></a>LINQ ve ADO.NET

Günümüzde, birçok iş geliştiricisi iki (veya daha fazla) programlama dili kullanmalıdır: iş mantığı ve sunum katmanları (görsel C# veya Visual Basic gibi) için üst düzey bir dil ve veritabanıyla etkileşime geçmek için bir sorgu dili (Transact-SQL gibi). Bunun yapılması, geliştiricinin birkaç dilde etkili olması için yeterlilisi olmasını ve ayrıca geliştirme ortamında dil uyuşmazlıklarını da sağlar. Örneğin, bir veritabanına karşı sorgu yürütmek için bir veri erişim API 'SI kullanan bir uygulama, tırnak işaretleri kullanarak sorguyu dize sabit değeri olarak belirtir. Bu sorgu dizesi derleyiciye okunamaz ve hatalı söz dizimi ya da başvurduğu sütunlarda veya satırlarda hata olup olmadığını denetlenemez. Sorgu parametrelerinin hiçbir tür denetlemesi yoktur ve `IntelliSense` desteklenmez.  
  
 Dil ile tümleşik sorgu (LINQ), geliştiricilerin ayrı bir sorgu dili kullanmak zorunda kalmadan kendi uygulama kodlarında küme tabanlı sorgular oluşturmasına olanak sağlar. LINQ sorgularını, bellek içi veri yapıları, XML belgeleri, SQL veritabanları ve <xref:System.Data.DataSet> nesneleri gibi çeşitli sıralanabilir veri kaynaklarına (yani <xref:System.Collections.IEnumerable> arabirimini uygulayan bir veri kaynağı) karşı yazabilirsiniz. Bu sıralanabilir veri kaynakları çeşitli yollarla uygulansa da, hepsi aynı söz dizimini ve dil yapılarını kullanıma sunar. Sorgular programlama dilinde biçimlendirilbildiğinden, derleyici tarafından anlaşılmayan veya doğrulanamayan dize sabit değerleri olarak katıştırılmış başka bir sorgu dili kullanmak zorunda değilsiniz. Sorguları programlama diliyle tümleştirmek, Visual Studio programcılarının derleme zamanı türü ve sözdizimi denetimi sağlayarak daha üretken olmalarını de sağlar ve `IntelliSense`. Bu özellikler sorgu hata ayıklaması ve hata düzeltme ihtiyacını azaltır.  
  
 Verileri SQL tablolarından bellekteki nesnelere aktarmak genellikle sıkıcı ve hataya açıktır. LINQ to DataSet ve [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] tarafından uygulanan LINQ sağlayıcısı, kaynak verileri <xref:System.Collections.IEnumerable>tabanlı nesne koleksiyonlarına dönüştürür. Programcılar her zaman verileri <xref:System.Collections.IEnumerable> bir koleksiyon olarak, her ikisi de ne zaman güncelleştirdiğinizde ve güncelleştirdiğinizde görüntüler. Bu koleksiyonlara karşı sorgu yazmak için tam `IntelliSense` desteği sağlanır.  
  
 Üç ayrı ADO.NET dil ile tümleşik sorgu (LINQ) teknolojisi vardır: LINQ to DataSet, [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)]ve LINQ to Entities. LINQ to DataSet, <xref:System.Data.DataSet> daha zengin, iyileştirilmiş sorgulama sağlar ve [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] SQL Server veritabanı şemalarını doğrudan sorgulayabilir ve LINQ to Entities varlık veri modeli sorgulamanızı sağlar.  
  
 Aşağıdaki diyagramda, ADO.NET LINQ teknolojilerinin üst düzey programlama dilleri ve LINQ özellikli veri kaynaklarıyla nasıl ilişkilendirileceğiyle bir genel bakış sunulmaktadır.  
  
 ![LINQ to ADO.NET genel bakış](./media/dpue-linqtoadonetoverview-bpuedev11.gif "DPUE_LinqToAdoNetOverview_bpuedev11")  
  
 LINQ hakkında daha fazla bilgi için bkz. [dil Ile tümleşik sorgu (LINQ)](../../../csharp/programming-guide/concepts/linq/index.md).
  
 Aşağıdaki bölümlerde LINQ to DataSet, [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)]ve LINQ to Entities hakkında daha fazla bilgi sağlanmaktadır.  
  
## <a name="linq-to-dataset"></a>LINQ - DataSet  
 <xref:System.Data.DataSet>, ADO.NET 'in üzerinde oluşturulduğu ve yaygın olarak kullanılan, bağlantısı kesilen programlama modelinin anahtar öğesidir. LINQ to DataSet, geliştiricilerin diğer birçok veri kaynağı için kullanılabilen aynı sorgu formül mekanizmasını kullanarak <xref:System.Data.DataSet> daha zengin sorgu özellikleri oluşturmalarına olanak sağlar. Daha fazla bilgi için bkz. [LINQ to DataSet](linq-to-dataset.md).  
  
## <a name="linq-to-sql"></a>LINQ - SQL  
 [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)], kavramsal bir modelle eşleme gerektirmeyen geliştiriciler için yararlı bir araçtır. [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)]kullanarak, LINQ programlama modelini doğrudan mevcut veritabanı şemasının üzerinde kullanabilirsiniz. [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)], geliştiricilerin verileri temsil eden .NET Framework sınıflar oluşturmasını sağlar. Kavramsal veri modeliyle eşleme yerine, bu oluşturulan sınıflar doğrudan veritabanı tabloları, görünümler, saklı yordamlar ve Kullanıcı tanımlı işlevlerle eşlenir.  
  
 [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)], geliştiriciler, bellek içi koleksiyonlar ve <xref:System.Data.DataSet>XML gibi diğer veri kaynaklarına ek olarak aynı LINQ programlama modelini kullanarak doğrudan depolama şemasına kod yazabilir. Daha fazla bilgi için bkz. [LINQ to SQL](./sql/linq/index.md).  
  
## <a name="linq-to-entities"></a>LINQ - Varlıklar  
 Çoğu uygulama şu anda ilişkisel veritabanlarının üzerine yazılmıştır. Bu uygulamaların bir noktada, ilişkisel bir formda temsil edilen verilerle etkileşim kurması gerekir. Veritabanı şemaları, uygulama oluşturmak için her zaman ideal değildir ve uygulamanın kavramsal modelleri, veritabanlarının mantıksal modelleriyle aynı değildir. Varlık Veri Modeli, uygulamaların nesneler olarak verilerle etkileşime girebilmesi için belirli bir etki alanının verilerini modellemek üzere kullanılabilen kavramsal bir veri modelidir. Daha fazla bilgi için bkz. [ADO.NET Entity Framework](./ef/index.md).  
  
 Varlık Veri Modeli, ilişkisel veriler .NET ortamında nesneler olarak sunulur. Bu, nesne katmanını LINQ desteği için ideal bir hedef haline getirir ve geliştiricilerin iş mantığını oluşturmak için kullanılan dilden sorguları veritabanına göre formüllemesini sağlar. Bu yetenek LINQ to Entities olarak bilinir. Daha fazla bilgi için bkz. [LINQ to Entities](./ef/language-reference/linq-to-entities.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to DataSet](linq-to-dataset.md)
- [LINQ to SQL](./sql/linq/index.md)
- [LINQ to Entities](./ef/language-reference/linq-to-entities.md)
- [Dil ile Tümleşik Sorgu (LINQ)](../../../csharp/programming-guide/concepts/linq/index.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)

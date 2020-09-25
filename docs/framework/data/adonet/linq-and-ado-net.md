---
title: LINQ ve ADO.NET
description: Ayrı bir sorgu dili kullanmak zorunda kalmadan, ADO.NET içinde dil ile tümleşik sorgu (LINQ) kullanarak uygulama kodundaki küme tabanlı sorguları nasıl ayarlayacağınızı öğrenin.
titleSuffix: ''
ms.date: 03/30/2017
ms.assetid: bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec
ms.openlocfilehash: 50e048a67d4a9bf62b2224664acb654b96da0cb7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194693"
---
# <a name="linq-and-adonet"></a>LINQ ve ADO.NET

Günümüzde, birçok iş geliştiricisi iki (veya daha fazla) programlama dili kullanmalıdır: iş mantığı ve sunum katmanları (örneğin, Visual C# veya Visual Basic) için üst düzey bir dil ve veritabanıyla etkileşime geçmek için bir sorgu dili (Transact-SQL gibi). Bunun yapılması, geliştiricinin birkaç dilde etkili olması için yeterlilisi olmasını ve ayrıca geliştirme ortamında dil uyuşmazlıklarını da sağlar. Örneğin, bir veritabanına karşı sorgu yürütmek için bir veri erişim API 'SI kullanan bir uygulama, tırnak işaretleri kullanarak sorguyu dize sabit değeri olarak belirtir. Bu sorgu dizesi derleyiciye okunamaz ve hatalı söz dizimi ya da başvurduğu sütunlarda veya satırlarda hata olup olmadığını denetlenemez. Sorgu parametrelerinin hiçbir tür denetlemesi yoktur `IntelliSense` , ya da desteklemez.  
  
 Dil ile tümleşik sorgu (LINQ), geliştiricilerin ayrı bir sorgu dili kullanmak zorunda kalmadan kendi uygulama kodlarında küme tabanlı sorgular oluşturmasına olanak sağlar. LINQ sorgularını, <xref:System.Collections.IEnumerable> bellek içi veri yapıları, XML belgeleri, SQL veritabanları ve nesneler gibi çeşitli sıralanabilir veri kaynaklarına (arabirimi uygulayan bir veri kaynağı) karşı yazabilirsiniz <xref:System.Data.DataSet> . Bu sıralanabilir veri kaynakları çeşitli yollarla uygulansa da, hepsi aynı söz dizimini ve dil yapılarını kullanıma sunar. Sorgular programlama dilinde biçimlendirilbildiğinden, derleyici tarafından anlaşılmayan veya doğrulanamayan dize sabit değerleri olarak katıştırılmış başka bir sorgu dili kullanmak zorunda değilsiniz. Sorguları programlama diliyle tümleştirmek, Visual Studio programcılarının derleme zamanı türü ve sözdizimi denetimi sağlayarak daha üretken olmasını da sağlar `IntelliSense` . Bu özellikler sorgu hata ayıklaması ve hata düzeltme ihtiyacını azaltır.  
  
 Verileri SQL tablolarından bellekteki nesnelere aktarmak genellikle sıkıcı ve hataya açıktır. LINQ to DataSet tarafından uygulanan LINQ sağlayıcısı, [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] kaynak verileri <xref:System.Collections.IEnumerable> tabanlı nesne koleksiyonlarına dönüştürür. Programcılar her zaman verileri bir koleksiyon olarak görüntüler <xref:System.Collections.IEnumerable> , her ikisi de ve güncelleştirdiğinizde. `IntelliSense`Bu koleksiyonlara karşı sorgu yazmak için tam destek sağlanır.  
  
 Üç ayrı ADO.NET dil ile tümleşik sorgu (LINQ) teknolojisi vardır: LINQ to DataSet, [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] ve LINQ to Entities. LINQ to DataSet, üzerinde daha zengin, iyileştirilmiş sorgulama sağlar <xref:System.Data.DataSet> ve [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] SQL Server veritabanı şemalarını doğrudan sorgulayabilir ve LINQ to Entities varlık veri modeli sorgulamanızı sağlar.  
  
 Aşağıdaki diyagramda, ADO.NET LINQ teknolojilerinin üst düzey programlama dilleri ve LINQ özellikli veri kaynaklarıyla nasıl ilişkilendirileceğiyle bir genel bakış sunulmaktadır.  
  
 ![LINQ to ADO.NET genel bakış](./media/dpue-linqtoadonetoverview-bpuedev11.gif "DPUE_LinqToAdoNetOverview_bpuedev11")  
  
 LINQ hakkında daha fazla bilgi için bkz. [dil Ile tümleşik sorgu (LINQ)](../../../csharp/programming-guide/concepts/linq/index.md).
  
 Aşağıdaki bölümlerde LINQ to DataSet, ve LINQ to Entities hakkında daha fazla bilgi sağlanmaktadır [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] .  
  
## <a name="linq-to-dataset"></a>LINQ - DataSet  

 , <xref:System.Data.DataSet> ADO.net 'in oluşturulduğu ve yaygın olarak kullanıldığı, bağlantısı kesilen programlama modelinin anahtar öğesidir. LINQ to DataSet, geliştiricilerin ' de <xref:System.Data.DataSet> diğer birçok veri kaynağı için kullanılabilen aynı sorgu formül mekanizmasını kullanarak daha zengin sorgu özellikleri oluşturmalarına olanak sağlar. Daha fazla bilgi için bkz. [LINQ to DataSet](linq-to-dataset.md).  
  
## <a name="linq-to-sql"></a>LINQ to SQL  

 [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] , kavramsal bir modelle eşleme gerektirmeyen geliştiriciler için yararlı bir araçtır. Kullanarak [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] , LINQ programlama modelini doğrudan mevcut veritabanı şemasının üzerinde kullanabilirsiniz. [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] geliştiricilerin verileri temsil eden .NET Framework sınıfları oluşturmasını sağlar. Kavramsal veri modeliyle eşleme yerine, bu oluşturulan sınıflar doğrudan veritabanı tabloları, görünümler, saklı yordamlar ve Kullanıcı tanımlı işlevlerle eşlenir.  
  
 Sayesinde [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] geliştiriciler, bellek içi koleksiyonlar ve <xref:System.Data.DataSet> XML gibi diğer veri kaynaklarına ek olarak aynı LINQ programlama modelini kullanarak doğrudan depolama şemasına kod yazabilir. Daha fazla bilgi için bkz. [LINQ to SQL](./sql/linq/index.md).  
  
## <a name="linq-to-entities"></a>LINQ - Varlıklar  

 Çoğu uygulama şu anda ilişkisel veritabanlarının üzerine yazılmıştır. Bu uygulamaların bir noktada, ilişkisel bir formda temsil edilen verilerle etkileşim kurması gerekir. Veritabanı şemaları, uygulama oluşturmak için her zaman ideal değildir ve uygulamanın kavramsal modelleri, veritabanlarının mantıksal modelleriyle aynı değildir. Varlık Veri Modeli, uygulamaların nesneler olarak verilerle etkileşime girebilmesi için belirli bir etki alanının verilerini modellemek üzere kullanılabilen kavramsal bir veri modelidir. Daha fazla bilgi için bkz. [ADO.NET Entity Framework](./ef/index.md).  
  
 Varlık Veri Modeli, ilişkisel veriler .NET ortamında nesneler olarak sunulur. Bu, nesne katmanını LINQ desteği için ideal bir hedef haline getirir ve geliştiricilerin iş mantığını oluşturmak için kullanılan dilden sorguları veritabanına göre formüllemesini sağlar. Bu yetenek LINQ to Entities olarak bilinir. Daha fazla bilgi için bkz. [LINQ to Entities](./ef/language-reference/linq-to-entities.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ - DataSet](linq-to-dataset.md)
- [LINQ to SQL](./sql/linq/index.md)
- [LINQ - Varlıklar](./ef/language-reference/linq-to-entities.md)
- [Dil ile Tümleşik Sorgu (LINQ)](../../../csharp/programming-guide/concepts/linq/index.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)

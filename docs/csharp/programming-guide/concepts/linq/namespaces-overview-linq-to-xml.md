---
title: Ad Alanlarına Genel Bakış (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 16283322-8238-4918-ab11-802ac6748eb7
ms.openlocfilehash: d4c43a407921e1a74d1792f7cae4e320ca1234c0
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68709905"
---
# <a name="namespaces-overview-linq-to-xml"></a>Ad Alanlarına Genel Bakış (LINQ to XML)

Bu makale ad alanlarını, <xref:System.Xml.Linq.XName> sınıfı <xref:System.Xml.Linq.XNamespace> ve sınıfı tanıtır.
  
## <a name="xml-names"></a>XML adları  

XML adları genellikle XML programlamada karmaşıklık kaynağıdır. Xml adı bir XML ad alanından (XML ad alanı URI 'SI olarak da bilinir) ve yerel bir ada oluşur. XML ad alanı, .NET Framework tabanlı programdaki bir ad alanına benzerdir. Öğelerin ve özniteliklerin adlarını benzersiz bir şekilde nitelemenize olanak sağlar. Bu, bir XML belgesinin çeşitli bölümleri arasında ad çakışmalarını önlemeye yardımcı olur. Bir XML ad alanı bildirdiyseniz, yalnızca bu ad alanı içinde benzersiz olması gereken yerel bir ad seçebilirsiniz.  
  
XML adlarının başka bir yönü XML *ad alanı ön ekleri*olur. XML ön ekleri, XML adlarının birçok karmaşıklığının oluşmasına neden olur. Bu ön ekler, XML belgesini daha kısa ve anlaşılır hale getiren bir XML ad alanı için kısayol oluşturmanızı sağlar. Ancak, XML ön ekleri, karmaşıklık ekleyen anlamı olan bağlamına bağımlıdır. Örneğin, XML ön eki `aw` bir xml ağacının tek bir bölümünde ve xml ağacının farklı bir bölümünde farklı bir XML ad alanıyla ilişkilendirilebilir.  
  
İle [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] C# kullanmanın avantajlarından biri, XML ön eklerini kullanmak zorunda değilsiniz. Bir XML belgesi yüklediğinde veya ayrıştırdığında, her bir XML ön eki karşılık gelen XML ad alanına çözümlenir. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Bundan sonra, ad alanları kullanan bir belgeyle çalışırken, ad alanı ön eki aracılığıyla değil, ad alanı URI 'SI aracılığıyla ad alanlarına neredeyse her zaman erişirsiniz. Geliştiriciler içindeki [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] XML adlarıyla çalıştığında, her zaman tam olarak nitelenmiş bir xml adı (yani bir XML ad alanı ve yerel bir ad) ile çalışır. Ancak, gerekli olduğunda, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ad alanı öneklerini birlikte çalışmanıza ve denetlemenize olanak tanır.  
  
İçinde [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], XML <xref:System.Xml.Linq.XName>adlarını temsil eden sınıf. XML adları, API 'nin [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] tamamında sık görünür ve bir XML adının gerekli olduğu her yerde bir <xref:System.Xml.Linq.XName> parametre bulacaksınız. Ancak, doğrudan ile <xref:System.Xml.Linq.XName>nadiren çalışmanız gerekir. <xref:System.Xml.Linq.XName>dizeden örtük bir dönüştürme içerir.  
  
Daha fazla bilgi için bkz. <xref:System.Xml.Linq.XNamespace> ve <xref:System.Xml.Linq.XName>.
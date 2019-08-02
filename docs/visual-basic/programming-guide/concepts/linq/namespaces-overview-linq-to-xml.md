---
title: Ad Alanlarına Genel Bakış (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: b8eb31fa-4b26-4acf-8050-6e705687f458
ms.openlocfilehash: bd83a423c8fd19506c5d23ea308bb56cced6ca93
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68710545"
---
# <a name="namespaces-overview-linq-to-xml"></a>Ad Alanlarına Genel Bakış (LINQ to XML)

Bu konu, ad alanlarını, <xref:System.Xml.Linq.XName> sınıfı <xref:System.Xml.Linq.XNamespace> ve sınıfı tanıtır.  
  
## <a name="xml-names"></a>XML adları  

XML adları genellikle XML programlamada karmaşıklık kaynağıdır. Xml adı bir XML ad alanından (XML ad alanı URI 'SI olarak da bilinir) ve yerel bir ada oluşur. XML ad alanı, .NET Framework tabanlı programdaki bir ad alanına benzerdir. Öğelerin ve özniteliklerin adlarını benzersiz bir şekilde nitelemenize olanak sağlar. Bu, bir XML belgesinin çeşitli bölümleri arasında ad çakışmalarını önlemeye yardımcı olur. Bir XML ad alanı bildirdiyseniz, yalnızca bu ad alanı içinde benzersiz olması gereken yerel bir ad seçebilirsiniz.  
  
 XML adlarının başka bir yönü XML *ad alanı ön ekleri*olur. XML ön ekleri, XML adlarının birçok karmaşıklığının oluşmasına neden olur. Bu ön ekler, XML belgesini daha kısa ve anlaşılır hale getiren bir XML ad alanı için kısayol oluşturmanızı sağlar. Ancak, XML ön ekleri, karmaşıklık ekleyen anlamı olan bağlamına bağımlıdır. Örneğin, XML ön eki `aw` bir xml ağacının tek bir bölümünde ve xml ağacının farklı bir bölümünde farklı bir XML ad alanıyla ilişkilendirilebilir.  
  
Visual Basic ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] XML değişmez değerleri ile kullanırken, ad alanları içindeki belgelerle çalışırken ad alanı öneklerini kullanmanız gerekir.  
  
İçinde [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], XML <xref:System.Xml.Linq.XName>adlarını temsil eden sınıf. XML adları, API 'nin [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] tamamında sık görünür ve bir XML adının gerekli olduğu her yerde bir <xref:System.Xml.Linq.XName> parametre bulacaksınız. Ancak, doğrudan ile <xref:System.Xml.Linq.XName>nadiren çalışmanız gerekir. <xref:System.Xml.Linq.XName>dizeden örtük bir dönüştürme içerir.  
  
Daha fazla bilgi için bkz. <xref:System.Xml.Linq.XNamespace> ve <xref:System.Xml.Linq.XName>.

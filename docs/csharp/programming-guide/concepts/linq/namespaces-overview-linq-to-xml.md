---
title: Ad Alanlarına Genel Bakış (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 16283322-8238-4918-ab11-802ac6748eb7
ms.openlocfilehash: 010d8661afe063c06f042084f6b320acb1235ac4
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241441"
---
# <a name="namespaces-overview-linq-to-xml"></a>Ad Alanlarına Genel Bakış (LINQ to XML)

Bu makale ad alanlarını, <xref:System.Xml.Linq.XName> sınıfı ve <xref:System.Xml.Linq.XNamespace> sınıfı tanıtır.

## <a name="xml-names"></a>XML adları

XML adları genellikle XML programlamada karmaşıklık kaynağıdır. Xml adı bir XML ad alanından (XML ad alanı URI 'SI olarak da bilinir) ve yerel bir ada oluşur. XML ad alanı, .NET programındaki bir ad alanına benzerdir. Öğelerin ve özniteliklerin adlarını benzersiz bir şekilde nitelemenize olanak sağlar. Bu, bir XML belgesinin çeşitli bölümleri arasında ad çakışmalarını önlemeye yardımcı olur. Bir XML ad alanı bildirdiyseniz, yalnızca bu ad alanı içinde benzersiz olması gereken yerel bir ad seçebilirsiniz.

XML adlarının başka bir yönü XML *ad alanı ön ekleri*olur. XML ön ekleri, XML adlarının birçok karmaşıklığının oluşmasına neden olur. Bu ön ekler, XML belgesini daha kısa ve anlaşılır hale getiren bir XML ad alanı için kısayol oluşturmanızı sağlar. Ancak, XML ön ekleri, karmaşıklık ekleyen anlamı olan bağlamına bağımlıdır. Örneğin, XML ön eki bir XML `aw` ağacının tek bir bölümünde ve xml ağacının farklı bir bölümünde farklı bır XML ad alanıyla ilişkilendirilebilir.

C# ile kullanmanın avantajlarından biri, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] XML ön eklerini kullanmak zorunda değilsiniz. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]BIR XML belgesi yüklediğinde veya ayrıştırdığında, her BIR XML ön eki karşılık gelen XML ad alanına çözümlenir. Bundan sonra, ad alanları kullanan bir belgeyle çalışırken, ad alanı ön eki aracılığıyla değil, ad alanı URI 'SI aracılığıyla ad alanlarına neredeyse her zaman erişirsiniz. Geliştiriciler içindeki XML adlarıyla çalıştığında [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , her zaman tam olarak nitelenmiş BIR XML adı (yani BIR XML ad alanı ve yerel bir ad) ile çalışır. Ancak, gerekli olduğunda, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ad alanı öneklerini birlikte çalışmanıza ve denetlemenize olanak tanır.

İçinde [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , XML adlarını temsil eden sınıf <xref:System.Xml.Linq.XName> . XML adları, API 'nin tamamında sık görünür [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ve BIR XML adının gerekli olduğu her yerde bir <xref:System.Xml.Linq.XName> parametre bulacaksınız. Ancak, doğrudan ile nadiren çalışmanız gerekir <xref:System.Xml.Linq.XName> . <xref:System.Xml.Linq.XName>dizeden örtük bir dönüştürme içerir.

Daha fazla bilgi için <xref:System.Xml.Linq.XNamespace> ve <xref:System.Xml.Linq.XName> bölümlerine bakın.

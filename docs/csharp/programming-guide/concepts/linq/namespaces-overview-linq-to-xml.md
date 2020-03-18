---
title: Ad Alanlarına Genel Bakış (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 16283322-8238-4918-ab11-802ac6748eb7
ms.openlocfilehash: d5f176a5561b77126ef23af996ab1e4bf51092ad
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "68868831"
---
# <a name="namespaces-overview-linq-to-xml"></a>Ad Alanlarına Genel Bakış (LINQ to XML)

Bu makalede ad alanları, <xref:System.Xml.Linq.XName> sınıf ve <xref:System.Xml.Linq.XNamespace> sınıf tanınır.

## <a name="xml-names"></a>XML Adları

XML adları genellikle XML programlamada karmaşıklık kaynağıdır. XML adı, XML ad alanı (XML ad alanı URI olarak da adlandırılır) ve yerel bir addan oluşur. XML ad alanı,.NET Framework tabanlı bir programdaki ad alanına benzer. Öğelerin ve özniteliklerin adlarını benzersiz olarak nitelemenizi sağlar. Bu, xml belgesinin çeşitli bölümleri arasındaki ad çakışmalarını önlemeye yardımcı olur. Bir XML ad alanı ilan ettiğinizde, yalnızca bu ad alanı içinde benzersiz olması gereken yerel bir ad seçebilirsiniz.

XML adlarının bir diğer yönü de XML *ad alanı önekleridir.* XML önekleri, XML adlarının karmaşıklığının çoğuna neden olur. Bu önekler, XML belgesini daha kısa ve anlaşılır hale getiren bir XML ad alanı için bir kısayol oluşturmanıza olanak tanır. Ancak, XML önekleri, karmaşıklık ekler anlam, kendi bağlamına bağlıdır. Örneğin, XML öneki, `aw` bir XML ağacının bir bölümünde bir XML ad alanıyla ve XML ağacının farklı bir bölümünde farklı bir XML ad alanıyla ilişkilendirilebilir.

C# ile kullanmanın [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] avantajlarından biri xml önekleri kullanmak zorunda kalmamanızdır. Bir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] XML belgesini yükler veya ayrıştırdığında, her XML öneki karşılık gelen XML ad alanına çözülür. Bundan sonra, ad alanları kullanan bir belgeyle çalışırken, ad alanı önekinden değil, ad alanı URI'den hemen hemen her zaman ad alanlarına erişirsiniz. Geliştiriciler XML adlarıyla [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] çalıştıklarında her zaman tam nitelikli bir XML adı (diğer bir deyişle, bir XML ad alanı ve yerel bir ad) ile çalışırlar. Ancak, gerektiğinde [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ad alanı önekleri ile çalışmanızı ve denetlemenizi sağlar.

Içinde [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], XML adlarını <xref:System.Xml.Linq.XName>temsil eden sınıf. XML adları [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] API boyunca sık sık görünür ve bir XML adı <xref:System.Xml.Linq.XName> gerektiğinde bir parametre bulursunuz. Ancak, nadiren doğrudan <xref:System.Xml.Linq.XName>bir . <xref:System.Xml.Linq.XName>dizeden örtülü bir dönüştürme içerir.

Daha fazla bilgi için <xref:System.Xml.Linq.XNamespace> ve <xref:System.Xml.Linq.XName> bölümlerine bakın.

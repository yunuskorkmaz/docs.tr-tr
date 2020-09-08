---
title: Ad alanlarına genel bakış-LINQ to XML
description: XML adları, XML ad alanları ve XML ad alanı önekleri hakkında ve XName ve XNamespace sınıfları hakkında bilgi edinin.
ms.date: 07/20/2015
ms.assetid: 16283322-8238-4918-ab11-802ac6748eb7
ms.openlocfilehash: 81fe678a8d6be32461c675cc527595033e826165
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553142"
---
# <a name="namespaces-overview-linq-to-xml"></a>Ad alanlarına genel bakış (LINQ to XML)

Bu makalede *XML adları*, *XML ad alanları*, *XML ad alanı önekleri*ve <xref:System.Xml.Linq.XName> ve sınıfları tanıtılmaktadır <xref:System.Xml.Linq.XNamespace> .

XML adları genellikle XML programlamada karmaşıklık kaynağıdır. Xml adı bir XML ad alanından (XML ad alanı URI 'SI olarak da bilinir) ve yerel bir ada oluşur. XML ad alanı, .NET programındaki bir ad alanına benzerdir. Bir XML belgesinin çeşitli bölümleri arasında ad çakışmalarını önlemek için öğelerin ve özniteliklerin adlarını benzersiz bir şekilde nitelemenize olanak sağlar. Bir XML ad alanı bildirdiyseniz, yalnızca bu ad alanı içinde benzersiz olması gereken yerel bir ad seçebilirsiniz.

XML adlarının başka bir yönü de XML ad alanı önekleri olur ve bu da XML adlarının karmaşıklığına neden olur. Bu ön ekler, XML belgesini daha kısa ve anlaşılır hale getiren bir XML ad alanı için kısayol oluşturmanızı sağlar. Ancak, bir XML ön ekinin anlamı karmaşıklık ekleyen içeriğe bağlıdır. Örneğin, XML ön eki bir `aw` XML ağacının bir parçası olan BIR XML ad alanıyla ve başka bir bölümde farklı bir ad alanıyla ilişkilendirilebilir.

C# ile LINQ to XML kullanmanın avantajlarından biri, XML öneklerini kullanmak zorunda kalmazsınız. LINQ to XML bir XML belgesi yüklediğinde veya ayrıştırdığında, her bir XML ön eki karşılık gelen XML ad alanına çözümlenir. Bundan sonra, ad alanları kullanan bir belgeyle çalışırken, ad alanı ön eki aracılığıyla değil, ad alanı URI 'SI aracılığıyla ad alanlarına neredeyse her zaman erişirsiniz. Geliştiriciler LINQ to XML içindeki XML adlarıyla çalıştığında, her zaman tam olarak nitelenmiş bir XML adı (yani bir XML ad alanı ve yerel bir ad) ile çalışır. Ancak LINQ to XML, gerektiğinde ad alanı öneklerini birlikte çalışmanıza ve denetlemenize olanak tanır.

Visual Basic ve XML değişmez değerleri ile LINQ to XML kullanırken, ad uzaylarındaki belgelerle çalışırken ad alanı öneklerini kullanmanız gerekir.

LINQ to XML, XML adlarını temsil eden sınıf <xref:System.Xml.Linq.XName> . XML adları, LINQ to XML API 'SI boyunca sık görünür ve bir XML adının gerekli olduğu her yerde bir <xref:System.Xml.Linq.XName> parametre bulacaksınız. Ancak, doğrudan ile nadiren çalışmanız gerekir <xref:System.Xml.Linq.XName> . <xref:System.Xml.Linq.XName> dizeden örtük bir dönüştürme içerir.

Daha fazla bilgi için <xref:System.Xml.Linq.XNamespace> ve <xref:System.Xml.Linq.XName> bölümlerine bakın.

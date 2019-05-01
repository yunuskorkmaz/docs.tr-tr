---
title: XML Şema Nesne Modeli (SOM)
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a897a599-ffd1-43f9-8807-e58c8a7194cd
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 40a792f91ecd343684ff4c7921d6b21d25abecf7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61958879"
---
# <a name="xml-schema-object-model-som"></a><span data-ttu-id="c36ae-102">XML Şema Nesne Modeli (SOM)</span><span class="sxs-lookup"><span data-stu-id="c36ae-102">XML Schema Object Model (SOM)</span></span>
<span data-ttu-id="c36ae-103">Bir XML şeması oluşturmak ve yapısı uyumlu XML belgeleri doğrulamak için güçlü ve karmaşık bir araçtır.</span><span class="sxs-lookup"><span data-stu-id="c36ae-103">An XML schema is a powerful and complex tool for creating and validating structure in compliant XML documents.</span></span> <span data-ttu-id="c36ae-104">Benzer şekilde bir ilişkisel veritabanı modelleme verileri, bir şema belgeleri yanı sıra yapı ve bu öğeler için tha geçerli olması için izlemeniz gereken türleri kullanılabilir öğeleri belirterek XML belgelerin yapısını tanımlamak için bir yol sağlar t belirli şeması.</span><span class="sxs-lookup"><span data-stu-id="c36ae-104">Similar to data modeling in a relational database, a schema provides a way to define the structure of XML documents, by specifying the elements that can be used in the documents, as well as the structure and types that these elements must follow in order to be valid for that specific schema.</span></span>  
  
 <span data-ttu-id="c36ae-105">Şema nesne modeli (SOM) sınıflarda takımına <xref:System.Xml.Schema?displayProperty=nameWithType> bir şema bir dosyadan okunan veya bir şema bellek içi programlı olarak oluşturmanıza olanak sağlayan bir ad alanı.</span><span class="sxs-lookup"><span data-stu-id="c36ae-105">The Schema Object Model (SOM) provides a set of classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace that allow you to read a schema from a file or to programmatically create a schema in-memory.</span></span> <span data-ttu-id="c36ae-106">Şema sonra düzenleme, derlenmiş doğrulandı ve bir dosyaya yazılır çevrilebilen.</span><span class="sxs-lookup"><span data-stu-id="c36ae-106">The schema can then be traversed, editing, compiled, validated, or written to a file.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c36ae-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="c36ae-107">In This Section</span></span>  
 [<span data-ttu-id="c36ae-108">XML Şema Nesne Modeline (SOM) Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c36ae-108">XML Schema Object Model Overview</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)  
 <span data-ttu-id="c36ae-109">Şema nesne modeli (SOM) özellikleri ve sağladığı sınıfları açıklar.</span><span class="sxs-lookup"><span data-stu-id="c36ae-109">Describes the Schema Object Model (SOM) and the features and classes it provides.</span></span>  
  
 [<span data-ttu-id="c36ae-110">XML Şemaları Okuma ve Yazma</span><span class="sxs-lookup"><span data-stu-id="c36ae-110">Reading and Writing XML Schemas</span></span>](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)  
 <span data-ttu-id="c36ae-111">Okuma ve dosyaları veya diğer kaynakları XML şemaları yazma açıklar.</span><span class="sxs-lookup"><span data-stu-id="c36ae-111">Describes how to read and write XML schemas from files or other sources.</span></span>  
  
 [<span data-ttu-id="c36ae-112">XML Şemaları Derleme</span><span class="sxs-lookup"><span data-stu-id="c36ae-112">Building XML Schemas</span></span>](../../../../docs/standard/data/xml/building-xml-schemas.md)  
 <span data-ttu-id="c36ae-113">Sınıflarda kullanmayı açıklar <xref:System.Xml.Schema?displayProperty=nameWithType> XML şemaları bellek içi derleme için ad alanı.</span><span class="sxs-lookup"><span data-stu-id="c36ae-113">Describes how to use the classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace to build XML schemas in-memory.</span></span>  
  
 [<span data-ttu-id="c36ae-114">XML Şemalarını Çapraz Geçirme</span><span class="sxs-lookup"><span data-stu-id="c36ae-114">Traversing XML Schemas</span></span>](../../../../docs/standard/data/xml/traversing-xml-schemas.md)  
 <span data-ttu-id="c36ae-115">Bir XML Şeması öğeleri, öznitelikleri ve SOM. içinde depolanan türleri erişmek için geçiş işlemini açıklamaktadır</span><span class="sxs-lookup"><span data-stu-id="c36ae-115">Describes how to traverse an XML schema to access the elements, attributes, and types stored in the SOM.</span></span>  
  
 [<span data-ttu-id="c36ae-116">XML Şemalarını Düzenleme</span><span class="sxs-lookup"><span data-stu-id="c36ae-116">Editing XML Schemas</span></span>](../../../../docs/standard/data/xml/editing-xml-schemas.md)  
 <span data-ttu-id="c36ae-117">Bir XML Şeması düzenlemeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="c36ae-117">Describes how to edit an XML schema.</span></span>  
  
 [<span data-ttu-id="c36ae-118">XML Şemalarını Dahil Etme veya İçeri Aktarma</span><span class="sxs-lookup"><span data-stu-id="c36ae-118">Including or Importing XML Schemas</span></span>](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)  
 <span data-ttu-id="c36ae-119">Dahil etmek veya diğer XML şemaları yapısı içerir veya bunları alır şemayı tamamlamak için içeri aktarma işlemini açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="c36ae-119">Describes how to include or import other XML schemas to supplement the structure of the schema that includes or imports them.</span></span>

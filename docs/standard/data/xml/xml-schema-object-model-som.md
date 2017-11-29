---
title: "XML şema nesne modeli (SOM)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a897a599-ffd1-43f9-8807-e58c8a7194cd
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 44ce1337e347020926fe2dee29d70fe226ad087a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="xml-schema-object-model-som"></a><span data-ttu-id="e1858-102">XML şema nesne modeli (SOM)</span><span class="sxs-lookup"><span data-stu-id="e1858-102">XML Schema Object Model (SOM)</span></span>
<span data-ttu-id="e1858-103">Bir XML şeması oluşturma ve uyumlu XML belgelerini yapısında doğrulama için güçlü ve karmaşık bir araçtır.</span><span class="sxs-lookup"><span data-stu-id="e1858-103">An XML schema is a powerful and complex tool for creating and validating structure in compliant XML documents.</span></span> <span data-ttu-id="e1858-104">Benzer şekilde bir ilişkisel veritabanı modelleme verileri, bir şema belgeleri yanı sıra yapısı ve bu öğeler için tha geçerli olması için izlemeniz gereken türleri kullanılabilir öğeleri belirterek XML belgelerinin yapısını tanımlamak için bir yol sağlar t belirli şema.</span><span class="sxs-lookup"><span data-stu-id="e1858-104">Similar to data modeling in a relational database, a schema provides a way to define the structure of XML documents, by specifying the elements that can be used in the documents, as well as the structure and types that these elements must follow in order to be valid for that specific schema.</span></span>  
  
 <span data-ttu-id="e1858-105">Şema nesne modeli (SOM) sınıfları kümesi sağlar <xref:System.Xml.Schema?displayProperty=nameWithType> , bir dosyadan bir şema okumak için bir şema bellek içi programlı olarak oluşturmanıza izin ad alanı.</span><span class="sxs-lookup"><span data-stu-id="e1858-105">The Schema Object Model (SOM) provides a set of classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace that allow you to read a schema from a file or to programmatically create a schema in-memory.</span></span> <span data-ttu-id="e1858-106">Şema sonra düzenleme, derlenmiş, doğrulanmış veya bir dosyaya yazılır geçmesi.</span><span class="sxs-lookup"><span data-stu-id="e1858-106">The schema can then be traversed, editing, compiled, validated, or written to a file.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e1858-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="e1858-107">In This Section</span></span>  
 [<span data-ttu-id="e1858-108">XML şema nesne modeline genel bakış</span><span class="sxs-lookup"><span data-stu-id="e1858-108">XML Schema Object Model Overview</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)  
 <span data-ttu-id="e1858-109">Şema nesne modeli (SOM) özellikleri ve sağladığı sınıfları açıklar.</span><span class="sxs-lookup"><span data-stu-id="e1858-109">Describes the Schema Object Model (SOM) and the features and classes it provides.</span></span>  
  
 [<span data-ttu-id="e1858-110">Okuma ve yazma XML şemaları</span><span class="sxs-lookup"><span data-stu-id="e1858-110">Reading and Writing XML Schemas</span></span>](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)  
 <span data-ttu-id="e1858-111">XML şemaları dosyaları veya diğer kaynakları okumasına ve yazmasına açıklar.</span><span class="sxs-lookup"><span data-stu-id="e1858-111">Describes how to read and write XML schemas from files or other sources.</span></span>  
  
 [<span data-ttu-id="e1858-112">Yapı XML şemaları</span><span class="sxs-lookup"><span data-stu-id="e1858-112">Building XML Schemas</span></span>](../../../../docs/standard/data/xml/building-xml-schemas.md)  
 <span data-ttu-id="e1858-113">Sınıflarda kullanmayı açıklar <xref:System.Xml.Schema?displayProperty=nameWithType> XML şemaları bellek içi oluşturmak için ad alanı.</span><span class="sxs-lookup"><span data-stu-id="e1858-113">Describes how to use the classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace to build XML schemas in-memory.</span></span>  
  
 [<span data-ttu-id="e1858-114">XML şemaları çapraz geçiş yapma</span><span class="sxs-lookup"><span data-stu-id="e1858-114">Traversing XML Schemas</span></span>](../../../../docs/standard/data/xml/traversing-xml-schemas.md)  
 <span data-ttu-id="e1858-115">Öğeleri, öznitelikleri ve SOM. depolanan türleri erişmek için bir XML Şeması gezme açıklar</span><span class="sxs-lookup"><span data-stu-id="e1858-115">Describes how to traverse an XML schema to access the elements, attributes, and types stored in the SOM.</span></span>  
  
 [<span data-ttu-id="e1858-116">XML şemaları düzenleme</span><span class="sxs-lookup"><span data-stu-id="e1858-116">Editing XML Schemas</span></span>](../../../../docs/standard/data/xml/editing-xml-schemas.md)  
 <span data-ttu-id="e1858-117">Bir XML Şeması düzenlemeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="e1858-117">Describes how to edit an XML schema.</span></span>  
  
 [<span data-ttu-id="e1858-118">Dahil olmak üzere veya XML şemalarını içeri aktarma</span><span class="sxs-lookup"><span data-stu-id="e1858-118">Including or Importing XML Schemas</span></span>](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)  
 <span data-ttu-id="e1858-119">Dahil etmek veya içerir veya bunları alır şema yapısını tamamlamak için diğer XML şemaları alma açıklar.</span><span class="sxs-lookup"><span data-stu-id="e1858-119">Describes how to include or import other XML schemas to supplement the structure of the schema that includes or imports them.</span></span>

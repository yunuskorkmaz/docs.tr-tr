---
title: XML şema nesne modeli (SOM)
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a897a599-ffd1-43f9-8807-e58c8a7194cd
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 40a792f91ecd343684ff4c7921d6b21d25abecf7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33570131"
---
# <a name="xml-schema-object-model-som"></a><span data-ttu-id="e38e8-102">XML şema nesne modeli (SOM)</span><span class="sxs-lookup"><span data-stu-id="e38e8-102">XML Schema Object Model (SOM)</span></span>
<span data-ttu-id="e38e8-103">Bir XML şeması oluşturma ve uyumlu XML belgelerini yapısında doğrulama için güçlü ve karmaşık bir araçtır.</span><span class="sxs-lookup"><span data-stu-id="e38e8-103">An XML schema is a powerful and complex tool for creating and validating structure in compliant XML documents.</span></span> <span data-ttu-id="e38e8-104">Benzer şekilde bir ilişkisel veritabanı modelleme verileri, bir şema belgeleri yanı sıra yapısı ve bu öğeler için tha geçerli olması için izlemeniz gereken türleri kullanılabilir öğeleri belirterek XML belgelerinin yapısını tanımlamak için bir yol sağlar t belirli şema.</span><span class="sxs-lookup"><span data-stu-id="e38e8-104">Similar to data modeling in a relational database, a schema provides a way to define the structure of XML documents, by specifying the elements that can be used in the documents, as well as the structure and types that these elements must follow in order to be valid for that specific schema.</span></span>  
  
 <span data-ttu-id="e38e8-105">Şema nesne modeli (SOM) sınıfları kümesi sağlar <xref:System.Xml.Schema?displayProperty=nameWithType> , bir dosyadan bir şema okumak için bir şema bellek içi programlı olarak oluşturmanıza izin ad alanı.</span><span class="sxs-lookup"><span data-stu-id="e38e8-105">The Schema Object Model (SOM) provides a set of classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace that allow you to read a schema from a file or to programmatically create a schema in-memory.</span></span> <span data-ttu-id="e38e8-106">Şema sonra düzenleme, derlenmiş, doğrulanmış veya bir dosyaya yazılır geçmesi.</span><span class="sxs-lookup"><span data-stu-id="e38e8-106">The schema can then be traversed, editing, compiled, validated, or written to a file.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e38e8-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="e38e8-107">In This Section</span></span>  
 [<span data-ttu-id="e38e8-108">XML Şema Nesne Modeline (SOM) Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e38e8-108">XML Schema Object Model Overview</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)  
 <span data-ttu-id="e38e8-109">Şema nesne modeli (SOM) özellikleri ve sağladığı sınıfları açıklar.</span><span class="sxs-lookup"><span data-stu-id="e38e8-109">Describes the Schema Object Model (SOM) and the features and classes it provides.</span></span>  
  
 [<span data-ttu-id="e38e8-110">XML Şemaları Okuma ve Yazma</span><span class="sxs-lookup"><span data-stu-id="e38e8-110">Reading and Writing XML Schemas</span></span>](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)  
 <span data-ttu-id="e38e8-111">XML şemaları dosyaları veya diğer kaynakları okumasına ve yazmasına açıklar.</span><span class="sxs-lookup"><span data-stu-id="e38e8-111">Describes how to read and write XML schemas from files or other sources.</span></span>  
  
 [<span data-ttu-id="e38e8-112">XML Şemaları Derleme</span><span class="sxs-lookup"><span data-stu-id="e38e8-112">Building XML Schemas</span></span>](../../../../docs/standard/data/xml/building-xml-schemas.md)  
 <span data-ttu-id="e38e8-113">Sınıflarda kullanmayı açıklar <xref:System.Xml.Schema?displayProperty=nameWithType> XML şemaları bellek içi oluşturmak için ad alanı.</span><span class="sxs-lookup"><span data-stu-id="e38e8-113">Describes how to use the classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace to build XML schemas in-memory.</span></span>  
  
 [<span data-ttu-id="e38e8-114">XML Şemalarını Çapraz Geçirme</span><span class="sxs-lookup"><span data-stu-id="e38e8-114">Traversing XML Schemas</span></span>](../../../../docs/standard/data/xml/traversing-xml-schemas.md)  
 <span data-ttu-id="e38e8-115">Öğeleri, öznitelikleri ve SOM. depolanan türleri erişmek için bir XML Şeması gezme açıklar</span><span class="sxs-lookup"><span data-stu-id="e38e8-115">Describes how to traverse an XML schema to access the elements, attributes, and types stored in the SOM.</span></span>  
  
 [<span data-ttu-id="e38e8-116">XML Şemalarını Düzenleme</span><span class="sxs-lookup"><span data-stu-id="e38e8-116">Editing XML Schemas</span></span>](../../../../docs/standard/data/xml/editing-xml-schemas.md)  
 <span data-ttu-id="e38e8-117">Bir XML Şeması düzenlemeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="e38e8-117">Describes how to edit an XML schema.</span></span>  
  
 [<span data-ttu-id="e38e8-118">XML Şemalarını Dahil Etme veya İçeri Aktarma</span><span class="sxs-lookup"><span data-stu-id="e38e8-118">Including or Importing XML Schemas</span></span>](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)  
 <span data-ttu-id="e38e8-119">Dahil etmek veya içerir veya bunları alır şema yapısını tamamlamak için diğer XML şemaları alma açıklar.</span><span class="sxs-lookup"><span data-stu-id="e38e8-119">Describes how to include or import other XML schemas to supplement the structure of the schema that includes or imports them.</span></span>

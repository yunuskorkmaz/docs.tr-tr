---
title: XML Şema Nesne Modeli (SOM)
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a897a599-ffd1-43f9-8807-e58c8a7194cd
ms.openlocfilehash: 45bfba7bdab31b3edda59a350788e50182123ce0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709913"
---
# <a name="xml-schema-object-model-som"></a><span data-ttu-id="a2408-102">XML Şema Nesne Modeli (SOM)</span><span class="sxs-lookup"><span data-stu-id="a2408-102">XML Schema Object Model (SOM)</span></span>
<span data-ttu-id="a2408-103">XML şeması, uyumlu XML belgelerinde yapı oluşturmaya ve doğrulamaya yönelik güçlü ve karmaşık bir araçtır.</span><span class="sxs-lookup"><span data-stu-id="a2408-103">An XML schema is a powerful and complex tool for creating and validating structure in compliant XML documents.</span></span> <span data-ttu-id="a2408-104">İlişkisel bir veritabanındaki veri modelleme ile benzer şekilde, bir şema, belgelerde kullanılabilecek öğeleri belirterek XML belgelerinin yapısını tanımlamaya yönelik bir yol sağlar ve bu öğelerin Tha için geçerli olması için izlenmesi gereken yapı ve türler t özel şeması.</span><span class="sxs-lookup"><span data-stu-id="a2408-104">Similar to data modeling in a relational database, a schema provides a way to define the structure of XML documents, by specifying the elements that can be used in the documents, as well as the structure and types that these elements must follow in order to be valid for that specific schema.</span></span>  
  
 <span data-ttu-id="a2408-105">Şema nesne modeli (SOM), bir dosyadaki şemayı okumanızı veya bellek içinde programlı bir şekilde bir şema oluşturmasını sağlayan <xref:System.Xml.Schema?displayProperty=nameWithType> ad alanında bir sınıf kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="a2408-105">The Schema Object Model (SOM) provides a set of classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace that allow you to read a schema from a file or to programmatically create a schema in-memory.</span></span> <span data-ttu-id="a2408-106">Şema daha sonra bir dosyaya çapraz, düzenlenebilir, derlenir, doğrulanabilir veya yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="a2408-106">The schema can then be traversed, editing, compiled, validated, or written to a file.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a2408-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="a2408-107">In This Section</span></span>  
 [<span data-ttu-id="a2408-108">XML Şema Nesne Modeline (SOM) Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a2408-108">XML Schema Object Model Overview</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)  
 <span data-ttu-id="a2408-109">Şema nesne modeli (SOM) ve sağladığı özellikleri ve sınıfları açıklar.</span><span class="sxs-lookup"><span data-stu-id="a2408-109">Describes the Schema Object Model (SOM) and the features and classes it provides.</span></span>  
  
 [<span data-ttu-id="a2408-110">XML Şemaları Okuma ve Yazma</span><span class="sxs-lookup"><span data-stu-id="a2408-110">Reading and Writing XML Schemas</span></span>](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)  
 <span data-ttu-id="a2408-111">Dosyalardan veya diğer kaynaklardan XML şemaları okumayı ve yazmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="a2408-111">Describes how to read and write XML schemas from files or other sources.</span></span>  
  
 [<span data-ttu-id="a2408-112">XML Şemaları Derleme</span><span class="sxs-lookup"><span data-stu-id="a2408-112">Building XML Schemas</span></span>](../../../../docs/standard/data/xml/building-xml-schemas.md)  
 <span data-ttu-id="a2408-113">Bellek içinde XML şemaları derlemek için <xref:System.Xml.Schema?displayProperty=nameWithType> ad alanındaki sınıfların nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="a2408-113">Describes how to use the classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace to build XML schemas in-memory.</span></span>  
  
 [<span data-ttu-id="a2408-114">XML Şemalarını Çapraz Geçirme</span><span class="sxs-lookup"><span data-stu-id="a2408-114">Traversing XML Schemas</span></span>](../../../../docs/standard/data/xml/traversing-xml-schemas.md)  
 <span data-ttu-id="a2408-115">Bir XML şemasının, SOM 'da depolanan öğelere, özniteliklere ve türlere erişmek için nasıl gezeceği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a2408-115">Describes how to traverse an XML schema to access the elements, attributes, and types stored in the SOM.</span></span>  
  
 [<span data-ttu-id="a2408-116">XML Şemalarını Düzenleme</span><span class="sxs-lookup"><span data-stu-id="a2408-116">Editing XML Schemas</span></span>](../../../../docs/standard/data/xml/editing-xml-schemas.md)  
 <span data-ttu-id="a2408-117">Bir XML şemasının nasıl düzenleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="a2408-117">Describes how to edit an XML schema.</span></span>  
  
 [<span data-ttu-id="a2408-118">XML Şemalarını Dahil Etme veya İçeri Aktarma</span><span class="sxs-lookup"><span data-stu-id="a2408-118">Including or Importing XML Schemas</span></span>](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)  
 <span data-ttu-id="a2408-119">Dahil edilen veya içeri aktaran şemanın yapısını tamamlamak için başka XML şemaları eklemeyi veya içe aktarmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="a2408-119">Describes how to include or import other XML schemas to supplement the structure of the schema that includes or imports them.</span></span>

---
description: 'Daha fazla bilgi edinin: XML şema nesne modeli (SOM)'
title: XML Şema Nesne Modeli (SOM)
ms.date: 03/30/2017
ms.assetid: a897a599-ffd1-43f9-8807-e58c8a7194cd
ms.openlocfilehash: 7829c42bf5a2daef2d1245703c04b956cae9540d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782708"
---
# <a name="xml-schema-object-model-som"></a><span data-ttu-id="d7206-103">XML Şema Nesne Modeli (SOM)</span><span class="sxs-lookup"><span data-stu-id="d7206-103">XML Schema Object Model (SOM)</span></span>

<span data-ttu-id="d7206-104">XML şeması, uyumlu XML belgelerinde yapı oluşturmaya ve doğrulamaya yönelik güçlü ve karmaşık bir araçtır.</span><span class="sxs-lookup"><span data-stu-id="d7206-104">An XML schema is a powerful and complex tool for creating and validating structure in compliant XML documents.</span></span> <span data-ttu-id="d7206-105">İlişkisel bir veritabanındaki veri modellemesi gibi, bir şema, belgelerde kullanılabilecek öğeleri belirterek XML belgelerinin yapısını tanımlamaya yönelik bir yol sağlar ve bu öğelerin söz konusu şema için geçerli olması için izlenmesi gereken yapı ve türler de vardır.</span><span class="sxs-lookup"><span data-stu-id="d7206-105">Similar to data modeling in a relational database, a schema provides a way to define the structure of XML documents, by specifying the elements that can be used in the documents, as well as the structure and types that these elements must follow in order to be valid for that specific schema.</span></span>  
  
 <span data-ttu-id="d7206-106">Şema nesne modeli (SOM), <xref:System.Xml.Schema?displayProperty=nameWithType> bir dosyadaki şemayı okumanızı veya bir bellek içinde programlı bir şekilde şema oluşturmasını sağlayan ad alanında bir sınıf kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d7206-106">The Schema Object Model (SOM) provides a set of classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace that allow you to read a schema from a file or to programmatically create a schema in-memory.</span></span> <span data-ttu-id="d7206-107">Şema daha sonra bir dosyaya çapraz, düzenlenebilir, derlenir, doğrulanabilir veya yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="d7206-107">The schema can then be traversed, editing, compiled, validated, or written to a file.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d7206-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="d7206-108">In This Section</span></span>  

 [<span data-ttu-id="d7206-109">XML Şema Nesne Modeline (SOM) Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d7206-109">XML Schema Object Model Overview</span></span>](xml-schema-object-model-overview.md)  
 <span data-ttu-id="d7206-110">Şema nesne modeli (SOM) ve sağladığı özellikleri ve sınıfları açıklar.</span><span class="sxs-lookup"><span data-stu-id="d7206-110">Describes the Schema Object Model (SOM) and the features and classes it provides.</span></span>  
  
 [<span data-ttu-id="d7206-111">XML Şemaları Okuma ve Yazma</span><span class="sxs-lookup"><span data-stu-id="d7206-111">Reading and Writing XML Schemas</span></span>](reading-and-writing-xml-schemas.md)  
 <span data-ttu-id="d7206-112">Dosyalardan veya diğer kaynaklardan XML şemaları okumayı ve yazmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="d7206-112">Describes how to read and write XML schemas from files or other sources.</span></span>  
  
 [<span data-ttu-id="d7206-113">XML Şemaları Derleme</span><span class="sxs-lookup"><span data-stu-id="d7206-113">Building XML Schemas</span></span>](building-xml-schemas.md)  
 <span data-ttu-id="d7206-114"><xref:System.Xml.Schema?displayProperty=nameWithType>Bellek IÇINDE XML şemaları oluşturmak için ad alanındaki sınıfların nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="d7206-114">Describes how to use the classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace to build XML schemas in-memory.</span></span>  
  
 [<span data-ttu-id="d7206-115">XML Şemalarını Çapraz Geçirme</span><span class="sxs-lookup"><span data-stu-id="d7206-115">Traversing XML Schemas</span></span>](traversing-xml-schemas.md)  
 <span data-ttu-id="d7206-116">Bir XML şemasının, SOM 'da depolanan öğelere, özniteliklere ve türlere erişmek için nasıl gezeceği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d7206-116">Describes how to traverse an XML schema to access the elements, attributes, and types stored in the SOM.</span></span>  
  
 [<span data-ttu-id="d7206-117">XML Şemalarını Düzenleme</span><span class="sxs-lookup"><span data-stu-id="d7206-117">Editing XML Schemas</span></span>](editing-xml-schemas.md)  
 <span data-ttu-id="d7206-118">Bir XML şemasının nasıl düzenleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="d7206-118">Describes how to edit an XML schema.</span></span>  
  
 [<span data-ttu-id="d7206-119">XML Şemalarını Dahil Etme veya İçeri Aktarma</span><span class="sxs-lookup"><span data-stu-id="d7206-119">Including or Importing XML Schemas</span></span>](including-or-importing-xml-schemas.md)  
 <span data-ttu-id="d7206-120">Dahil edilen veya içeri aktaran şemanın yapısını tamamlamak için başka XML şemaları eklemeyi veya içe aktarmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="d7206-120">Describes how to include or import other XML schemas to supplement the structure of the schema that includes or imports them.</span></span>

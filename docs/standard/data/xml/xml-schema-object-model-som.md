---
title: XML Şema Nesne Modeli (SOM)
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a897a599-ffd1-43f9-8807-e58c8a7194cd
ms.openlocfilehash: 1de9fdf9950ba3ae356779ca802afb71f24a345e
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290324"
---
# <a name="xml-schema-object-model-som"></a><span data-ttu-id="5d5e3-102">XML Şema Nesne Modeli (SOM)</span><span class="sxs-lookup"><span data-stu-id="5d5e3-102">XML Schema Object Model (SOM)</span></span>
<span data-ttu-id="5d5e3-103">XML şeması, uyumlu XML belgelerinde yapı oluşturmaya ve doğrulamaya yönelik güçlü ve karmaşık bir araçtır.</span><span class="sxs-lookup"><span data-stu-id="5d5e3-103">An XML schema is a powerful and complex tool for creating and validating structure in compliant XML documents.</span></span> <span data-ttu-id="5d5e3-104">İlişkisel bir veritabanındaki veri modellemesi gibi, bir şema, belgelerde kullanılabilecek öğeleri belirterek XML belgelerinin yapısını tanımlamaya yönelik bir yol sağlar ve bu öğelerin söz konusu şema için geçerli olması için izlenmesi gereken yapı ve türler de vardır.</span><span class="sxs-lookup"><span data-stu-id="5d5e3-104">Similar to data modeling in a relational database, a schema provides a way to define the structure of XML documents, by specifying the elements that can be used in the documents, as well as the structure and types that these elements must follow in order to be valid for that specific schema.</span></span>  
  
 <span data-ttu-id="5d5e3-105">Şema nesne modeli (SOM), <xref:System.Xml.Schema?displayProperty=nameWithType> bir dosyadaki şemayı okumanızı veya bir bellek içinde programlı bir şekilde şema oluşturmasını sağlayan ad alanında bir sınıf kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="5d5e3-105">The Schema Object Model (SOM) provides a set of classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace that allow you to read a schema from a file or to programmatically create a schema in-memory.</span></span> <span data-ttu-id="5d5e3-106">Şema daha sonra bir dosyaya çapraz, düzenlenebilir, derlenir, doğrulanabilir veya yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="5d5e3-106">The schema can then be traversed, editing, compiled, validated, or written to a file.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5d5e3-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="5d5e3-107">In This Section</span></span>  
 [<span data-ttu-id="5d5e3-108">XML Şema Nesne Modeline (SOM) Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5d5e3-108">XML Schema Object Model Overview</span></span>](xml-schema-object-model-overview.md)  
 <span data-ttu-id="5d5e3-109">Şema nesne modeli (SOM) ve sağladığı özellikleri ve sınıfları açıklar.</span><span class="sxs-lookup"><span data-stu-id="5d5e3-109">Describes the Schema Object Model (SOM) and the features and classes it provides.</span></span>  
  
 [<span data-ttu-id="5d5e3-110">XML Şemaları Okuma ve Yazma</span><span class="sxs-lookup"><span data-stu-id="5d5e3-110">Reading and Writing XML Schemas</span></span>](reading-and-writing-xml-schemas.md)  
 <span data-ttu-id="5d5e3-111">Dosyalardan veya diğer kaynaklardan XML şemaları okumayı ve yazmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="5d5e3-111">Describes how to read and write XML schemas from files or other sources.</span></span>  
  
 [<span data-ttu-id="5d5e3-112">XML Şemaları Derleme</span><span class="sxs-lookup"><span data-stu-id="5d5e3-112">Building XML Schemas</span></span>](building-xml-schemas.md)  
 <span data-ttu-id="5d5e3-113"><xref:System.Xml.Schema?displayProperty=nameWithType>Bellek IÇINDE XML şemaları oluşturmak için ad alanındaki sınıfların nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="5d5e3-113">Describes how to use the classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace to build XML schemas in-memory.</span></span>  
  
 [<span data-ttu-id="5d5e3-114">XML Şemalarını Çapraz Geçirme</span><span class="sxs-lookup"><span data-stu-id="5d5e3-114">Traversing XML Schemas</span></span>](traversing-xml-schemas.md)  
 <span data-ttu-id="5d5e3-115">Bir XML şemasının, SOM 'da depolanan öğelere, özniteliklere ve türlere erişmek için nasıl gezeceği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5d5e3-115">Describes how to traverse an XML schema to access the elements, attributes, and types stored in the SOM.</span></span>  
  
 [<span data-ttu-id="5d5e3-116">XML Şemalarını Düzenleme</span><span class="sxs-lookup"><span data-stu-id="5d5e3-116">Editing XML Schemas</span></span>](editing-xml-schemas.md)  
 <span data-ttu-id="5d5e3-117">Bir XML şemasının nasıl düzenleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="5d5e3-117">Describes how to edit an XML schema.</span></span>  
  
 [<span data-ttu-id="5d5e3-118">XML Şemalarını Dahil Etme veya İçeri Aktarma</span><span class="sxs-lookup"><span data-stu-id="5d5e3-118">Including or Importing XML Schemas</span></span>](including-or-importing-xml-schemas.md)  
 <span data-ttu-id="5d5e3-119">Dahil edilen veya içeri aktaran şemanın yapısını tamamlamak için başka XML şemaları eklemeyi veya içe aktarmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="5d5e3-119">Describes how to include or import other XML schemas to supplement the structure of the schema that includes or imports them.</span></span>

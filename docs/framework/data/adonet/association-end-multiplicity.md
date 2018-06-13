---
title: İlişki uç Çokluk
ms.date: 03/30/2017
ms.assetid: 340926ee-aefb-4bef-92cc-453e5251fd03
ms.openlocfilehash: 2f70fa4b163b957ea1e43506033863c3540b0418
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32755880"
---
# <a name="association-end-multiplicity"></a><span data-ttu-id="bf68f-102">İlişki uç Çokluk</span><span class="sxs-lookup"><span data-stu-id="bf68f-102">association end multiplicity</span></span>
<span data-ttu-id="bf68f-103">*İlişki uç Çokluk* sayısını tanımlar [varlık türü](../../../../docs/framework/data/adonet/entity-type.md) bir sonunda olabilir örnekleri bir [ilişkilendirme](../../../../docs/framework/data/adonet/association-type.md).</span><span class="sxs-lookup"><span data-stu-id="bf68f-103">*Association end multiplicity* defines the number of [entity type](../../../../docs/framework/data/adonet/entity-type.md) instances that can be at one end of an [association](../../../../docs/framework/data/adonet/association-type.md).</span></span>  
  
 <span data-ttu-id="bf68f-104">Bir ilişkilendirme end Çokluk şu değerlerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="bf68f-104">An association end multiplicity can have one of the following values:</span></span>  
  
-   <span data-ttu-id="bf68f-105">bir (1): Bu tam olarak bir varlık türü örneği var ilişkisi sonunda gösterir.</span><span class="sxs-lookup"><span data-stu-id="bf68f-105">one (1): Indicates that exactly one entity type instance exists at the association end.</span></span>  
  
-   <span data-ttu-id="bf68f-106">sıfır veya bir (0.. 1 çokluğa): sıfır veya bir varlık türü örnekleri ilişkilendirme sonunda mevcut olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="bf68f-106">zero or one (0..1): Indicates that zero or one entity type instances exist at the association end.</span></span>  
  
-   <span data-ttu-id="bf68f-107">birçok (\*): sıfır, bir veya daha fazla varlık türü örnekleri ilişkilendirme sonunda mevcut olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="bf68f-107">many (\*): Indicates that zero, one, or more entity type instances exist at the association end.</span></span>  
  
 <span data-ttu-id="bf68f-108">Bir ilişkilendirme genellikle kendi ilişkilendirme son Çeşitlilikler tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="bf68f-108">An association is often characterized by its association end multiplicities.</span></span> <span data-ttu-id="bf68f-109">Örneğin, bir ilişki uçlarından biri (1) ve çok sayıda Çeşitlilikler (\*) varsa, ilişki bir-çok ilişkisi adı verilir.</span><span class="sxs-lookup"><span data-stu-id="bf68f-109">For example, if the ends of an association have multiplicities one (1) and many (\*), the association is called a one-to-many association.</span></span> <span data-ttu-id="bf68f-110">Aşağıdaki örnekte `PublishedBy` ilişkilendirmedir bir-çok ilişkisi (birçok books yayımcı yayımlar ve kitap bir yayımcı tarafından yayımlanan).</span><span class="sxs-lookup"><span data-stu-id="bf68f-110">In the example below, the `PublishedBy` association is a one-to-many association (a publisher publishes many books and a book is published by one publisher).</span></span> <span data-ttu-id="bf68f-111">`WrittenBy` İlişkilendirmedir bir çok-çok ilişkisi (kitap birden çok yazar olabilir ve bir yazar birden çok books yazabilirsiniz).</span><span class="sxs-lookup"><span data-stu-id="bf68f-111">The `WrittenBy` association is a many-to-many association (a book can have multiple authors and an author can write multiple books).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf68f-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="bf68f-112">Example</span></span>  
 <span data-ttu-id="bf68f-113">Aşağıdaki diyagramda iki ilişkilendirmeleri kavramsal modelle gösterir: `PublishedBy` ve `WrittenBy`.</span><span class="sxs-lookup"><span data-stu-id="bf68f-113">The diagram below shows a conceptual model with two associations: `PublishedBy` and `WrittenBy`.</span></span> <span data-ttu-id="bf68f-114">İlişkilendirme sona `PublishedBy` ilişkisi olan `Book` ve `Publisher` varlık türleri.</span><span class="sxs-lookup"><span data-stu-id="bf68f-114">The association ends for the `PublishedBy` association are the `Book` and `Publisher` entity types.</span></span> <span data-ttu-id="bf68f-115">Çokluğu `Publisher` sonudur bir (1) ve çokluğu `Book` sonudur birçok (\*).</span><span class="sxs-lookup"><span data-stu-id="bf68f-115">The multiplicity of the `Publisher` end is one (1) and the multiplicity of the `Book` end is many (\*).</span></span>  
  
 <span data-ttu-id="bf68f-116">![Örnek modeli](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span><span class="sxs-lookup"><span data-stu-id="bf68f-116">![Example Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span></span>  
  
 <span data-ttu-id="bf68f-117">Kavramsal şema tanım dili adlı bir etki alanına özgü dil (DSL) ADO.NET Entity Framework kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="bf68f-117">The ADO.NET Entity Framework uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="bf68f-118">Aşağıdaki CSDL tanımlar `PublishedBy` Yukarıdaki diyagramda gösterildiği ilişkilendirme:</span><span class="sxs-lookup"><span data-stu-id="bf68f-118">The following CSDL defines the `PublishedBy` association shown in the diagram above:</span></span>  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a><span data-ttu-id="bf68f-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bf68f-119">See Also</span></span>  
 [<span data-ttu-id="bf68f-120">Varlık Veri Modeli Temel Kavramları</span><span class="sxs-lookup"><span data-stu-id="bf68f-120">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="bf68f-121">Varlık Veri Modeli</span><span class="sxs-lookup"><span data-stu-id="bf68f-121">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)

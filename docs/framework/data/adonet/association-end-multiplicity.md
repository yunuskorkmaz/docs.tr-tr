---
title: İlişki sonu çeşitlilik
ms.date: 03/30/2017
ms.assetid: 340926ee-aefb-4bef-92cc-453e5251fd03
ms.openlocfilehash: 151b15a6df021a25f6c3ecea00af147c6b7196ff
ms.sourcegitcommit: 462dc41a13942e467984e48f4018d1f79ae67346
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58185681"
---
# <a name="association-end-multiplicity"></a><span data-ttu-id="54608-102">İlişki sonu çeşitlilik</span><span class="sxs-lookup"><span data-stu-id="54608-102">association end multiplicity</span></span>
<span data-ttu-id="54608-103">*İlişki sonu çoğulluk* sayısını tanımlayan [varlık türü](../../../../docs/framework/data/adonet/entity-type.md) bir sonunda olabilir örnekleri bir [ilişkilendirme](../../../../docs/framework/data/adonet/association-type.md).</span><span class="sxs-lookup"><span data-stu-id="54608-103">*Association end multiplicity* defines the number of [entity type](../../../../docs/framework/data/adonet/entity-type.md) instances that can be at one end of an [association](../../../../docs/framework/data/adonet/association-type.md).</span></span>  
  
 <span data-ttu-id="54608-104">Bir ilişkilendirme end çoğulluk aşağıdaki değerlerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="54608-104">An association end multiplicity can have one of the following values:</span></span>  
  
-   <span data-ttu-id="54608-105">bir (1): Bu tam olarak bir varlık türü örneği ilişkilendirme sonunda olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="54608-105">one (1): Indicates that exactly one entity type instance exists at the association end.</span></span>  
  
-   <span data-ttu-id="54608-106">sıfır veya bir (0..1): Sıfır veya bir varlık türü örneklerini ilişkilendirme sonunda bulunduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="54608-106">zero or one (0..1): Indicates that zero or one entity type instances exist at the association end.</span></span>  
  
-   <span data-ttu-id="54608-107">çok sayıda (\*): sıfır, bir veya daha fazla varlık türü örneklerini ilişkilendirme sonunda bulunduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="54608-107">many (\*): Indicates that zero, one, or more entity type instances exist at the association end.</span></span>  
  
 <span data-ttu-id="54608-108">Bir ilişkilendirme genellikle, ilişki uç Çeşitlilikler tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="54608-108">An association is often characterized by its association end multiplicities.</span></span> <span data-ttu-id="54608-109">Örneğin, bir ilişki sonu bir (1) ve çok sayıda Çeşitlilikler varsa (\*), ilişkilendirmenin bir-çok ilişkisi adı verilir.</span><span class="sxs-lookup"><span data-stu-id="54608-109">For example, if the ends of an association have multiplicities one (1) and many (\*), the association is called a one-to-many association.</span></span> <span data-ttu-id="54608-110">Aşağıdaki örnekte `PublishedBy` işbirliğidir bir-çok ilişkisi (bir çok kitap bir yayımcı yayımlar ve bir kitap bir yayımcı tarafından yayımlanır).</span><span class="sxs-lookup"><span data-stu-id="54608-110">In the example below, the `PublishedBy` association is a one-to-many association (a publisher publishes many books and a book is published by one publisher).</span></span> <span data-ttu-id="54608-111">`WrittenBy` Bir çoktan çoğa ilişki bir ilişkilendirmedir (bir kitap birden çok yazarlar olabilir ve birden çok books Yazar yazabilirsiniz).</span><span class="sxs-lookup"><span data-stu-id="54608-111">The `WrittenBy` association is a many-to-many association (a book can have multiple authors and an author can write multiple books).</span></span>  
  
## <a name="example"></a><span data-ttu-id="54608-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="54608-112">Example</span></span>  
 <span data-ttu-id="54608-113">Aşağıdaki diyagramda iki ilişkilendirmeleri kavramsal bir modelle gösterilmektedir: `PublishedBy` ve `WrittenBy`.</span><span class="sxs-lookup"><span data-stu-id="54608-113">The diagram below shows a conceptual model with two associations: `PublishedBy` and `WrittenBy`.</span></span> <span data-ttu-id="54608-114">İlişkilendirme sona için `PublishedBy` ilişkisi olan `Book` ve `Publisher` varlık türleri.</span><span class="sxs-lookup"><span data-stu-id="54608-114">The association ends for the `PublishedBy` association are the `Book` and `Publisher` entity types.</span></span> <span data-ttu-id="54608-115">Çokluğu `Publisher` sonudur bir (1) ve çeşitliliğini `Book` sonudur birçok (\*).</span><span class="sxs-lookup"><span data-stu-id="54608-115">The multiplicity of the `Publisher` end is one (1) and the multiplicity of the `Book` end is many (\*).</span></span>  
  
 <span data-ttu-id="54608-116">![Örnek Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span><span class="sxs-lookup"><span data-stu-id="54608-116">![Example Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span></span>  
  
 <span data-ttu-id="54608-117">ADO.NET varlık çerçevesi kavramsal şema tanım dili olarak adlandırılan bir etki alanına özgü dil (DSL) kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="54608-117">The ADO.NET Entity Framework uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="54608-118">Aşağıdaki CSDL tanımlar `PublishedBy` Yukarıdaki diyagramda gösterilen ilişkiyi:</span><span class="sxs-lookup"><span data-stu-id="54608-118">The following CSDL defines the `PublishedBy` association shown in the diagram above:</span></span>  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a><span data-ttu-id="54608-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="54608-119">See also</span></span>
- [<span data-ttu-id="54608-120">Varlık Veri Modeli Temel Kavramları</span><span class="sxs-lookup"><span data-stu-id="54608-120">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [<span data-ttu-id="54608-121">Varlık Veri Modeli</span><span class="sxs-lookup"><span data-stu-id="54608-121">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)

---
title: association end
ms.date: 03/30/2017
ms.assetid: 2c345213-0296-4d90-ac6d-cef179798a75
ms.openlocfilehash: 00e3a7d855957ae539ea652dc8cde3ed8841dda5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153449"
---
# <a name="association-end"></a><span data-ttu-id="59560-102">association end</span><span class="sxs-lookup"><span data-stu-id="59560-102">association end</span></span>

<span data-ttu-id="59560-103">Bir *ilişkilendirme End* 'i, [bir ilişkilendirmenin bir](association-type.md) sonundaki [varlık türünü](entity-type.md) ve bir ilişkinin o ucunda bulunabilir varlık türü örneklerinin sayısını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="59560-103">An *association end* identifies the [entity type](entity-type.md) on one end of an [association](association-type.md) and the number of entity type instances that can exist at that end of an association.</span></span> <span data-ttu-id="59560-104">İlişki uçları bir ilişkinin parçası olarak tanımlanır; bir ilişkilendirme tam olarak iki ilişkilendirme bitmelidir.</span><span class="sxs-lookup"><span data-stu-id="59560-104">Association ends are defined as part of an association; an association must have exactly two association ends.</span></span> <span data-ttu-id="59560-105">[Gezinti özellikleri](navigation-property.md) , bir ilişkilendirme ucundan diğerine kadar gezinmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="59560-105">[Navigation properties](navigation-property.md) allow for navigation from one association end to the other.</span></span>  
  
 <span data-ttu-id="59560-106">Bir ilişkilendirme End tanımı aşağıdaki bilgileri içerir:</span><span class="sxs-lookup"><span data-stu-id="59560-106">An association end definition contains the following information:</span></span>  
  
- <span data-ttu-id="59560-107">İlişkilendirmede yer alan varlık türlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="59560-107">One of the entity types involved in the association.</span></span> <span data-ttu-id="59560-108">Istenir</span><span class="sxs-lookup"><span data-stu-id="59560-108">(Required)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="59560-109">Belirli bir ilişki için, her ilişkilendirme ucu için belirtilen varlık türü aynı olabilir.</span><span class="sxs-lookup"><span data-stu-id="59560-109">For a given association, the entity type specified for each association end can be the same.</span></span> <span data-ttu-id="59560-110">Bu, kendine ilişkilendirme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="59560-110">This creates a self-association.</span></span>  
  
- <span data-ttu-id="59560-111">İlişkilendirmenin bir ucunda olabilecek varlık türü örneklerinin sayısını gösteren bir [ilişkilendirme End çoğulluğu](association-end-multiplicity.md) .</span><span class="sxs-lookup"><span data-stu-id="59560-111">An [association end multiplicity](association-end-multiplicity.md) that indicates the number of entity type instances that can be at one end of the association.</span></span> <span data-ttu-id="59560-112">Bir ilişki uç çoğulluğu bir (1), sıfır veya bir (0.. 1) veya çok () değerine sahip olabilir \* .</span><span class="sxs-lookup"><span data-stu-id="59560-112">An association end multiplicity can have a value of one (1), zero or one (0..1), or many (\*).</span></span>  
  
- <span data-ttu-id="59560-113">İlişki ucu için bir ad.</span><span class="sxs-lookup"><span data-stu-id="59560-113">A name for the association end.</span></span> <span data-ttu-id="59560-114">(İsteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="59560-114">(Optional)</span></span>  
  
- <span data-ttu-id="59560-115">İlişki ucunda gerçekleştirilen, silme sırasında Cascade gibi işlemler hakkında bilgiler.</span><span class="sxs-lookup"><span data-stu-id="59560-115">Information about operations that are performed on the association end, such as cascade on delete.</span></span> <span data-ttu-id="59560-116">(İsteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="59560-116">(Optional)</span></span>  
  
## <a name="example"></a><span data-ttu-id="59560-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="59560-117">Example</span></span>  

 <span data-ttu-id="59560-118">Aşağıdaki diyagramda iki ilişkiye sahip kavramsal bir model gösterilmektedir: `PublishedBy` ve `WrittenBy` .</span><span class="sxs-lookup"><span data-stu-id="59560-118">The diagram below shows a conceptual model with two associations: `PublishedBy` and `WrittenBy`.</span></span> <span data-ttu-id="59560-119">İlişkilendirme için ilişkilendirme sonlanır `PublishedBy` `Book` ve `Publisher` varlık türleridir.</span><span class="sxs-lookup"><span data-stu-id="59560-119">The association ends for the `PublishedBy` association are the `Book` and `Publisher` entity types.</span></span> <span data-ttu-id="59560-120">Ucun çoğulluğu `Publisher` bir (1) ve ucun çoğulluğu `Book` birçok (), bir \* yayımcının çok sayıda kitap yayımladığını ve bir kitabın bir yayımcı tarafından yayımlandığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="59560-120">The multiplicity of the `Publisher` end is one (1) and the multiplicity of the `Book` end is many (\*), indicating that a publisher publishes many books and a book is published by one publisher.</span></span>  
  
 ![Üç varlık türüne sahip örnek model](./media/association-end/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="59560-122">ADO.NET Entity Framework kavramsal model tanımlamak için kavramsal şema tanım dili ([csdl](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) adlı bir etki alanına özgü DIL (DSL) kullanır.</span><span class="sxs-lookup"><span data-stu-id="59560-122">The ADO.NET Entity Framework uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="59560-123">Aşağıdaki CSDL, `PublishedBy` Yukarıdaki diyagramda gösterilen ilişkilendirmeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="59560-123">The CSDL below defines the `PublishedBy` association shown in the diagram above.</span></span> <span data-ttu-id="59560-124">Her ilişkilendirme ucunun türü, adı ve çoğulluk özelliklerinin, XML öznitelikleri ( `Type` `Role` sırasıyla, ve öznitelikleri) tarafından belirtildiğine unutmayın `Multiplicity` .</span><span class="sxs-lookup"><span data-stu-id="59560-124">Note that the type, name, and multiplicity of each association end are specified by XML attributes (the `Type`, `Role`, and `Multiplicity` attributes, respectively).</span></span> <span data-ttu-id="59560-125">Bir uçta gerçekleştirilen işlemlerle ilgili isteğe bağlı bilgiler bir XML öğesinde ( `OnDelete` öğesi) belirtilir.</span><span class="sxs-lookup"><span data-stu-id="59560-125">Optional information about operations performed on an end is specified in an XML element (the `OnDelete` element).</span></span> <span data-ttu-id="59560-126">Bu durumda, bir yayımcı silinirse tüm ilişkili kitaplardır.</span><span class="sxs-lookup"><span data-stu-id="59560-126">In this case, if a publisher is deleted, so are all associated books.</span></span>  
  
 [!code-xml[EDM_Example_Model#AssociationEnd](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#associationend)]  
  
## <a name="see-also"></a><span data-ttu-id="59560-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="59560-127">See also</span></span>

- [<span data-ttu-id="59560-128">Varlık Veri Modeli Temel Kavramları</span><span class="sxs-lookup"><span data-stu-id="59560-128">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="59560-129">Varlık Veri Modeli</span><span class="sxs-lookup"><span data-stu-id="59560-129">Entity Data Model</span></span>](entity-data-model.md)

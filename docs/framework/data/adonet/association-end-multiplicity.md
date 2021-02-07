---
description: 'Daha fazla bilgi edinin: ilişkilendirme uç çoğulluğu'
title: association end multiplicity
ms.date: 03/30/2017
ms.assetid: 340926ee-aefb-4bef-92cc-453e5251fd03
ms.openlocfilehash: 4b708406192e8a6e34119b47261d8986829f2a43
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697705"
---
# <a name="association-end-multiplicity"></a><span data-ttu-id="d34f2-103">association end multiplicity</span><span class="sxs-lookup"><span data-stu-id="d34f2-103">association end multiplicity</span></span>

<span data-ttu-id="d34f2-104">*Association End çoğulluğu* , [ilişkilendirmenin](association-type.md)bir ucunda olabilecek [varlık türü](entity-type.md) örneklerinin sayısını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d34f2-104">*Association end multiplicity* defines the number of [entity type](entity-type.md) instances that can be at one end of an [association](association-type.md).</span></span>  
  
 <span data-ttu-id="d34f2-105">Bir ilişkilendirme End çoğulluğu aşağıdaki değerlerden birine sahip olabilir:</span><span class="sxs-lookup"><span data-stu-id="d34f2-105">An association end multiplicity can have one of the following values:</span></span>  
  
- <span data-ttu-id="d34f2-106">bir (1): ilişkilendirme ucunda tam olarak bir varlık türü örneğinin bulunduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="d34f2-106">one (1): Indicates that exactly one entity type instance exists at the association end.</span></span>  
  
- <span data-ttu-id="d34f2-107">sıfır veya bir (0.. 1): ilişkilendirme ucunda sıfır veya bir varlık türü örneklerinin bulunduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="d34f2-107">zero or one (0..1): Indicates that zero or one entity type instances exist at the association end.</span></span>  
  
- <span data-ttu-id="d34f2-108">Çok ( \* ): ilişkilendirme ucunda sıfır, bir veya daha fazla varlık türü örneğinin var olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="d34f2-108">many (\*): Indicates that zero, one, or more entity type instances exist at the association end.</span></span>  
  
 <span data-ttu-id="d34f2-109">İlişki genellikle ilişkilendirme uç çarpanlarıyla belirlenir.</span><span class="sxs-lookup"><span data-stu-id="d34f2-109">An association is often characterized by its association end multiplicities.</span></span> <span data-ttu-id="d34f2-110">Örneğin, bir ilişkinin uçları bir (1) ve çok () çarpanlarına sahip olursa \* , ilişkilendirme bire çok ilişkilendirme olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="d34f2-110">For example, if the ends of an association have multiplicities one (1) and many (\*), the association is called a one-to-many association.</span></span> <span data-ttu-id="d34f2-111">Aşağıdaki örnekte, `PublishedBy` ilişkilendirme bire çok ilişkidir (yayımcı birçok kitabı yayınlar ve bir kitap tek bir yayımcı tarafından yayımlanır).</span><span class="sxs-lookup"><span data-stu-id="d34f2-111">In the example below, the `PublishedBy` association is a one-to-many association (a publisher publishes many books and a book is published by one publisher).</span></span> <span data-ttu-id="d34f2-112">`WrittenBy`İlişkilendirme çok-çok ilişkisi (bir kitapta birden çok yazar olabilir ve bir yazar birden çok kitap yazabilir).</span><span class="sxs-lookup"><span data-stu-id="d34f2-112">The `WrittenBy` association is a many-to-many association (a book can have multiple authors and an author can write multiple books).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d34f2-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="d34f2-113">Example</span></span>  

 <span data-ttu-id="d34f2-114">Aşağıdaki diyagramda iki ilişkiye sahip kavramsal bir model gösterilmektedir: `PublishedBy` ve `WrittenBy` .</span><span class="sxs-lookup"><span data-stu-id="d34f2-114">The diagram below shows a conceptual model with two associations: `PublishedBy` and `WrittenBy`.</span></span> <span data-ttu-id="d34f2-115">İlişkilendirme için ilişkilendirme sonlanır `PublishedBy` `Book` ve `Publisher` varlık türleridir.</span><span class="sxs-lookup"><span data-stu-id="d34f2-115">The association ends for the `PublishedBy` association are the `Book` and `Publisher` entity types.</span></span> <span data-ttu-id="d34f2-116">Ucunun çoğulluğu `Publisher` bir (1), ucun çoğulluğu ise `Book` çok ( \* ).</span><span class="sxs-lookup"><span data-stu-id="d34f2-116">The multiplicity of the `Publisher` end is one (1) and the multiplicity of the `Book` end is many (\*).</span></span>  
  
 ![Üç varlık türüne sahip örnek model](./media/association-end-multiplicity/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="d34f2-118">ADO.NET Entity Framework kavramsal model tanımlamak için kavramsal şema tanım dili ([csdl](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) adlı bir etki alanına özgü DIL (DSL) kullanır.</span><span class="sxs-lookup"><span data-stu-id="d34f2-118">The ADO.NET Entity Framework uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="d34f2-119">Aşağıdaki CSDL, `PublishedBy` Yukarıdaki diyagramda gösterilen ilişkilendirmeyi tanımlar:</span><span class="sxs-lookup"><span data-stu-id="d34f2-119">The following CSDL defines the `PublishedBy` association shown in the diagram above:</span></span>  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a><span data-ttu-id="d34f2-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d34f2-120">See also</span></span>

- [<span data-ttu-id="d34f2-121">Varlık Veri Modeli Temel Kavramları</span><span class="sxs-lookup"><span data-stu-id="d34f2-121">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="d34f2-122">Varlık Veri Modeli</span><span class="sxs-lookup"><span data-stu-id="d34f2-122">Entity Data Model</span></span>](entity-data-model.md)

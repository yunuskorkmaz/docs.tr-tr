---
title: association end multiplicity
ms.date: 03/30/2017
ms.assetid: 340926ee-aefb-4bef-92cc-453e5251fd03
ms.openlocfilehash: cf9e6b5af0dc6a33af364901c631b4ce66fe0480
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153514"
---
# <a name="association-end-multiplicity"></a><span data-ttu-id="8eddd-102">association end multiplicity</span><span class="sxs-lookup"><span data-stu-id="8eddd-102">association end multiplicity</span></span>

<span data-ttu-id="8eddd-103">*Association End çoğulluğu* , [ilişkilendirmenin](association-type.md)bir ucunda olabilecek [varlık türü](entity-type.md) örneklerinin sayısını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8eddd-103">*Association end multiplicity* defines the number of [entity type](entity-type.md) instances that can be at one end of an [association](association-type.md).</span></span>  
  
 <span data-ttu-id="8eddd-104">Bir ilişkilendirme End çoğulluğu aşağıdaki değerlerden birine sahip olabilir:</span><span class="sxs-lookup"><span data-stu-id="8eddd-104">An association end multiplicity can have one of the following values:</span></span>  
  
- <span data-ttu-id="8eddd-105">bir (1): ilişkilendirme ucunda tam olarak bir varlık türü örneğinin bulunduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="8eddd-105">one (1): Indicates that exactly one entity type instance exists at the association end.</span></span>  
  
- <span data-ttu-id="8eddd-106">sıfır veya bir (0.. 1): ilişkilendirme ucunda sıfır veya bir varlık türü örneklerinin bulunduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="8eddd-106">zero or one (0..1): Indicates that zero or one entity type instances exist at the association end.</span></span>  
  
- <span data-ttu-id="8eddd-107">Çok ( \* ): ilişkilendirme ucunda sıfır, bir veya daha fazla varlık türü örneğinin var olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="8eddd-107">many (\*): Indicates that zero, one, or more entity type instances exist at the association end.</span></span>  
  
 <span data-ttu-id="8eddd-108">İlişki genellikle ilişkilendirme uç çarpanlarıyla belirlenir.</span><span class="sxs-lookup"><span data-stu-id="8eddd-108">An association is often characterized by its association end multiplicities.</span></span> <span data-ttu-id="8eddd-109">Örneğin, bir ilişkinin uçları bir (1) ve çok () çarpanlarına sahip olursa \* , ilişkilendirme bire çok ilişkilendirme olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="8eddd-109">For example, if the ends of an association have multiplicities one (1) and many (\*), the association is called a one-to-many association.</span></span> <span data-ttu-id="8eddd-110">Aşağıdaki örnekte, `PublishedBy` ilişkilendirme bire çok ilişkidir (yayımcı birçok kitabı yayınlar ve bir kitap tek bir yayımcı tarafından yayımlanır).</span><span class="sxs-lookup"><span data-stu-id="8eddd-110">In the example below, the `PublishedBy` association is a one-to-many association (a publisher publishes many books and a book is published by one publisher).</span></span> <span data-ttu-id="8eddd-111">`WrittenBy`İlişkilendirme çok-çok ilişkisi (bir kitapta birden çok yazar olabilir ve bir yazar birden çok kitap yazabilir).</span><span class="sxs-lookup"><span data-stu-id="8eddd-111">The `WrittenBy` association is a many-to-many association (a book can have multiple authors and an author can write multiple books).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8eddd-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="8eddd-112">Example</span></span>  

 <span data-ttu-id="8eddd-113">Aşağıdaki diyagramda iki ilişkiye sahip kavramsal bir model gösterilmektedir: `PublishedBy` ve `WrittenBy` .</span><span class="sxs-lookup"><span data-stu-id="8eddd-113">The diagram below shows a conceptual model with two associations: `PublishedBy` and `WrittenBy`.</span></span> <span data-ttu-id="8eddd-114">İlişkilendirme için ilişkilendirme sonlanır `PublishedBy` `Book` ve `Publisher` varlık türleridir.</span><span class="sxs-lookup"><span data-stu-id="8eddd-114">The association ends for the `PublishedBy` association are the `Book` and `Publisher` entity types.</span></span> <span data-ttu-id="8eddd-115">Ucunun çoğulluğu `Publisher` bir (1), ucun çoğulluğu ise `Book` çok ( \* ).</span><span class="sxs-lookup"><span data-stu-id="8eddd-115">The multiplicity of the `Publisher` end is one (1) and the multiplicity of the `Book` end is many (\*).</span></span>  
  
 ![Üç varlık türüne sahip örnek model](./media/association-end-multiplicity/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="8eddd-117">ADO.NET Entity Framework kavramsal model tanımlamak için kavramsal şema tanım dili ([csdl](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) adlı bir etki alanına özgü DIL (DSL) kullanır.</span><span class="sxs-lookup"><span data-stu-id="8eddd-117">The ADO.NET Entity Framework uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="8eddd-118">Aşağıdaki CSDL, `PublishedBy` Yukarıdaki diyagramda gösterilen ilişkilendirmeyi tanımlar:</span><span class="sxs-lookup"><span data-stu-id="8eddd-118">The following CSDL defines the `PublishedBy` association shown in the diagram above:</span></span>  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a><span data-ttu-id="8eddd-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8eddd-119">See also</span></span>

- [<span data-ttu-id="8eddd-120">Varlık Veri Modeli Temel Kavramları</span><span class="sxs-lookup"><span data-stu-id="8eddd-120">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="8eddd-121">Varlık Veri Modeli</span><span class="sxs-lookup"><span data-stu-id="8eddd-121">Entity Data Model</span></span>](entity-data-model.md)

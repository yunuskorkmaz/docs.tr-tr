---
title: association end multiplicity
ms.date: 03/30/2017
ms.assetid: 340926ee-aefb-4bef-92cc-453e5251fd03
ms.openlocfilehash: cdcf69e7118620b2f8febd02d7695d429bf8cc2c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786950"
---
# <a name="association-end-multiplicity"></a><span data-ttu-id="1e445-102">association end multiplicity</span><span class="sxs-lookup"><span data-stu-id="1e445-102">association end multiplicity</span></span>
<span data-ttu-id="1e445-103">*Association End çoğulluğu* , [ilişkilendirmenin](association-type.md)bir ucunda olabilecek [varlık türü](entity-type.md) örneklerinin sayısını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1e445-103">*Association end multiplicity* defines the number of [entity type](entity-type.md) instances that can be at one end of an [association](association-type.md).</span></span>  
  
 <span data-ttu-id="1e445-104">Bir ilişkilendirme End çoğulluğu aşağıdaki değerlerden birine sahip olabilir:</span><span class="sxs-lookup"><span data-stu-id="1e445-104">An association end multiplicity can have one of the following values:</span></span>  
  
- <span data-ttu-id="1e445-105">bir (1): İlişki ucunda tam olarak bir varlık türü örneğinin bulunduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="1e445-105">one (1): Indicates that exactly one entity type instance exists at the association end.</span></span>  
  
- <span data-ttu-id="1e445-106">sıfır veya bir (0.. 1): İlişki ucunda sıfır veya bir varlık türü örneklerinin bulunduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="1e445-106">zero or one (0..1): Indicates that zero or one entity type instances exist at the association end.</span></span>  
  
- <span data-ttu-id="1e445-107">Çok (\*): İlişkilendirme ucunda sıfır, bir veya daha fazla varlık türü örneğinin var olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="1e445-107">many (\*): Indicates that zero, one, or more entity type instances exist at the association end.</span></span>  
  
 <span data-ttu-id="1e445-108">İlişki genellikle ilişkilendirme uç çarpanlarıyla belirlenir.</span><span class="sxs-lookup"><span data-stu-id="1e445-108">An association is often characterized by its association end multiplicities.</span></span> <span data-ttu-id="1e445-109">Örneğin, bir ilişkinin uçları bir (1) ve çok (\*) çarpanlarına sahip olursa, ilişkilendirme bire çok ilişkilendirme olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="1e445-109">For example, if the ends of an association have multiplicities one (1) and many (\*), the association is called a one-to-many association.</span></span> <span data-ttu-id="1e445-110">Aşağıdaki örnekte, `PublishedBy` ilişkilendirme bire çok ilişkidir (yayımcı birçok kitabı yayınlar ve bir kitap tek bir yayımcı tarafından yayımlanır).</span><span class="sxs-lookup"><span data-stu-id="1e445-110">In the example below, the `PublishedBy` association is a one-to-many association (a publisher publishes many books and a book is published by one publisher).</span></span> <span data-ttu-id="1e445-111">`WrittenBy` İlişkilendirme çok-çok ilişkisi (bir kitapta birden çok yazar olabilir ve bir yazar birden çok kitap yazabilir).</span><span class="sxs-lookup"><span data-stu-id="1e445-111">The `WrittenBy` association is a many-to-many association (a book can have multiple authors and an author can write multiple books).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e445-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="1e445-112">Example</span></span>  
 <span data-ttu-id="1e445-113">Aşağıdaki diyagramda iki ilişkiye sahip kavramsal bir model gösterilmektedir: `PublishedBy` ve. `WrittenBy`</span><span class="sxs-lookup"><span data-stu-id="1e445-113">The diagram below shows a conceptual model with two associations: `PublishedBy` and `WrittenBy`.</span></span> <span data-ttu-id="1e445-114">İlişkilendirme için `PublishedBy` `Publisher` ilişkilendirme sonlanır `Book` ve varlık türleridir.</span><span class="sxs-lookup"><span data-stu-id="1e445-114">The association ends for the `PublishedBy` association are the `Book` and `Publisher` entity types.</span></span> <span data-ttu-id="1e445-115">`Publisher` Ucunun çoğulluğu bir (1), `Book` ucun çoğulluğu ise çok (\*).</span><span class="sxs-lookup"><span data-stu-id="1e445-115">The multiplicity of the `Publisher` end is one (1) and the multiplicity of the `Book` end is many (\*).</span></span>  
  
 ![Üç varlık türüne sahip örnek model](./media/association-end-multiplicity/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="1e445-117">ADO.NET Entity Framework kavramsal model tanımlamak için kavramsal şema tanım dili ([csdl](./ef/language-reference/csdl-specification.md)) adlı bir etki alanına özgü DIL (DSL) kullanır.</span><span class="sxs-lookup"><span data-stu-id="1e445-117">The ADO.NET Entity Framework uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](./ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="1e445-118">Aşağıdaki csdl, Yukarıdaki diyagramda `PublishedBy` gösterilen ilişkilendirmeyi tanımlar:</span><span class="sxs-lookup"><span data-stu-id="1e445-118">The following CSDL defines the `PublishedBy` association shown in the diagram above:</span></span>  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a><span data-ttu-id="1e445-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1e445-119">See also</span></span>

- [<span data-ttu-id="1e445-120">Varlık Veri Modeli Temel Kavramları</span><span class="sxs-lookup"><span data-stu-id="1e445-120">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="1e445-121">Varlık Veri Modeli</span><span class="sxs-lookup"><span data-stu-id="1e445-121">Entity Data Model</span></span>](entity-data-model.md)

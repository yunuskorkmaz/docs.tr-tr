---
title: association end multiplicity
ms.date: 03/30/2017
ms.assetid: 340926ee-aefb-4bef-92cc-453e5251fd03
ms.openlocfilehash: 3f3d8ba9f7e68065024dd3efb599b847496740cd
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738575"
---
# <a name="association-end-multiplicity"></a><span data-ttu-id="490ca-102">association end multiplicity</span><span class="sxs-lookup"><span data-stu-id="490ca-102">association end multiplicity</span></span>
<span data-ttu-id="490ca-103">*Association End çoğulluğu* , [ilişkilendirmenin](association-type.md)bir ucunda olabilecek [varlık türü](entity-type.md) örneklerinin sayısını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="490ca-103">*Association end multiplicity* defines the number of [entity type](entity-type.md) instances that can be at one end of an [association](association-type.md).</span></span>  
  
 <span data-ttu-id="490ca-104">Bir ilişkilendirme End çoğulluğu aşağıdaki değerlerden birine sahip olabilir:</span><span class="sxs-lookup"><span data-stu-id="490ca-104">An association end multiplicity can have one of the following values:</span></span>  
  
- <span data-ttu-id="490ca-105">bir (1): ilişkilendirme ucunda tam olarak bir varlık türü örneğinin bulunduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="490ca-105">one (1): Indicates that exactly one entity type instance exists at the association end.</span></span>  
  
- <span data-ttu-id="490ca-106">sıfır veya bir (0.. 1): ilişkilendirme ucunda sıfır veya bir varlık türü örneklerinin bulunduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="490ca-106">zero or one (0..1): Indicates that zero or one entity type instances exist at the association end.</span></span>  
  
- <span data-ttu-id="490ca-107">Çok (\*): ilişkilendirme ucunda sıfır, bir veya daha fazla varlık türü örneğinin var olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="490ca-107">many (\*): Indicates that zero, one, or more entity type instances exist at the association end.</span></span>  
  
 <span data-ttu-id="490ca-108">İlişki genellikle ilişkilendirme uç çarpanlarıyla belirlenir.</span><span class="sxs-lookup"><span data-stu-id="490ca-108">An association is often characterized by its association end multiplicities.</span></span> <span data-ttu-id="490ca-109">Örneğin, bir ilişkinin uçları bir (1) ve birçok (\*) çarpanlarına sahip olursa, ilişkilendirme bire çok ilişkilendirme olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="490ca-109">For example, if the ends of an association have multiplicities one (1) and many (\*), the association is called a one-to-many association.</span></span> <span data-ttu-id="490ca-110">Aşağıdaki örnekte, `PublishedBy` ilişkilendirmesi bire çok ilişkidir (yayımcı birçok kitabı yayınlar ve bir kitap tek bir yayımcı tarafından yayımlanır).</span><span class="sxs-lookup"><span data-stu-id="490ca-110">In the example below, the `PublishedBy` association is a one-to-many association (a publisher publishes many books and a book is published by one publisher).</span></span> <span data-ttu-id="490ca-111">`WrittenBy` ilişkilendirmesi çoktan çoğa bir ilişkidir (bir kitapta birden çok yazar olabilir ve bir yazar birden çok kitap yazabilir).</span><span class="sxs-lookup"><span data-stu-id="490ca-111">The `WrittenBy` association is a many-to-many association (a book can have multiple authors and an author can write multiple books).</span></span>  
  
## <a name="example"></a><span data-ttu-id="490ca-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="490ca-112">Example</span></span>  
 <span data-ttu-id="490ca-113">Aşağıdaki diyagramda iki ilişkiye sahip bir kavramsal model görülmektedir: `PublishedBy` ve `WrittenBy`.</span><span class="sxs-lookup"><span data-stu-id="490ca-113">The diagram below shows a conceptual model with two associations: `PublishedBy` and `WrittenBy`.</span></span> <span data-ttu-id="490ca-114">İlişki `PublishedBy` ilişkilendirme için sonlanır `Book` ve `Publisher` varlık türleridir.</span><span class="sxs-lookup"><span data-stu-id="490ca-114">The association ends for the `PublishedBy` association are the `Book` and `Publisher` entity types.</span></span> <span data-ttu-id="490ca-115">`Publisher` ucunun çoğulluğu bir (1), `Book` ucunun çokluğu ise çok (\*).</span><span class="sxs-lookup"><span data-stu-id="490ca-115">The multiplicity of the `Publisher` end is one (1) and the multiplicity of the `Book` end is many (\*).</span></span>  
  
 ![Üç varlık türüne sahip örnek model](./media/association-end-multiplicity/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="490ca-117">ADO.NET Entity Framework kavramsal model tanımlamak için kavramsal şema tanım dili ([csdl](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) adlı bir etki alanına özgü DIL (DSL) kullanır.</span><span class="sxs-lookup"><span data-stu-id="490ca-117">The ADO.NET Entity Framework uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="490ca-118">Aşağıdaki CSDL, Yukarıdaki diyagramda gösterilen `PublishedBy` ilişkilendirmesini tanımlar:</span><span class="sxs-lookup"><span data-stu-id="490ca-118">The following CSDL defines the `PublishedBy` association shown in the diagram above:</span></span>  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a><span data-ttu-id="490ca-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="490ca-119">See also</span></span>

- [<span data-ttu-id="490ca-120">Varlık Veri Modeli Temel Kavramları</span><span class="sxs-lookup"><span data-stu-id="490ca-120">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="490ca-121">Varlık Veri Modeli</span><span class="sxs-lookup"><span data-stu-id="490ca-121">Entity Data Model</span></span>](entity-data-model.md)

---
title: association set
ms.date: 03/30/2017
ms.assetid: a65247b6-ce59-44ea-974c-14ae20a7995f
ms.openlocfilehash: e279322f9e950cd4359db8c6dce39bfc46d188f6
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73732369"
---
# <a name="association-set"></a><span data-ttu-id="3d9a1-102">association set</span><span class="sxs-lookup"><span data-stu-id="3d9a1-102">association set</span></span>
<span data-ttu-id="3d9a1-103">*İlişki kümesi* , aynı türde [ilişki](association-type.md) örnekleri için mantıksal bir kapsayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="3d9a1-103">An *association set* is a logical container for [association](association-type.md) instances of the same type.</span></span> <span data-ttu-id="3d9a1-104">Bir ilişki kümesi, bir veri modelleme yapısı değildir; diğer bir deyişle, verilerin veya ilişkilerin yapısını tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="3d9a1-104">An association set is not a data modeling construct; that is, it does not describe the structure of data or relationships.</span></span> <span data-ttu-id="3d9a1-105">Bunun yerine, bir ilişki kümesi, ilişki örneklerini gruplamak için bir barındırma veya depolama ortamı (ortak dil çalışma zamanı veya bir SQL Server veritabanı gibi) için bir yapı sağlar. böylece bir veri deposuna eşlenebilir.</span><span class="sxs-lookup"><span data-stu-id="3d9a1-105">Instead, an association set provides a construct for a hosting or storage environment (such as the common language runtime or a SQL Server database) to group association instances so that they can be mapped to a data store.</span></span>  
  
 <span data-ttu-id="3d9a1-106">Bir ilişki kümesi, [varlık kümelerinin](entity-set.md) ve ilişkilendirme kümelerinin mantıksal bir gruplandırması olan bir [varlık kapsayıcısı](entity-container.md)içinde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="3d9a1-106">An association set is defined within an [entity container](entity-container.md), which is a logical grouping of [entity sets](entity-set.md) and association sets.</span></span>  
  
 <span data-ttu-id="3d9a1-107">İlişki kümesi için bir tanım aşağıdaki bilgileri içerir:</span><span class="sxs-lookup"><span data-stu-id="3d9a1-107">A definition for an association set contains the following information:</span></span>  
  
- <span data-ttu-id="3d9a1-108">İlişki kümesi adı.</span><span class="sxs-lookup"><span data-stu-id="3d9a1-108">The association set name.</span></span> <span data-ttu-id="3d9a1-109">Istenir</span><span class="sxs-lookup"><span data-stu-id="3d9a1-109">(Required)</span></span>  
  
- <span data-ttu-id="3d9a1-110">Örnek içereceği ilişki.</span><span class="sxs-lookup"><span data-stu-id="3d9a1-110">The association of which it will contain instances.</span></span> <span data-ttu-id="3d9a1-111">Istenir</span><span class="sxs-lookup"><span data-stu-id="3d9a1-111">(Required)</span></span>  
  
- <span data-ttu-id="3d9a1-112">İki [ilişkilendirme kümesi sona erer](association-set-end.md).</span><span class="sxs-lookup"><span data-stu-id="3d9a1-112">Two [association set ends](association-set-end.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d9a1-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="3d9a1-113">Example</span></span>  
 <span data-ttu-id="3d9a1-114">Aşağıdaki diyagramda iki ilişkiye sahip bir kavramsal model gösterilmektedir: `PublishedBy`ve `WrittenBy`.</span><span class="sxs-lookup"><span data-stu-id="3d9a1-114">The diagram below shows a conceptual model with two associations: `PublishedBy`, and `WrittenBy`.</span></span> <span data-ttu-id="3d9a1-115">İlişki kümeleri hakkındaki bilgiler diyagramda bir şekilde gelse de, sonraki diyagramda bu modele göre ilişki kümelerinin ve varlık kümelerinin bir örneği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3d9a1-115">Although information about association sets is not conveyed in the diagram, the next diagram shows an example of association sets and entity sets based on this model.</span></span>  
  
 ![Üç varlık türüne sahip örnek model](./media/association-set/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="3d9a1-117">Aşağıdaki örnek, yukarıda gösterilen kavramsal modele bağlı olarak bir ilişki kümesini (`PublishedBy`) ve iki varlık kümesini (`Books` ve `Publishers`) gösterir.</span><span class="sxs-lookup"><span data-stu-id="3d9a1-117">The following example shows an association set (`PublishedBy`) and two entity sets (`Books` and `Publishers`) based on the conceptual model shown above.</span></span> <span data-ttu-id="3d9a1-118">`Books` varlık kümesindeki bı, çalışma zamanında `Book` varlık türünün bir örneğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3d9a1-118">Bi in the `Books` entity set represents an instance of the `Book` entity type at run time.</span></span> <span data-ttu-id="3d9a1-119">Benzer şekilde, PJ, `Publishers` varlık kümesindeki bir `Publisher` örneğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3d9a1-119">Similarly, Pj represents a `Publisher` instance in the `Publishers` entity set.</span></span> <span data-ttu-id="3d9a1-120">BiPj, `PublishedBy` ilişkilendirme kümesindeki `PublishedBy` ilişkisinin bir örneğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3d9a1-120">BiPj represents an instance of the `PublishedBy` association in the `PublishedBy` association set.</span></span>  
  
 ![Bir küme örneği gösteren ekran görüntüsü.](./media/association-set/sets-example-association.gif)  
  
 <span data-ttu-id="3d9a1-122">[ADO.NET Entity Framework](./ef/index.md) kavramsal model tanımlamak için kavramsal şema tanım dili ([csdl](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) adlı bir etki ALANıNA özgü dil (DSL) kullanır.</span><span class="sxs-lookup"><span data-stu-id="3d9a1-122">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="3d9a1-123">Aşağıdaki CSDL, Yukarıdaki diyagramda bulunan her ilişkilendirme için bir ilişki kümesiyle bir varlık kapsayıcısını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3d9a1-123">The following CSDL defines an entity container with one association set for each association in the diagram above.</span></span> <span data-ttu-id="3d9a1-124">Her ilişkilendirme kümesi için ad ve ilişkilendirmenin XML öznitelikleri kullanılarak tanımlandığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="3d9a1-124">Note that the name and association for each association set are defined using XML attributes.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 <span data-ttu-id="3d9a1-125">İki ilişkilendirme kümesi bir [ilişki kümesi ucu](association-set-end.md)paylaştığından, ilişkilendirme başına birden çok ilişki kümesi tanımlanması mümkündür.</span><span class="sxs-lookup"><span data-stu-id="3d9a1-125">It is possible to define multiple association sets per association, as long as no two association sets share an [association set end](association-set-end.md).</span></span> <span data-ttu-id="3d9a1-126">Aşağıdaki CSDL `WrittenBy` ilişkilendirmesi için iki ilişkilendirme kümesiyle bir varlık kapsayıcısını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3d9a1-126">The following CSDL defines an entity container with two association sets for the `WrittenBy` association.</span></span> <span data-ttu-id="3d9a1-127">`Book` ve `Author` varlık türleri için birden çok varlık kümesi tanımlandığından ve hiçbir ilişkilendirme kümesinin bir ilişki kümesi ucu paylaştığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="3d9a1-127">Notice that multiple entity sets have been defined for the `Book` and `Author` entity types and that no association set shares an association set end.</span></span>  
  
 [!code-xml[EDM_Example_Model#MultipleAssociationSets](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#multipleassociationsets)]  
  
## <a name="see-also"></a><span data-ttu-id="3d9a1-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3d9a1-128">See also</span></span>

- [<span data-ttu-id="3d9a1-129">Varlık Veri Modeli Temel Kavramları</span><span class="sxs-lookup"><span data-stu-id="3d9a1-129">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="3d9a1-130">Varlık Veri Modeli</span><span class="sxs-lookup"><span data-stu-id="3d9a1-130">Entity Data Model</span></span>](entity-data-model.md)
- [<span data-ttu-id="3d9a1-131">foreign key property</span><span class="sxs-lookup"><span data-stu-id="3d9a1-131">foreign key property</span></span>](foreign-key-property.md)

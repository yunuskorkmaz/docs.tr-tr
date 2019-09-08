---
title: association set
ms.date: 03/30/2017
ms.assetid: a65247b6-ce59-44ea-974c-14ae20a7995f
ms.openlocfilehash: 43ab6cf9f1ee8cb971810add6b9a89467726f3e2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785036"
---
# <a name="association-set"></a><span data-ttu-id="4a281-102">association set</span><span class="sxs-lookup"><span data-stu-id="4a281-102">association set</span></span>
<span data-ttu-id="4a281-103">*İlişki kümesi* , aynı türde [ilişki](association-type.md) örnekleri için mantıksal bir kapsayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="4a281-103">An *association set* is a logical container for [association](association-type.md) instances of the same type.</span></span> <span data-ttu-id="4a281-104">Bir ilişki kümesi, bir veri modelleme yapısı değildir; diğer bir deyişle, verilerin veya ilişkilerin yapısını tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="4a281-104">An association set is not a data modeling construct; that is, it does not describe the structure of data or relationships.</span></span> <span data-ttu-id="4a281-105">Bunun yerine, bir ilişki kümesi, ilişki örneklerini gruplamak için bir barındırma veya depolama ortamı (ortak dil çalışma zamanı veya bir SQL Server veritabanı gibi) için bir yapı sağlar. böylece bir veri deposuna eşlenebilir.</span><span class="sxs-lookup"><span data-stu-id="4a281-105">Instead, an association set provides a construct for a hosting or storage environment (such as the common language runtime or a SQL Server database) to group association instances so that they can be mapped to a data store.</span></span>  
  
 <span data-ttu-id="4a281-106">Bir ilişki kümesi, [varlık kümelerinin](entity-set.md) ve ilişkilendirme kümelerinin mantıksal bir gruplandırması olan bir [varlık kapsayıcısı](entity-container.md)içinde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="4a281-106">An association set is defined within an [entity container](entity-container.md), which is a logical grouping of [entity sets](entity-set.md) and association sets.</span></span>  
  
 <span data-ttu-id="4a281-107">İlişki kümesi için bir tanım aşağıdaki bilgileri içerir:</span><span class="sxs-lookup"><span data-stu-id="4a281-107">A definition for an association set contains the following information:</span></span>  
  
- <span data-ttu-id="4a281-108">İlişki kümesi adı.</span><span class="sxs-lookup"><span data-stu-id="4a281-108">The association set name.</span></span> <span data-ttu-id="4a281-109">Istenir</span><span class="sxs-lookup"><span data-stu-id="4a281-109">(Required)</span></span>  
  
- <span data-ttu-id="4a281-110">Örnek içereceği ilişki.</span><span class="sxs-lookup"><span data-stu-id="4a281-110">The association of which it will contain instances.</span></span> <span data-ttu-id="4a281-111">Istenir</span><span class="sxs-lookup"><span data-stu-id="4a281-111">(Required)</span></span>  
  
- <span data-ttu-id="4a281-112">İki [ilişkilendirme kümesi sona erer](association-set-end.md).</span><span class="sxs-lookup"><span data-stu-id="4a281-112">Two [association set ends](association-set-end.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4a281-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="4a281-113">Example</span></span>  
 <span data-ttu-id="4a281-114">Aşağıdaki diyagramda iki ilişkiye sahip kavramsal bir model gösterilmektedir: `PublishedBy`ve. `WrittenBy`</span><span class="sxs-lookup"><span data-stu-id="4a281-114">The diagram below shows a conceptual model with two associations: `PublishedBy`, and `WrittenBy`.</span></span> <span data-ttu-id="4a281-115">İlişki kümeleri hakkındaki bilgiler diyagramda bir şekilde gelse de, sonraki diyagramda bu modele göre ilişki kümelerinin ve varlık kümelerinin bir örneği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4a281-115">Although information about association sets is not conveyed in the diagram, the next diagram shows an example of association sets and entity sets based on this model.</span></span>  
  
 ![Üç varlık türüne sahip örnek model](./media/association-set/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="4a281-117">Aşağıdaki örnek, yukarıda gösterilen kavramsal modele bağlı`PublishedBy`olarak bir ilişki kümesi ()`Books` ve `Publishers`iki varlık kümesini (ve) gösterir.</span><span class="sxs-lookup"><span data-stu-id="4a281-117">The following example shows an association set (`PublishedBy`) and two entity sets (`Books` and `Publishers`) based on the conceptual model shown above.</span></span> <span data-ttu-id="4a281-118">Varlık kümesindeki bı, çalışma zamanında `Book` varlık türünün bir örneğini temsil eder. `Books`</span><span class="sxs-lookup"><span data-stu-id="4a281-118">Bi in the `Books` entity set represents an instance of the `Book` entity type at run time.</span></span> <span data-ttu-id="4a281-119">Benzer şekilde, PJ `Publisher` `Publishers` varlık kümesindeki bir örneği temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4a281-119">Similarly, Pj represents a `Publisher` instance in the `Publishers` entity set.</span></span> <span data-ttu-id="4a281-120">Bipj, `PublishedBy` `PublishedBy` ilişki kümesindeki ilişkilendirmenin bir örneğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4a281-120">BiPj represents an instance of the `PublishedBy` association in the `PublishedBy` association set.</span></span>  
  
 ![Bir küme örneği gösteren ekran görüntüsü.](./media/association-set/sets-example-association.gif)  
  
 <span data-ttu-id="4a281-122">[ADO.NET Entity Framework](./ef/index.md) kavramsal model tanımlamak için kavramsal şema tanım dili ([csdl](./ef/language-reference/csdl-specification.md)) adlı bir etki ALANıNA özgü dil (DSL) kullanır.</span><span class="sxs-lookup"><span data-stu-id="4a281-122">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](./ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="4a281-123">Aşağıdaki CSDL, Yukarıdaki diyagramda bulunan her ilişkilendirme için bir ilişki kümesiyle bir varlık kapsayıcısını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4a281-123">The following CSDL defines an entity container with one association set for each association in the diagram above.</span></span> <span data-ttu-id="4a281-124">Her ilişkilendirme kümesi için ad ve ilişkilendirmenin XML öznitelikleri kullanılarak tanımlandığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="4a281-124">Note that the name and association for each association set are defined using XML attributes.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 <span data-ttu-id="4a281-125">İki ilişkilendirme kümesi bir [ilişki kümesi ucu](association-set-end.md)paylaştığından, ilişkilendirme başına birden çok ilişki kümesi tanımlanması mümkündür.</span><span class="sxs-lookup"><span data-stu-id="4a281-125">It is possible to define multiple association sets per association, as long as no two association sets share an [association set end](association-set-end.md).</span></span> <span data-ttu-id="4a281-126">Aşağıdaki csdl `WrittenBy` ilişki için iki ilişkilendirme kümesiyle bir varlık kapsayıcısını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4a281-126">The following CSDL defines an entity container with two association sets for the `WrittenBy` association.</span></span> <span data-ttu-id="4a281-127">`Book` Ve`Author` varlık türleri için birden çok varlık kümesi tanımlandığından ve hiçbir ilişkilendirme kümesinin bir ilişki kümesi ucu paylaştığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="4a281-127">Notice that multiple entity sets have been defined for the `Book` and `Author` entity types and that no association set shares an association set end.</span></span>  
  
 [!code-xml[EDM_Example_Model#MultipleAssociationSets](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#multipleassociationsets)]  
  
## <a name="see-also"></a><span data-ttu-id="4a281-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4a281-128">See also</span></span>

- [<span data-ttu-id="4a281-129">Varlık Veri Modeli Temel Kavramları</span><span class="sxs-lookup"><span data-stu-id="4a281-129">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="4a281-130">Varlık Veri Modeli</span><span class="sxs-lookup"><span data-stu-id="4a281-130">Entity Data Model</span></span>](entity-data-model.md)
- [<span data-ttu-id="4a281-131">foreign key property</span><span class="sxs-lookup"><span data-stu-id="4a281-131">foreign key property</span></span>](foreign-key-property.md)

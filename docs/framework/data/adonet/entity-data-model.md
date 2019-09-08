---
title: Varlık Veri Modeli
ms.date: 03/30/2017
ms.assetid: 2dda3d5b-4582-4ba0-a91d-fcd7a1498137
ms.openlocfilehash: 1742b04d0e3d8387e990d40d832e355dd15c4311
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783952"
---
# <a name="entity-data-model"></a><span data-ttu-id="ab997-102">Varlık Veri Modeli</span><span class="sxs-lookup"><span data-stu-id="ab997-102">Entity Data Model</span></span>
<span data-ttu-id="ab997-103">Varlık Veri Modeli (EDM), depolanan formdan bağımsız olarak verilerin yapısını tanımlayan bir kavram kümesidir.</span><span class="sxs-lookup"><span data-stu-id="ab997-103">The Entity Data Model (EDM) is a set of concepts that describe the structure of data, regardless of its stored form.</span></span> <span data-ttu-id="ab997-104">Varlık ilişkisi modelinden 1976 ' de Peter Chen tarafından tanımlanan EDM bulunamadığında, ancak aynı zamanda varlık ilişkisi modelinde oluşturulup geleneksel kullanımları genişletiyor.</span><span class="sxs-lookup"><span data-stu-id="ab997-104">The EDM borrows from the Entity-Relationship Model described by Peter Chen in 1976, but it also builds on the Entity-Relationship Model and extends its traditional uses.</span></span>  
  
 <span data-ttu-id="ab997-105">EDM, verilerin birçok biçimde depolanmasından kaynaklanan zorlukları ele alır.</span><span class="sxs-lookup"><span data-stu-id="ab997-105">The EDM addresses the challenges that arise from having data stored in many forms.</span></span> <span data-ttu-id="ab997-106">Örneğin, verileri ilişkisel veritabanlarında, metin dosyalarında, XML dosyalarında, elektronik tablolarda ve raporlarda depolayan bir işletmeyi düşünün.</span><span class="sxs-lookup"><span data-stu-id="ab997-106">For example, consider a business that stores data in relational databases, text files, XML files, spreadsheets, and reports.</span></span> <span data-ttu-id="ab997-107">Bu, veri modellemesi, uygulama tasarımı ve veri erişimi konularında önemli zorluk gösterir.</span><span class="sxs-lookup"><span data-stu-id="ab997-107">This presents significant challenges in data modeling, application design, and data access.</span></span> <span data-ttu-id="ab997-108">Veri odaklı bir uygulama tasarlarken, sınama, verimli veri erişimi, depolama ve ölçeklenebilirlik olmadan verimli ve sürdürülebilir kodlar yazmak olacaktır.</span><span class="sxs-lookup"><span data-stu-id="ab997-108">When designing a data-oriented application, the challenge is to write efficient and maintainable code without sacrificing efficient data access, storage, and scalability.</span></span> <span data-ttu-id="ab997-109">Veriler ilişkisel bir yapıya sahip olduğunda, veri erişimi, depolama ve ölçeklenebilirlik oldukça etkilidir, ancak verimli ve sürdürülebilir kod yazmak daha zor hale gelir.</span><span class="sxs-lookup"><span data-stu-id="ab997-109">When data has a relational structure, data access, storage, and scalability are very efficient, but writing efficient and maintainable code becomes more difficult.</span></span> <span data-ttu-id="ab997-110">Verilerin bir nesne yapısına sahip olduğu durumlarda, denge ters çevrilir: Verimli ve sürdürülebilir kod yazma, verimli veri erişimi, depolama ve ölçeklenebilirlik maliyetlerine göre sunulur.</span><span class="sxs-lookup"><span data-stu-id="ab997-110">When data has an object structure, the trade-offs are reversed: Writing efficient and maintainable code comes at the cost of efficient data access, storage, and scalability.</span></span> <span data-ttu-id="ab997-111">Bu denge arasındaki doğru denge bulunabildiğinden bile, veriler bir formdan diğerine taşındığında yeni sorunlar oluşur.</span><span class="sxs-lookup"><span data-stu-id="ab997-111">Even if the right balance between these trade-offs can be found, new challenges arise when data is moved from one form to another.</span></span> <span data-ttu-id="ab997-112">Varlık Veri Modeli, verilerin yapısını herhangi bir depolama şemadan bağımsız olan varlıklar ve ilişkiler bakımından açıklayarak bu zorlukları ele alır.</span><span class="sxs-lookup"><span data-stu-id="ab997-112">The Entity Data Model addresses these challenges by describing the structure of data in terms of entities and relationships that are independent of any storage schema.</span></span> <span data-ttu-id="ab997-113">Bu, depolanmış veri formunu uygulama tasarımı ve geliştirmeyle ilgisiz hale getirir.</span><span class="sxs-lookup"><span data-stu-id="ab997-113">This makes the stored form of data irrelevant to application design and development.</span></span> <span data-ttu-id="ab997-114">Ayrıca, varlıklar ve ilişkiler bir uygulamada (saklı form değil) kullanılan verilerin yapısını açıkladığı için, bir uygulama geliştikçe gelişir.</span><span class="sxs-lookup"><span data-stu-id="ab997-114">And, because entities and relationships describe the structure of data as it is used in an application (not its stored form), they can evolve as an application evolves.</span></span>  
  
 <span data-ttu-id="ab997-115">`conceptual model` , Verilerin yapısının varlık ve ilişkiler olarak belirli bir gösterimidir ve genellikle EDM kavramlarını uygulayan, etki alanına özgü bir dilde (DSL) tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="ab997-115">A `conceptual model` is a specific representation of the structure of data as entities and relationships, and is generally defined in a domain-specific language (DSL) that implements the concepts of the EDM.</span></span> <span data-ttu-id="ab997-116">[Kavramsal şema tanım dili (csdl)](./ef/language-reference/csdl-specification.md) , bu tür bir etki alanına özgü dilin bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="ab997-116">[Conceptual schema definition language (CSDL)](./ef/language-reference/csdl-specification.md) is an example of such a domain-specific language.</span></span> <span data-ttu-id="ab997-117">Kavramsal modelde tanımlanan varlıklar ve ilişkiler, bir uygulamadaki nesne ve ilişkilerin soyutlamalarını olarak düşünülebilir.</span><span class="sxs-lookup"><span data-stu-id="ab997-117">Entities and relationships described in a conceptual model can be thought of as abstractions of objects and associations in an application.</span></span> <span data-ttu-id="ab997-118">Bu, geliştiricilerin depolama şemasına gerek kalmadan kavramsal modele odaklanmasını sağlar ve verimlilik ve bakımsız kod yazmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="ab997-118">This allows developers to focus on the conceptual model without concern for the storage schema, and allows them to write code with efficiency and maintainability in mind.</span></span> <span data-ttu-id="ab997-119">Bu arada, depolama şeması tasarımcıları veri erişimi, depolama ve ölçeklenebilirlik verimliliğine odaklanabilir.</span><span class="sxs-lookup"><span data-stu-id="ab997-119">Meanwhile storage schema designers can focus on the efficiency of data access, storage, and scalability.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ab997-120">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="ab997-120">In This Section</span></span>  
 <span data-ttu-id="ab997-121">Bu bölümdeki konular Varlık Veri Modeli kavramlarını anlatmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ab997-121">Topics in this section describe the concepts of the Entity Data Model.</span></span> <span data-ttu-id="ab997-122">EDM 'yi uygulayan herhangi bir DSL, burada açıklanan kavramları içermelidir.</span><span class="sxs-lookup"><span data-stu-id="ab997-122">Any DSL that implements the EDM should include the concepts described here.</span></span> <span data-ttu-id="ab997-123">[ADO.NET Entity Framework](./ef/index.md) 'nin, kavramsal modelleri tanımlamak için csdl kullandığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="ab997-123">Note that the [ADO.NET Entity Framework](./ef/index.md) uses CSDL to define conceptual models.</span></span> <span data-ttu-id="ab997-124">Daha fazla bilgi için bkz. [csdl belirtimi](./ef/language-reference/csdl-specification.md).</span><span class="sxs-lookup"><span data-stu-id="ab997-124">For more information, see [CSDL Specification](./ef/language-reference/csdl-specification.md).</span></span>  
  
 [<span data-ttu-id="ab997-125">Varlık Veri Modeli Temel Kavramları</span><span class="sxs-lookup"><span data-stu-id="ab997-125">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)  
  
 [<span data-ttu-id="ab997-126">Varlık Veri Modeli: Öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="ab997-126">Entity Data Model: Namespaces</span></span>](entity-data-model-namespaces.md)  
  
 [<span data-ttu-id="ab997-127">Varlık Veri Modeli: İlkel veri türleri</span><span class="sxs-lookup"><span data-stu-id="ab997-127">Entity Data Model: Primitive Data Types</span></span>](entity-data-model-primitive-data-types.md)  
  
 [<span data-ttu-id="ab997-128">Varlık Veri Modeli: Devralmayı</span><span class="sxs-lookup"><span data-stu-id="ab997-128">Entity Data Model: Inheritance</span></span>](entity-data-model-inheritance.md)  
  
 [<span data-ttu-id="ab997-129">association end</span><span class="sxs-lookup"><span data-stu-id="ab997-129">association end</span></span>](association-end.md)  
  
 [<span data-ttu-id="ab997-130">association end multiplicity</span><span class="sxs-lookup"><span data-stu-id="ab997-130">association end multiplicity</span></span>](association-end-multiplicity.md)  
  
 [<span data-ttu-id="ab997-131">association set</span><span class="sxs-lookup"><span data-stu-id="ab997-131">association set</span></span>](association-set.md)  
  
 [<span data-ttu-id="ab997-132">association set end</span><span class="sxs-lookup"><span data-stu-id="ab997-132">association set end</span></span>](association-set-end.md)  
  
 [<span data-ttu-id="ab997-133">association type</span><span class="sxs-lookup"><span data-stu-id="ab997-133">association type</span></span>](association-type.md)  
  
 [<span data-ttu-id="ab997-134">complex type</span><span class="sxs-lookup"><span data-stu-id="ab997-134">complex type</span></span>](complex-type.md)  
  
 [<span data-ttu-id="ab997-135">entity container</span><span class="sxs-lookup"><span data-stu-id="ab997-135">entity container</span></span>](entity-container.md)  
  
 [<span data-ttu-id="ab997-136">entity key</span><span class="sxs-lookup"><span data-stu-id="ab997-136">entity key</span></span>](entity-key.md)  
  
 [<span data-ttu-id="ab997-137">entity set</span><span class="sxs-lookup"><span data-stu-id="ab997-137">entity set</span></span>](entity-set.md)  
  
 [<span data-ttu-id="ab997-138">entity type</span><span class="sxs-lookup"><span data-stu-id="ab997-138">entity type</span></span>](entity-type.md)  
  
 [<span data-ttu-id="ab997-139">facet</span><span class="sxs-lookup"><span data-stu-id="ab997-139">facet</span></span>](facet.md)  
  
 [<span data-ttu-id="ab997-140">foreign key property</span><span class="sxs-lookup"><span data-stu-id="ab997-140">foreign key property</span></span>](foreign-key-property.md)  
  
 [<span data-ttu-id="ab997-141">model-declared function</span><span class="sxs-lookup"><span data-stu-id="ab997-141">model-declared function</span></span>](model-declared-function.md)  
  
 [<span data-ttu-id="ab997-142">model-defined function</span><span class="sxs-lookup"><span data-stu-id="ab997-142">model-defined function</span></span>](model-defined-function.md)  
  
 [<span data-ttu-id="ab997-143">navigation property</span><span class="sxs-lookup"><span data-stu-id="ab997-143">navigation property</span></span>](navigation-property.md)  
  
 [<span data-ttu-id="ab997-144">property</span><span class="sxs-lookup"><span data-stu-id="ab997-144">property</span></span>](property.md)  
  
 [<span data-ttu-id="ab997-145">referential integrity constraint</span><span class="sxs-lookup"><span data-stu-id="ab997-145">referential integrity constraint</span></span>](referential-integrity-constraint.md)  
  
## <a name="see-also"></a><span data-ttu-id="ab997-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ab997-146">See also</span></span>

- <span data-ttu-id="ab997-147">[ADO.NET Varlık Veri Modeli araçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ab997-147">[ADO.NET Entity Data Model Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
- <span data-ttu-id="ab997-148">[. edmx dosyasına genel bakış](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ab997-148">[.edmx File Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span></span>
- [<span data-ttu-id="ab997-149">CSDL Belirtimi</span><span class="sxs-lookup"><span data-stu-id="ab997-149">CSDL Specification</span></span>](./ef/language-reference/csdl-specification.md)

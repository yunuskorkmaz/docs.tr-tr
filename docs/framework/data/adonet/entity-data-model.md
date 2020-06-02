---
title: Varlık Veri Modeli
description: Varlık Veri Modeli, depolanan formdan bağımsız olarak verilerin yapısını açıklar ve bu da verileri birçok biçimde depolamaktan kaynaklanan sorunları giderir.
ms.date: 03/30/2017
ms.assetid: 2dda3d5b-4582-4ba0-a91d-fcd7a1498137
ms.openlocfilehash: c98b1f4559ef297f8b11051940fd91f5f6fa06fd
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286746"
---
# <a name="entity-data-model"></a><span data-ttu-id="f8faf-103">Varlık Veri Modeli</span><span class="sxs-lookup"><span data-stu-id="f8faf-103">Entity Data Model</span></span>
<span data-ttu-id="f8faf-104">Varlık Veri Modeli (EDM), depolanan formdan bağımsız olarak verilerin yapısını tanımlayan bir kavram kümesidir.</span><span class="sxs-lookup"><span data-stu-id="f8faf-104">The Entity Data Model (EDM) is a set of concepts that describe the structure of data, regardless of its stored form.</span></span> <span data-ttu-id="f8faf-105">Varlık ilişkisi modelinden 1976 ' de Peter Chen tarafından tanımlanan EDM bulunamadığında, ancak aynı zamanda varlık ilişkisi modelinde oluşturulup geleneksel kullanımları genişletiyor.</span><span class="sxs-lookup"><span data-stu-id="f8faf-105">The EDM borrows from the Entity-Relationship Model described by Peter Chen in 1976, but it also builds on the Entity-Relationship Model and extends its traditional uses.</span></span>  
  
 <span data-ttu-id="f8faf-106">EDM, verilerin birçok biçimde depolanmasından kaynaklanan zorlukları ele alır.</span><span class="sxs-lookup"><span data-stu-id="f8faf-106">The EDM addresses the challenges that arise from having data stored in many forms.</span></span> <span data-ttu-id="f8faf-107">Örneğin, verileri ilişkisel veritabanlarında, metin dosyalarında, XML dosyalarında, elektronik tablolarda ve raporlarda depolayan bir işletmeyi düşünün.</span><span class="sxs-lookup"><span data-stu-id="f8faf-107">For example, consider a business that stores data in relational databases, text files, XML files, spreadsheets, and reports.</span></span> <span data-ttu-id="f8faf-108">Bu, veri modellemesi, uygulama tasarımı ve veri erişimi konularında önemli zorluk gösterir.</span><span class="sxs-lookup"><span data-stu-id="f8faf-108">This presents significant challenges in data modeling, application design, and data access.</span></span> <span data-ttu-id="f8faf-109">Veri odaklı bir uygulama tasarlarken, sınama, verimli veri erişimi, depolama ve ölçeklenebilirlik olmadan verimli ve sürdürülebilir kodlar yazmak olacaktır.</span><span class="sxs-lookup"><span data-stu-id="f8faf-109">When designing a data-oriented application, the challenge is to write efficient and maintainable code without sacrificing efficient data access, storage, and scalability.</span></span> <span data-ttu-id="f8faf-110">Veriler ilişkisel bir yapıya sahip olduğunda, veri erişimi, depolama ve ölçeklenebilirlik oldukça etkilidir, ancak verimli ve sürdürülebilir kod yazmak daha zor hale gelir.</span><span class="sxs-lookup"><span data-stu-id="f8faf-110">When data has a relational structure, data access, storage, and scalability are very efficient, but writing efficient and maintainable code becomes more difficult.</span></span> <span data-ttu-id="f8faf-111">Verilerin bir nesne yapısına sahip olduğu durumlarda, denge ters kaydedilir: etkili ve sürdürülebilir kodun yazılması, verimli veri erişimi, depolama ve ölçeklenebilirlik maliyetlerine gelir.</span><span class="sxs-lookup"><span data-stu-id="f8faf-111">When data has an object structure, the trade-offs are reversed: Writing efficient and maintainable code comes at the cost of efficient data access, storage, and scalability.</span></span> <span data-ttu-id="f8faf-112">Bu denge arasındaki doğru denge bulunabildiğinden bile, veriler bir formdan diğerine taşındığında yeni sorunlar oluşur.</span><span class="sxs-lookup"><span data-stu-id="f8faf-112">Even if the right balance between these trade-offs can be found, new challenges arise when data is moved from one form to another.</span></span> <span data-ttu-id="f8faf-113">Varlık Veri Modeli, verilerin yapısını herhangi bir depolama şemadan bağımsız olan varlıklar ve ilişkiler bakımından açıklayarak bu zorlukları ele alır.</span><span class="sxs-lookup"><span data-stu-id="f8faf-113">The Entity Data Model addresses these challenges by describing the structure of data in terms of entities and relationships that are independent of any storage schema.</span></span> <span data-ttu-id="f8faf-114">Bu, depolanmış veri formunu uygulama tasarımı ve geliştirmeyle ilgisiz hale getirir.</span><span class="sxs-lookup"><span data-stu-id="f8faf-114">This makes the stored form of data irrelevant to application design and development.</span></span> <span data-ttu-id="f8faf-115">Ayrıca, varlıklar ve ilişkiler bir uygulamada (saklı form değil) kullanılan verilerin yapısını açıkladığı için, bir uygulama geliştikçe gelişir.</span><span class="sxs-lookup"><span data-stu-id="f8faf-115">And, because entities and relationships describe the structure of data as it is used in an application (not its stored form), they can evolve as an application evolves.</span></span>  
  
 <span data-ttu-id="f8faf-116">, `conceptual model` Verilerin yapısının varlık ve ilişkiler olarak belirli bir gösterimidir ve genellıkle EDM kavramlarını uygulayan, etki alanına özgü bir dilde (DSL) tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="f8faf-116">A `conceptual model` is a specific representation of the structure of data as entities and relationships, and is generally defined in a domain-specific language (DSL) that implements the concepts of the EDM.</span></span> <span data-ttu-id="f8faf-117">[Kavramsal şema tanım dili (csdl)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec) , bu tür bir etki alanına özgü dilin bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="f8faf-117">[Conceptual schema definition language (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec) is an example of such a domain-specific language.</span></span> <span data-ttu-id="f8faf-118">Kavramsal modelde tanımlanan varlıklar ve ilişkiler, bir uygulamadaki nesne ve ilişkilerin soyutlamalarını olarak düşünülebilir.</span><span class="sxs-lookup"><span data-stu-id="f8faf-118">Entities and relationships described in a conceptual model can be thought of as abstractions of objects and associations in an application.</span></span> <span data-ttu-id="f8faf-119">Bu, geliştiricilerin depolama şemasına gerek kalmadan kavramsal modele odaklanmasını sağlar ve verimlilik ve bakımsız kod yazmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="f8faf-119">This allows developers to focus on the conceptual model without concern for the storage schema, and allows them to write code with efficiency and maintainability in mind.</span></span> <span data-ttu-id="f8faf-120">Bu arada, depolama şeması tasarımcıları veri erişimi, depolama ve ölçeklenebilirlik verimliliğine odaklanabilir.</span><span class="sxs-lookup"><span data-stu-id="f8faf-120">Meanwhile storage schema designers can focus on the efficiency of data access, storage, and scalability.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f8faf-121">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="f8faf-121">In This Section</span></span>  
 <span data-ttu-id="f8faf-122">Bu bölümdeki konular Varlık Veri Modeli kavramlarını anlatmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f8faf-122">Topics in this section describe the concepts of the Entity Data Model.</span></span> <span data-ttu-id="f8faf-123">EDM 'yi uygulayan herhangi bir DSL, burada açıklanan kavramları içermelidir.</span><span class="sxs-lookup"><span data-stu-id="f8faf-123">Any DSL that implements the EDM should include the concepts described here.</span></span> <span data-ttu-id="f8faf-124">[ADO.NET Entity Framework](./ef/index.md) 'nin, kavramsal modelleri tanımlamak için csdl kullandığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f8faf-124">Note that the [ADO.NET Entity Framework](./ef/index.md) uses CSDL to define conceptual models.</span></span> <span data-ttu-id="f8faf-125">Daha fazla bilgi için bkz. [csdl belirtimi](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec).</span><span class="sxs-lookup"><span data-stu-id="f8faf-125">For more information, see [CSDL Specification](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec).</span></span>  
  
 [<span data-ttu-id="f8faf-126">Varlık Veri Modeli Temel Kavramları</span><span class="sxs-lookup"><span data-stu-id="f8faf-126">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)  
  
 [<span data-ttu-id="f8faf-127">Varlık Veri Modeli: Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="f8faf-127">Entity Data Model: Namespaces</span></span>](entity-data-model-namespaces.md)  
  
 [<span data-ttu-id="f8faf-128">Varlık Veri Modeli: Basit Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="f8faf-128">Entity Data Model: Primitive Data Types</span></span>](entity-data-model-primitive-data-types.md)  
  
 [<span data-ttu-id="f8faf-129">Varlık Veri Modeli: Devralma</span><span class="sxs-lookup"><span data-stu-id="f8faf-129">Entity Data Model: Inheritance</span></span>](entity-data-model-inheritance.md)  
  
 [<span data-ttu-id="f8faf-130">association end</span><span class="sxs-lookup"><span data-stu-id="f8faf-130">association end</span></span>](association-end.md)  
  
 [<span data-ttu-id="f8faf-131">association end multiplicity</span><span class="sxs-lookup"><span data-stu-id="f8faf-131">association end multiplicity</span></span>](association-end-multiplicity.md)  
  
 [<span data-ttu-id="f8faf-132">association set</span><span class="sxs-lookup"><span data-stu-id="f8faf-132">association set</span></span>](association-set.md)  
  
 [<span data-ttu-id="f8faf-133">association set end</span><span class="sxs-lookup"><span data-stu-id="f8faf-133">association set end</span></span>](association-set-end.md)  
  
 [<span data-ttu-id="f8faf-134">association type</span><span class="sxs-lookup"><span data-stu-id="f8faf-134">association type</span></span>](association-type.md)  
  
 [<span data-ttu-id="f8faf-135">complex type</span><span class="sxs-lookup"><span data-stu-id="f8faf-135">complex type</span></span>](complex-type.md)  
  
 [<span data-ttu-id="f8faf-136">entity container</span><span class="sxs-lookup"><span data-stu-id="f8faf-136">entity container</span></span>](entity-container.md)  
  
 [<span data-ttu-id="f8faf-137">entity key</span><span class="sxs-lookup"><span data-stu-id="f8faf-137">entity key</span></span>](entity-key.md)  
  
 [<span data-ttu-id="f8faf-138">entity set</span><span class="sxs-lookup"><span data-stu-id="f8faf-138">entity set</span></span>](entity-set.md)  
  
 [<span data-ttu-id="f8faf-139">entity type</span><span class="sxs-lookup"><span data-stu-id="f8faf-139">entity type</span></span>](entity-type.md)  
  
 [<span data-ttu-id="f8faf-140">facet</span><span class="sxs-lookup"><span data-stu-id="f8faf-140">facet</span></span>](facet.md)  
  
 [<span data-ttu-id="f8faf-141">foreign key property</span><span class="sxs-lookup"><span data-stu-id="f8faf-141">foreign key property</span></span>](foreign-key-property.md)  
  
 [<span data-ttu-id="f8faf-142">model-declared function</span><span class="sxs-lookup"><span data-stu-id="f8faf-142">model-declared function</span></span>](model-declared-function.md)  
  
 [<span data-ttu-id="f8faf-143">model-defined function</span><span class="sxs-lookup"><span data-stu-id="f8faf-143">model-defined function</span></span>](model-defined-function.md)  
  
 [<span data-ttu-id="f8faf-144">navigation property</span><span class="sxs-lookup"><span data-stu-id="f8faf-144">navigation property</span></span>](navigation-property.md)  
  
 [<span data-ttu-id="f8faf-145">özelliði</span><span class="sxs-lookup"><span data-stu-id="f8faf-145">property</span></span>](property.md)  
  
 [<span data-ttu-id="f8faf-146">referential integrity constraint</span><span class="sxs-lookup"><span data-stu-id="f8faf-146">referential integrity constraint</span></span>](referential-integrity-constraint.md)  
  
## <a name="see-also"></a><span data-ttu-id="f8faf-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f8faf-147">See also</span></span>

- <span data-ttu-id="f8faf-148">[ADO.NET Varlık Veri Modeli araçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f8faf-148">[ADO.NET Entity Data Model Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
- <span data-ttu-id="f8faf-149">[. edmx dosyasına genel bakış](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f8faf-149">[.edmx File Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span></span>
- [<span data-ttu-id="f8faf-150">CSDL belirtimi</span><span class="sxs-lookup"><span data-stu-id="f8faf-150">CSDL Specification</span></span>](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)

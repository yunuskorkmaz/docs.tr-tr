---
description: 'Daha fazla bilgi edinin: sorgu tahminleri (WCF Veri Hizmetleri)'
title: Sorgu tahminleri (WCF Veri Hizmetleri)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- projection [WCF Data Services]
- WCF Data Services, projection
- query projection [WCF Data Services]
- WCF Data Services, querying
ms.assetid: a09f4985-9f0d-48c8-b183-83d67a3dfe5f
ms.openlocfilehash: 35427a4bc74691f366711c30cfa7af23de1caa35
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794968"
---
# <a name="query-projections-wcf-data-services"></a><span data-ttu-id="3300b-103">Sorgu tahminleri (WCF Veri Hizmetleri)</span><span class="sxs-lookup"><span data-stu-id="3300b-103">Query Projections (WCF Data Services)</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="3300b-104">Projeksiyon, yanıtta bir varlığın yalnızca belirli özelliklerinin döndürülüp döndürülmeyeceğini belirterek, bir sorgu tarafından döndürülen akıştaki veri miktarını azaltmak için açık veri Protokolü (OData) içinde bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="3300b-104">Projection provides a mechanism in the Open Data Protocol (OData) to reduce the amount of data in the feed returned by a query by specifying that only certain properties of an entity are returned in the response.</span></span> <span data-ttu-id="3300b-105">Daha fazla bilgi için bkz. Bölüm 4,8.</span><span class="sxs-lookup"><span data-stu-id="3300b-105">For more information, see section 4.8.</span></span> <span data-ttu-id="3300b-106">[URI kuralları (OData sürüm 2,0)](https://www.odata.org/documentation/odata-version-2-0/uri-conventions/)Içindeki sistem sorgu seçeneğini ($Select) seçin.</span><span class="sxs-lookup"><span data-stu-id="3300b-106">Select System Query Option ($select) in [URI Conventions (OData Version 2.0)](https://www.odata.org/documentation/odata-version-2-0/uri-conventions/).</span></span>

<span data-ttu-id="3300b-107">Bu konu, bir sorgu projeksiyonu, varlık ve varlık olmayan türler için gereksinimlerin ne olduğunu, öngörülen sonuçlara yönelik güncelleştirmeler yapmayı, tasarlanan türleri oluşturmayı ve bazı projeksiyon konularını listeler.</span><span class="sxs-lookup"><span data-stu-id="3300b-107">This topic describes how to define a query projection, what the requirements are for entity and non-entity types, making updates to projected results, creating projected types, and lists some projection considerations.</span></span>

## <a name="defining-a-query-projection"></a><span data-ttu-id="3300b-108">Sorgu projeksiyonu tanımlama</span><span class="sxs-lookup"><span data-stu-id="3300b-108">Defining a Query Projection</span></span>

<span data-ttu-id="3300b-109">Bir `$select` URI 'de sorgu seçeneğini kullanarak veya BIR LINQ sorgusunda [Select](../../../csharp/language-reference/keywords/select-clause.md) yan tümcesini (Visual Basic içinde[seçin](../../../visual-basic/language-reference/queries/select-clause.md) ) kullanarak bir sorguya projeksiyon yan tümcesi ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3300b-109">You can add a projection clause to a query either by using the `$select` query option in a URI or by using the [select](../../../csharp/language-reference/keywords/select-clause.md) clause ([Select](../../../visual-basic/language-reference/queries/select-clause.md) in Visual Basic) in a LINQ query.</span></span> <span data-ttu-id="3300b-110">Döndürülen varlık verileri, istemci üzerindeki varlık türlerine veya varlık olmayan türlere yansıtılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3300b-110">Returned entity data can be projected into either entity types or non-entity types on the client.</span></span> <span data-ttu-id="3300b-111">Bu konudaki örneklerde `select` BIR LINQ sorgusunda yan tümcesinin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3300b-111">Examples in this topic demonstrate how to use the `select` clause in a LINQ query.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3300b-112">Tasarlanan türlerde yapılan güncelleştirmeleri kaydettiğinizde veri hizmetinde veri kaybı oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="3300b-112">Data loss might occur in the data service when you save updates that were made to projected types.</span></span> <span data-ttu-id="3300b-113">Daha fazla bilgi için bkz. [projeksiyon konuları](#considerations).</span><span class="sxs-lookup"><span data-stu-id="3300b-113">For more information, see [Projection Considerations](#considerations).</span></span>

## <a name="requirements-for-entity-and-non-entity-types"></a><span data-ttu-id="3300b-114">Varlık ve varlık olmayan türler için gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3300b-114">Requirements for Entity and Non-Entity Types</span></span>

<span data-ttu-id="3300b-115">Varlık türlerinin, varlık anahtarını oluşturan bir veya daha fazla kimlik özelliği olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3300b-115">Entity types must have one or more identity properties that make up the entity key.</span></span> <span data-ttu-id="3300b-116">Varlık türleri, istemcilerde aşağıdaki yollarla tanımlanmıştır:</span><span class="sxs-lookup"><span data-stu-id="3300b-116">Entity types are defined on clients in one of the following ways:</span></span>

- <span data-ttu-id="3300b-117"><xref:System.Data.Services.Common.DataServiceKeyAttribute>Ya da türünü uygulayarak <xref:System.Data.Services.Common.DataServiceEntityAttribute> .</span><span class="sxs-lookup"><span data-stu-id="3300b-117">By applying the <xref:System.Data.Services.Common.DataServiceKeyAttribute> or <xref:System.Data.Services.Common.DataServiceEntityAttribute> to the type.</span></span>

- <span data-ttu-id="3300b-118">Türün adında bir özelliği olduğunda `ID` .</span><span class="sxs-lookup"><span data-stu-id="3300b-118">When the type has a property named `ID`.</span></span>

- <span data-ttu-id="3300b-119">*Türün Type adlı bir* özelliği varsa `ID` , burada tür adıdır  .</span><span class="sxs-lookup"><span data-stu-id="3300b-119">When the type has a property named *type*`ID`, where *type* is the name of the type.</span></span>

<span data-ttu-id="3300b-120">Varsayılan olarak, sorgu sonuçlarını istemcide tanımlı bir türe proje yaparken, projeksiyde istenen özellikler istemci türünde bulunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3300b-120">By default, when you project query results into a type defined at the client, the properties requested in the projection must exist in the client type.</span></span> <span data-ttu-id="3300b-121">Ancak, özelliği için bir değeri belirttiğinizde, `true` <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> <xref:System.Data.Services.Client.DataServiceContext> projeksiyonda belirtilen özelliklerin istemci türünde gerçekleşmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="3300b-121">However, when you specify a value of `true` for the <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> property of the <xref:System.Data.Services.Client.DataServiceContext>, properties specified in the projection are not required to occur in the client type.</span></span>

### <a name="making-updates-to-projected-results"></a><span data-ttu-id="3300b-122">Yansıtılan sonuçlara güncelleştirmeler yapılıyor</span><span class="sxs-lookup"><span data-stu-id="3300b-122">Making Updates to Projected Results</span></span>

<span data-ttu-id="3300b-123">Sorgu sonuçlarını istemcideki varlık türlerine proje yaparken, <xref:System.Data.Services.Client.DataServiceContext> Bu nesneleri, yöntem çağrıldığında veri hizmetine geri gönderilmek üzere güncelleştirmeler ile izleyebilir <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> .</span><span class="sxs-lookup"><span data-stu-id="3300b-123">When you project query results into entity types on the client, the <xref:System.Data.Services.Client.DataServiceContext> can track those objects with updates to be sent back to the data service when the <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> method is called.</span></span> <span data-ttu-id="3300b-124">Ancak, istemcideki varlık olmayan türlere yapılan veriler veri hizmetine geri gönderilemez.</span><span class="sxs-lookup"><span data-stu-id="3300b-124">However, updates that are made to data projected into non-entity types on the client cannot be sent back to the data service.</span></span> <span data-ttu-id="3300b-125">Bunun nedeni, varlık örneğini tanımlamak için bir anahtar olmadığı için veri hizmeti veri kaynağındaki doğru varlığı güncelleştiremez.</span><span class="sxs-lookup"><span data-stu-id="3300b-125">This is because without a key to identify the entity instance, the data service cannot update the correct entity in the data source.</span></span> <span data-ttu-id="3300b-126">Varlık dışı türler öğesine eklenmez <xref:System.Data.Services.Client.DataServiceContext> .</span><span class="sxs-lookup"><span data-stu-id="3300b-126">Non-entity types are not attached to the <xref:System.Data.Services.Client.DataServiceContext>.</span></span>

<span data-ttu-id="3300b-127">Veri hizmetinde tanımlanan bir veya daha fazla varlık türünün bir veya daha fazla özelliği, varlığın yansıtıldıkları istemci türünde gerçekleşmezse, yeni varlıkların ekleme işlemi bu eksik özellikleri içermez.</span><span class="sxs-lookup"><span data-stu-id="3300b-127">When one or more properties of an entity type defined in the data service do not occur in the client type into which the entity is projected, inserts of new entities will not contain these missing properties.</span></span> <span data-ttu-id="3300b-128">Bu durumda, mevcut varlıklarda yapılan güncelleştirmeler bu eksik özellikleri **de** içermez.</span><span class="sxs-lookup"><span data-stu-id="3300b-128">In this case, updates that are made to existing entities will **also** not include these missing properties.</span></span> <span data-ttu-id="3300b-129">Bu tür bir özellik için bir değer varsa, güncelleştirme onu veri kaynağında tanımlandığı şekilde özellik için varsayılan değere sıfırlar.</span><span class="sxs-lookup"><span data-stu-id="3300b-129">When a value exists for such a property, the update resets it to the default value for the property, as defined in the data source.</span></span>

### <a name="creating-projected-types"></a><span data-ttu-id="3300b-130">Öngörülen türler oluşturuluyor</span><span class="sxs-lookup"><span data-stu-id="3300b-130">Creating Projected Types</span></span>

<span data-ttu-id="3300b-131">Aşağıdaki örnek, türün adresle ilgili özelliklerini, `Customers` `CustomerAddress` istemcisinde tanımlanmış olan ve bir varlık türü olarak öznitelikli yeni bir türe uygulayan anonım bir LINQ sorgusu kullanır:</span><span class="sxs-lookup"><span data-stu-id="3300b-131">The following example uses an anonymous LINQ query that projects the address-related properties of the `Customers` type into a new `CustomerAddress` type, which is defined on the client and is attributed as an entity type:</span></span>

[!code-csharp[Astoria Northwind Client#SelectCustomerAddressSpecific](~/samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#selectcustomeraddressspecific)]
[!code-vb[Astoria Northwind Client#SelectCustomerAddressSpecific](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#selectcustomeraddressspecific)]

<span data-ttu-id="3300b-132">Bu örnekte, nesne Başlatıcısı, `CustomerAddress` bir oluşturucuyu çağırmak yerine türün yeni bir örneğini oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3300b-132">In this example, the object initializer pattern is used to create a new instance of the `CustomerAddress` type instead of calling a constructor.</span></span> <span data-ttu-id="3300b-133">Oluşturucular varlık türlerine yansıtılamayan desteklenmez, ancak varlık dışı ve anonim türler halinde yansıtılarınızda kullanılabilirler.</span><span class="sxs-lookup"><span data-stu-id="3300b-133">Constructors are not supported when projecting into entity types, but they can be used when projecting into non-entity and anonymous types.</span></span> <span data-ttu-id="3300b-134">`CustomerAddress`Bir varlık türü olduğundan, değişiklikler yapılabilir ve veri hizmetine geri gönderilebilir.</span><span class="sxs-lookup"><span data-stu-id="3300b-134">Because `CustomerAddress` is an entity type, changes can be made and sent back to the data service.</span></span>

<span data-ttu-id="3300b-135">Ayrıca, türdeki veriler anonim bir `Customer` `CustomerAddress` tür yerine varlık türünün bir örneğine yansıtıldır.</span><span class="sxs-lookup"><span data-stu-id="3300b-135">Also, the data from the `Customer` type is projected into an instance of the `CustomerAddress` entity type instead of an anonymous type.</span></span> <span data-ttu-id="3300b-136">Anonim türlere yansıtma desteklenir, ancak anonim türler varlık dışı türler olarak değerlendirildiğinden veriler salt okunurdur.</span><span class="sxs-lookup"><span data-stu-id="3300b-136">Projection into anonymous types is supported, but the data is read-only because anonymous types are treated as non-entity types.</span></span>

<span data-ttu-id="3300b-137"><xref:System.Data.Services.Client.MergeOption>Ayarları, <xref:System.Data.Services.Client.DataServiceContext> sorgu projeksiyonu sırasında kimlik çözümlemesi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3300b-137">The <xref:System.Data.Services.Client.MergeOption> settings of the <xref:System.Data.Services.Client.DataServiceContext> are used for identity resolution during query projection.</span></span> <span data-ttu-id="3300b-138">Bu, türünün bir örneği `Customer` içinde zaten mevcutsa <xref:System.Data.Services.Client.DataServiceContext> , `CustomerAddress` aynı kimliğe sahip bir örneği, tarafından ayarlanan kimlik çözümleme kurallarını takip eder. <xref:System.Data.Services.Client.MergeOption></span><span class="sxs-lookup"><span data-stu-id="3300b-138">This means that if an instance of the `Customer` type already exists in the <xref:System.Data.Services.Client.DataServiceContext>, an instance of `CustomerAddress` with the same identity will follow the identity resolution rules set by the <xref:System.Data.Services.Client.MergeOption></span></span>

<span data-ttu-id="3300b-139">Aşağıda, sonuçlar varlık ve varlık olmayan türlere yansıtılanmakta olan davranışlar açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="3300b-139">The following describes the behaviors when projecting results into entity and non-entity types:</span></span>

<span data-ttu-id="3300b-140">**Başlatıcıları kullanarak yeni bir öngörülen örnek oluşturma**</span><span class="sxs-lookup"><span data-stu-id="3300b-140">**Creating a new projected instance by using initializers**</span></span>

- <span data-ttu-id="3300b-141">Örnek:</span><span class="sxs-lookup"><span data-stu-id="3300b-141">Example:</span></span>

   [!code-csharp[Astoria Northwind Client#ProjectWithInitializer](~/samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#projectwithinitializer)]
   [!code-vb[Astoria Northwind Client#ProjectWithInitializer](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#projectwithinitializer)]

- <span data-ttu-id="3300b-142">Varlık türü: destekleniyor</span><span class="sxs-lookup"><span data-stu-id="3300b-142">Entity type: Supported</span></span>

- <span data-ttu-id="3300b-143">Varlık olmayan tür: destekleniyor</span><span class="sxs-lookup"><span data-stu-id="3300b-143">Non-entity type: Supported</span></span>

<span data-ttu-id="3300b-144">**Oluşturucular kullanarak yeni bir öngörülen örnek oluşturma**</span><span class="sxs-lookup"><span data-stu-id="3300b-144">**Creating a new projected instance by using constructors**</span></span>

- <span data-ttu-id="3300b-145">Örnek:</span><span class="sxs-lookup"><span data-stu-id="3300b-145">Example:</span></span>

   [!code-csharp[Astoria Northwind Client#ProjectWithConstructor](~/samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#projectwithconstructor)]
   [!code-vb[Astoria Northwind Client#ProjectWithConstructor](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#projectwithconstructor)]

- <span data-ttu-id="3300b-146">Varlık türü: A <xref:System.NotSupportedException> tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="3300b-146">Entity type: A <xref:System.NotSupportedException> is raised.</span></span>

- <span data-ttu-id="3300b-147">Varlık olmayan tür: destekleniyor</span><span class="sxs-lookup"><span data-stu-id="3300b-147">Non-entity type: Supported</span></span>

<span data-ttu-id="3300b-148">**Bir özellik değerini dönüştürmek için projeksiyonu kullanma**</span><span class="sxs-lookup"><span data-stu-id="3300b-148">**Using projection to transform a property value**</span></span>

- <span data-ttu-id="3300b-149">Örnek:</span><span class="sxs-lookup"><span data-stu-id="3300b-149">Example:</span></span>

   [!code-csharp[Astoria Northwind Client#ProjectWithTransform](~/samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#projectwithtransform)]
   [!code-vb[Astoria Northwind Client#ProjectWithTransform](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#projectwithtransform)]

- <span data-ttu-id="3300b-150">Varlık türü: Bu dönüşüm, varlık türleri için desteklenmez çünkü bu, başka bir varlığa ait veri kaynağındaki verilerin üzerine yazılmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="3300b-150">Entity type: This transformation is not supported for entity types because it can lead to confusion and potentially overwriting the data in the data source that belongs to another entity.</span></span> <span data-ttu-id="3300b-151">Bir <xref:System.NotSupportedException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3300b-151">A <xref:System.NotSupportedException> is raised.</span></span>

- <span data-ttu-id="3300b-152">Varlık olmayan tür: destekleniyor</span><span class="sxs-lookup"><span data-stu-id="3300b-152">Non-entity type: Supported</span></span>

<a name="considerations"></a>

## <a name="projection-considerations"></a><span data-ttu-id="3300b-153">Projeksiyon konuları</span><span class="sxs-lookup"><span data-stu-id="3300b-153">Projection Considerations</span></span>

<span data-ttu-id="3300b-154">Bir sorgu projeksiyonu tanımlarken aşağıdaki ek konular geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="3300b-154">The following additional considerations apply when defining a query projection.</span></span>

- <span data-ttu-id="3300b-155">Atom biçimi için özel akışlar tanımladığınızda, tanımlanmış özel eşlemelere sahip tüm varlık özelliklerinin projeksiyonda eklendiğinden emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3300b-155">When you define custom feeds for the Atom format, you must make sure that all entity properties that have custom mappings defined are included in the projection.</span></span> <span data-ttu-id="3300b-156">Eşlenen bir varlık özelliği projeksiyonde yer olmadığında veri kaybı oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="3300b-156">When a mapped entity property is not included in the projection, data loss might occur.</span></span> <span data-ttu-id="3300b-157">Daha fazla bilgi için bkz. [akış özelleştirmesi](feed-customization-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="3300b-157">For more information, see [Feed Customization](feed-customization-wcf-data-services.md).</span></span>

- <span data-ttu-id="3300b-158">Veri hizmetinin veri modelindeki varlık özelliklerinin tümünü içermeyen bir öngörülen türe ekleme yapıldığında, istemcideki projeksiyonde bulunmayan özellikler varsayılan değerlerine ayarlanır...</span><span class="sxs-lookup"><span data-stu-id="3300b-158">When inserts are made to a projected type that does not contain all of the properties of the entity in the data model of the data service, the properties not included in the projection at the client are set to their default values.</span></span>

- <span data-ttu-id="3300b-159">Veri hizmetinin veri modelindeki varlık özelliklerinin tümünü içermeyen bir öngörülen tür için güncelleştirmeler yapıldığında, istemcideki projeksiyonde bulunmayan mevcut değerlerin üzerine başlatılmamış varsayılan değerler eklenir.</span><span class="sxs-lookup"><span data-stu-id="3300b-159">When updates are made to a projected type that does not contain all of the properties of the entity in the data model of the data service, existing values not included in the projection on the client will be overwritten with uninitialized default values.</span></span>

- <span data-ttu-id="3300b-160">Projeksiyon karmaşık bir özellik içerdiğinde, tüm karmaşık nesne döndürülmelidir.</span><span class="sxs-lookup"><span data-stu-id="3300b-160">When a projection includes a complex property, the entire complex object must be returned.</span></span>

- <span data-ttu-id="3300b-161">Projeksiyon bir gezinti özelliği içerdiğinde, ilgili nesneler yöntemi çağırmak zorunda kalmadan örtük olarak yüklenir <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> .</span><span class="sxs-lookup"><span data-stu-id="3300b-161">When a projection includes a navigation property, the related objects are loaded implicitly without having to call the <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> method.</span></span> <span data-ttu-id="3300b-162"><xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A>Yöntem, tasarlanan bir sorguda kullanım için desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="3300b-162">The <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> method is not supported for use in a projected query.</span></span>

- <span data-ttu-id="3300b-163">İstemcideki sorgu tahminleri sorguları, `$select` Istek URI 'sindeki sorgu seçeneğini kullanacak şekilde çevrilir.</span><span class="sxs-lookup"><span data-stu-id="3300b-163">Query projections queries on the client are translated to use the `$select` query option in the request URI.</span></span> <span data-ttu-id="3300b-164">Projeksiyon içeren bir sorgu, sorgu seçeneğini desteklemeyen WCF Veri Hizmetleri önceki bir sürümüne karşı yürütüldüğünde `$select` bir hata döndürülür.</span><span class="sxs-lookup"><span data-stu-id="3300b-164">When a query with projection is executed against a previous version of WCF Data Services that does not support the `$select` query option, an error is returned.</span></span> <span data-ttu-id="3300b-165">Bu durum, <xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A> <xref:System.Data.Services.DataServiceBehavior> veri hizmeti için öğesinin bir değerine ayarlandığı durumlarda da gerçekleşebilir <xref:System.Data.Services.Common.DataServiceProtocolVersion.V1> .</span><span class="sxs-lookup"><span data-stu-id="3300b-165">This can also happen when the <xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A> of the <xref:System.Data.Services.DataServiceBehavior> for the data service is set to a value of <xref:System.Data.Services.Common.DataServiceProtocolVersion.V1>.</span></span> <span data-ttu-id="3300b-166">Daha fazla bilgi için bkz. [veri hizmeti sürümü oluşturma](data-service-versioning-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="3300b-166">For more information, see [Data Service Versioning](data-service-versioning-wcf-data-services.md).</span></span>

<span data-ttu-id="3300b-167">Daha fazla bilgi için bkz. [nasıl yapılır: Proje sorgu sonuçları](how-to-project-query-results-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="3300b-167">For more information, see [How to: Project Query Results](how-to-project-query-results-wcf-data-services.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3300b-168">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3300b-168">See also</span></span>

- [<span data-ttu-id="3300b-169">Veri Hizmetini Sorgulama</span><span class="sxs-lookup"><span data-stu-id="3300b-169">Querying the Data Service</span></span>](querying-the-data-service-wcf-data-services.md)

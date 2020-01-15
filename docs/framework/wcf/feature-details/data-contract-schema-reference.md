---
title: Veri Sözleşmesi Şema Başvurusu
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts [WCF], schema reference
ms.assetid: 9ebb0ebe-8166-4c93-980a-7c8f1f38f7c0
ms.openlocfilehash: af183fa02ea3ec98f316979198624351d9b25f21
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/15/2020
ms.locfileid: "75963365"
---
# <a name="data-contract-schema-reference"></a><span data-ttu-id="a8294-102">Veri Sözleşmesi Şema Başvurusu</span><span class="sxs-lookup"><span data-stu-id="a8294-102">Data Contract Schema Reference</span></span>

<span data-ttu-id="a8294-103">Bu konu, XML serileştirmesi için ortak dil çalışma zamanı (CLR) türlerini tarif etmek üzere <xref:System.Runtime.Serialization.DataContractSerializer> tarafından kullanılan XML şemasının (XSD) alt kümesini açıklar.</span><span class="sxs-lookup"><span data-stu-id="a8294-103">This topic describes the subset of the XML Schema (XSD) used by <xref:System.Runtime.Serialization.DataContractSerializer> to describe common language runtime (CLR) types for XML serialization.</span></span>

## <a name="datacontractserializer-mappings"></a><span data-ttu-id="a8294-104">DataContractSerializer eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="a8294-104">DataContractSerializer Mappings</span></span>

<span data-ttu-id="a8294-105">`DataContractSerializer` meta veriler, meta veri uç noktası veya [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)kullanılarak bir WINDOWS COMMUNICATION FOUNDATION (WCF) HIZMETINDEN aktarıldığında CLR türlerini xsd ile eşler.</span><span class="sxs-lookup"><span data-stu-id="a8294-105">The `DataContractSerializer` maps CLR types to XSD when metadata is exported from a Windows Communication Foundation (WCF) service using a metadata endpoint or the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="a8294-106">Daha fazla bilgi için bkz. [veri sözleşmesi serileştiricisi](../../../../docs/framework/wcf/feature-details/data-contract-serializer.md).</span><span class="sxs-lookup"><span data-stu-id="a8294-106">For more information, see [Data Contract Serializer](../../../../docs/framework/wcf/feature-details/data-contract-serializer.md).</span></span>

<span data-ttu-id="a8294-107">Ayrıca, Web Hizmetleri Açıklama Dili (WSDL) veya XSD belgelerine erişmek ve hizmetler veya istemciler için veri sözleşmeleri oluşturmak için Svcutil. exe kullanıldığında `DataContractSerializer` XSD 'yi CLR türlerine eşler.</span><span class="sxs-lookup"><span data-stu-id="a8294-107">The `DataContractSerializer` also maps XSD to CLR types when Svcutil.exe is used to access Web Services Description Language (WSDL) or XSD documents and generate data contracts for services or clients.</span></span>

<span data-ttu-id="a8294-108">Yalnızca bu belgede belirtilen gereksinimlere uyan XML şema örnekleri, `DataContractSerializer`kullanılarak CLR türleriyle eşleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="a8294-108">Only XML Schema instances that conform to requirements stated in this document can be mapped to CLR types using `DataContractSerializer`.</span></span>

### <a name="support-levels"></a><span data-ttu-id="a8294-109">Destek Düzeyleri</span><span class="sxs-lookup"><span data-stu-id="a8294-109">Support Levels</span></span>

<span data-ttu-id="a8294-110">`DataContractSerializer`, belirli bir XML şeması özelliği için aşağıdaki destek düzeylerini sağlar:</span><span class="sxs-lookup"><span data-stu-id="a8294-110">The `DataContractSerializer` provides the following levels of support for a given XML Schema feature:</span></span>

- <span data-ttu-id="a8294-111">**Desteklenir**.</span><span class="sxs-lookup"><span data-stu-id="a8294-111">**Supported**.</span></span> <span data-ttu-id="a8294-112">`DataContractSerializer`kullanarak bu özellikten CLR türlerine veya özniteliklerine (ya da her ikisine) açık eşleme vardır.</span><span class="sxs-lookup"><span data-stu-id="a8294-112">There is explicit mapping from this feature to CLR types or attributes (or both) using `DataContractSerializer`.</span></span>

- <span data-ttu-id="a8294-113">**Yoksayıldı**.</span><span class="sxs-lookup"><span data-stu-id="a8294-113">**Ignored**.</span></span> <span data-ttu-id="a8294-114">Özelliğe `DataContractSerializer`tarafından içeri aktarılan şemalarda izin verilir, ancak kod üretimi üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="a8294-114">The feature is allowed in schemas imported by the `DataContractSerializer`, but has no effect on code generation.</span></span>

- <span data-ttu-id="a8294-115">**Yasak**.</span><span class="sxs-lookup"><span data-stu-id="a8294-115">**Forbidden**.</span></span> <span data-ttu-id="a8294-116">`DataContractSerializer`, özelliği kullanarak bir şemanın içeri aktarılmasını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="a8294-116">The `DataContractSerializer` does not support importing a schema using the feature.</span></span> <span data-ttu-id="a8294-117">Örneğin, bu tür bir özelliği kullanan bir şemaya sahip bir WSDL 'ye erişirken Svcutil. exe, bunun yerine <xref:System.Xml.Serialization.XmlSerializer> kullanmaya geri döner.</span><span class="sxs-lookup"><span data-stu-id="a8294-117">For example, Svcutil.exe, when accessing a WSDL with a schema that uses such a feature, falls back to using the <xref:System.Xml.Serialization.XmlSerializer> instead.</span></span> <span data-ttu-id="a8294-118">Bu varsayılan olarak olur.</span><span class="sxs-lookup"><span data-stu-id="a8294-118">This is by default.</span></span>

## <a name="general-information"></a><span data-ttu-id="a8294-119">Genel Bilgiler</span><span class="sxs-lookup"><span data-stu-id="a8294-119">General Information</span></span>

- <span data-ttu-id="a8294-120">Şema ad alanı [XML şemasında](https://www.w3.org/2001/XMLSchema)açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a8294-120">The schema namespace is described at [XML Schema](https://www.w3.org/2001/XMLSchema).</span></span> <span data-ttu-id="a8294-121">"Xs" ön eki bu belgede kullanılıyor.</span><span class="sxs-lookup"><span data-stu-id="a8294-121">The prefix "xs" is used in this document.</span></span>

- <span data-ttu-id="a8294-122">Şema olmayan bir ad alanı olan herhangi bir öznitelik yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="a8294-122">Any attributes with a non-schema namespace are ignored.</span></span>

- <span data-ttu-id="a8294-123">Tüm ek açıklamalar (Bu belgede açıklananlar dışında) yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="a8294-123">Any annotations (except for those described in this document) are ignored.</span></span>

### <a name="xsschema-attributes"></a><span data-ttu-id="a8294-124">\<xs: Schema >: öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a8294-124">\<xs:schema>: attributes</span></span>

|<span data-ttu-id="a8294-125">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a8294-125">Attribute</span></span>|<span data-ttu-id="a8294-126">DataContract</span><span class="sxs-lookup"><span data-stu-id="a8294-126">DataContract</span></span>|
|---------------|------------------|
|`attributeFormDefault`|<span data-ttu-id="a8294-127">LIP.</span><span class="sxs-lookup"><span data-stu-id="a8294-127">Ignored.</span></span>|
|`blockDefault`|<span data-ttu-id="a8294-128">LIP.</span><span class="sxs-lookup"><span data-stu-id="a8294-128">Ignored.</span></span>|
|`elementFormDefault`|<span data-ttu-id="a8294-129">Nitelenmiş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a8294-129">Must be qualified.</span></span> <span data-ttu-id="a8294-130">Bir şemanın `DataContractSerializer`tarafından desteklenmesi için tüm öğelerin nitelenmiş olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a8294-130">All elements must be qualified for a schema to be supported by `DataContractSerializer`.</span></span> <span data-ttu-id="a8294-131">Bu, xs:schema/@elementFormDefault "nitelikli" olarak ayarlanarak veya her bir öğe bildiriminde xs:element/@form "Qualified" olarak ayarlanarak gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="a8294-131">This can be accomplished by either setting xs:schema/@elementFormDefault to "qualified" or by setting xs:element/@form to "qualified" on each individual element declaration.</span></span>|
|`finalDefault`|<span data-ttu-id="a8294-132">LIP.</span><span class="sxs-lookup"><span data-stu-id="a8294-132">Ignored.</span></span>|
|`Id`|<span data-ttu-id="a8294-133">LIP.</span><span class="sxs-lookup"><span data-stu-id="a8294-133">Ignored.</span></span>|
|`targetNamespace`|<span data-ttu-id="a8294-134">Desteklenir ve veri sözleşmesi ad alanıyla eşleştirilir.</span><span class="sxs-lookup"><span data-stu-id="a8294-134">Supported and mapped to the data contract namespace.</span></span> <span data-ttu-id="a8294-135">Bu öznitelik belirtilmemişse boş ad alanı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a8294-135">If this attribute is not specified, the blank namespace is used.</span></span> <span data-ttu-id="a8294-136">Ayrılmış ad alanı `http://schemas.microsoft.com/2003/10/Serialization/`olamaz.</span><span class="sxs-lookup"><span data-stu-id="a8294-136">Cannot be the reserved namespace `http://schemas.microsoft.com/2003/10/Serialization/`.</span></span>|
|`version`|<span data-ttu-id="a8294-137">LIP.</span><span class="sxs-lookup"><span data-stu-id="a8294-137">Ignored.</span></span>|

### <a name="xsschema-contents"></a><span data-ttu-id="a8294-138">\<xs: Schema >: içerikler</span><span class="sxs-lookup"><span data-stu-id="a8294-138">\<xs:schema>: contents</span></span>

|<span data-ttu-id="a8294-139">İçindekiler</span><span class="sxs-lookup"><span data-stu-id="a8294-139">Contents</span></span>|<span data-ttu-id="a8294-140">Şema</span><span class="sxs-lookup"><span data-stu-id="a8294-140">Schema</span></span>|
|--------------|------------|
|`include`|<span data-ttu-id="a8294-141">Desteklenen.</span><span class="sxs-lookup"><span data-stu-id="a8294-141">Supported.</span></span> <span data-ttu-id="a8294-142">`DataContractSerializer` xs: include ve xs: import destekler.</span><span class="sxs-lookup"><span data-stu-id="a8294-142">`DataContractSerializer` supports xs:include and xs:import.</span></span> <span data-ttu-id="a8294-143">Ancak, Svcutil. exe, meta veriler yerel bir dosyadan yüklendiğinde aşağıdaki `xs:include/@schemaLocation` ve `xs:import/@location` başvurularını kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="a8294-143">However, Svcutil.exe restricts following `xs:include/@schemaLocation` and `xs:import/@location` references when metadata is loaded from a local file.</span></span> <span data-ttu-id="a8294-144">Şema dosyalarının listesi, bu durumda `include` değil, bant dışı bir mekanizmaya geçirilmelidir; `include`d şema belgeleri yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="a8294-144">The list of schema files must be passed through an out-of-band mechanism and not through `include` in this case; `include`d schema documents are ignored.</span></span>|
|`redefine`|<span data-ttu-id="a8294-145">Inı.</span><span class="sxs-lookup"><span data-stu-id="a8294-145">Forbidden.</span></span> <span data-ttu-id="a8294-146">`xs:redefine` kullanımı, güvenlik nedenleriyle `DataContractSerializer` yasaktır: `x:redefine`, `schemaLocation` 'in izlenmesinin gerekli olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="a8294-146">The use of `xs:redefine` is forbidden by `DataContractSerializer` for security reasons: `x:redefine` requires `schemaLocation` to be followed.</span></span> <span data-ttu-id="a8294-147">Bazı durumlarda, DataContract kullanan Svcutil. exe `schemaLocation`kullanımını kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="a8294-147">In certain circumstances, Svcutil.exe using DataContract restricts use of `schemaLocation`.</span></span>|
|`import`|<span data-ttu-id="a8294-148">Desteklenen.</span><span class="sxs-lookup"><span data-stu-id="a8294-148">Supported.</span></span> <span data-ttu-id="a8294-149">`DataContractSerializer` `xs:include` ve `xs:import`destekler.</span><span class="sxs-lookup"><span data-stu-id="a8294-149">`DataContractSerializer` supports `xs:include` and `xs:import`.</span></span> <span data-ttu-id="a8294-150">Ancak, Svcutil. exe, meta veriler yerel bir dosyadan yüklendiğinde aşağıdaki `xs:include/@schemaLocation` ve `xs:import/@location` başvurularını kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="a8294-150">However, Svcutil.exe restricts following `xs:include/@schemaLocation` and `xs:import/@location` references when metadata is loaded from a local file.</span></span> <span data-ttu-id="a8294-151">Şema dosyalarının listesi, bu durumda `include` değil, bant dışı bir mekanizmaya geçirilmelidir; `include`d şema belgeleri yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="a8294-151">The list of schema files must be passed through an out-of-band mechanism and not through `include` in this case; `include`d schema documents are ignored.</span></span>|
|`simpleType`|<span data-ttu-id="a8294-152">Desteklenen.</span><span class="sxs-lookup"><span data-stu-id="a8294-152">Supported.</span></span> <span data-ttu-id="a8294-153">`xs:simpleType` bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="a8294-153">See the `xs:simpleType` section.</span></span>|
|`complexType`|<span data-ttu-id="a8294-154">Desteklenir, veri sözleşmeleri ile eşlenir.</span><span class="sxs-lookup"><span data-stu-id="a8294-154">Supported, maps to data contracts.</span></span> <span data-ttu-id="a8294-155">`xs:complexType` bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="a8294-155">See the `xs:complexType` section.</span></span>|
|`group`|<span data-ttu-id="a8294-156">LIP.</span><span class="sxs-lookup"><span data-stu-id="a8294-156">Ignored.</span></span> <span data-ttu-id="a8294-157">`DataContractSerializer` `xs:group`, `xs:attributeGroup`ve `xs:attribute`kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="a8294-157">`DataContractSerializer` does not support use of `xs:group`, `xs:attributeGroup`, and `xs:attribute`.</span></span> <span data-ttu-id="a8294-158">Bu bildirimler `xs:schema`alt öğeleri olarak yok sayılır, ancak `complexType` veya desteklenen diğer yapıların içinde başvurulamaz.</span><span class="sxs-lookup"><span data-stu-id="a8294-158">These declarations are ignored as children of `xs:schema`, but cannot be referenced from within `complexType` or other supported constructs.</span></span>|
|`attributeGroup`|<span data-ttu-id="a8294-159">LIP.</span><span class="sxs-lookup"><span data-stu-id="a8294-159">Ignored.</span></span> <span data-ttu-id="a8294-160">`DataContractSerializer` `xs:group`, `xs:attributeGroup`ve `xs:attribute`kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="a8294-160">`DataContractSerializer` does not support use of `xs:group`, `xs:attributeGroup`, and `xs:attribute`.</span></span> <span data-ttu-id="a8294-161">Bu bildirimler `xs:schema`alt öğeleri olarak yok sayılır, ancak `complexType` veya desteklenen diğer yapıların içinde başvurulamaz.</span><span class="sxs-lookup"><span data-stu-id="a8294-161">These declarations are ignored as children of `xs:schema`, but cannot be referenced from within `complexType` or other supported constructs.</span></span>|
|`element`|<span data-ttu-id="a8294-162">Desteklenen.</span><span class="sxs-lookup"><span data-stu-id="a8294-162">Supported.</span></span> <span data-ttu-id="a8294-163">Bkz. genel öğe bildirimi (ŞLı).</span><span class="sxs-lookup"><span data-stu-id="a8294-163">See Global Element Declaration (GED).</span></span>|
|`attribute`|<span data-ttu-id="a8294-164">LIP.</span><span class="sxs-lookup"><span data-stu-id="a8294-164">Ignored.</span></span> <span data-ttu-id="a8294-165">`DataContractSerializer` `xs:group`, `xs:attributeGroup`ve `xs:attribute`kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="a8294-165">`DataContractSerializer` does not support use of `xs:group`, `xs:attributeGroup`, and `xs:attribute`.</span></span> <span data-ttu-id="a8294-166">Bu bildirimler `xs:schema`alt öğeleri olarak yok sayılır, ancak `complexType` veya desteklenen diğer yapıların içinde başvurulamaz.</span><span class="sxs-lookup"><span data-stu-id="a8294-166">These declarations are ignored as children of `xs:schema`, but cannot be referenced from within `complexType` or other supported constructs.</span></span>|
|`notation`|<span data-ttu-id="a8294-167">LIP.</span><span class="sxs-lookup"><span data-stu-id="a8294-167">Ignored.</span></span>|

## <a name="complex-types--xscomplextype"></a><span data-ttu-id="a8294-168">Karmaşık türler – \<xs: complexType ></span><span class="sxs-lookup"><span data-stu-id="a8294-168">Complex Types – \<xs:complexType></span></span>

### <a name="general-information"></a><span data-ttu-id="a8294-169">Genel Bilgiler</span><span class="sxs-lookup"><span data-stu-id="a8294-169">General Information</span></span>

<span data-ttu-id="a8294-170">Her karmaşık tür \<xs: complexType > bir veri sözleşmesine eşlenir.</span><span class="sxs-lookup"><span data-stu-id="a8294-170">Each complex type \<xs:complexType> maps to a data contract.</span></span>

### <a name="xscomplextype-attributes"></a><span data-ttu-id="a8294-171">\<xs: complexType >: öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a8294-171">\<xs:complexType>: attributes</span></span>

|<span data-ttu-id="a8294-172">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a8294-172">Attribute</span></span>|<span data-ttu-id="a8294-173">Şema</span><span class="sxs-lookup"><span data-stu-id="a8294-173">Schema</span></span>|
|---------------|------------|
|`abstract`|<span data-ttu-id="a8294-174">False (varsayılan) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a8294-174">Must be false (default).</span></span>|
|`block`|<span data-ttu-id="a8294-175">Inı.</span><span class="sxs-lookup"><span data-stu-id="a8294-175">Forbidden.</span></span>|
|`final`|<span data-ttu-id="a8294-176">LIP.</span><span class="sxs-lookup"><span data-stu-id="a8294-176">Ignored.</span></span>|
|`id`|<span data-ttu-id="a8294-177">LIP.</span><span class="sxs-lookup"><span data-stu-id="a8294-177">Ignored.</span></span>|
|`mixed`|<span data-ttu-id="a8294-178">False (varsayılan) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a8294-178">Must be false (default).</span></span>|
|`name`|<span data-ttu-id="a8294-179">Desteklenir ve veri sözleşmesi adına eşlenir.</span><span class="sxs-lookup"><span data-stu-id="a8294-179">Supported and mapped to the data contract name.</span></span> <span data-ttu-id="a8294-180">Adda dönemler varsa, türü bir iç türle eşlemek için bir girişimde bulunuldu.</span><span class="sxs-lookup"><span data-stu-id="a8294-180">If there are periods in the name, an attempt is made to map the type to an inner type.</span></span> <span data-ttu-id="a8294-181">Örneğin, `A.B` adlı karmaşık bir tür, `A`veri sözleşmesi adına sahip bir türün iç türü olan bir veri sözleşmesi türüyle eşlenir, ancak bu tür bir veri anlaşması türü varsa.</span><span class="sxs-lookup"><span data-stu-id="a8294-181">For example, a complex type named `A.B` maps to a data contract type that is an inner type of a type with the data contract name `A`, but only if such a data contract type exists.</span></span> <span data-ttu-id="a8294-182">Birden fazla iç içe geçme olabilir: Örneğin, `A.B.C` bir iç tür olabilir, ancak yalnızca `A` ve `A.B` ikisi de vardır.</span><span class="sxs-lookup"><span data-stu-id="a8294-182">More than one level of nesting is possible: for example, `A.B.C` can be an inner type, but only if `A` and `A.B` both exist.</span></span>|

### <a name="xscomplextype-contents"></a><span data-ttu-id="a8294-183">\<xs: complexType >: içerikler</span><span class="sxs-lookup"><span data-stu-id="a8294-183">\<xs:complexType>: contents</span></span>

|<span data-ttu-id="a8294-184">İçindekiler</span><span class="sxs-lookup"><span data-stu-id="a8294-184">Contents</span></span>|<span data-ttu-id="a8294-185">Şema</span><span class="sxs-lookup"><span data-stu-id="a8294-185">Schema</span></span>|
|--------------|------------|
|`simpleContent`|<span data-ttu-id="a8294-186">Uzantılar yasaktır.</span><span class="sxs-lookup"><span data-stu-id="a8294-186">Extensions are forbidden.</span></span><br /><br /> <span data-ttu-id="a8294-187">Kısıtlamaya yalnızca `anySimpleType`izin verilir.</span><span class="sxs-lookup"><span data-stu-id="a8294-187">Restriction is allowed only from `anySimpleType`.</span></span>|
|`complexContent`|<span data-ttu-id="a8294-188">Desteklenen.</span><span class="sxs-lookup"><span data-stu-id="a8294-188">Supported.</span></span> <span data-ttu-id="a8294-189">Bkz. "devralma".</span><span class="sxs-lookup"><span data-stu-id="a8294-189">See "Inheritance".</span></span>|
|`group`|<span data-ttu-id="a8294-190">Inı.</span><span class="sxs-lookup"><span data-stu-id="a8294-190">Forbidden.</span></span>|
|`all`|<span data-ttu-id="a8294-191">Inı.</span><span class="sxs-lookup"><span data-stu-id="a8294-191">Forbidden.</span></span>|
|`choice`|<span data-ttu-id="a8294-192">Yasak</span><span class="sxs-lookup"><span data-stu-id="a8294-192">Forbidden</span></span>|
|`sequence`|<span data-ttu-id="a8294-193">Desteklenir, bir veri sözleşmesinin veri üyeleriyle eşlenir.</span><span class="sxs-lookup"><span data-stu-id="a8294-193">Supported, maps to data members of a data contract.</span></span>|
|`attribute`|<span data-ttu-id="a8294-194">Use = "yasaklanmış" (bir özel durum) olsa bile yasak.</span><span class="sxs-lookup"><span data-stu-id="a8294-194">Forbidden, even if use="prohibited" (with one exception).</span></span> <span data-ttu-id="a8294-195">Yalnızca standart serileştirme şeması ad alanındaki isteğe bağlı öznitelikler desteklenir.</span><span class="sxs-lookup"><span data-stu-id="a8294-195">Only optional attributes from the Standard Serialization Schema namespace are supported.</span></span> <span data-ttu-id="a8294-196">Veri sözleşmesi programlama modelindeki veri üyeleriyle eşlemeirler.</span><span class="sxs-lookup"><span data-stu-id="a8294-196">They do not map to data members in the data contract programming model.</span></span> <span data-ttu-id="a8294-197">Şu anda yalnızca bir özniteliğin anlamı vardır ve ISerializable bölümünde ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="a8294-197">Currently, only one such attribute has meaning and is discussed in the ISerializable section.</span></span> <span data-ttu-id="a8294-198">Diğerlerinin hepsi yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="a8294-198">All others are ignored.</span></span>|
|`attributeGroup`|<span data-ttu-id="a8294-199">Inı.</span><span class="sxs-lookup"><span data-stu-id="a8294-199">Forbidden.</span></span> <span data-ttu-id="a8294-200">WCF v1 sürümünde, `DataContractSerializer` `xs:complexType`içindeki `attributeGroup` varlığını yoksayar.</span><span class="sxs-lookup"><span data-stu-id="a8294-200">In the WCF v1 release, `DataContractSerializer` ignores the presence of `attributeGroup` inside `xs:complexType`.</span></span>|
|`anyAttribute`|<span data-ttu-id="a8294-201">Inı.</span><span class="sxs-lookup"><span data-stu-id="a8294-201">Forbidden.</span></span>|
|<span data-ttu-id="a8294-202">olmamalıdır</span><span class="sxs-lookup"><span data-stu-id="a8294-202">(empty)</span></span>|<span data-ttu-id="a8294-203">Veri üyesi olmayan bir veri sözleşmesine eşlenir.</span><span class="sxs-lookup"><span data-stu-id="a8294-203">Maps to a data contract with no data members.</span></span>|

### <a name="xssequence-in-a-complex-type-attributes"></a><span data-ttu-id="a8294-204">\<xs: dizi > karmaşık türde: öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a8294-204">\<xs:sequence> in a complex type: attributes</span></span>

|<span data-ttu-id="a8294-205">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a8294-205">Attribute</span></span>|<span data-ttu-id="a8294-206">Şema</span><span class="sxs-lookup"><span data-stu-id="a8294-206">Schema</span></span>|
|---------------|------------|
|`id`|<span data-ttu-id="a8294-207">LIP.</span><span class="sxs-lookup"><span data-stu-id="a8294-207">Ignored.</span></span>|
|`maxOccurs`|<span data-ttu-id="a8294-208">1 (varsayılan) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a8294-208">Must be 1 (default).</span></span>|
|`minOccurs`|<span data-ttu-id="a8294-209">1 (varsayılan) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a8294-209">Must be 1 (default).</span></span>|

### <a name="xssequence-in-a-complex-type-contents"></a><span data-ttu-id="a8294-210">\<xs: dizi > karmaşık türde: içerikler</span><span class="sxs-lookup"><span data-stu-id="a8294-210">\<xs:sequence> in a complex type: contents</span></span>

|<span data-ttu-id="a8294-211">İçindekiler</span><span class="sxs-lookup"><span data-stu-id="a8294-211">Contents</span></span>|<span data-ttu-id="a8294-212">Şema</span><span class="sxs-lookup"><span data-stu-id="a8294-212">Schema</span></span>|
|--------------|------------|
|`element`|<span data-ttu-id="a8294-213">Her örnek bir veri üyesine eşlenir.</span><span class="sxs-lookup"><span data-stu-id="a8294-213">Each instance maps to a data member.</span></span>|
|`group`|<span data-ttu-id="a8294-214">Inı.</span><span class="sxs-lookup"><span data-stu-id="a8294-214">Forbidden.</span></span>|
|`choice`|<span data-ttu-id="a8294-215">Inı.</span><span class="sxs-lookup"><span data-stu-id="a8294-215">Forbidden.</span></span>|
|`sequence`|<span data-ttu-id="a8294-216">Inı.</span><span class="sxs-lookup"><span data-stu-id="a8294-216">Forbidden.</span></span>|
|`any`|<span data-ttu-id="a8294-217">Inı.</span><span class="sxs-lookup"><span data-stu-id="a8294-217">Forbidden.</span></span>|
|<span data-ttu-id="a8294-218">olmamalıdır</span><span class="sxs-lookup"><span data-stu-id="a8294-218">(empty)</span></span>|<span data-ttu-id="a8294-219">Veri üyesi olmayan bir veri sözleşmesine eşlenir.</span><span class="sxs-lookup"><span data-stu-id="a8294-219">Maps to a data contract with no data members.</span></span>|

## <a name="elements--xselement"></a><span data-ttu-id="a8294-220">Öğeler – \<xs: element ></span><span class="sxs-lookup"><span data-stu-id="a8294-220">Elements – \<xs:element></span></span>

### <a name="general-information"></a><span data-ttu-id="a8294-221">Genel Bilgiler</span><span class="sxs-lookup"><span data-stu-id="a8294-221">General Information</span></span>

<span data-ttu-id="a8294-222">`<xs:element>`, aşağıdaki bağlamlarda gerçekleşebilir:</span><span class="sxs-lookup"><span data-stu-id="a8294-222">`<xs:element>` can occur in the following contexts:</span></span>

- <span data-ttu-id="a8294-223">Düzenli (koleksiyon olmayan) bir veri sözleşmesinin veri üyesini açıklayan bir `<xs:sequence>`içinde meydana gelebilir.</span><span class="sxs-lookup"><span data-stu-id="a8294-223">It can occur within an `<xs:sequence>`, which describes a data member of a regular (non-collection) data contract.</span></span> <span data-ttu-id="a8294-224">Bu durumda `maxOccurs` özniteliği 1 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a8294-224">In this case, the `maxOccurs` attribute must be 1.</span></span> <span data-ttu-id="a8294-225">(0 değerine izin verilmez).</span><span class="sxs-lookup"><span data-stu-id="a8294-225">(A value of 0 is not allowed).</span></span>

- <span data-ttu-id="a8294-226">Bu, bir koleksiyon veri sözleşmesinin veri üyesini açıklayan bir `<xs:sequence>`içinde meydana gelebilir.</span><span class="sxs-lookup"><span data-stu-id="a8294-226">It can occur within an `<xs:sequence>`, which describes a data member of a collection data contract.</span></span> <span data-ttu-id="a8294-227">Bu durumda `maxOccurs` özniteliği 1 ' den büyük veya "sınırsız" olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a8294-227">In this case, the `maxOccurs` attribute must be greater than 1 or "unbounded".</span></span>

- <span data-ttu-id="a8294-228">Bir `<xs:schema>` içinde genel bir öğe bildirimi (ŞLı) olarak meydana gelebilir.</span><span class="sxs-lookup"><span data-stu-id="a8294-228">It can occur within an `<xs:schema>` as a Global Element Declaration (GED).</span></span>

### <a name="xselement-with-maxoccurs1-within-an-xssequence-data-members"></a><span data-ttu-id="a8294-229">\<xs: element >, bir \<xs: Sequence > (veri üyeleri) içinde maxOccurs = 1 ile</span><span class="sxs-lookup"><span data-stu-id="a8294-229">\<xs:element> with maxOccurs=1 within an \<xs:sequence> (Data Members)</span></span>

|<span data-ttu-id="a8294-230">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a8294-230">Attribute</span></span>|<span data-ttu-id="a8294-231">Şema</span><span class="sxs-lookup"><span data-stu-id="a8294-231">Schema</span></span>|
|---------------|------------|
|`ref`|<span data-ttu-id="a8294-232">Inı.</span><span class="sxs-lookup"><span data-stu-id="a8294-232">Forbidden.</span></span>|
|`name`|<span data-ttu-id="a8294-233">Desteklenir, veri üyesi adı ile eşlenir.</span><span class="sxs-lookup"><span data-stu-id="a8294-233">Supported, maps to the data member name.</span></span>|
|`type`|<span data-ttu-id="a8294-234">Desteklenir, veri üyesi türüyle eşlenir.</span><span class="sxs-lookup"><span data-stu-id="a8294-234">Supported, maps to the data member type.</span></span> <span data-ttu-id="a8294-235">Daha fazla bilgi için bkz. tür/temel öğe eşleme.</span><span class="sxs-lookup"><span data-stu-id="a8294-235">For more information, see Type/primitive mapping.</span></span> <span data-ttu-id="a8294-236">Belirtilmemişse (ve öğesi anonim bir tür içermiyorsa), `xs:anyType` varsayılır.</span><span class="sxs-lookup"><span data-stu-id="a8294-236">If not specified (and the element does not contain an anonymous type), `xs:anyType` is assumed.</span></span>|
|`block`|<span data-ttu-id="a8294-237">LIP.</span><span class="sxs-lookup"><span data-stu-id="a8294-237">Ignored.</span></span>|
|`default`|<span data-ttu-id="a8294-238">Inı.</span><span class="sxs-lookup"><span data-stu-id="a8294-238">Forbidden.</span></span>|
|`fixed`|<span data-ttu-id="a8294-239">Inı.</span><span class="sxs-lookup"><span data-stu-id="a8294-239">Forbidden.</span></span>|
|`form`|<span data-ttu-id="a8294-240">Nitelenmiş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a8294-240">Must be qualified.</span></span> <span data-ttu-id="a8294-241">Bu öznitelik, `xs:schema``elementFormDefault` aracılığıyla ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="a8294-241">This attribute can be set through `elementFormDefault` on `xs:schema`.</span></span>|
|`id`|<span data-ttu-id="a8294-242">LIP.</span><span class="sxs-lookup"><span data-stu-id="a8294-242">Ignored.</span></span>|
|`maxOccurs`|<span data-ttu-id="a8294-243">1\.</span><span class="sxs-lookup"><span data-stu-id="a8294-243">1</span></span>|
|`minOccurs`|<span data-ttu-id="a8294-244">Bir veri üyesinin <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> özelliğine eşlenir (`minOccurs` 1 olduğunda`IsRequired` true 'dur).</span><span class="sxs-lookup"><span data-stu-id="a8294-244">Maps to the <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> property of a data member (`IsRequired` is true when `minOccurs` is 1).</span></span>|
|`nillable`|<span data-ttu-id="a8294-245">Tür eşlemesini etkiler.</span><span class="sxs-lookup"><span data-stu-id="a8294-245">Affects type mapping.</span></span> <span data-ttu-id="a8294-246">Bkz. tür/temel eşleme.</span><span class="sxs-lookup"><span data-stu-id="a8294-246">See Type/primitive mapping.</span></span>|

### <a name="xselement-with-maxoccurs1-within-an-xssequence-collections"></a><span data-ttu-id="a8294-247">\<xs: element >, \<xs: Sequence > (koleksiyonlar) içinde maxOccurs > 1</span><span class="sxs-lookup"><span data-stu-id="a8294-247">\<xs:element> with maxOccurs>1 within an \<xs:sequence> (Collections)</span></span>

- <span data-ttu-id="a8294-248">Bir <xref:System.Runtime.Serialization.CollectionDataContractAttribute>eşler.</span><span class="sxs-lookup"><span data-stu-id="a8294-248">Maps to a <xref:System.Runtime.Serialization.CollectionDataContractAttribute>.</span></span>

- <span data-ttu-id="a8294-249">Koleksiyon türlerinde, xs: Sequence içinde yalnızca bir xs: element öğesine izin verilir.</span><span class="sxs-lookup"><span data-stu-id="a8294-249">In collection types, only one xs:element is allowed within an xs:sequence.</span></span>

 <span data-ttu-id="a8294-250">Koleksiyonlar aşağıdaki türlerde olabilir:</span><span class="sxs-lookup"><span data-stu-id="a8294-250">Collections can be of the following types:</span></span>

- <span data-ttu-id="a8294-251">Normal Koleksiyonlar (örneğin, diziler).</span><span class="sxs-lookup"><span data-stu-id="a8294-251">Regular collections (for example, arrays).</span></span>

- <span data-ttu-id="a8294-252">Sözlük koleksiyonları (bir değeri başka bir değerle eşleme; Örneğin, bir <xref:System.Collections.Hashtable>).</span><span class="sxs-lookup"><span data-stu-id="a8294-252">Dictionary collections (mapping one value to another; for example, a <xref:System.Collections.Hashtable>).</span></span>

- <span data-ttu-id="a8294-253">Bir sözlük ile anahtar/değer çifti türündeki bir dizi arasındaki tek fark, oluşturulan programlama modelidir.</span><span class="sxs-lookup"><span data-stu-id="a8294-253">The only difference between a dictionary and an array of a key/value pair type is in the generated programming model.</span></span> <span data-ttu-id="a8294-254">Belirli bir türün sözlük koleksiyonu olduğunu göstermek için kullanılabilecek bir şema ek açıklaması mekanizması vardır.</span><span class="sxs-lookup"><span data-stu-id="a8294-254">There is a schema annotation mechanism that can be used to indicate that a given type is a dictionary collection.</span></span>

<span data-ttu-id="a8294-255">`ref`, `block`, `default`, `fixed`, `form`ve `id` özniteliklerinin kuralları koleksiyon olmayan durum ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="a8294-255">The rules for the `ref`, `block`, `default`, `fixed`, `form`, and `id` attributes are the same as for the non-collection case.</span></span> <span data-ttu-id="a8294-256">Diğer öznitelikler aşağıdaki tabloda yer alır.</span><span class="sxs-lookup"><span data-stu-id="a8294-256">Other attributes include those in the following table.</span></span>

|<span data-ttu-id="a8294-257">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a8294-257">Attribute</span></span>|<span data-ttu-id="a8294-258">Şema</span><span class="sxs-lookup"><span data-stu-id="a8294-258">Schema</span></span>|
|---------------|------------|
|`name`|<span data-ttu-id="a8294-259">Desteklenir, `CollectionDataContractAttribute` özniteliğinde <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> özelliği ile eşlenir.</span><span class="sxs-lookup"><span data-stu-id="a8294-259">Supported, maps to the <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> property in the `CollectionDataContractAttribute` attribute.</span></span>|
|`type`|<span data-ttu-id="a8294-260">Desteklenir, koleksiyonda depolanan türle eşlenir.</span><span class="sxs-lookup"><span data-stu-id="a8294-260">Supported, maps to the type stored in the collection.</span></span>|
|`maxOccurs`|<span data-ttu-id="a8294-261">1 ' den büyük veya "sınırsız".</span><span class="sxs-lookup"><span data-stu-id="a8294-261">Greater than 1 or "unbounded".</span></span> <span data-ttu-id="a8294-262">DC şeması "sınırsız" kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a8294-262">The DC schema should use "unbounded".</span></span>|
|`minOccurs`|<span data-ttu-id="a8294-263">LIP.</span><span class="sxs-lookup"><span data-stu-id="a8294-263">Ignored.</span></span>|
|`nillable`|<span data-ttu-id="a8294-264">Tür eşlemesini etkiler.</span><span class="sxs-lookup"><span data-stu-id="a8294-264">Affects type mapping.</span></span> <span data-ttu-id="a8294-265">Bu öznitelik, sözlük koleksiyonları için yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="a8294-265">This attribute is ignored for dictionary collections.</span></span>|

### <a name="xselement-within-an-xsschema-global-element-declaration"></a><span data-ttu-id="a8294-266">\<xs: element > bir \<xs: Schema > Genel öğe bildirimi</span><span class="sxs-lookup"><span data-stu-id="a8294-266">\<xs:element> within an \<xs:schema> Global Element Declaration</span></span>

- <span data-ttu-id="a8294-267">Şemadaki bir türle aynı ada ve ad alanına sahip olan veya kendisi içinde anonim bir tür tanımlayan genel öğe bildirimi (ŞLı), türle ilişkili olarak söylenir.</span><span class="sxs-lookup"><span data-stu-id="a8294-267">A Global Element Declaration (GED) that has the same name and namespace as a type in schema, or that defines an anonymous type inside itself, is said to be associated with the type.</span></span>

- <span data-ttu-id="a8294-268">Şema dışarı aktarma: ilişkili GEDs, hem basit hem de karmaşık oluşturulan her tür için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a8294-268">Schema export: associated GEDs are generated for every generated type, both simple and complex.</span></span>

- <span data-ttu-id="a8294-269">Seri durumdan çıkarma/serileştirme: ilişkili GEDs, tür için kök öğe olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a8294-269">Deserialization/serialization: associated GEDs are used as root elements for the type.</span></span>

- <span data-ttu-id="a8294-270">Şema içeri aktarma: ilişkili GEDs 'ler gerekli değildir ve aşağıdaki kurallara uyar (türleri tanımladıkça).</span><span class="sxs-lookup"><span data-stu-id="a8294-270">Schema import: associated GEDs are not required and are ignored if they follow the following rules (unless they define types).</span></span>

|<span data-ttu-id="a8294-271">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a8294-271">Attribute</span></span>|<span data-ttu-id="a8294-272">Şema</span><span class="sxs-lookup"><span data-stu-id="a8294-272">Schema</span></span>|
|---------------|------------|
|`abstract`|<span data-ttu-id="a8294-273">İlişkili GEDs 'ler için false olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a8294-273">Must be false for associated GEDs.</span></span>|
|`block`|<span data-ttu-id="a8294-274">İlişkili GEDs 'de yasak.</span><span class="sxs-lookup"><span data-stu-id="a8294-274">Forbidden in associated GEDs.</span></span>|
|`default`|<span data-ttu-id="a8294-275">İlişkili GEDs 'de yasak.</span><span class="sxs-lookup"><span data-stu-id="a8294-275">Forbidden in associated GEDs.</span></span>|
|`final`|<span data-ttu-id="a8294-276">İlişkili GEDs 'ler için false olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a8294-276">Must be false for associated GEDs.</span></span>|
|`fixed`|<span data-ttu-id="a8294-277">İlişkili GEDs 'de yasak.</span><span class="sxs-lookup"><span data-stu-id="a8294-277">Forbidden in associated GEDs.</span></span>|
|`id`|<span data-ttu-id="a8294-278">LIP.</span><span class="sxs-lookup"><span data-stu-id="a8294-278">Ignored.</span></span>|
|`name`|<span data-ttu-id="a8294-279">Desteklenen.</span><span class="sxs-lookup"><span data-stu-id="a8294-279">Supported.</span></span> <span data-ttu-id="a8294-280">İlişkili GEDs tanımına bakın.</span><span class="sxs-lookup"><span data-stu-id="a8294-280">See the definition of associated GEDs.</span></span>|
|`nillable`|<span data-ttu-id="a8294-281">İlişkili GEDs 'ler için doğru olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a8294-281">Must be true for associated GEDs.</span></span>|
|`substitutionGroup`|<span data-ttu-id="a8294-282">İlişkili GEDs 'de yasak.</span><span class="sxs-lookup"><span data-stu-id="a8294-282">Forbidden in associated GEDs.</span></span>|
|`type`|<span data-ttu-id="a8294-283">Desteklenir ve ilişkili GEDs için ilişkili tür ile eşleşmelidir (öğe anonim bir tür içermiyorsa).</span><span class="sxs-lookup"><span data-stu-id="a8294-283">Supported, and must match the associated type for associated GEDs (unless the element contains an anonymous type).</span></span>|

### <a name="xselement-contents"></a><span data-ttu-id="a8294-284">\<xs: element >: içerikler</span><span class="sxs-lookup"><span data-stu-id="a8294-284">\<xs:element>: contents</span></span>

|<span data-ttu-id="a8294-285">İçindekiler</span><span class="sxs-lookup"><span data-stu-id="a8294-285">Contents</span></span>|<span data-ttu-id="a8294-286">Şema</span><span class="sxs-lookup"><span data-stu-id="a8294-286">Schema</span></span>|
|--------------|------------|
|`simpleType`|<span data-ttu-id="a8294-287">Desteklenir. \*</span><span class="sxs-lookup"><span data-stu-id="a8294-287">Supported.\*</span></span>|
|`complexType`|<span data-ttu-id="a8294-288">Desteklenir. \*</span><span class="sxs-lookup"><span data-stu-id="a8294-288">Supported.\*</span></span>|
|`unique`|<span data-ttu-id="a8294-289">LIP.</span><span class="sxs-lookup"><span data-stu-id="a8294-289">Ignored.</span></span>|
|`key`|<span data-ttu-id="a8294-290">LIP.</span><span class="sxs-lookup"><span data-stu-id="a8294-290">Ignored.</span></span>|
|`keyref`|<span data-ttu-id="a8294-291">LIP.</span><span class="sxs-lookup"><span data-stu-id="a8294-291">Ignored.</span></span>|
|<span data-ttu-id="a8294-292">(boş)</span><span class="sxs-lookup"><span data-stu-id="a8294-292">(blank)</span></span>|<span data-ttu-id="a8294-293">Desteklenen.</span><span class="sxs-lookup"><span data-stu-id="a8294-293">Supported.</span></span>|

<span data-ttu-id="a8294-294">anonim türler için `simpleType` ve `complexType,` eşleme kullanılırken \* anonim olmayan türler için aynı olduğunda, anonim veri sözleşmeleri olmaması dışında, adlandırılmış bir veri sözleşmesinin oluşturulması ve bu nedenle, öğe adından elde edilen oluşturulmuş bir ada sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a8294-294">\* When using the `simpleType` and `complexType,` mapping for anonymous types is the same as for non-anonymous types, except that there is no anonymous data contracts, and so a named data contract is created, with a generated name derived from the element name.</span></span> <span data-ttu-id="a8294-295">Anonim türlerin kuralları aşağıdaki listede verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="a8294-295">The rules for anonymous types are in the following list:</span></span>

- <span data-ttu-id="a8294-296">WCF uygulama ayrıntısı: `xs:element` adı nokta içermiyorsa, anonim tür dış veri sözleşmesi türünün bir iç türüyle eşlenir.</span><span class="sxs-lookup"><span data-stu-id="a8294-296">WCF implementation detail: If the `xs:element` name does not contain periods, the anonymous type maps to an inner type of the outer data contract type.</span></span> <span data-ttu-id="a8294-297">Ad nokta içeriyorsa, sonuçta elde edilen veri anlaşması türü bağımsızdır (bir iç tür değildir).</span><span class="sxs-lookup"><span data-stu-id="a8294-297">If the name contains periods, the resulting data contract type is independent (not an inner type).</span></span>

- <span data-ttu-id="a8294-298">İç türün üretilen veri sözleşme adı, dış türün veri sözleşmesinin adı ve ardından bir nokta, öğenin adı ve "tür" dizesi gelir.</span><span class="sxs-lookup"><span data-stu-id="a8294-298">The generated data contract name of the inner type is the data contract name of the outer type followed by a period, the name of the element, and the string "Type".</span></span>

- <span data-ttu-id="a8294-299">Böyle bir ada sahip bir veri sözleşmesi zaten varsa, benzersiz bir ad oluşturuluncaya kadar "1", "2", "3" vb. eklenerek ad benzersiz hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="a8294-299">If a data contract with such a name already exists, the name is made unique by appending "1", "2", "3", and so on until a unique name is created.</span></span>

## <a name="simple-types---xssimpletype"></a><span data-ttu-id="a8294-300">Basit türler-\<xs: simpleType ></span><span class="sxs-lookup"><span data-stu-id="a8294-300">Simple Types - \<xs:simpleType></span></span>

### <a name="xssimpletype-attributes"></a><span data-ttu-id="a8294-301">\<xs: simpleType >: öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a8294-301">\<xs:simpleType>: attributes</span></span>

|<span data-ttu-id="a8294-302">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a8294-302">Attribute</span></span>|<span data-ttu-id="a8294-303">Şema</span><span class="sxs-lookup"><span data-stu-id="a8294-303">Schema</span></span>|
|---------------|------------|
|`final`|<span data-ttu-id="a8294-304">LIP.</span><span class="sxs-lookup"><span data-stu-id="a8294-304">Ignored.</span></span>|
|`id`|<span data-ttu-id="a8294-305">LIP.</span><span class="sxs-lookup"><span data-stu-id="a8294-305">Ignored.</span></span>|
|`name`|<span data-ttu-id="a8294-306">Desteklenir, veri sözleşmesi adıyla eşlenir.</span><span class="sxs-lookup"><span data-stu-id="a8294-306">Supported, maps to the data contract name.</span></span>|

### <a name="xssimpletype-contents"></a><span data-ttu-id="a8294-307">\<xs: simpleType >: içerik</span><span class="sxs-lookup"><span data-stu-id="a8294-307">\<xs:simpleType>: contents</span></span>

|<span data-ttu-id="a8294-308">İçindekiler</span><span class="sxs-lookup"><span data-stu-id="a8294-308">Contents</span></span>|<span data-ttu-id="a8294-309">Şema</span><span class="sxs-lookup"><span data-stu-id="a8294-309">Schema</span></span>|
|--------------|------------|
|`restriction`|<span data-ttu-id="a8294-310">Desteklenen.</span><span class="sxs-lookup"><span data-stu-id="a8294-310">Supported.</span></span> <span data-ttu-id="a8294-311">Sabit listesi veri sözleşmeleri ile eşlenir.</span><span class="sxs-lookup"><span data-stu-id="a8294-311">Maps to enumeration data contracts.</span></span> <span data-ttu-id="a8294-312">Bu öznitelik, numaralandırma düzeniyle eşleşmezse yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="a8294-312">This attribute is ignored if it does not match the enumeration pattern.</span></span> <span data-ttu-id="a8294-313">`xs:simpleType` kısıtlamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="a8294-313">See the `xs:simpleType` restrictions section.</span></span>|
|`list`|<span data-ttu-id="a8294-314">Desteklenen.</span><span class="sxs-lookup"><span data-stu-id="a8294-314">Supported.</span></span> <span data-ttu-id="a8294-315">Bayrak sıralama veri sözleşmeleri ile eşlenir.</span><span class="sxs-lookup"><span data-stu-id="a8294-315">Maps to flag enumeration data contracts.</span></span> <span data-ttu-id="a8294-316">`xs:simpleType` listeleri bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="a8294-316">See the `xs:simpleType` lists section.</span></span>|
|`union`|<span data-ttu-id="a8294-317">Inı.</span><span class="sxs-lookup"><span data-stu-id="a8294-317">Forbidden.</span></span>|

### <a name="xsrestriction"></a><span data-ttu-id="a8294-318">\<xs: kısıtlama ></span><span class="sxs-lookup"><span data-stu-id="a8294-318">\<xs:restriction></span></span>

- <span data-ttu-id="a8294-319">Karmaşık tür kısıtlamaları yalnızca Base = "`xs:anyType`" için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="a8294-319">Complex type restrictions are supported only for base="`xs:anyType`".</span></span>

- <span data-ttu-id="a8294-320">`xs:enumeration` dışındaki kısıtlama modelleri olmayan `xs:string` basit tür kısıtlamaları, sabit listesi veri sözleşmeleri ile eşleştirilir.</span><span class="sxs-lookup"><span data-stu-id="a8294-320">Simple type restrictions of `xs:string` that do not have any restriction facets other than `xs:enumeration` are mapped to enumeration data contracts.</span></span>

- <span data-ttu-id="a8294-321">Diğer tüm basit tür kısıtlamaları, kısıttıkları türlere eşlenir.</span><span class="sxs-lookup"><span data-stu-id="a8294-321">All other simple type restrictions are mapped to the types they restrict.</span></span> <span data-ttu-id="a8294-322">Örneğin, bir `xs:int` kısıtlaması, tıpkı `xs:int` olduğu gibi bir tamsayı ile eşlenir.</span><span class="sxs-lookup"><span data-stu-id="a8294-322">For example, a restriction of `xs:int` maps to an integer, just as `xs:int` itself does.</span></span> <span data-ttu-id="a8294-323">İlkel tür eşlemesi hakkında daha fazla bilgi için bkz. tür/temel eşleme.</span><span class="sxs-lookup"><span data-stu-id="a8294-323">For more information about primitive type mapping, see Type/primitive mapping.</span></span>

### <a name="xsrestriction-attributes"></a><span data-ttu-id="a8294-324">\<xs: restriction >: öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a8294-324">\<xs:restriction>: attributes</span></span>

|<span data-ttu-id="a8294-325">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a8294-325">Attribute</span></span>|<span data-ttu-id="a8294-326">Şema</span><span class="sxs-lookup"><span data-stu-id="a8294-326">Schema</span></span>|
|---------------|------------|
|`base`|<span data-ttu-id="a8294-327">Desteklenen bir basit tür veya `xs:anyType`olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a8294-327">Must be a supported simple type or `xs:anyType`.</span></span>|
|`id`|<span data-ttu-id="a8294-328">LIP.</span><span class="sxs-lookup"><span data-stu-id="a8294-328">Ignored.</span></span>|

### <a name="xsrestriction-for-all-other-cases-contents"></a><span data-ttu-id="a8294-329">\<xs: kısıtlama > diğer tüm durumlarda: içerikler</span><span class="sxs-lookup"><span data-stu-id="a8294-329">\<xs:restriction> for all other cases: contents</span></span>

|<span data-ttu-id="a8294-330">İçindekiler</span><span class="sxs-lookup"><span data-stu-id="a8294-330">Contents</span></span>|<span data-ttu-id="a8294-331">Şema</span><span class="sxs-lookup"><span data-stu-id="a8294-331">Schema</span></span>|
|--------------|------------|
|`simpleType`|<span data-ttu-id="a8294-332">Varsa, desteklenen bir temel türden türetilmiş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a8294-332">If present, must be derived from a supported primitive type.</span></span>|
|`minExclusive`|<span data-ttu-id="a8294-333">LIP.</span><span class="sxs-lookup"><span data-stu-id="a8294-333">Ignored.</span></span>|
|`minInclusive`|<span data-ttu-id="a8294-334">LIP.</span><span class="sxs-lookup"><span data-stu-id="a8294-334">Ignored.</span></span>|
|`maxExclusive`|<span data-ttu-id="a8294-335">LIP.</span><span class="sxs-lookup"><span data-stu-id="a8294-335">Ignored.</span></span>|
|`maxInclusive`|<span data-ttu-id="a8294-336">LIP.</span><span class="sxs-lookup"><span data-stu-id="a8294-336">Ignored.</span></span>|
|`totalDigits`|<span data-ttu-id="a8294-337">LIP.</span><span class="sxs-lookup"><span data-stu-id="a8294-337">Ignored.</span></span>|
|`fractionDigits`|<span data-ttu-id="a8294-338">LIP.</span><span class="sxs-lookup"><span data-stu-id="a8294-338">Ignored.</span></span>|
|`length`|<span data-ttu-id="a8294-339">LIP.</span><span class="sxs-lookup"><span data-stu-id="a8294-339">Ignored.</span></span>|
|`minLength`|<span data-ttu-id="a8294-340">LIP.</span><span class="sxs-lookup"><span data-stu-id="a8294-340">Ignored.</span></span>|
|`maxLength`|<span data-ttu-id="a8294-341">LIP.</span><span class="sxs-lookup"><span data-stu-id="a8294-341">Ignored.</span></span>|
|`enumeration`|<span data-ttu-id="a8294-342">LIP.</span><span class="sxs-lookup"><span data-stu-id="a8294-342">Ignored.</span></span>|
|`whiteSpace`|<span data-ttu-id="a8294-343">LIP.</span><span class="sxs-lookup"><span data-stu-id="a8294-343">Ignored.</span></span>|
|`pattern`|<span data-ttu-id="a8294-344">LIP.</span><span class="sxs-lookup"><span data-stu-id="a8294-344">Ignored.</span></span>|
|<span data-ttu-id="a8294-345">(boş)</span><span class="sxs-lookup"><span data-stu-id="a8294-345">(blank)</span></span>|<span data-ttu-id="a8294-346">Desteklenen.</span><span class="sxs-lookup"><span data-stu-id="a8294-346">Supported.</span></span>|

## <a name="enumeration"></a><span data-ttu-id="a8294-347">Numaralandırma</span><span class="sxs-lookup"><span data-stu-id="a8294-347">Enumeration</span></span>

### <a name="xsrestriction-for-enumerations-attributes"></a><span data-ttu-id="a8294-348">\<xs:, numaralandırmalar için kısıtlama >: öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a8294-348">\<xs:restriction> for enumerations: attributes</span></span>

|<span data-ttu-id="a8294-349">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a8294-349">Attribute</span></span>|<span data-ttu-id="a8294-350">Şema</span><span class="sxs-lookup"><span data-stu-id="a8294-350">Schema</span></span>|
|---------------|------------|
|`base`|<span data-ttu-id="a8294-351">Varsa, `xs:string`olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a8294-351">If present, must be `xs:string`.</span></span>|
|`id`|<span data-ttu-id="a8294-352">LIP.</span><span class="sxs-lookup"><span data-stu-id="a8294-352">Ignored.</span></span>|

### <a name="xsrestriction-for-enumerations-contents"></a><span data-ttu-id="a8294-353">\<xs:, numaralandırmalar için kısıtlama >: içerikler</span><span class="sxs-lookup"><span data-stu-id="a8294-353">\<xs:restriction> for enumerations: contents</span></span>

|<span data-ttu-id="a8294-354">İçindekiler</span><span class="sxs-lookup"><span data-stu-id="a8294-354">Contents</span></span>|<span data-ttu-id="a8294-355">Şema</span><span class="sxs-lookup"><span data-stu-id="a8294-355">Schema</span></span>|
|--------------|------------|
|`simpleType`|<span data-ttu-id="a8294-356">Varsa, veri anlaşması (Bu bölüm) tarafından desteklenen bir numaralandırma kısıtlaması olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a8294-356">If present, must be an enumeration restriction supported by the data contract (this section).</span></span>|
|`minExclusive`|<span data-ttu-id="a8294-357">LIP.</span><span class="sxs-lookup"><span data-stu-id="a8294-357">Ignored.</span></span>|
|`minInclusive`|<span data-ttu-id="a8294-358">LIP.</span><span class="sxs-lookup"><span data-stu-id="a8294-358">Ignored.</span></span>|
|`maxExclusive`|<span data-ttu-id="a8294-359">LIP.</span><span class="sxs-lookup"><span data-stu-id="a8294-359">Ignored.</span></span>|
|`maxInclusive`|<span data-ttu-id="a8294-360">LIP.</span><span class="sxs-lookup"><span data-stu-id="a8294-360">Ignored.</span></span>|
|`totalDigits`|<span data-ttu-id="a8294-361">LIP.</span><span class="sxs-lookup"><span data-stu-id="a8294-361">Ignored.</span></span>|
|`fractionDigits`|<span data-ttu-id="a8294-362">LIP.</span><span class="sxs-lookup"><span data-stu-id="a8294-362">Ignored.</span></span>|
|`length`|<span data-ttu-id="a8294-363">Inı.</span><span class="sxs-lookup"><span data-stu-id="a8294-363">Forbidden.</span></span>|
|`minLength`|<span data-ttu-id="a8294-364">Inı.</span><span class="sxs-lookup"><span data-stu-id="a8294-364">Forbidden.</span></span>|
|`maxLength`|<span data-ttu-id="a8294-365">Inı.</span><span class="sxs-lookup"><span data-stu-id="a8294-365">Forbidden.</span></span>|
|`enumeration`|<span data-ttu-id="a8294-366">Desteklenen.</span><span class="sxs-lookup"><span data-stu-id="a8294-366">Supported.</span></span> <span data-ttu-id="a8294-367">"Kimlik" numaralandırması yok sayılır ve "değer" sabit listesi veri sözleşmesindeki değer adıyla eşlenir.</span><span class="sxs-lookup"><span data-stu-id="a8294-367">Enumeration "id" is ignored, and "value" maps to the value name in the enumeration data contract.</span></span>|
|`whiteSpace`|<span data-ttu-id="a8294-368">Inı.</span><span class="sxs-lookup"><span data-stu-id="a8294-368">Forbidden.</span></span>|
|`pattern`|<span data-ttu-id="a8294-369">Inı.</span><span class="sxs-lookup"><span data-stu-id="a8294-369">Forbidden.</span></span>|
|<span data-ttu-id="a8294-370">olmamalıdır</span><span class="sxs-lookup"><span data-stu-id="a8294-370">(empty)</span></span>|<span data-ttu-id="a8294-371">Desteklenir, boş sabit listesi türüne eşlenir.</span><span class="sxs-lookup"><span data-stu-id="a8294-371">Supported, maps to empty enumeration type.</span></span>|

 <span data-ttu-id="a8294-372">Aşağıdaki kod bir C# numaralandırma sınıfını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a8294-372">The following code shows a C# enumeration class.</span></span>

```csharp
public enum MyEnum
{
  first = 3,
  second = 4,
  third =5
}
```

<span data-ttu-id="a8294-373">Bu sınıf, `DataContractSerializer`tarafından aşağıdaki şemaya eşlenir.</span><span class="sxs-lookup"><span data-stu-id="a8294-373">This class maps to the following schema by the `DataContractSerializer`.</span></span> <span data-ttu-id="a8294-374">Numaralandırma değerleri 1 ' den başlar `xs:annotation` bloklar oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="a8294-374">If enumeration values start from 1, `xs:annotation` blocks are not generated.</span></span>

```xml
<xs:simpleType name="MyEnum">
  <xs:restriction base="xs:string">
    <xs:enumeration value="first">
      <xs:annotation>
        <xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">
          3
          </EnumerationValue>
        </xs:appinfo>
      </xs:annotation>
    </xs:enumeration>
    <xs:enumeration value="second">
      <xs:annotation>
        <xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">
          4
          </EnumerationValue>
        </xs:appinfo>
      </xs:annotation>
    </xs:enumeration>
  </xs:restriction>
</xs:simpleType>
```

### <a name="xslist"></a><span data-ttu-id="a8294-375">\<xs: List ></span><span class="sxs-lookup"><span data-stu-id="a8294-375">\<xs:list></span></span>

<span data-ttu-id="a8294-376">`DataContractSerializer`, `System.FlagsAttribute` ile işaretlenen numaralandırma türlerini `xs:string`türetilmiş `xs:list` olarak eşleştirir.</span><span class="sxs-lookup"><span data-stu-id="a8294-376">`DataContractSerializer` maps enumeration types marked with `System.FlagsAttribute` to `xs:list` derived from `xs:string`.</span></span> <span data-ttu-id="a8294-377">Başka `xs:list` çeşitlemeleri desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="a8294-377">No other `xs:list` variations are supported.</span></span>

### <a name="xslist-attributes"></a><span data-ttu-id="a8294-378">\<xs: List >: öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a8294-378">\<xs:list>: attributes</span></span>

|<span data-ttu-id="a8294-379">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a8294-379">Attribute</span></span>|<span data-ttu-id="a8294-380">Şema</span><span class="sxs-lookup"><span data-stu-id="a8294-380">Schema</span></span>|
|---------------|------------|
|`itemType`|<span data-ttu-id="a8294-381">Inı.</span><span class="sxs-lookup"><span data-stu-id="a8294-381">Forbidden.</span></span>|
|`id`|<span data-ttu-id="a8294-382">LIP.</span><span class="sxs-lookup"><span data-stu-id="a8294-382">Ignored.</span></span>|

### <a name="xslist-contents"></a><span data-ttu-id="a8294-383">\<xs: List >: Contents</span><span class="sxs-lookup"><span data-stu-id="a8294-383">\<xs:list>: contents</span></span>

|<span data-ttu-id="a8294-384">İçindekiler</span><span class="sxs-lookup"><span data-stu-id="a8294-384">Contents</span></span>|<span data-ttu-id="a8294-385">Şema</span><span class="sxs-lookup"><span data-stu-id="a8294-385">Schema</span></span>|
|--------------|------------|
|`simpleType`|<span data-ttu-id="a8294-386">`xs:enumeration` modeli kullanılarak `xs:string` kısıtlaması olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a8294-386">Must be restriction from `xs:string` using `xs:enumeration` facet.</span></span>|

<span data-ttu-id="a8294-387">Numaralandırma değeri 2 ilerlemenin gücünden (bayraklar için varsayılan) eşleşmezse, değer `xs:annotation/xs:appInfo/ser:EnumerationValue` öğesinde depolanır.</span><span class="sxs-lookup"><span data-stu-id="a8294-387">If enumeration value does not follow a power of 2 progression (default for Flags), the value is stored in the `xs:annotation/xs:appInfo/ser:EnumerationValue` element.</span></span>

<span data-ttu-id="a8294-388">Örneğin, aşağıdaki kod bir numaralandırma türünü bayraklar.</span><span class="sxs-lookup"><span data-stu-id="a8294-388">For example, the following code flags an enumeration type.</span></span>

```csharp
[Flags]
public enum AuthFlags
{
  AuthAnonymous = 1,
  AuthBasic = 2,
  AuthNTLM = 4,
  AuthMD5 = 16,
  AuthWindowsLiveID = 64,
}
```

<span data-ttu-id="a8294-389">Bu tür aşağıdaki şemaya eşlenir.</span><span class="sxs-lookup"><span data-stu-id="a8294-389">This type maps to the following schema.</span></span>

```xml
<xs:simpleType name="AuthFlags">
    <xs:list>
      <xs:simpleType>
        <xs:restriction base="xs:string">
          <xs:enumeration value="AuthAnonymous" />
          <xs:enumeration value="AuthBasic" />
          <xs:enumeration value="AuthNTLM" />
          <xs:enumeration value="AuthMD5">
            <xs:annotation>
              <xs:appinfo>
                <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">16</EnumerationValue>
              </xs:appinfo>
            </xs:annotation>
          </xs:enumeration>
          <xs:enumeration value="AuthWindowsLiveID">
            <xs:annotation>
              <xs:appinfo>
                <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">64</EnumerationValue>
              </xs:appinfo>
            </xs:annotation>
          </xs:enumeration>
        </xs:restriction>
      </xs:simpleType>
    </xs:list>
  </xs:simpleType>
```

## <a name="inheritance"></a><span data-ttu-id="a8294-390">Devralma</span><span class="sxs-lookup"><span data-stu-id="a8294-390">Inheritance</span></span>

### <a name="general-rules"></a><span data-ttu-id="a8294-391">Genel kurallar</span><span class="sxs-lookup"><span data-stu-id="a8294-391">General rules</span></span>

<span data-ttu-id="a8294-392">Bir veri sözleşmesi, başka bir veri sözleşmesinden devralınabilir.</span><span class="sxs-lookup"><span data-stu-id="a8294-392">A data contract can inherit from another data contract.</span></span> <span data-ttu-id="a8294-393">Bu tür veri sözleşmeleri bir temel ile eşlenir ve `<xs:extension>` XML şema yapısı kullanılarak uzantı türlerine göre türetilir.</span><span class="sxs-lookup"><span data-stu-id="a8294-393">Such data contracts map to a base and are derived by extension types using the `<xs:extension>` XML Schema construct.</span></span>

<span data-ttu-id="a8294-394">Veri sözleşmesi bir koleksiyon veri sözleşmesinden devralınabilir.</span><span class="sxs-lookup"><span data-stu-id="a8294-394">A data contract cannot inherit from a collection data contract.</span></span>

<span data-ttu-id="a8294-395">Örneğin, aşağıdaki kod bir veri sözleşmedir.</span><span class="sxs-lookup"><span data-stu-id="a8294-395">For example, the following code is a data contract.</span></span>

```csharp
[DataContract]
public class Person
{
  [DataMember]
  public string Name;
}
[DataContract]
public class Employee : Person
{
  [DataMember]
  public int ID;
}
```

<span data-ttu-id="a8294-396">Bu veri sözleşmesi, aşağıdaki XML Şeması tür bildirimiyle eşlenir.</span><span class="sxs-lookup"><span data-stu-id="a8294-396">This data contract maps to the following XML Schema type declaration.</span></span>

```xml
<xs:complexType name="Employee">
 <xs:complexContent mixed="false">
  <xs:extension base="tns:Person">
   <xs:sequence>
    <xs:element minOccurs="0" name="ID" type="xs:int"/>
   </xs:sequence>
  </xs:extension>
 </xs:complexContent>
</xs:complexType>
<xs:complexType name="Person">
 <xs:sequence>
  <xs:element minOccurs="0" name="Name"
    nillable="true" type="xs:string"/>
 </xs:sequence>
</xs:complexType>
```

### <a name="xscomplexcontent-attributes"></a><span data-ttu-id="a8294-397">\<xs: complexContent >: öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a8294-397">\<xs:complexContent>: attributes</span></span>

|<span data-ttu-id="a8294-398">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a8294-398">Attribute</span></span>|<span data-ttu-id="a8294-399">Şema</span><span class="sxs-lookup"><span data-stu-id="a8294-399">Schema</span></span>|
|---------------|------------|
|`id`|<span data-ttu-id="a8294-400">LIP.</span><span class="sxs-lookup"><span data-stu-id="a8294-400">Ignored.</span></span>|
|`mixed`|<span data-ttu-id="a8294-401">False olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a8294-401">Must be false.</span></span>|

### <a name="xscomplexcontent-contents"></a><span data-ttu-id="a8294-402">\<xs: complexContent >: içerikler</span><span class="sxs-lookup"><span data-stu-id="a8294-402">\<xs:complexContent>: contents</span></span>

|<span data-ttu-id="a8294-403">İçindekiler</span><span class="sxs-lookup"><span data-stu-id="a8294-403">Contents</span></span>|<span data-ttu-id="a8294-404">Şema</span><span class="sxs-lookup"><span data-stu-id="a8294-404">Schema</span></span>|
|--------------|------------|
|`restriction`|<span data-ttu-id="a8294-405">Yasak, Base = "`xs:anyType`" dışında.</span><span class="sxs-lookup"><span data-stu-id="a8294-405">Forbidden, except when base="`xs:anyType`".</span></span> <span data-ttu-id="a8294-406">İkincisi, `xs:restriction` içeriğini doğrudan `xs:complexContent`kapsayıcısının altına yerleştirmeye eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="a8294-406">The latter is equivalent to placing the content of the `xs:restriction` directly under the container of the `xs:complexContent`.</span></span>|
|`extension`|<span data-ttu-id="a8294-407">Desteklenen.</span><span class="sxs-lookup"><span data-stu-id="a8294-407">Supported.</span></span> <span data-ttu-id="a8294-408">Veri sözleşmesi devralmayla eşlenir.</span><span class="sxs-lookup"><span data-stu-id="a8294-408">Maps to data contract inheritance.</span></span>|

### <a name="xsextension-in-xscomplexcontent-attributes"></a><span data-ttu-id="a8294-409">\<xs:extension> in \<xs:complexContent>: attributes</span><span class="sxs-lookup"><span data-stu-id="a8294-409">\<xs:extension> in \<xs:complexContent>: attributes</span></span>

|<span data-ttu-id="a8294-410">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a8294-410">Attribute</span></span>|<span data-ttu-id="a8294-411">Şema</span><span class="sxs-lookup"><span data-stu-id="a8294-411">Schema</span></span>|
|---------------|------------|
|`id`|<span data-ttu-id="a8294-412">LIP.</span><span class="sxs-lookup"><span data-stu-id="a8294-412">Ignored.</span></span>|
|`base`|<span data-ttu-id="a8294-413">Desteklenen.</span><span class="sxs-lookup"><span data-stu-id="a8294-413">Supported.</span></span> <span data-ttu-id="a8294-414">Bu türün devraldığı temel veri sözleşmesi türüyle eşlenir.</span><span class="sxs-lookup"><span data-stu-id="a8294-414">Maps to the base data contract type that this type inherits from.</span></span>|

### <a name="xsextension-in-xscomplexcontent-contents"></a><span data-ttu-id="a8294-415">\<xs: \<xs: complexContent >: Contents içindeki uzantı ></span><span class="sxs-lookup"><span data-stu-id="a8294-415">\<xs:extension> in \<xs:complexContent>: contents</span></span>

<span data-ttu-id="a8294-416">Kurallar `<xs:complexType>` içeriğiyle aynı.</span><span class="sxs-lookup"><span data-stu-id="a8294-416">The rules are the same as for `<xs:complexType>` contents.</span></span>

<span data-ttu-id="a8294-417">Bir `<xs:sequence>` sağlanmışsa, üye öğeleri türetilmiş veri sözleşmesinde bulunan ek veri üyeleriyle eşlenir.</span><span class="sxs-lookup"><span data-stu-id="a8294-417">If an `<xs:sequence>` is provided, its member elements map to additional data members that are present in the derived data contract.</span></span>

<span data-ttu-id="a8294-418">Türetilmiş bir tür, temel türdeki bir öğeyle aynı ada sahip bir öğe içeriyorsa, yinelenen öğe bildirimi benzersiz olması için oluşturulan bir adla veri üyesine eşlenir.</span><span class="sxs-lookup"><span data-stu-id="a8294-418">If a derived type contains an element with the same name as an element in a base type, the duplicate element declaration maps to a data member with a name that is generated to be unique.</span></span> <span data-ttu-id="a8294-419">Benzersiz bir ad bulunana kadar ("member1", "member2" vb.) veri üyesi adına pozitif tamsayı numaraları eklenir.</span><span class="sxs-lookup"><span data-stu-id="a8294-419">Positive integer numbers are added to the data member name ("member1", "member2", and so on) until a unique name is found.</span></span> <span data-ttu-id="a8294-420">Buna karşılık</span><span class="sxs-lookup"><span data-stu-id="a8294-420">Conversely:</span></span>

- <span data-ttu-id="a8294-421">Türetilmiş bir veri sözleşmesinin, temel veri sözleşmesindeki bir veri üyesi ile aynı ada ve türe sahip bir veri üyesi varsa `DataContractSerializer` türetilen türde bu karşılık gelen öğeyi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a8294-421">If a derived data contract has a data member with the same name and type as a data member in a base data contract, `DataContractSerializer` generates this corresponding element in the derived type.</span></span>

- <span data-ttu-id="a8294-422">Türetilmiş bir veri sözleşmesinin, temel veri sözleşmesindeki bir veri üyesi ile aynı ada sahip bir veri üyesi, ancak farklı bir tür varsa, `DataContractSerializer` hem temel tür hem de türetilmiş tür bildirimlerinde `xs:anyType` türündeki bir öğeyi içeren bir şemayı içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="a8294-422">If a derived data contract has a data member with the same name as a data member in a base data contract but a different type, the `DataContractSerializer` imports a schema with an element of the type `xs:anyType` in both base type and derived type declarations.</span></span> <span data-ttu-id="a8294-423">Özgün tür adı `xs:annotations/xs:appInfo/ser:ActualType/@Name`saklanır.</span><span class="sxs-lookup"><span data-stu-id="a8294-423">The original type name is preserved in `xs:annotations/xs:appInfo/ser:ActualType/@Name`.</span></span>

<span data-ttu-id="a8294-424">Her iki çeşitleme de, ilgili veri üyelerinin sırasına bağlı olarak belirsiz bir içerik modeli olan bir şemaya neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="a8294-424">Both variations may lead to a schema with an ambiguous content model, which depends on the order of the respective data members.</span></span>

## <a name="typeprimitive-mapping"></a><span data-ttu-id="a8294-425">Tür/basit eşleme</span><span class="sxs-lookup"><span data-stu-id="a8294-425">Type/primitive mapping</span></span>

<span data-ttu-id="a8294-426">`DataContractSerializer`, XML şeması temel türleri için aşağıdaki eşlemeyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="a8294-426">The `DataContractSerializer` uses the following mapping for XML Schema primitive types.</span></span>

|<span data-ttu-id="a8294-427">XSD türü</span><span class="sxs-lookup"><span data-stu-id="a8294-427">XSD type</span></span>|<span data-ttu-id="a8294-428">.NET türü</span><span class="sxs-lookup"><span data-stu-id="a8294-428">.NET type</span></span>|
|--------------|---------------|
|`anyType`|<span data-ttu-id="a8294-429"><xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="a8294-429"><xref:System.Object>.</span></span>|
|`anySimpleType`|<span data-ttu-id="a8294-430"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="a8294-430"><xref:System.String>.</span></span>|
|`duration`|<span data-ttu-id="a8294-431"><xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="a8294-431"><xref:System.TimeSpan>.</span></span>|
|`dateTime`|<span data-ttu-id="a8294-432"><xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="a8294-432"><xref:System.DateTime>.</span></span>|
|`dateTimeOffset`|<span data-ttu-id="a8294-433"><xref:System.DateTime> ve konum için <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="a8294-433"><xref:System.DateTime> and <xref:System.TimeSpan> for the offset.</span></span> <span data-ttu-id="a8294-434">Aşağıdaki DateTimeOffset serileştirme ' i inceleyin.</span><span class="sxs-lookup"><span data-stu-id="a8294-434">See DateTimeOffset Serialization below.</span></span>|
|`time`|<span data-ttu-id="a8294-435"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="a8294-435"><xref:System.String>.</span></span>|
|`date`|<span data-ttu-id="a8294-436"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="a8294-436"><xref:System.String>.</span></span>|
|`gYearMonth`|<span data-ttu-id="a8294-437"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="a8294-437"><xref:System.String>.</span></span>|
|`gYear`|<span data-ttu-id="a8294-438"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="a8294-438"><xref:System.String>.</span></span>|
|`gMonthDay`|<span data-ttu-id="a8294-439"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="a8294-439"><xref:System.String>.</span></span>|
|`gDay`|<span data-ttu-id="a8294-440"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="a8294-440"><xref:System.String>.</span></span>|
|`gMonth`|<span data-ttu-id="a8294-441"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="a8294-441"><xref:System.String>.</span></span>|
|`boolean`|<xref:System.Boolean>|
|`base64Binary`|<span data-ttu-id="a8294-442"><xref:System.Byte> dizi.</span><span class="sxs-lookup"><span data-stu-id="a8294-442"><xref:System.Byte> array.</span></span>|
|`hexBinary`|<span data-ttu-id="a8294-443"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="a8294-443"><xref:System.String>.</span></span>|
|`float`|<span data-ttu-id="a8294-444"><xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="a8294-444"><xref:System.Single>.</span></span>|
|`double`|<span data-ttu-id="a8294-445"><xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="a8294-445"><xref:System.Double>.</span></span>|
|`anyURI`|<span data-ttu-id="a8294-446"><xref:System.Uri>.</span><span class="sxs-lookup"><span data-stu-id="a8294-446"><xref:System.Uri>.</span></span>|
|`QName`|<span data-ttu-id="a8294-447"><xref:System.Xml.XmlQualifiedName>.</span><span class="sxs-lookup"><span data-stu-id="a8294-447"><xref:System.Xml.XmlQualifiedName>.</span></span>|
|`string`|<span data-ttu-id="a8294-448"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="a8294-448"><xref:System.String>.</span></span>|
|`normalizedString`|<span data-ttu-id="a8294-449"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="a8294-449"><xref:System.String>.</span></span>|
|`token`|<span data-ttu-id="a8294-450"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="a8294-450"><xref:System.String>.</span></span>|
|`language`|<span data-ttu-id="a8294-451"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="a8294-451"><xref:System.String>.</span></span>|
|`Name`|<span data-ttu-id="a8294-452"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="a8294-452"><xref:System.String>.</span></span>|
|`NCName`|<span data-ttu-id="a8294-453"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="a8294-453"><xref:System.String>.</span></span>|
|`ID`|<span data-ttu-id="a8294-454"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="a8294-454"><xref:System.String>.</span></span>|
|`IDREF`|<span data-ttu-id="a8294-455"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="a8294-455"><xref:System.String>.</span></span>|
|`IDREFS`|<span data-ttu-id="a8294-456"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="a8294-456"><xref:System.String>.</span></span>|
|`ENTITY`|<span data-ttu-id="a8294-457"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="a8294-457"><xref:System.String>.</span></span>|
|`ENTITIES`|<span data-ttu-id="a8294-458"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="a8294-458"><xref:System.String>.</span></span>|
|`NMTOKEN`|<span data-ttu-id="a8294-459"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="a8294-459"><xref:System.String>.</span></span>|
|`NMTOKENS`|<span data-ttu-id="a8294-460"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="a8294-460"><xref:System.String>.</span></span>|
|`decimal`|<span data-ttu-id="a8294-461"><xref:System.Decimal>.</span><span class="sxs-lookup"><span data-stu-id="a8294-461"><xref:System.Decimal>.</span></span>|
|`integer`|<span data-ttu-id="a8294-462"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="a8294-462"><xref:System.Int64>.</span></span>|
|`nonPositiveInteger`|<span data-ttu-id="a8294-463"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="a8294-463"><xref:System.Int64>.</span></span>|
|`negativeInteger`|<span data-ttu-id="a8294-464"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="a8294-464"><xref:System.Int64>.</span></span>|
|`long`|<span data-ttu-id="a8294-465"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="a8294-465"><xref:System.Int64>.</span></span>|
|`int`|<span data-ttu-id="a8294-466"><xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="a8294-466"><xref:System.Int32>.</span></span>|
|`short`|<span data-ttu-id="a8294-467"><xref:System.Int16>.</span><span class="sxs-lookup"><span data-stu-id="a8294-467"><xref:System.Int16>.</span></span>|
|`Byte`|<span data-ttu-id="a8294-468"><xref:System.SByte>.</span><span class="sxs-lookup"><span data-stu-id="a8294-468"><xref:System.SByte>.</span></span>|
|`nonNegativeInteger`|<span data-ttu-id="a8294-469"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="a8294-469"><xref:System.Int64>.</span></span>|
|`unsignedLong`|<span data-ttu-id="a8294-470"><xref:System.UInt64>.</span><span class="sxs-lookup"><span data-stu-id="a8294-470"><xref:System.UInt64>.</span></span>|
|`unsignedInt`|<span data-ttu-id="a8294-471"><xref:System.UInt32>.</span><span class="sxs-lookup"><span data-stu-id="a8294-471"><xref:System.UInt32>.</span></span>|
|`unsignedShort`|<span data-ttu-id="a8294-472"><xref:System.UInt16>.</span><span class="sxs-lookup"><span data-stu-id="a8294-472"><xref:System.UInt16>.</span></span>|
|`unsignedByte`|<span data-ttu-id="a8294-473"><xref:System.Byte>.</span><span class="sxs-lookup"><span data-stu-id="a8294-473"><xref:System.Byte>.</span></span>|
|`positiveInteger`|<span data-ttu-id="a8294-474"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="a8294-474"><xref:System.Int64>.</span></span>|

## <a name="iserializable-types-mapping"></a><span data-ttu-id="a8294-475">ISerializable türleri eşleme</span><span class="sxs-lookup"><span data-stu-id="a8294-475">ISerializable types mapping</span></span>

<span data-ttu-id="a8294-476">.NET Framework sürüm 1,0 ' de, <xref:System.Runtime.Serialization.ISerializable> kalıcı veya veri aktarımı için nesneleri serileştirmek üzere genel bir mekanizma olarak sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="a8294-476">In .NET Framework version 1.0, <xref:System.Runtime.Serialization.ISerializable> was introduced as a general mechanism to serialize objects for persistence or data transfer.</span></span> <span data-ttu-id="a8294-477">`ISerializable` uygulayan ve uygulamalar arasında geçirilebilecek pek çok .NET Framework türü vardır.</span><span class="sxs-lookup"><span data-stu-id="a8294-477">There are many .NET Framework types that implement `ISerializable` and that can be passed between applications.</span></span> <span data-ttu-id="a8294-478"><xref:System.Runtime.Serialization.DataContractSerializer> doğal olarak `ISerializable` sınıfları için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="a8294-478"><xref:System.Runtime.Serialization.DataContractSerializer> naturally provides support for `ISerializable` classes.</span></span> <span data-ttu-id="a8294-479">`DataContractSerializer`, yalnızca türün QName (nitelenmiş adı) ile farklı `ISerializable` uygulama şeması türlerini eşleştirir ve etkin özellik koleksiyonlarıdır.</span><span class="sxs-lookup"><span data-stu-id="a8294-479">The `DataContractSerializer` maps `ISerializable` implementation schema types that differ only by the QName (qualified name) of the type and are effectively property collections.</span></span> <span data-ttu-id="a8294-480">Örneğin, `DataContractSerializer` <xref:System.Exception> `http://schemas.datacontract.org/2004/07/System` ad alanında aşağıdaki XSD türüne eşlenir.</span><span class="sxs-lookup"><span data-stu-id="a8294-480">For example, the `DataContractSerializer` maps <xref:System.Exception> to the following XSD type in the `http://schemas.datacontract.org/2004/07/System` namespace.</span></span>

```xml
<xs:complexType name="Exception">
 <xs:sequence>
  <xs:any minOccurs="0" maxOccurs="unbounded"
      namespace="##local" processContents="skip"/>
 </xs:sequence>
 <xs:attribute ref="ser:FactoryType"/>
</xs:complexType>
```

<span data-ttu-id="a8294-481">Veri sözleşmesi serileştirme şemasında bildirildiği `ser:FactoryType` isteğe bağlı öznitelik, türü seri durumdan çıkarılabilecek bir fabrika sınıfına başvurur.</span><span class="sxs-lookup"><span data-stu-id="a8294-481">The optional attribute `ser:FactoryType` declared in the Data Contract Serialization schema references a factory class that can deserialize the type.</span></span> <span data-ttu-id="a8294-482">Factory sınıfı, kullanılan `DataContractSerializer` örneğinin bilinen türler koleksiyonunun bir parçası olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a8294-482">The factory class must be part of the known types collection of the `DataContractSerializer` instance being used.</span></span> <span data-ttu-id="a8294-483">Bilinen türler hakkında daha fazla bilgi için bkz. [veri sözleşmesi bilinen türler](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="a8294-483">For more information about known types, see [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>

## <a name="datacontract-serialization-schema"></a><span data-ttu-id="a8294-484">DataContract serileştirme şeması</span><span class="sxs-lookup"><span data-stu-id="a8294-484">DataContract Serialization Schema</span></span>

<span data-ttu-id="a8294-485">`DataContractSerializer` tarafından dışarıya aktarılmış bir dizi şema, özel bir veri sözleşmesi serileştirme ad alanından türler, öğeler ve öznitelikler kullanır:</span><span class="sxs-lookup"><span data-stu-id="a8294-485">A number of schemas exported by the `DataContractSerializer` use types, elements, and attributes from a special Data Contract Serialization namespace:</span></span>

`http://schemas.microsoft.com/2003/10/Serialization`

<span data-ttu-id="a8294-486">Aşağıda, tüm veri anlaşması serileştirme şeması bildirimi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a8294-486">The following is a complete Data Contract Serialization schema declaration.</span></span>

```xml
<xs:schema attributeFormDefault="qualified"
   elementFormDefault="qualified"
   targetNamespace =
    "http://schemas.microsoft.com/2003/10/Serialization/"
   xmlns:xs="http://www.w3.org/2001/XMLSchema"
   xmlns:tns="http://schemas.microsoft.com/2003/10/Serialization/">

 <!-- Top-level elements for primitive types. -->
 <xs:element name="anyType" nillable="true" type="xs:anyType"/>
 <xs:element name="anyURI" nillable="true" type="xs:anyURI"/>
 <xs:element name="base64Binary"
       nillable="true" type="xs:base64Binary"/>
 <xs:element name="boolean" nillable="true" type="xs:boolean"/>
 <xs:element name="byte" nillable="true" type="xs:byte"/>
 <xs:element name="dateTime" nillable="true" type="xs:dateTime"/>
 <xs:element name="decimal" nillable="true" type="xs:decimal"/>
 <xs:element name="double" nillable="true" type="xs:double"/>
 <xs:element name="float" nillable="true" type="xs:float"/>
 <xs:element name="int" nillable="true" type="xs:int"/>
 <xs:element name="long" nillable="true" type="xs:long"/>
 <xs:element name="QName" nillable="true" type="xs:QName"/>
 <xs:element name="short" nillable="true" type="xs:short"/>
 <xs:element name="string" nillable="true" type="xs:string"/>
 <xs:element name="unsignedByte"
       nillable="true" type="xs:unsignedByte"/>
 <xs:element name="unsignedInt"
       nillable="true" type="xs:unsignedInt"/>
 <xs:element name="unsignedLong"
       nillable="true" type="xs:unsignedLong"/>
 <xs:element name="unsignedShort"
       nillable="true" type="xs:unsignedShort"/>

 <!-- Primitive types introduced for certain .NET simple types. -->
 <xs:element name="char" nillable="true" type="tns:char"/>
 <xs:simpleType name="char">
  <xs:restriction base="xs:int"/>
 </xs:simpleType>

 <!-- xs:duration is restricted to an ordered value space,
    to map to System.TimeSpan -->
 <xs:element name="duration" nillable="true" type="tns:duration"/>
 <xs:simpleType name="duration">
  <xs:restriction base="xs:duration">
   <xs:pattern
     value="\-?P(\d*D)?(T(\d*H)?(\d*M)?(\d*(\.\d*)?S)?)?"/>
   <xs:minInclusive value="-P10675199DT2H48M5.4775808S"/>
   <xs:maxInclusive value="P10675199DT2H48M5.4775807S"/>
  </xs:restriction>
 </xs:simpleType>

 <xs:element name="guid" nillable="true" type="tns:guid"/>
 <xs:simpleType name="guid">
  <xs:restriction base="xs:string">
   <xs:pattern value="[\da-fA-F]{8}-[\da-fA-F]{4}-[\da-fA-F]{4}-[\da-fA-F]{4}-[\da-fA-F]{12}"/>
  </xs:restriction>
 </xs:simpleType>

 <!-- This is used for schemas exported from ISerializable type. -->
 <xs:attribute name="FactoryType" type="xs:QName"/>
</xs:schema>
```

<span data-ttu-id="a8294-487">Aşağıdakiler not edilmelidir:</span><span class="sxs-lookup"><span data-stu-id="a8294-487">The following should be noted:</span></span>

- <span data-ttu-id="a8294-488">`ser:char`, <xref:System.Char>türündeki Unicode karakterlerini temsil edecek şekilde sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="a8294-488">`ser:char` is introduced to represent Unicode characters of type <xref:System.Char>.</span></span>

- <span data-ttu-id="a8294-489">`xs:duration` `valuespace`, bir <xref:System.TimeSpan>eşleştirileceğinden, sıralı bir küme ile azaltılır.</span><span class="sxs-lookup"><span data-stu-id="a8294-489">The `valuespace` of `xs:duration` is reduced to an ordered set so that it can be mapped to a <xref:System.TimeSpan>.</span></span>

- <span data-ttu-id="a8294-490">`FactoryType`, <xref:System.Runtime.Serialization.ISerializable>türetilen türlerden aktarılmış şemalarda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a8294-490">`FactoryType` is used in schemas exported from types that are derived from <xref:System.Runtime.Serialization.ISerializable>.</span></span>

## <a name="importing-non-datacontract-schemas"></a><span data-ttu-id="a8294-491">DataContract olmayan şemaları içeri aktarma</span><span class="sxs-lookup"><span data-stu-id="a8294-491">Importing non-DataContract schemas</span></span>

<span data-ttu-id="a8294-492">`DataContractSerializer`, `DataContractSerializer` XSD profiliyle uyumlu olmayan şemalardan içeri aktarmaya izin veren `ImportXmlTypes` seçeneğine sahiptir (bkz. <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> özelliği).</span><span class="sxs-lookup"><span data-stu-id="a8294-492">`DataContractSerializer` has the `ImportXmlTypes` option to allow import of schemas that do not conform to the `DataContractSerializer` XSD profile (see the <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> property).</span></span> <span data-ttu-id="a8294-493">Bu seçeneğin `true` ayarlanması, uyumsuz şema türlerinin kabul edilmesine ve bunları aşağıdaki uygulamayla eşleştirmenize <xref:System.Xml.XmlNode> <xref:System.Xml.Serialization.IXmlSerializable> (yalnızca sınıf adı farklıdır).</span><span class="sxs-lookup"><span data-stu-id="a8294-493">Setting this option to `true` enables acceptance of non-conforming schema types and mapping them to the following implementation, <xref:System.Xml.Serialization.IXmlSerializable> wrapping an array of <xref:System.Xml.XmlNode> (only the class name differs).</span></span>

```csharp
[GeneratedCodeAttribute("System.Runtime.Serialization", "3.0.0.0")]
[System.Xml.Serialization.XmlSchemaProviderAttribute("ExportSchema")]
[System.Xml.Serialization.XmlRootAttribute(IsNullable=false)]
public partial class Person : object, IXmlSerializable
{
  private XmlNode[] nodesField;
  private static XmlQualifiedName typeName =
new XmlQualifiedName("Person","http://Microsoft.ServiceModel.Samples");
  public XmlNode[] Nodes
  {
    get {return this.nodesField;}
    set {this.nodesField = value;}
  }
  public void ReadXml(XmlReader reader)
  {
    this.nodesField = XmlSerializableServices.ReadNodes(reader);
  }
  public void WriteXml(XmlWriter writer)
  {
    XmlSerializableServices.WriteNodes(writer, this.Nodes);
  }
  public System.Xml.Schema.XmlSchema GetSchema()
  {
    return null;
  }
  public static XmlQualifiedName ExportSchema(XmlSchemaSet schemas)
  {
    XmlSerializableServices.AddDefaultSchema(schemas, typeName);
    return typeName;
  }
}
```

## <a name="datetimeoffset-serialization"></a><span data-ttu-id="a8294-494">DateTimeOffset serileştirme</span><span class="sxs-lookup"><span data-stu-id="a8294-494">DateTimeOffset Serialization</span></span>

<span data-ttu-id="a8294-495"><xref:System.DateTimeOffset> ilkel bir tür olarak değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="a8294-495">The <xref:System.DateTimeOffset> is not treated as a primitive type.</span></span> <span data-ttu-id="a8294-496">Bunun yerine, iki bölümden oluşan karmaşık bir öğe olarak serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="a8294-496">Instead, it is serialized as a complex element with two parts.</span></span> <span data-ttu-id="a8294-497">İlk bölüm Tarih saatini temsil eder ve ikinci bölüm Tarih saatinden itibaren olan sapmayı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a8294-497">The first part represents the date time, and the second part represents the offset from the date time.</span></span> <span data-ttu-id="a8294-498">Aşağıdaki kodda serileştirilmiş bir DateTimeOffset değeri örneği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a8294-498">An example of a serialized DateTimeOffset value is shown in the following code.</span></span>

```xml
<OffSet xmlns:a="http://schemas.datacontract.org/2004/07/System">
  <DateTime i:type="b:dateTime" xmlns=""
    xmlns:b="http://www.w3.org/2001/XMLSchema">2008-08-28T08:00:00
  </DateTime>
  <OffsetMinutes i:type="b:short" xmlns=""
   xmlns:b="http://www.w3.org/2001/XMLSchema">-480
   </OffsetMinutes>
</OffSet>
```

<span data-ttu-id="a8294-499">Şema aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="a8294-499">The schema is as follows.</span></span>

```xml
<xs:schema targetNamespace="http://schemas.datacontract.org/2004/07/System">
   <xs:complexType name="DateTimeOffset">
      <xs:sequence minOccurs="1" maxOccurs="1">
         <xs:element name="DateTime" type="xs:dateTime"
         minOccurs="1" maxOccurs="1" />
         <xs:element name="OffsetMinutes" type="xs:short"
         minOccurs="1" maxOccurs="1" />
      </xs:sequence>
   </xs:complexType>
</xs:schema>
```

## <a name="see-also"></a><span data-ttu-id="a8294-500">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a8294-500">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- <xref:System.Runtime.Serialization.XsdDataContractImporter>
- [<span data-ttu-id="a8294-501">Veri Anlaşmalarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="a8294-501">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)

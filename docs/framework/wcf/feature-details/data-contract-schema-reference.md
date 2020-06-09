---
title: Veri Sözleşmesi Şema Başvurusu
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts [WCF], schema reference
ms.assetid: 9ebb0ebe-8166-4c93-980a-7c8f1f38f7c0
ms.openlocfilehash: 04d1f753e5788460404942a21a29e1612f674e90
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593574"
---
# <a name="data-contract-schema-reference"></a><span data-ttu-id="11b35-102">Veri Sözleşmesi Şema Başvurusu</span><span class="sxs-lookup"><span data-stu-id="11b35-102">Data Contract Schema Reference</span></span>

<span data-ttu-id="11b35-103">Bu konu, <xref:System.Runtime.Serialization.DataContractSerializer> XML serileştirmesi için ortak dil çalışma zamanı (CLR) türlerini tarif etmek üzere tarafından kullanılan XML şemasının (xsd) alt kümesini açıklar.</span><span class="sxs-lookup"><span data-stu-id="11b35-103">This topic describes the subset of the XML Schema (XSD) used by <xref:System.Runtime.Serialization.DataContractSerializer> to describe common language runtime (CLR) types for XML serialization.</span></span>

## <a name="datacontractserializer-mappings"></a><span data-ttu-id="11b35-104">DataContractSerializer eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="11b35-104">DataContractSerializer Mappings</span></span>

<span data-ttu-id="11b35-105">Meta veriler, `DataContractSerializer` meta veri uç noktası veya [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)kullanılarak BIR Windows Communication Foundation (WCF) hizmetinden VERILDIĞINDE CLR türlerini xsd olarak eşler.</span><span class="sxs-lookup"><span data-stu-id="11b35-105">The `DataContractSerializer` maps CLR types to XSD when metadata is exported from a Windows Communication Foundation (WCF) service using a metadata endpoint or the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="11b35-106">Daha fazla bilgi için bkz. [veri sözleşmesi serileştiricisi](data-contract-serializer.md).</span><span class="sxs-lookup"><span data-stu-id="11b35-106">For more information, see [Data Contract Serializer](data-contract-serializer.md).</span></span>

<span data-ttu-id="11b35-107">`DataContractSerializer`Ayrıca, Svcutil. exe dosyası Web Hizmetleri Açıklama Dili (wsdl) veya xsd belgelerine erişmek için kullanıldığında ve hizmetler veya istemciler için veri sözleşmeleri oluştururken de xsd 'YI clr türlerine eşler.</span><span class="sxs-lookup"><span data-stu-id="11b35-107">The `DataContractSerializer` also maps XSD to CLR types when Svcutil.exe is used to access Web Services Description Language (WSDL) or XSD documents and generate data contracts for services or clients.</span></span>

<span data-ttu-id="11b35-108">Yalnızca bu belgede belirtilen gereksinimlere uyan XML şema örnekleri kullanılarak CLR türleriyle eşlenebilir `DataContractSerializer` .</span><span class="sxs-lookup"><span data-stu-id="11b35-108">Only XML Schema instances that conform to requirements stated in this document can be mapped to CLR types using `DataContractSerializer`.</span></span>

### <a name="support-levels"></a><span data-ttu-id="11b35-109">Destek düzeyleri</span><span class="sxs-lookup"><span data-stu-id="11b35-109">Support Levels</span></span>

<span data-ttu-id="11b35-110">, `DataContractSerializer` Belirli BIR XML şeması özelliği için aşağıdaki destek düzeylerini sağlar:</span><span class="sxs-lookup"><span data-stu-id="11b35-110">The `DataContractSerializer` provides the following levels of support for a given XML Schema feature:</span></span>

- <span data-ttu-id="11b35-111">**Desteklenir**.</span><span class="sxs-lookup"><span data-stu-id="11b35-111">**Supported**.</span></span> <span data-ttu-id="11b35-112">Kullanılarak bu özellikten CLR türlerine veya özniteliklerine (veya her ikisine) açık eşleme vardır `DataContractSerializer` .</span><span class="sxs-lookup"><span data-stu-id="11b35-112">There is explicit mapping from this feature to CLR types or attributes (or both) using `DataContractSerializer`.</span></span>

- <span data-ttu-id="11b35-113">**Yoksayıldı**.</span><span class="sxs-lookup"><span data-stu-id="11b35-113">**Ignored**.</span></span> <span data-ttu-id="11b35-114">Özelliği tarafından içeri aktarılan şemalarda, `DataContractSerializer` ancak kod üretimi üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="11b35-114">The feature is allowed in schemas imported by the `DataContractSerializer`, but has no effect on code generation.</span></span>

- <span data-ttu-id="11b35-115">**Yasak**.</span><span class="sxs-lookup"><span data-stu-id="11b35-115">**Forbidden**.</span></span> <span data-ttu-id="11b35-116">`DataContractSerializer`Özelliği kullanılarak şemanın içeri aktarılmasını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="11b35-116">The `DataContractSerializer` does not support importing a schema using the feature.</span></span> <span data-ttu-id="11b35-117">Örneğin, bu tür bir özelliği kullanan bir şemaya sahip bir WSDL 'ye erişirken Svcutil. exe, bunun yerine kullanmaya geri döner <xref:System.Xml.Serialization.XmlSerializer> .</span><span class="sxs-lookup"><span data-stu-id="11b35-117">For example, Svcutil.exe, when accessing a WSDL with a schema that uses such a feature, falls back to using the <xref:System.Xml.Serialization.XmlSerializer> instead.</span></span> <span data-ttu-id="11b35-118">Bu varsayılan olarak olur.</span><span class="sxs-lookup"><span data-stu-id="11b35-118">This is by default.</span></span>

## <a name="general-information"></a><span data-ttu-id="11b35-119">Genel Bilgiler</span><span class="sxs-lookup"><span data-stu-id="11b35-119">General Information</span></span>

- <span data-ttu-id="11b35-120">Şema ad alanı [XML şemasında](https://www.w3.org/2001/XMLSchema)açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="11b35-120">The schema namespace is described at [XML Schema](https://www.w3.org/2001/XMLSchema).</span></span> <span data-ttu-id="11b35-121">"Xs" ön eki bu belgede kullanılıyor.</span><span class="sxs-lookup"><span data-stu-id="11b35-121">The prefix "xs" is used in this document.</span></span>

- <span data-ttu-id="11b35-122">Şema olmayan bir ad alanı olan herhangi bir öznitelik yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="11b35-122">Any attributes with a non-schema namespace are ignored.</span></span>

- <span data-ttu-id="11b35-123">Tüm ek açıklamalar (Bu belgede açıklananlar dışında) yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="11b35-123">Any annotations (except for those described in this document) are ignored.</span></span>

### <a name="xsschema-attributes"></a><span data-ttu-id="11b35-124">\<xs:schema>: öznitelikler</span><span class="sxs-lookup"><span data-stu-id="11b35-124">\<xs:schema>: attributes</span></span>

|<span data-ttu-id="11b35-125">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="11b35-125">Attribute</span></span>|<span data-ttu-id="11b35-126">DataContract</span><span class="sxs-lookup"><span data-stu-id="11b35-126">DataContract</span></span>|
|---------------|------------------|
|`attributeFormDefault`|<span data-ttu-id="11b35-127">LIP.</span><span class="sxs-lookup"><span data-stu-id="11b35-127">Ignored.</span></span>|
|`blockDefault`|<span data-ttu-id="11b35-128">LIP.</span><span class="sxs-lookup"><span data-stu-id="11b35-128">Ignored.</span></span>|
|`elementFormDefault`|<span data-ttu-id="11b35-129">Nitelenmiş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="11b35-129">Must be qualified.</span></span> <span data-ttu-id="11b35-130">Şemanın desteklenmesi için tüm öğelerin nitelendirilmelidir `DataContractSerializer` .</span><span class="sxs-lookup"><span data-stu-id="11b35-130">All elements must be qualified for a schema to be supported by `DataContractSerializer`.</span></span> <span data-ttu-id="11b35-131">Bu, herhangi bir xs:schema/@elementFormDefault öğe bildiriminde "nitelikli" veya xs:element/@form "nitelikli" olarak ayarlanarak gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="11b35-131">This can be accomplished by either setting xs:schema/@elementFormDefault to "qualified" or by setting xs:element/@form to "qualified" on each individual element declaration.</span></span>|
|`finalDefault`|<span data-ttu-id="11b35-132">LIP.</span><span class="sxs-lookup"><span data-stu-id="11b35-132">Ignored.</span></span>|
|`Id`|<span data-ttu-id="11b35-133">LIP.</span><span class="sxs-lookup"><span data-stu-id="11b35-133">Ignored.</span></span>|
|`targetNamespace`|<span data-ttu-id="11b35-134">Desteklenir ve veri sözleşmesi ad alanıyla eşleştirilir.</span><span class="sxs-lookup"><span data-stu-id="11b35-134">Supported and mapped to the data contract namespace.</span></span> <span data-ttu-id="11b35-135">Bu öznitelik belirtilmemişse boş ad alanı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="11b35-135">If this attribute is not specified, the blank namespace is used.</span></span> <span data-ttu-id="11b35-136">Ayrılmış ad alanı olamaz `http://schemas.microsoft.com/2003/10/Serialization/` .</span><span class="sxs-lookup"><span data-stu-id="11b35-136">Cannot be the reserved namespace `http://schemas.microsoft.com/2003/10/Serialization/`.</span></span>|
|`version`|<span data-ttu-id="11b35-137">LIP.</span><span class="sxs-lookup"><span data-stu-id="11b35-137">Ignored.</span></span>|

### <a name="xsschema-contents"></a><span data-ttu-id="11b35-138">\<xs:schema>: içerik</span><span class="sxs-lookup"><span data-stu-id="11b35-138">\<xs:schema>: contents</span></span>

|<span data-ttu-id="11b35-139">İçindekiler</span><span class="sxs-lookup"><span data-stu-id="11b35-139">Contents</span></span>|<span data-ttu-id="11b35-140">Şema</span><span class="sxs-lookup"><span data-stu-id="11b35-140">Schema</span></span>|
|--------------|------------|
|`include`|<span data-ttu-id="11b35-141">Destekleniyor.</span><span class="sxs-lookup"><span data-stu-id="11b35-141">Supported.</span></span> <span data-ttu-id="11b35-142">`DataContractSerializer`xs: include ve xs: import destekler.</span><span class="sxs-lookup"><span data-stu-id="11b35-142">`DataContractSerializer` supports xs:include and xs:import.</span></span> <span data-ttu-id="11b35-143">Ancak, Svcutil. exe `xs:include/@schemaLocation` `xs:import/@location` yerel bir dosyadan meta veriler yüklendiğinde aşağıdaki ve başvuruları kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="11b35-143">However, Svcutil.exe restricts following `xs:include/@schemaLocation` and `xs:import/@location` references when metadata is loaded from a local file.</span></span> <span data-ttu-id="11b35-144">Şema dosyalarının listesi, bu durumda değil, bant dışı bir mekanizmaya geçirilmelidir `include` ; `include` d şema belgeleri yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="11b35-144">The list of schema files must be passed through an out-of-band mechanism and not through `include` in this case; `include`d schema documents are ignored.</span></span>|
|`redefine`|<span data-ttu-id="11b35-145">Inı.</span><span class="sxs-lookup"><span data-stu-id="11b35-145">Forbidden.</span></span> <span data-ttu-id="11b35-146">Öğesinin kullanımı `xs:redefine` `DataContractSerializer` Güvenlik nedeniyle yasaktır: bunun `x:redefine` `schemaLocation` izlenmesinin gerekli olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="11b35-146">The use of `xs:redefine` is forbidden by `DataContractSerializer` for security reasons: `x:redefine` requires `schemaLocation` to be followed.</span></span> <span data-ttu-id="11b35-147">Bazı durumlarda, DataContract kullanan Svcutil. exe ' nin kullanımını kısıtlar `schemaLocation` .</span><span class="sxs-lookup"><span data-stu-id="11b35-147">In certain circumstances, Svcutil.exe using DataContract restricts use of `schemaLocation`.</span></span>|
|`import`|<span data-ttu-id="11b35-148">Destekleniyor.</span><span class="sxs-lookup"><span data-stu-id="11b35-148">Supported.</span></span> <span data-ttu-id="11b35-149">`DataContractSerializer``xs:include`, ve destekler `xs:import` .</span><span class="sxs-lookup"><span data-stu-id="11b35-149">`DataContractSerializer` supports `xs:include` and `xs:import`.</span></span> <span data-ttu-id="11b35-150">Ancak, Svcutil. exe `xs:include/@schemaLocation` `xs:import/@location` yerel bir dosyadan meta veriler yüklendiğinde aşağıdaki ve başvuruları kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="11b35-150">However, Svcutil.exe restricts following `xs:include/@schemaLocation` and `xs:import/@location` references when metadata is loaded from a local file.</span></span> <span data-ttu-id="11b35-151">Şema dosyalarının listesi, bu durumda değil, bant dışı bir mekanizmaya geçirilmelidir `include` ; `include` d şema belgeleri yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="11b35-151">The list of schema files must be passed through an out-of-band mechanism and not through `include` in this case; `include`d schema documents are ignored.</span></span>|
|`simpleType`|<span data-ttu-id="11b35-152">Destekleniyor.</span><span class="sxs-lookup"><span data-stu-id="11b35-152">Supported.</span></span> <span data-ttu-id="11b35-153">Bölümüne bakın `xs:simpleType` .</span><span class="sxs-lookup"><span data-stu-id="11b35-153">See the `xs:simpleType` section.</span></span>|
|`complexType`|<span data-ttu-id="11b35-154">Desteklenir, veri sözleşmeleri ile eşlenir.</span><span class="sxs-lookup"><span data-stu-id="11b35-154">Supported, maps to data contracts.</span></span> <span data-ttu-id="11b35-155">Bölümüne bakın `xs:complexType` .</span><span class="sxs-lookup"><span data-stu-id="11b35-155">See the `xs:complexType` section.</span></span>|
|`group`|<span data-ttu-id="11b35-156">LIP.</span><span class="sxs-lookup"><span data-stu-id="11b35-156">Ignored.</span></span> <span data-ttu-id="11b35-157">`DataContractSerializer``xs:group`, ve kullanımını desteklemez `xs:attributeGroup` `xs:attribute` .</span><span class="sxs-lookup"><span data-stu-id="11b35-157">`DataContractSerializer` does not support use of `xs:group`, `xs:attributeGroup`, and `xs:attribute`.</span></span> <span data-ttu-id="11b35-158">Bu bildirimler, öğesinin alt öğesi olarak yok sayılır `xs:schema` , ancak içinden `complexType` veya desteklenen diğer yapılardan başvurulamaz.</span><span class="sxs-lookup"><span data-stu-id="11b35-158">These declarations are ignored as children of `xs:schema`, but cannot be referenced from within `complexType` or other supported constructs.</span></span>|
|`attributeGroup`|<span data-ttu-id="11b35-159">LIP.</span><span class="sxs-lookup"><span data-stu-id="11b35-159">Ignored.</span></span> <span data-ttu-id="11b35-160">`DataContractSerializer``xs:group`, ve kullanımını desteklemez `xs:attributeGroup` `xs:attribute` .</span><span class="sxs-lookup"><span data-stu-id="11b35-160">`DataContractSerializer` does not support use of `xs:group`, `xs:attributeGroup`, and `xs:attribute`.</span></span> <span data-ttu-id="11b35-161">Bu bildirimler, öğesinin alt öğesi olarak yok sayılır `xs:schema` , ancak içinden `complexType` veya desteklenen diğer yapılardan başvurulamaz.</span><span class="sxs-lookup"><span data-stu-id="11b35-161">These declarations are ignored as children of `xs:schema`, but cannot be referenced from within `complexType` or other supported constructs.</span></span>|
|`element`|<span data-ttu-id="11b35-162">Destekleniyor.</span><span class="sxs-lookup"><span data-stu-id="11b35-162">Supported.</span></span> <span data-ttu-id="11b35-163">Bkz. genel öğe bildirimi (ŞLı).</span><span class="sxs-lookup"><span data-stu-id="11b35-163">See Global Element Declaration (GED).</span></span>|
|`attribute`|<span data-ttu-id="11b35-164">LIP.</span><span class="sxs-lookup"><span data-stu-id="11b35-164">Ignored.</span></span> <span data-ttu-id="11b35-165">`DataContractSerializer``xs:group`, ve kullanımını desteklemez `xs:attributeGroup` `xs:attribute` .</span><span class="sxs-lookup"><span data-stu-id="11b35-165">`DataContractSerializer` does not support use of `xs:group`, `xs:attributeGroup`, and `xs:attribute`.</span></span> <span data-ttu-id="11b35-166">Bu bildirimler, öğesinin alt öğesi olarak yok sayılır `xs:schema` , ancak içinden `complexType` veya desteklenen diğer yapılardan başvurulamaz.</span><span class="sxs-lookup"><span data-stu-id="11b35-166">These declarations are ignored as children of `xs:schema`, but cannot be referenced from within `complexType` or other supported constructs.</span></span>|
|`notation`|<span data-ttu-id="11b35-167">LIP.</span><span class="sxs-lookup"><span data-stu-id="11b35-167">Ignored.</span></span>|

## <a name="complex-types--xscomplextype"></a><span data-ttu-id="11b35-168">Karmaşık türler –\<xs:complexType></span><span class="sxs-lookup"><span data-stu-id="11b35-168">Complex Types – \<xs:complexType></span></span>

### <a name="general-information"></a><span data-ttu-id="11b35-169">Genel Bilgiler</span><span class="sxs-lookup"><span data-stu-id="11b35-169">General Information</span></span>

<span data-ttu-id="11b35-170">Her karmaşık tür \<xs:complexType> bir veri sözleşmesine eşlenir.</span><span class="sxs-lookup"><span data-stu-id="11b35-170">Each complex type \<xs:complexType> maps to a data contract.</span></span>

### <a name="xscomplextype-attributes"></a><span data-ttu-id="11b35-171">\<xs:complexType>: öznitelikler</span><span class="sxs-lookup"><span data-stu-id="11b35-171">\<xs:complexType>: attributes</span></span>

|<span data-ttu-id="11b35-172">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="11b35-172">Attribute</span></span>|<span data-ttu-id="11b35-173">Şema</span><span class="sxs-lookup"><span data-stu-id="11b35-173">Schema</span></span>|
|---------------|------------|
|`abstract`|<span data-ttu-id="11b35-174">False (varsayılan) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="11b35-174">Must be false (default).</span></span>|
|`block`|<span data-ttu-id="11b35-175">Inı.</span><span class="sxs-lookup"><span data-stu-id="11b35-175">Forbidden.</span></span>|
|`final`|<span data-ttu-id="11b35-176">LIP.</span><span class="sxs-lookup"><span data-stu-id="11b35-176">Ignored.</span></span>|
|`id`|<span data-ttu-id="11b35-177">LIP.</span><span class="sxs-lookup"><span data-stu-id="11b35-177">Ignored.</span></span>|
|`mixed`|<span data-ttu-id="11b35-178">False (varsayılan) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="11b35-178">Must be false (default).</span></span>|
|`name`|<span data-ttu-id="11b35-179">Desteklenir ve veri sözleşmesi adına eşlenir.</span><span class="sxs-lookup"><span data-stu-id="11b35-179">Supported and mapped to the data contract name.</span></span> <span data-ttu-id="11b35-180">Adda dönemler varsa, türü bir iç türle eşlemek için bir girişimde bulunuldu.</span><span class="sxs-lookup"><span data-stu-id="11b35-180">If there are periods in the name, an attempt is made to map the type to an inner type.</span></span> <span data-ttu-id="11b35-181">Örneğin, adlı karmaşık bir tür, veri sözleşmesi `A.B` adına sahip bir türün iç türü olan bir veri sözleşmesi türüyle eşlenir `A` , ancak bu tür bir veri anlaşması türü varsa.</span><span class="sxs-lookup"><span data-stu-id="11b35-181">For example, a complex type named `A.B` maps to a data contract type that is an inner type of a type with the data contract name `A`, but only if such a data contract type exists.</span></span> <span data-ttu-id="11b35-182">Birden fazla iç içe geçme olabilir: Örneğin, `A.B.C` bir iç tür olabilir, ancak yalnızca `A` ve `A.B` her ikisi de vardır.</span><span class="sxs-lookup"><span data-stu-id="11b35-182">More than one level of nesting is possible: for example, `A.B.C` can be an inner type, but only if `A` and `A.B` both exist.</span></span>|

### <a name="xscomplextype-contents"></a><span data-ttu-id="11b35-183">\<xs:complexType>: içerik</span><span class="sxs-lookup"><span data-stu-id="11b35-183">\<xs:complexType>: contents</span></span>

|<span data-ttu-id="11b35-184">İçindekiler</span><span class="sxs-lookup"><span data-stu-id="11b35-184">Contents</span></span>|<span data-ttu-id="11b35-185">Şema</span><span class="sxs-lookup"><span data-stu-id="11b35-185">Schema</span></span>|
|--------------|------------|
|`simpleContent`|<span data-ttu-id="11b35-186">Uzantılar yasaktır.</span><span class="sxs-lookup"><span data-stu-id="11b35-186">Extensions are forbidden.</span></span><br /><br /> <span data-ttu-id="11b35-187">Kısıtlamaya yalnızca öğesinden izin verilir `anySimpleType` .</span><span class="sxs-lookup"><span data-stu-id="11b35-187">Restriction is allowed only from `anySimpleType`.</span></span>|
|`complexContent`|<span data-ttu-id="11b35-188">Destekleniyor.</span><span class="sxs-lookup"><span data-stu-id="11b35-188">Supported.</span></span> <span data-ttu-id="11b35-189">Bkz. "devralma".</span><span class="sxs-lookup"><span data-stu-id="11b35-189">See "Inheritance".</span></span>|
|`group`|<span data-ttu-id="11b35-190">Inı.</span><span class="sxs-lookup"><span data-stu-id="11b35-190">Forbidden.</span></span>|
|`all`|<span data-ttu-id="11b35-191">Inı.</span><span class="sxs-lookup"><span data-stu-id="11b35-191">Forbidden.</span></span>|
|`choice`|<span data-ttu-id="11b35-192">Yasak</span><span class="sxs-lookup"><span data-stu-id="11b35-192">Forbidden</span></span>|
|`sequence`|<span data-ttu-id="11b35-193">Desteklenir, bir veri sözleşmesinin veri üyeleriyle eşlenir.</span><span class="sxs-lookup"><span data-stu-id="11b35-193">Supported, maps to data members of a data contract.</span></span>|
|`attribute`|<span data-ttu-id="11b35-194">Use = "yasaklanmış" (bir özel durum) olsa bile yasak.</span><span class="sxs-lookup"><span data-stu-id="11b35-194">Forbidden, even if use="prohibited" (with one exception).</span></span> <span data-ttu-id="11b35-195">Yalnızca standart serileştirme şeması ad alanındaki isteğe bağlı öznitelikler desteklenir.</span><span class="sxs-lookup"><span data-stu-id="11b35-195">Only optional attributes from the Standard Serialization Schema namespace are supported.</span></span> <span data-ttu-id="11b35-196">Veri sözleşmesi programlama modelindeki veri üyeleriyle eşlemeirler.</span><span class="sxs-lookup"><span data-stu-id="11b35-196">They do not map to data members in the data contract programming model.</span></span> <span data-ttu-id="11b35-197">Şu anda yalnızca bir özniteliğin anlamı vardır ve ISerializable bölümünde ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="11b35-197">Currently, only one such attribute has meaning and is discussed in the ISerializable section.</span></span> <span data-ttu-id="11b35-198">Diğerlerinin hepsi yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="11b35-198">All others are ignored.</span></span>|
|`attributeGroup`|<span data-ttu-id="11b35-199">Inı.</span><span class="sxs-lookup"><span data-stu-id="11b35-199">Forbidden.</span></span> <span data-ttu-id="11b35-200">WCF v1 sürümünde, `DataContractSerializer` içinde varlığını yoksayar `attributeGroup` `xs:complexType` .</span><span class="sxs-lookup"><span data-stu-id="11b35-200">In the WCF v1 release, `DataContractSerializer` ignores the presence of `attributeGroup` inside `xs:complexType`.</span></span>|
|`anyAttribute`|<span data-ttu-id="11b35-201">Inı.</span><span class="sxs-lookup"><span data-stu-id="11b35-201">Forbidden.</span></span>|
|<span data-ttu-id="11b35-202">olmamalıdır</span><span class="sxs-lookup"><span data-stu-id="11b35-202">(empty)</span></span>|<span data-ttu-id="11b35-203">Veri üyesi olmayan bir veri sözleşmesine eşlenir.</span><span class="sxs-lookup"><span data-stu-id="11b35-203">Maps to a data contract with no data members.</span></span>|

### <a name="xssequence-in-a-complex-type-attributes"></a><span data-ttu-id="11b35-204">\<xs:sequence>karmaşık bir tür: öznitelikler</span><span class="sxs-lookup"><span data-stu-id="11b35-204">\<xs:sequence> in a complex type: attributes</span></span>

|<span data-ttu-id="11b35-205">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="11b35-205">Attribute</span></span>|<span data-ttu-id="11b35-206">Şema</span><span class="sxs-lookup"><span data-stu-id="11b35-206">Schema</span></span>|
|---------------|------------|
|`id`|<span data-ttu-id="11b35-207">LIP.</span><span class="sxs-lookup"><span data-stu-id="11b35-207">Ignored.</span></span>|
|`maxOccurs`|<span data-ttu-id="11b35-208">1 (varsayılan) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="11b35-208">Must be 1 (default).</span></span>|
|`minOccurs`|<span data-ttu-id="11b35-209">1 (varsayılan) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="11b35-209">Must be 1 (default).</span></span>|

### <a name="xssequence-in-a-complex-type-contents"></a><span data-ttu-id="11b35-210">\<xs:sequence>karmaşık bir tür: içerikler</span><span class="sxs-lookup"><span data-stu-id="11b35-210">\<xs:sequence> in a complex type: contents</span></span>

|<span data-ttu-id="11b35-211">İçindekiler</span><span class="sxs-lookup"><span data-stu-id="11b35-211">Contents</span></span>|<span data-ttu-id="11b35-212">Şema</span><span class="sxs-lookup"><span data-stu-id="11b35-212">Schema</span></span>|
|--------------|------------|
|`element`|<span data-ttu-id="11b35-213">Her örnek bir veri üyesine eşlenir.</span><span class="sxs-lookup"><span data-stu-id="11b35-213">Each instance maps to a data member.</span></span>|
|`group`|<span data-ttu-id="11b35-214">Inı.</span><span class="sxs-lookup"><span data-stu-id="11b35-214">Forbidden.</span></span>|
|`choice`|<span data-ttu-id="11b35-215">Inı.</span><span class="sxs-lookup"><span data-stu-id="11b35-215">Forbidden.</span></span>|
|`sequence`|<span data-ttu-id="11b35-216">Inı.</span><span class="sxs-lookup"><span data-stu-id="11b35-216">Forbidden.</span></span>|
|`any`|<span data-ttu-id="11b35-217">Inı.</span><span class="sxs-lookup"><span data-stu-id="11b35-217">Forbidden.</span></span>|
|<span data-ttu-id="11b35-218">olmamalıdır</span><span class="sxs-lookup"><span data-stu-id="11b35-218">(empty)</span></span>|<span data-ttu-id="11b35-219">Veri üyesi olmayan bir veri sözleşmesine eşlenir.</span><span class="sxs-lookup"><span data-stu-id="11b35-219">Maps to a data contract with no data members.</span></span>|

## <a name="elements--xselement"></a><span data-ttu-id="11b35-220">Ög\<xs:element></span><span class="sxs-lookup"><span data-stu-id="11b35-220">Elements – \<xs:element></span></span>

### <a name="general-information"></a><span data-ttu-id="11b35-221">Genel Bilgiler</span><span class="sxs-lookup"><span data-stu-id="11b35-221">General Information</span></span>

<span data-ttu-id="11b35-222">`<xs:element>`, aşağıdaki bağlamlarda gerçekleşebilir:</span><span class="sxs-lookup"><span data-stu-id="11b35-222">`<xs:element>` can occur in the following contexts:</span></span>

- <span data-ttu-id="11b35-223">`<xs:sequence>`Normal (koleksiyon olmayan) bir veri sözleşmesinin veri üyesini açıklayan bir içinde meydana gelebilir.</span><span class="sxs-lookup"><span data-stu-id="11b35-223">It can occur within an `<xs:sequence>`, which describes a data member of a regular (non-collection) data contract.</span></span> <span data-ttu-id="11b35-224">Bu durumda, `maxOccurs` öznitelik 1 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="11b35-224">In this case, the `maxOccurs` attribute must be 1.</span></span> <span data-ttu-id="11b35-225">(0 değerine izin verilmez).</span><span class="sxs-lookup"><span data-stu-id="11b35-225">(A value of 0 is not allowed).</span></span>

- <span data-ttu-id="11b35-226">Bir `<xs:sequence>` koleksiyon veri sözleşmesinin veri üyesini açıklayan bir içinde meydana gelebilir.</span><span class="sxs-lookup"><span data-stu-id="11b35-226">It can occur within an `<xs:sequence>`, which describes a data member of a collection data contract.</span></span> <span data-ttu-id="11b35-227">Bu durumda, `maxOccurs` öznitelik 1 veya "sınırsız" değerinden büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="11b35-227">In this case, the `maxOccurs` attribute must be greater than 1 or "unbounded".</span></span>

- <span data-ttu-id="11b35-228">Bu, bir `<xs:schema>` genel öğe bildirimi (şlı) olarak bir içinde gerçekleşebilir.</span><span class="sxs-lookup"><span data-stu-id="11b35-228">It can occur within an `<xs:schema>` as a Global Element Declaration (GED).</span></span>

### <a name="xselement-with-maxoccurs1-within-an-xssequence-data-members"></a><span data-ttu-id="11b35-229">\<xs:element>(veri üyeleri) içinde maxOccurs = 1 ile \<xs:sequence></span><span class="sxs-lookup"><span data-stu-id="11b35-229">\<xs:element> with maxOccurs=1 within an \<xs:sequence> (Data Members)</span></span>

|<span data-ttu-id="11b35-230">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="11b35-230">Attribute</span></span>|<span data-ttu-id="11b35-231">Şema</span><span class="sxs-lookup"><span data-stu-id="11b35-231">Schema</span></span>|
|---------------|------------|
|`ref`|<span data-ttu-id="11b35-232">Inı.</span><span class="sxs-lookup"><span data-stu-id="11b35-232">Forbidden.</span></span>|
|`name`|<span data-ttu-id="11b35-233">Desteklenir, veri üyesi adı ile eşlenir.</span><span class="sxs-lookup"><span data-stu-id="11b35-233">Supported, maps to the data member name.</span></span>|
|`type`|<span data-ttu-id="11b35-234">Desteklenir, veri üyesi türüyle eşlenir.</span><span class="sxs-lookup"><span data-stu-id="11b35-234">Supported, maps to the data member type.</span></span> <span data-ttu-id="11b35-235">Daha fazla bilgi için bkz. tür/temel öğe eşleme.</span><span class="sxs-lookup"><span data-stu-id="11b35-235">For more information, see Type/primitive mapping.</span></span> <span data-ttu-id="11b35-236">Belirtilmemişse (ve öğe anonim bir tür içermiyorsa) `xs:anyType` varsayılır.</span><span class="sxs-lookup"><span data-stu-id="11b35-236">If not specified (and the element does not contain an anonymous type), `xs:anyType` is assumed.</span></span>|
|`block`|<span data-ttu-id="11b35-237">LIP.</span><span class="sxs-lookup"><span data-stu-id="11b35-237">Ignored.</span></span>|
|`default`|<span data-ttu-id="11b35-238">Inı.</span><span class="sxs-lookup"><span data-stu-id="11b35-238">Forbidden.</span></span>|
|`fixed`|<span data-ttu-id="11b35-239">Inı.</span><span class="sxs-lookup"><span data-stu-id="11b35-239">Forbidden.</span></span>|
|`form`|<span data-ttu-id="11b35-240">Nitelenmiş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="11b35-240">Must be qualified.</span></span> <span data-ttu-id="11b35-241">Bu öznitelik, üzerinden ayarlanabilir `elementFormDefault` `xs:schema` .</span><span class="sxs-lookup"><span data-stu-id="11b35-241">This attribute can be set through `elementFormDefault` on `xs:schema`.</span></span>|
|`id`|<span data-ttu-id="11b35-242">LIP.</span><span class="sxs-lookup"><span data-stu-id="11b35-242">Ignored.</span></span>|
|`maxOccurs`|<span data-ttu-id="11b35-243">1</span><span class="sxs-lookup"><span data-stu-id="11b35-243">1</span></span>|
|`minOccurs`|<span data-ttu-id="11b35-244"><xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A>Bir veri üyesinin özelliğine eşlenir ( `IsRequired` 1 olduğunda doğru olur `minOccurs` ).</span><span class="sxs-lookup"><span data-stu-id="11b35-244">Maps to the <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> property of a data member (`IsRequired` is true when `minOccurs` is 1).</span></span>|
|`nillable`|<span data-ttu-id="11b35-245">Tür eşlemesini etkiler.</span><span class="sxs-lookup"><span data-stu-id="11b35-245">Affects type mapping.</span></span> <span data-ttu-id="11b35-246">Bkz. tür/temel eşleme.</span><span class="sxs-lookup"><span data-stu-id="11b35-246">See Type/primitive mapping.</span></span>|

### <a name="xselement-with-maxoccurs1-within-an-xssequence-collections"></a><span data-ttu-id="11b35-247">\<xs:element>(koleksiyonlar) içinde maxOccurs>1 ile \<xs:sequence></span><span class="sxs-lookup"><span data-stu-id="11b35-247">\<xs:element> with maxOccurs>1 within an \<xs:sequence> (Collections)</span></span>

- <span data-ttu-id="11b35-248">İle eşlenir <xref:System.Runtime.Serialization.CollectionDataContractAttribute> .</span><span class="sxs-lookup"><span data-stu-id="11b35-248">Maps to a <xref:System.Runtime.Serialization.CollectionDataContractAttribute>.</span></span>

- <span data-ttu-id="11b35-249">Koleksiyon türlerinde, xs: Sequence içinde yalnızca bir xs: element öğesine izin verilir.</span><span class="sxs-lookup"><span data-stu-id="11b35-249">In collection types, only one xs:element is allowed within an xs:sequence.</span></span>

 <span data-ttu-id="11b35-250">Koleksiyonlar aşağıdaki türlerde olabilir:</span><span class="sxs-lookup"><span data-stu-id="11b35-250">Collections can be of the following types:</span></span>

- <span data-ttu-id="11b35-251">Normal Koleksiyonlar (örneğin, diziler).</span><span class="sxs-lookup"><span data-stu-id="11b35-251">Regular collections (for example, arrays).</span></span>

- <span data-ttu-id="11b35-252">Sözlük koleksiyonları (bir değeri başka bir değerle eşleme; Örneğin, a <xref:System.Collections.Hashtable> ).</span><span class="sxs-lookup"><span data-stu-id="11b35-252">Dictionary collections (mapping one value to another; for example, a <xref:System.Collections.Hashtable>).</span></span>

- <span data-ttu-id="11b35-253">Bir sözlük ile anahtar/değer çifti türündeki bir dizi arasındaki tek fark, oluşturulan programlama modelidir.</span><span class="sxs-lookup"><span data-stu-id="11b35-253">The only difference between a dictionary and an array of a key/value pair type is in the generated programming model.</span></span> <span data-ttu-id="11b35-254">Belirli bir türün sözlük koleksiyonu olduğunu göstermek için kullanılabilecek bir şema ek açıklaması mekanizması vardır.</span><span class="sxs-lookup"><span data-stu-id="11b35-254">There is a schema annotation mechanism that can be used to indicate that a given type is a dictionary collection.</span></span>

<span data-ttu-id="11b35-255">,,,, `ref` `block` `default` Ve özniteliklerinin kuralları `fixed` , `form` `id` koleksiyon olmayan durum için ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="11b35-255">The rules for the `ref`, `block`, `default`, `fixed`, `form`, and `id` attributes are the same as for the non-collection case.</span></span> <span data-ttu-id="11b35-256">Diğer öznitelikler aşağıdaki tabloda yer alır.</span><span class="sxs-lookup"><span data-stu-id="11b35-256">Other attributes include those in the following table.</span></span>

|<span data-ttu-id="11b35-257">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="11b35-257">Attribute</span></span>|<span data-ttu-id="11b35-258">Şema</span><span class="sxs-lookup"><span data-stu-id="11b35-258">Schema</span></span>|
|---------------|------------|
|`name`|<span data-ttu-id="11b35-259">Desteklenir, <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> özniteliğinde özelliği ile eşlenir `CollectionDataContractAttribute` .</span><span class="sxs-lookup"><span data-stu-id="11b35-259">Supported, maps to the <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> property in the `CollectionDataContractAttribute` attribute.</span></span>|
|`type`|<span data-ttu-id="11b35-260">Desteklenir, koleksiyonda depolanan türle eşlenir.</span><span class="sxs-lookup"><span data-stu-id="11b35-260">Supported, maps to the type stored in the collection.</span></span>|
|`maxOccurs`|<span data-ttu-id="11b35-261">1 ' den büyük veya "sınırsız".</span><span class="sxs-lookup"><span data-stu-id="11b35-261">Greater than 1 or "unbounded".</span></span> <span data-ttu-id="11b35-262">DC şeması "sınırsız" kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="11b35-262">The DC schema should use "unbounded".</span></span>|
|`minOccurs`|<span data-ttu-id="11b35-263">LIP.</span><span class="sxs-lookup"><span data-stu-id="11b35-263">Ignored.</span></span>|
|`nillable`|<span data-ttu-id="11b35-264">Tür eşlemesini etkiler.</span><span class="sxs-lookup"><span data-stu-id="11b35-264">Affects type mapping.</span></span> <span data-ttu-id="11b35-265">Bu öznitelik, sözlük koleksiyonları için yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="11b35-265">This attribute is ignored for dictionary collections.</span></span>|

### <a name="xselement-within-an-xsschema-global-element-declaration"></a><span data-ttu-id="11b35-266">\<xs:element>genel bir \<xs:schema> öğe bildirimi içinde</span><span class="sxs-lookup"><span data-stu-id="11b35-266">\<xs:element> within an \<xs:schema> Global Element Declaration</span></span>

- <span data-ttu-id="11b35-267">Şemadaki bir türle aynı ada ve ad alanına sahip olan veya kendisi içinde anonim bir tür tanımlayan genel öğe bildirimi (ŞLı), türle ilişkili olarak söylenir.</span><span class="sxs-lookup"><span data-stu-id="11b35-267">A Global Element Declaration (GED) that has the same name and namespace as a type in schema, or that defines an anonymous type inside itself, is said to be associated with the type.</span></span>

- <span data-ttu-id="11b35-268">Şema dışarı aktarma: ilişkili GEDs, hem basit hem de karmaşık oluşturulan her tür için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="11b35-268">Schema export: associated GEDs are generated for every generated type, both simple and complex.</span></span>

- <span data-ttu-id="11b35-269">Seri durumdan çıkarma/serileştirme: ilişkili GEDs, tür için kök öğe olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="11b35-269">Deserialization/serialization: associated GEDs are used as root elements for the type.</span></span>

- <span data-ttu-id="11b35-270">Şema içeri aktarma: ilişkili GEDs 'ler gerekli değildir ve aşağıdaki kurallara uyar (türleri tanımladıkça).</span><span class="sxs-lookup"><span data-stu-id="11b35-270">Schema import: associated GEDs are not required and are ignored if they follow the following rules (unless they define types).</span></span>

|<span data-ttu-id="11b35-271">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="11b35-271">Attribute</span></span>|<span data-ttu-id="11b35-272">Şema</span><span class="sxs-lookup"><span data-stu-id="11b35-272">Schema</span></span>|
|---------------|------------|
|`abstract`|<span data-ttu-id="11b35-273">İlişkili GEDs 'ler için false olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="11b35-273">Must be false for associated GEDs.</span></span>|
|`block`|<span data-ttu-id="11b35-274">İlişkili GEDs 'de yasak.</span><span class="sxs-lookup"><span data-stu-id="11b35-274">Forbidden in associated GEDs.</span></span>|
|`default`|<span data-ttu-id="11b35-275">İlişkili GEDs 'de yasak.</span><span class="sxs-lookup"><span data-stu-id="11b35-275">Forbidden in associated GEDs.</span></span>|
|`final`|<span data-ttu-id="11b35-276">İlişkili GEDs 'ler için false olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="11b35-276">Must be false for associated GEDs.</span></span>|
|`fixed`|<span data-ttu-id="11b35-277">İlişkili GEDs 'de yasak.</span><span class="sxs-lookup"><span data-stu-id="11b35-277">Forbidden in associated GEDs.</span></span>|
|`id`|<span data-ttu-id="11b35-278">LIP.</span><span class="sxs-lookup"><span data-stu-id="11b35-278">Ignored.</span></span>|
|`name`|<span data-ttu-id="11b35-279">Destekleniyor.</span><span class="sxs-lookup"><span data-stu-id="11b35-279">Supported.</span></span> <span data-ttu-id="11b35-280">İlişkili GEDs tanımına bakın.</span><span class="sxs-lookup"><span data-stu-id="11b35-280">See the definition of associated GEDs.</span></span>|
|`nillable`|<span data-ttu-id="11b35-281">İlişkili GEDs 'ler için doğru olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="11b35-281">Must be true for associated GEDs.</span></span>|
|`substitutionGroup`|<span data-ttu-id="11b35-282">İlişkili GEDs 'de yasak.</span><span class="sxs-lookup"><span data-stu-id="11b35-282">Forbidden in associated GEDs.</span></span>|
|`type`|<span data-ttu-id="11b35-283">Desteklenir ve ilişkili GEDs için ilişkili tür ile eşleşmelidir (öğe anonim bir tür içermiyorsa).</span><span class="sxs-lookup"><span data-stu-id="11b35-283">Supported, and must match the associated type for associated GEDs (unless the element contains an anonymous type).</span></span>|

### <a name="xselement-contents"></a><span data-ttu-id="11b35-284">\<xs:element>: içerik</span><span class="sxs-lookup"><span data-stu-id="11b35-284">\<xs:element>: contents</span></span>

|<span data-ttu-id="11b35-285">İçindekiler</span><span class="sxs-lookup"><span data-stu-id="11b35-285">Contents</span></span>|<span data-ttu-id="11b35-286">Şema</span><span class="sxs-lookup"><span data-stu-id="11b35-286">Schema</span></span>|
|--------------|------------|
|`simpleType`|<span data-ttu-id="11b35-287">Desteklenir. \*</span><span class="sxs-lookup"><span data-stu-id="11b35-287">Supported.\*</span></span>|
|`complexType`|<span data-ttu-id="11b35-288">Desteklenir. \*</span><span class="sxs-lookup"><span data-stu-id="11b35-288">Supported.\*</span></span>|
|`unique`|<span data-ttu-id="11b35-289">LIP.</span><span class="sxs-lookup"><span data-stu-id="11b35-289">Ignored.</span></span>|
|`key`|<span data-ttu-id="11b35-290">LIP.</span><span class="sxs-lookup"><span data-stu-id="11b35-290">Ignored.</span></span>|
|`keyref`|<span data-ttu-id="11b35-291">LIP.</span><span class="sxs-lookup"><span data-stu-id="11b35-291">Ignored.</span></span>|
|<span data-ttu-id="11b35-292">adet</span><span class="sxs-lookup"><span data-stu-id="11b35-292">(blank)</span></span>|<span data-ttu-id="11b35-293">Destekleniyor.</span><span class="sxs-lookup"><span data-stu-id="11b35-293">Supported.</span></span>|

<span data-ttu-id="11b35-294">\*Anonim `simpleType` `complexType,` türler için ve eşlemesini kullandığınızda anonim olmayan türler için aynı, anonim veri sözleşmeleri olmaması dışında, adlandırılmış bir veri sözleşmesinin oluşturulduğu ve öğe adından türetilmiş oluşturulmuş bir adla aynı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="11b35-294">\* When using the `simpleType` and `complexType,` mapping for anonymous types is the same as for non-anonymous types, except that there is no anonymous data contracts, and so a named data contract is created, with a generated name derived from the element name.</span></span> <span data-ttu-id="11b35-295">Anonim türlerin kuralları aşağıdaki listede verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="11b35-295">The rules for anonymous types are in the following list:</span></span>

- <span data-ttu-id="11b35-296">WCF uygulama ayrıntısı: `xs:element` ad nokta içermiyorsa, anonim tür dış veri sözleşmesi türünün bir iç türüyle eşlenir.</span><span class="sxs-lookup"><span data-stu-id="11b35-296">WCF implementation detail: If the `xs:element` name does not contain periods, the anonymous type maps to an inner type of the outer data contract type.</span></span> <span data-ttu-id="11b35-297">Ad nokta içeriyorsa, sonuçta elde edilen veri anlaşması türü bağımsızdır (bir iç tür değildir).</span><span class="sxs-lookup"><span data-stu-id="11b35-297">If the name contains periods, the resulting data contract type is independent (not an inner type).</span></span>

- <span data-ttu-id="11b35-298">İç türün üretilen veri sözleşme adı, dış türün veri sözleşmesinin adı ve ardından bir nokta, öğenin adı ve "tür" dizesi gelir.</span><span class="sxs-lookup"><span data-stu-id="11b35-298">The generated data contract name of the inner type is the data contract name of the outer type followed by a period, the name of the element, and the string "Type".</span></span>

- <span data-ttu-id="11b35-299">Böyle bir ada sahip bir veri sözleşmesi zaten varsa, benzersiz bir ad oluşturuluncaya kadar "1", "2", "3" vb. eklenerek ad benzersiz hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="11b35-299">If a data contract with such a name already exists, the name is made unique by appending "1", "2", "3", and so on until a unique name is created.</span></span>

## <a name="simple-types---xssimpletype"></a><span data-ttu-id="11b35-300">Basit türler-\<xs:simpleType></span><span class="sxs-lookup"><span data-stu-id="11b35-300">Simple Types - \<xs:simpleType></span></span>

### <a name="xssimpletype-attributes"></a><span data-ttu-id="11b35-301">\<xs:simpleType>: öznitelikler</span><span class="sxs-lookup"><span data-stu-id="11b35-301">\<xs:simpleType>: attributes</span></span>

|<span data-ttu-id="11b35-302">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="11b35-302">Attribute</span></span>|<span data-ttu-id="11b35-303">Şema</span><span class="sxs-lookup"><span data-stu-id="11b35-303">Schema</span></span>|
|---------------|------------|
|`final`|<span data-ttu-id="11b35-304">LIP.</span><span class="sxs-lookup"><span data-stu-id="11b35-304">Ignored.</span></span>|
|`id`|<span data-ttu-id="11b35-305">LIP.</span><span class="sxs-lookup"><span data-stu-id="11b35-305">Ignored.</span></span>|
|`name`|<span data-ttu-id="11b35-306">Desteklenir, veri sözleşmesi adıyla eşlenir.</span><span class="sxs-lookup"><span data-stu-id="11b35-306">Supported, maps to the data contract name.</span></span>|

### <a name="xssimpletype-contents"></a><span data-ttu-id="11b35-307">\<xs:simpleType>: içerik</span><span class="sxs-lookup"><span data-stu-id="11b35-307">\<xs:simpleType>: contents</span></span>

|<span data-ttu-id="11b35-308">İçindekiler</span><span class="sxs-lookup"><span data-stu-id="11b35-308">Contents</span></span>|<span data-ttu-id="11b35-309">Şema</span><span class="sxs-lookup"><span data-stu-id="11b35-309">Schema</span></span>|
|--------------|------------|
|`restriction`|<span data-ttu-id="11b35-310">Destekleniyor.</span><span class="sxs-lookup"><span data-stu-id="11b35-310">Supported.</span></span> <span data-ttu-id="11b35-311">Sabit listesi veri sözleşmeleri ile eşlenir.</span><span class="sxs-lookup"><span data-stu-id="11b35-311">Maps to enumeration data contracts.</span></span> <span data-ttu-id="11b35-312">Bu öznitelik, numaralandırma düzeniyle eşleşmezse yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="11b35-312">This attribute is ignored if it does not match the enumeration pattern.</span></span> <span data-ttu-id="11b35-313">`xs:simpleType`Kısıtlamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="11b35-313">See the `xs:simpleType` restrictions section.</span></span>|
|`list`|<span data-ttu-id="11b35-314">Destekleniyor.</span><span class="sxs-lookup"><span data-stu-id="11b35-314">Supported.</span></span> <span data-ttu-id="11b35-315">Bayrak sıralama veri sözleşmeleri ile eşlenir.</span><span class="sxs-lookup"><span data-stu-id="11b35-315">Maps to flag enumeration data contracts.</span></span> <span data-ttu-id="11b35-316">`xs:simpleType`Listeler bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="11b35-316">See the `xs:simpleType` lists section.</span></span>|
|`union`|<span data-ttu-id="11b35-317">Inı.</span><span class="sxs-lookup"><span data-stu-id="11b35-317">Forbidden.</span></span>|

### \<xs:restriction>

- <span data-ttu-id="11b35-318">Karmaşık tür kısıtlamaları yalnızca Base = "" için desteklenir `xs:anyType` .</span><span class="sxs-lookup"><span data-stu-id="11b35-318">Complex type restrictions are supported only for base="`xs:anyType`".</span></span>

- <span data-ttu-id="11b35-319">' Nin farklı kısıtlama modelleri bulunmayan basit tür kısıtlamaları, `xs:string` `xs:enumeration` sabit listesi veri sözleşmeleri ile eşleştirilir.</span><span class="sxs-lookup"><span data-stu-id="11b35-319">Simple type restrictions of `xs:string` that do not have any restriction facets other than `xs:enumeration` are mapped to enumeration data contracts.</span></span>

- <span data-ttu-id="11b35-320">Diğer tüm basit tür kısıtlamaları, kısıttıkları türlere eşlenir.</span><span class="sxs-lookup"><span data-stu-id="11b35-320">All other simple type restrictions are mapped to the types they restrict.</span></span> <span data-ttu-id="11b35-321">Örneğin, `xs:int` tam olarak olduğu gibi, bir tamsayı ile eşleme kısıtlaması `xs:int` .</span><span class="sxs-lookup"><span data-stu-id="11b35-321">For example, a restriction of `xs:int` maps to an integer, just as `xs:int` itself does.</span></span> <span data-ttu-id="11b35-322">İlkel tür eşlemesi hakkında daha fazla bilgi için bkz. tür/temel eşleme.</span><span class="sxs-lookup"><span data-stu-id="11b35-322">For more information about primitive type mapping, see Type/primitive mapping.</span></span>

### <a name="xsrestriction-attributes"></a><span data-ttu-id="11b35-323">\<xs:restriction>: öznitelikler</span><span class="sxs-lookup"><span data-stu-id="11b35-323">\<xs:restriction>: attributes</span></span>

|<span data-ttu-id="11b35-324">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="11b35-324">Attribute</span></span>|<span data-ttu-id="11b35-325">Şema</span><span class="sxs-lookup"><span data-stu-id="11b35-325">Schema</span></span>|
|---------------|------------|
|`base`|<span data-ttu-id="11b35-326">Desteklenen bir basit tür veya olmalıdır `xs:anyType` .</span><span class="sxs-lookup"><span data-stu-id="11b35-326">Must be a supported simple type or `xs:anyType`.</span></span>|
|`id`|<span data-ttu-id="11b35-327">LIP.</span><span class="sxs-lookup"><span data-stu-id="11b35-327">Ignored.</span></span>|

### <a name="xsrestriction-for-all-other-cases-contents"></a><span data-ttu-id="11b35-328">\<xs:restriction>diğer tüm durumlar için: içerikler</span><span class="sxs-lookup"><span data-stu-id="11b35-328">\<xs:restriction> for all other cases: contents</span></span>

|<span data-ttu-id="11b35-329">İçindekiler</span><span class="sxs-lookup"><span data-stu-id="11b35-329">Contents</span></span>|<span data-ttu-id="11b35-330">Şema</span><span class="sxs-lookup"><span data-stu-id="11b35-330">Schema</span></span>|
|--------------|------------|
|`simpleType`|<span data-ttu-id="11b35-331">Varsa, desteklenen bir temel türden türetilmiş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="11b35-331">If present, must be derived from a supported primitive type.</span></span>|
|`minExclusive`|<span data-ttu-id="11b35-332">LIP.</span><span class="sxs-lookup"><span data-stu-id="11b35-332">Ignored.</span></span>|
|`minInclusive`|<span data-ttu-id="11b35-333">LIP.</span><span class="sxs-lookup"><span data-stu-id="11b35-333">Ignored.</span></span>|
|`maxExclusive`|<span data-ttu-id="11b35-334">LIP.</span><span class="sxs-lookup"><span data-stu-id="11b35-334">Ignored.</span></span>|
|`maxInclusive`|<span data-ttu-id="11b35-335">LIP.</span><span class="sxs-lookup"><span data-stu-id="11b35-335">Ignored.</span></span>|
|`totalDigits`|<span data-ttu-id="11b35-336">LIP.</span><span class="sxs-lookup"><span data-stu-id="11b35-336">Ignored.</span></span>|
|`fractionDigits`|<span data-ttu-id="11b35-337">LIP.</span><span class="sxs-lookup"><span data-stu-id="11b35-337">Ignored.</span></span>|
|`length`|<span data-ttu-id="11b35-338">LIP.</span><span class="sxs-lookup"><span data-stu-id="11b35-338">Ignored.</span></span>|
|`minLength`|<span data-ttu-id="11b35-339">LIP.</span><span class="sxs-lookup"><span data-stu-id="11b35-339">Ignored.</span></span>|
|`maxLength`|<span data-ttu-id="11b35-340">LIP.</span><span class="sxs-lookup"><span data-stu-id="11b35-340">Ignored.</span></span>|
|`enumeration`|<span data-ttu-id="11b35-341">LIP.</span><span class="sxs-lookup"><span data-stu-id="11b35-341">Ignored.</span></span>|
|`whiteSpace`|<span data-ttu-id="11b35-342">LIP.</span><span class="sxs-lookup"><span data-stu-id="11b35-342">Ignored.</span></span>|
|`pattern`|<span data-ttu-id="11b35-343">LIP.</span><span class="sxs-lookup"><span data-stu-id="11b35-343">Ignored.</span></span>|
|<span data-ttu-id="11b35-344">adet</span><span class="sxs-lookup"><span data-stu-id="11b35-344">(blank)</span></span>|<span data-ttu-id="11b35-345">Destekleniyor.</span><span class="sxs-lookup"><span data-stu-id="11b35-345">Supported.</span></span>|

## <a name="enumeration"></a><span data-ttu-id="11b35-346">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="11b35-346">Enumeration</span></span>

### <a name="xsrestriction-for-enumerations-attributes"></a><span data-ttu-id="11b35-347">\<xs:restriction>Numaralandırmalar için: öznitelikler</span><span class="sxs-lookup"><span data-stu-id="11b35-347">\<xs:restriction> for enumerations: attributes</span></span>

|<span data-ttu-id="11b35-348">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="11b35-348">Attribute</span></span>|<span data-ttu-id="11b35-349">Şema</span><span class="sxs-lookup"><span data-stu-id="11b35-349">Schema</span></span>|
|---------------|------------|
|`base`|<span data-ttu-id="11b35-350">Varsa, olmalıdır `xs:string` .</span><span class="sxs-lookup"><span data-stu-id="11b35-350">If present, must be `xs:string`.</span></span>|
|`id`|<span data-ttu-id="11b35-351">LIP.</span><span class="sxs-lookup"><span data-stu-id="11b35-351">Ignored.</span></span>|

### <a name="xsrestriction-for-enumerations-contents"></a><span data-ttu-id="11b35-352">\<xs:restriction>Numaralandırmalar için: içerikler</span><span class="sxs-lookup"><span data-stu-id="11b35-352">\<xs:restriction> for enumerations: contents</span></span>

|<span data-ttu-id="11b35-353">İçindekiler</span><span class="sxs-lookup"><span data-stu-id="11b35-353">Contents</span></span>|<span data-ttu-id="11b35-354">Şema</span><span class="sxs-lookup"><span data-stu-id="11b35-354">Schema</span></span>|
|--------------|------------|
|`simpleType`|<span data-ttu-id="11b35-355">Varsa, veri anlaşması (Bu bölüm) tarafından desteklenen bir numaralandırma kısıtlaması olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="11b35-355">If present, must be an enumeration restriction supported by the data contract (this section).</span></span>|
|`minExclusive`|<span data-ttu-id="11b35-356">LIP.</span><span class="sxs-lookup"><span data-stu-id="11b35-356">Ignored.</span></span>|
|`minInclusive`|<span data-ttu-id="11b35-357">LIP.</span><span class="sxs-lookup"><span data-stu-id="11b35-357">Ignored.</span></span>|
|`maxExclusive`|<span data-ttu-id="11b35-358">LIP.</span><span class="sxs-lookup"><span data-stu-id="11b35-358">Ignored.</span></span>|
|`maxInclusive`|<span data-ttu-id="11b35-359">LIP.</span><span class="sxs-lookup"><span data-stu-id="11b35-359">Ignored.</span></span>|
|`totalDigits`|<span data-ttu-id="11b35-360">LIP.</span><span class="sxs-lookup"><span data-stu-id="11b35-360">Ignored.</span></span>|
|`fractionDigits`|<span data-ttu-id="11b35-361">LIP.</span><span class="sxs-lookup"><span data-stu-id="11b35-361">Ignored.</span></span>|
|`length`|<span data-ttu-id="11b35-362">Inı.</span><span class="sxs-lookup"><span data-stu-id="11b35-362">Forbidden.</span></span>|
|`minLength`|<span data-ttu-id="11b35-363">Inı.</span><span class="sxs-lookup"><span data-stu-id="11b35-363">Forbidden.</span></span>|
|`maxLength`|<span data-ttu-id="11b35-364">Inı.</span><span class="sxs-lookup"><span data-stu-id="11b35-364">Forbidden.</span></span>|
|`enumeration`|<span data-ttu-id="11b35-365">Destekleniyor.</span><span class="sxs-lookup"><span data-stu-id="11b35-365">Supported.</span></span> <span data-ttu-id="11b35-366">"Kimlik" numaralandırması yok sayılır ve "değer" sabit listesi veri sözleşmesindeki değer adıyla eşlenir.</span><span class="sxs-lookup"><span data-stu-id="11b35-366">Enumeration "id" is ignored, and "value" maps to the value name in the enumeration data contract.</span></span>|
|`whiteSpace`|<span data-ttu-id="11b35-367">Inı.</span><span class="sxs-lookup"><span data-stu-id="11b35-367">Forbidden.</span></span>|
|`pattern`|<span data-ttu-id="11b35-368">Inı.</span><span class="sxs-lookup"><span data-stu-id="11b35-368">Forbidden.</span></span>|
|<span data-ttu-id="11b35-369">olmamalıdır</span><span class="sxs-lookup"><span data-stu-id="11b35-369">(empty)</span></span>|<span data-ttu-id="11b35-370">Desteklenir, boş sabit listesi türüne eşlenir.</span><span class="sxs-lookup"><span data-stu-id="11b35-370">Supported, maps to empty enumeration type.</span></span>|

 <span data-ttu-id="11b35-371">Aşağıdaki kod bir C# numaralandırma sınıfını gösterir.</span><span class="sxs-lookup"><span data-stu-id="11b35-371">The following code shows a C# enumeration class.</span></span>

```csharp
public enum MyEnum
{
  first = 3,
  second = 4,
  third =5
}
```

<span data-ttu-id="11b35-372">Bu sınıf, tarafından aşağıdaki şemaya eşlenir `DataContractSerializer` .</span><span class="sxs-lookup"><span data-stu-id="11b35-372">This class maps to the following schema by the `DataContractSerializer`.</span></span> <span data-ttu-id="11b35-373">Numaralandırma değerleri 1 ' den başlar, `xs:annotation` bloklar oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="11b35-373">If enumeration values start from 1, `xs:annotation` blocks are not generated.</span></span>

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

### \<xs:list>

<span data-ttu-id="11b35-374">`DataContractSerializer`ile işaretlenmiş numaralandırma türlerini `System.FlagsAttribute` `xs:list` öğesinden türetilmişle eşleştirir `xs:string` .</span><span class="sxs-lookup"><span data-stu-id="11b35-374">`DataContractSerializer` maps enumeration types marked with `System.FlagsAttribute` to `xs:list` derived from `xs:string`.</span></span> <span data-ttu-id="11b35-375">Başka `xs:list` Çeşitlemeler desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="11b35-375">No other `xs:list` variations are supported.</span></span>

### <a name="xslist-attributes"></a><span data-ttu-id="11b35-376">\<xs:list>: öznitelikler</span><span class="sxs-lookup"><span data-stu-id="11b35-376">\<xs:list>: attributes</span></span>

|<span data-ttu-id="11b35-377">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="11b35-377">Attribute</span></span>|<span data-ttu-id="11b35-378">Şema</span><span class="sxs-lookup"><span data-stu-id="11b35-378">Schema</span></span>|
|---------------|------------|
|`itemType`|<span data-ttu-id="11b35-379">Inı.</span><span class="sxs-lookup"><span data-stu-id="11b35-379">Forbidden.</span></span>|
|`id`|<span data-ttu-id="11b35-380">LIP.</span><span class="sxs-lookup"><span data-stu-id="11b35-380">Ignored.</span></span>|

### <a name="xslist-contents"></a><span data-ttu-id="11b35-381">\<xs:list>: içerik</span><span class="sxs-lookup"><span data-stu-id="11b35-381">\<xs:list>: contents</span></span>

|<span data-ttu-id="11b35-382">İçindekiler</span><span class="sxs-lookup"><span data-stu-id="11b35-382">Contents</span></span>|<span data-ttu-id="11b35-383">Şema</span><span class="sxs-lookup"><span data-stu-id="11b35-383">Schema</span></span>|
|--------------|------------|
|`simpleType`|<span data-ttu-id="11b35-384">Modelinin kullanım kısıtlaması olmalıdır `xs:string` `xs:enumeration` .</span><span class="sxs-lookup"><span data-stu-id="11b35-384">Must be restriction from `xs:string` using `xs:enumeration` facet.</span></span>|

<span data-ttu-id="11b35-385">Sabit listesi değeri 2 ilerleme değerinin (bayraklar için varsayılan) bir kuvvetle eşleşmezse, değer `xs:annotation/xs:appInfo/ser:EnumerationValue` öğesinde depolanır.</span><span class="sxs-lookup"><span data-stu-id="11b35-385">If enumeration value does not follow a power of 2 progression (default for Flags), the value is stored in the `xs:annotation/xs:appInfo/ser:EnumerationValue` element.</span></span>

<span data-ttu-id="11b35-386">Örneğin, aşağıdaki kod bir numaralandırma türünü bayraklar.</span><span class="sxs-lookup"><span data-stu-id="11b35-386">For example, the following code flags an enumeration type.</span></span>

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

<span data-ttu-id="11b35-387">Bu tür aşağıdaki şemaya eşlenir.</span><span class="sxs-lookup"><span data-stu-id="11b35-387">This type maps to the following schema.</span></span>

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

## <a name="inheritance"></a><span data-ttu-id="11b35-388">Devralma</span><span class="sxs-lookup"><span data-stu-id="11b35-388">Inheritance</span></span>

### <a name="general-rules"></a><span data-ttu-id="11b35-389">Genel kurallar</span><span class="sxs-lookup"><span data-stu-id="11b35-389">General rules</span></span>

<span data-ttu-id="11b35-390">Bir veri sözleşmesi, başka bir veri sözleşmesinden devralınabilir.</span><span class="sxs-lookup"><span data-stu-id="11b35-390">A data contract can inherit from another data contract.</span></span> <span data-ttu-id="11b35-391">Bu tür veri sözleşmeleri bir temel ile eşlenir ve XML şema yapısı kullanılarak uzantı türlerine göre türetilir `<xs:extension>` .</span><span class="sxs-lookup"><span data-stu-id="11b35-391">Such data contracts map to a base and are derived by extension types using the `<xs:extension>` XML Schema construct.</span></span>

<span data-ttu-id="11b35-392">Veri sözleşmesi bir koleksiyon veri sözleşmesinden devralınabilir.</span><span class="sxs-lookup"><span data-stu-id="11b35-392">A data contract cannot inherit from a collection data contract.</span></span>

<span data-ttu-id="11b35-393">Örneğin, aşağıdaki kod bir veri sözleşmedir.</span><span class="sxs-lookup"><span data-stu-id="11b35-393">For example, the following code is a data contract.</span></span>

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

<span data-ttu-id="11b35-394">Bu veri sözleşmesi, aşağıdaki XML Şeması tür bildirimiyle eşlenir.</span><span class="sxs-lookup"><span data-stu-id="11b35-394">This data contract maps to the following XML Schema type declaration.</span></span>

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

### <a name="xscomplexcontent-attributes"></a><span data-ttu-id="11b35-395">\<xs:complexContent>: öznitelikler</span><span class="sxs-lookup"><span data-stu-id="11b35-395">\<xs:complexContent>: attributes</span></span>

|<span data-ttu-id="11b35-396">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="11b35-396">Attribute</span></span>|<span data-ttu-id="11b35-397">Şema</span><span class="sxs-lookup"><span data-stu-id="11b35-397">Schema</span></span>|
|---------------|------------|
|`id`|<span data-ttu-id="11b35-398">LIP.</span><span class="sxs-lookup"><span data-stu-id="11b35-398">Ignored.</span></span>|
|`mixed`|<span data-ttu-id="11b35-399">False olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="11b35-399">Must be false.</span></span>|

### <a name="xscomplexcontent-contents"></a><span data-ttu-id="11b35-400">\<xs:complexContent>: içerik</span><span class="sxs-lookup"><span data-stu-id="11b35-400">\<xs:complexContent>: contents</span></span>

|<span data-ttu-id="11b35-401">İçindekiler</span><span class="sxs-lookup"><span data-stu-id="11b35-401">Contents</span></span>|<span data-ttu-id="11b35-402">Şema</span><span class="sxs-lookup"><span data-stu-id="11b35-402">Schema</span></span>|
|--------------|------------|
|`restriction`|<span data-ttu-id="11b35-403">Yasak, temel = "" dışında `xs:anyType` .</span><span class="sxs-lookup"><span data-stu-id="11b35-403">Forbidden, except when base="`xs:anyType`".</span></span> <span data-ttu-id="11b35-404">İkincisi, öğesinin içeriğini `xs:restriction` doğrudan kapsayıcısının altına yerleştirmeye eşdeğerdir `xs:complexContent` .</span><span class="sxs-lookup"><span data-stu-id="11b35-404">The latter is equivalent to placing the content of the `xs:restriction` directly under the container of the `xs:complexContent`.</span></span>|
|`extension`|<span data-ttu-id="11b35-405">Destekleniyor.</span><span class="sxs-lookup"><span data-stu-id="11b35-405">Supported.</span></span> <span data-ttu-id="11b35-406">Veri sözleşmesi devralmayla eşlenir.</span><span class="sxs-lookup"><span data-stu-id="11b35-406">Maps to data contract inheritance.</span></span>|

### <a name="xsextension-in-xscomplexcontent-attributes"></a><span data-ttu-id="11b35-407">\<xs:extension>içinde \<xs:complexContent> : öznitelikler</span><span class="sxs-lookup"><span data-stu-id="11b35-407">\<xs:extension> in \<xs:complexContent>: attributes</span></span>

|<span data-ttu-id="11b35-408">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="11b35-408">Attribute</span></span>|<span data-ttu-id="11b35-409">Şema</span><span class="sxs-lookup"><span data-stu-id="11b35-409">Schema</span></span>|
|---------------|------------|
|`id`|<span data-ttu-id="11b35-410">LIP.</span><span class="sxs-lookup"><span data-stu-id="11b35-410">Ignored.</span></span>|
|`base`|<span data-ttu-id="11b35-411">Destekleniyor.</span><span class="sxs-lookup"><span data-stu-id="11b35-411">Supported.</span></span> <span data-ttu-id="11b35-412">Bu türün devraldığı temel veri sözleşmesi türüyle eşlenir.</span><span class="sxs-lookup"><span data-stu-id="11b35-412">Maps to the base data contract type that this type inherits from.</span></span>|

### <a name="xsextension-in-xscomplexcontent-contents"></a><span data-ttu-id="11b35-413">\<xs:extension>içinde \<xs:complexContent> : içerik</span><span class="sxs-lookup"><span data-stu-id="11b35-413">\<xs:extension> in \<xs:complexContent>: contents</span></span>

<span data-ttu-id="11b35-414">Kurallar, içerik için ile aynıdır `<xs:complexType>` .</span><span class="sxs-lookup"><span data-stu-id="11b35-414">The rules are the same as for `<xs:complexType>` contents.</span></span>

<span data-ttu-id="11b35-415">Bir `<xs:sequence>` sağlanmışsa, üye öğeleri türetilmiş veri sözleşmesindeki diğer veri üyeleriyle eşlenir.</span><span class="sxs-lookup"><span data-stu-id="11b35-415">If an `<xs:sequence>` is provided, its member elements map to additional data members that are present in the derived data contract.</span></span>

<span data-ttu-id="11b35-416">Türetilmiş bir tür, temel türdeki bir öğeyle aynı ada sahip bir öğe içeriyorsa, yinelenen öğe bildirimi benzersiz olması için oluşturulan bir adla veri üyesine eşlenir.</span><span class="sxs-lookup"><span data-stu-id="11b35-416">If a derived type contains an element with the same name as an element in a base type, the duplicate element declaration maps to a data member with a name that is generated to be unique.</span></span> <span data-ttu-id="11b35-417">Benzersiz bir ad bulunana kadar ("member1", "member2" vb.) veri üyesi adına pozitif tamsayı numaraları eklenir.</span><span class="sxs-lookup"><span data-stu-id="11b35-417">Positive integer numbers are added to the data member name ("member1", "member2", and so on) until a unique name is found.</span></span> <span data-ttu-id="11b35-418">Buna karşılık</span><span class="sxs-lookup"><span data-stu-id="11b35-418">Conversely:</span></span>

- <span data-ttu-id="11b35-419">Türetilmiş bir veri sözleşmesinin, temel veri sözleşmesindeki bir veri üyesi ile aynı ada ve türe sahip bir veri üyesi varsa, `DataContractSerializer` Bu ilgili öğeyi türetilmiş tür içinde oluşturur.</span><span class="sxs-lookup"><span data-stu-id="11b35-419">If a derived data contract has a data member with the same name and type as a data member in a base data contract, `DataContractSerializer` generates this corresponding element in the derived type.</span></span>

- <span data-ttu-id="11b35-420">Türetilmiş bir veri sözleşmesinin, temel veri sözleşmesindeki bir veri üyesi ile aynı ada sahip bir veri üyesi, ancak farklı bir tür varsa, bu, `DataContractSerializer` `xs:anyType` hem temel türdeki hem de türetilmiş tür bildirimlerinde türü bir olan bir şemayı içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="11b35-420">If a derived data contract has a data member with the same name as a data member in a base data contract but a different type, the `DataContractSerializer` imports a schema with an element of the type `xs:anyType` in both base type and derived type declarations.</span></span> <span data-ttu-id="11b35-421">Özgün tür adı ' de korunur `xs:annotations/xs:appInfo/ser:ActualType/@Name` .</span><span class="sxs-lookup"><span data-stu-id="11b35-421">The original type name is preserved in `xs:annotations/xs:appInfo/ser:ActualType/@Name`.</span></span>

<span data-ttu-id="11b35-422">Her iki çeşitleme de, ilgili veri üyelerinin sırasına bağlı olarak belirsiz bir içerik modeli olan bir şemaya neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="11b35-422">Both variations may lead to a schema with an ambiguous content model, which depends on the order of the respective data members.</span></span>

## <a name="typeprimitive-mapping"></a><span data-ttu-id="11b35-423">Tür/basit eşleme</span><span class="sxs-lookup"><span data-stu-id="11b35-423">Type/primitive mapping</span></span>

<span data-ttu-id="11b35-424">, `DataContractSerializer` XML şeması temel türleri için aşağıdaki eşlemeyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="11b35-424">The `DataContractSerializer` uses the following mapping for XML Schema primitive types.</span></span>

|<span data-ttu-id="11b35-425">XSD türü</span><span class="sxs-lookup"><span data-stu-id="11b35-425">XSD type</span></span>|<span data-ttu-id="11b35-426">.NET türü</span><span class="sxs-lookup"><span data-stu-id="11b35-426">.NET type</span></span>|
|--------------|---------------|
|`anyType`|<span data-ttu-id="11b35-427"><xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="11b35-427"><xref:System.Object>.</span></span>|
|`anySimpleType`|<span data-ttu-id="11b35-428"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="11b35-428"><xref:System.String>.</span></span>|
|`duration`|<span data-ttu-id="11b35-429"><xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="11b35-429"><xref:System.TimeSpan>.</span></span>|
|`dateTime`|<span data-ttu-id="11b35-430"><xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="11b35-430"><xref:System.DateTime>.</span></span>|
|`dateTimeOffset`|<span data-ttu-id="11b35-431"><xref:System.DateTime>ve <xref:System.TimeSpan> daha fazla.</span><span class="sxs-lookup"><span data-stu-id="11b35-431"><xref:System.DateTime> and <xref:System.TimeSpan> for the offset.</span></span> <span data-ttu-id="11b35-432">Aşağıdaki DateTimeOffset serileştirme ' i inceleyin.</span><span class="sxs-lookup"><span data-stu-id="11b35-432">See DateTimeOffset Serialization below.</span></span>|
|`time`|<span data-ttu-id="11b35-433"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="11b35-433"><xref:System.String>.</span></span>|
|`date`|<span data-ttu-id="11b35-434"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="11b35-434"><xref:System.String>.</span></span>|
|`gYearMonth`|<span data-ttu-id="11b35-435"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="11b35-435"><xref:System.String>.</span></span>|
|`gYear`|<span data-ttu-id="11b35-436"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="11b35-436"><xref:System.String>.</span></span>|
|`gMonthDay`|<span data-ttu-id="11b35-437"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="11b35-437"><xref:System.String>.</span></span>|
|`gDay`|<span data-ttu-id="11b35-438"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="11b35-438"><xref:System.String>.</span></span>|
|`gMonth`|<span data-ttu-id="11b35-439"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="11b35-439"><xref:System.String>.</span></span>|
|`boolean`|<xref:System.Boolean>|
|`base64Binary`|<span data-ttu-id="11b35-440"><xref:System.Byte>dizide.</span><span class="sxs-lookup"><span data-stu-id="11b35-440"><xref:System.Byte> array.</span></span>|
|`hexBinary`|<span data-ttu-id="11b35-441"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="11b35-441"><xref:System.String>.</span></span>|
|`float`|<span data-ttu-id="11b35-442"><xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="11b35-442"><xref:System.Single>.</span></span>|
|`double`|<span data-ttu-id="11b35-443"><xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="11b35-443"><xref:System.Double>.</span></span>|
|`anyURI`|<span data-ttu-id="11b35-444"><xref:System.Uri>.</span><span class="sxs-lookup"><span data-stu-id="11b35-444"><xref:System.Uri>.</span></span>|
|`QName`|<span data-ttu-id="11b35-445"><xref:System.Xml.XmlQualifiedName>.</span><span class="sxs-lookup"><span data-stu-id="11b35-445"><xref:System.Xml.XmlQualifiedName>.</span></span>|
|`string`|<span data-ttu-id="11b35-446"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="11b35-446"><xref:System.String>.</span></span>|
|`normalizedString`|<span data-ttu-id="11b35-447"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="11b35-447"><xref:System.String>.</span></span>|
|`token`|<span data-ttu-id="11b35-448"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="11b35-448"><xref:System.String>.</span></span>|
|`language`|<span data-ttu-id="11b35-449"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="11b35-449"><xref:System.String>.</span></span>|
|`Name`|<span data-ttu-id="11b35-450"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="11b35-450"><xref:System.String>.</span></span>|
|`NCName`|<span data-ttu-id="11b35-451"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="11b35-451"><xref:System.String>.</span></span>|
|`ID`|<span data-ttu-id="11b35-452"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="11b35-452"><xref:System.String>.</span></span>|
|`IDREF`|<span data-ttu-id="11b35-453"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="11b35-453"><xref:System.String>.</span></span>|
|`IDREFS`|<span data-ttu-id="11b35-454"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="11b35-454"><xref:System.String>.</span></span>|
|`ENTITY`|<span data-ttu-id="11b35-455"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="11b35-455"><xref:System.String>.</span></span>|
|`ENTITIES`|<span data-ttu-id="11b35-456"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="11b35-456"><xref:System.String>.</span></span>|
|`NMTOKEN`|<span data-ttu-id="11b35-457"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="11b35-457"><xref:System.String>.</span></span>|
|`NMTOKENS`|<span data-ttu-id="11b35-458"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="11b35-458"><xref:System.String>.</span></span>|
|`decimal`|<span data-ttu-id="11b35-459"><xref:System.Decimal>.</span><span class="sxs-lookup"><span data-stu-id="11b35-459"><xref:System.Decimal>.</span></span>|
|`integer`|<span data-ttu-id="11b35-460"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="11b35-460"><xref:System.Int64>.</span></span>|
|`nonPositiveInteger`|<span data-ttu-id="11b35-461"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="11b35-461"><xref:System.Int64>.</span></span>|
|`negativeInteger`|<span data-ttu-id="11b35-462"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="11b35-462"><xref:System.Int64>.</span></span>|
|`long`|<span data-ttu-id="11b35-463"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="11b35-463"><xref:System.Int64>.</span></span>|
|`int`|<span data-ttu-id="11b35-464"><xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="11b35-464"><xref:System.Int32>.</span></span>|
|`short`|<span data-ttu-id="11b35-465"><xref:System.Int16>.</span><span class="sxs-lookup"><span data-stu-id="11b35-465"><xref:System.Int16>.</span></span>|
|`Byte`|<span data-ttu-id="11b35-466"><xref:System.SByte>.</span><span class="sxs-lookup"><span data-stu-id="11b35-466"><xref:System.SByte>.</span></span>|
|`nonNegativeInteger`|<span data-ttu-id="11b35-467"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="11b35-467"><xref:System.Int64>.</span></span>|
|`unsignedLong`|<span data-ttu-id="11b35-468"><xref:System.UInt64>.</span><span class="sxs-lookup"><span data-stu-id="11b35-468"><xref:System.UInt64>.</span></span>|
|`unsignedInt`|<span data-ttu-id="11b35-469"><xref:System.UInt32>.</span><span class="sxs-lookup"><span data-stu-id="11b35-469"><xref:System.UInt32>.</span></span>|
|`unsignedShort`|<span data-ttu-id="11b35-470"><xref:System.UInt16>.</span><span class="sxs-lookup"><span data-stu-id="11b35-470"><xref:System.UInt16>.</span></span>|
|`unsignedByte`|<span data-ttu-id="11b35-471"><xref:System.Byte>.</span><span class="sxs-lookup"><span data-stu-id="11b35-471"><xref:System.Byte>.</span></span>|
|`positiveInteger`|<span data-ttu-id="11b35-472"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="11b35-472"><xref:System.Int64>.</span></span>|

## <a name="iserializable-types-mapping"></a><span data-ttu-id="11b35-473">ISerializable türleri eşleme</span><span class="sxs-lookup"><span data-stu-id="11b35-473">ISerializable types mapping</span></span>

<span data-ttu-id="11b35-474">.NET Framework sürüm 1,0 ' de, <xref:System.Runtime.Serialization.ISerializable> kalıcı veya veri aktarımı için nesneleri serileştirmek üzere genel bir mekanizma olarak sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="11b35-474">In .NET Framework version 1.0, <xref:System.Runtime.Serialization.ISerializable> was introduced as a general mechanism to serialize objects for persistence or data transfer.</span></span> <span data-ttu-id="11b35-475">`ISerializable`Uygulamaları arasında geçirilebileceğini ve uygulayan birçok .NET Framework türü vardır.</span><span class="sxs-lookup"><span data-stu-id="11b35-475">There are many .NET Framework types that implement `ISerializable` and that can be passed between applications.</span></span> <span data-ttu-id="11b35-476"><xref:System.Runtime.Serialization.DataContractSerializer>doğal olarak sınıflar için destek sağlar `ISerializable` .</span><span class="sxs-lookup"><span data-stu-id="11b35-476"><xref:System.Runtime.Serialization.DataContractSerializer> naturally provides support for `ISerializable` classes.</span></span> <span data-ttu-id="11b35-477">`DataContractSerializer` `ISerializable` Yalnızca türün QName (nitelenmiş adı) ile farklı olan ve etkin özellik koleksiyonları olan eşleme uygulama şeması türleri.</span><span class="sxs-lookup"><span data-stu-id="11b35-477">The `DataContractSerializer` maps `ISerializable` implementation schema types that differ only by the QName (qualified name) of the type and are effectively property collections.</span></span> <span data-ttu-id="11b35-478">Örneğin, `DataContractSerializer` <xref:System.Exception> ad alanında aşağıdaki xsd türüyle eşlenir `http://schemas.datacontract.org/2004/07/System` .</span><span class="sxs-lookup"><span data-stu-id="11b35-478">For example, the `DataContractSerializer` maps <xref:System.Exception> to the following XSD type in the `http://schemas.datacontract.org/2004/07/System` namespace.</span></span>

```xml
<xs:complexType name="Exception">
 <xs:sequence>
  <xs:any minOccurs="0" maxOccurs="unbounded"
      namespace="##local" processContents="skip"/>
 </xs:sequence>
 <xs:attribute ref="ser:FactoryType"/>
</xs:complexType>
```

<span data-ttu-id="11b35-479">`ser:FactoryType`Veri sözleşmesi serileştirme şemasında belirtilen isteğe bağlı öznitelik, türü seri durumdan çıkarılabilecek bir fabrika sınıfına başvurur.</span><span class="sxs-lookup"><span data-stu-id="11b35-479">The optional attribute `ser:FactoryType` declared in the Data Contract Serialization schema references a factory class that can deserialize the type.</span></span> <span data-ttu-id="11b35-480">Factory sınıfı, kullanılan örneğin bilinen türler koleksiyonunun bir parçası olmalıdır `DataContractSerializer` .</span><span class="sxs-lookup"><span data-stu-id="11b35-480">The factory class must be part of the known types collection of the `DataContractSerializer` instance being used.</span></span> <span data-ttu-id="11b35-481">Bilinen türler hakkında daha fazla bilgi için bkz. [veri sözleşmesi bilinen türler](data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="11b35-481">For more information about known types, see [Data Contract Known Types](data-contract-known-types.md).</span></span>

## <a name="datacontract-serialization-schema"></a><span data-ttu-id="11b35-482">DataContract serileştirme şeması</span><span class="sxs-lookup"><span data-stu-id="11b35-482">DataContract Serialization Schema</span></span>

<span data-ttu-id="11b35-483">`DataContractSerializer`Özel bir veri sözleşmesi serileştirme ad alanındaki kullanım türleri, öğeler ve öznitelikler tarafından dışarıya aktarılmış bir dizi şema:</span><span class="sxs-lookup"><span data-stu-id="11b35-483">A number of schemas exported by the `DataContractSerializer` use types, elements, and attributes from a special Data Contract Serialization namespace:</span></span>

`http://schemas.microsoft.com/2003/10/Serialization`

<span data-ttu-id="11b35-484">Aşağıda, tüm veri anlaşması serileştirme şeması bildirimi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="11b35-484">The following is a complete Data Contract Serialization schema declaration.</span></span>

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

<span data-ttu-id="11b35-485">Aşağıdakiler not edilmelidir:</span><span class="sxs-lookup"><span data-stu-id="11b35-485">The following should be noted:</span></span>

- <span data-ttu-id="11b35-486">`ser:char`, türünün Unicode karakterlerini temsil edecek şekilde sunulmuştur <xref:System.Char> .</span><span class="sxs-lookup"><span data-stu-id="11b35-486">`ser:char` is introduced to represent Unicode characters of type <xref:System.Char>.</span></span>

- <span data-ttu-id="11b35-487">, `valuespace` ' `xs:duration` A eşlenecek şekilde, sıralı bir küme için azaltılır <xref:System.TimeSpan> .</span><span class="sxs-lookup"><span data-stu-id="11b35-487">The `valuespace` of `xs:duration` is reduced to an ordered set so that it can be mapped to a <xref:System.TimeSpan>.</span></span>

- <span data-ttu-id="11b35-488">`FactoryType`, öğesinden türetilmiş türlerden aktarılmış şemalarda kullanılır <xref:System.Runtime.Serialization.ISerializable> .</span><span class="sxs-lookup"><span data-stu-id="11b35-488">`FactoryType` is used in schemas exported from types that are derived from <xref:System.Runtime.Serialization.ISerializable>.</span></span>

## <a name="importing-non-datacontract-schemas"></a><span data-ttu-id="11b35-489">DataContract olmayan şemaları içeri aktarma</span><span class="sxs-lookup"><span data-stu-id="11b35-489">Importing non-DataContract schemas</span></span>

<span data-ttu-id="11b35-490">`DataContractSerializer``ImportXmlTypes`XSD profiliyle uyumlu olmayan şemaların içeri aktarılması için izin verme seçeneği vardır `DataContractSerializer` (bkz <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> . özelliği).</span><span class="sxs-lookup"><span data-stu-id="11b35-490">`DataContractSerializer` has the `ImportXmlTypes` option to allow import of schemas that do not conform to the `DataContractSerializer` XSD profile (see the <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> property).</span></span> <span data-ttu-id="11b35-491">Bu seçeneğin ayarlanması `true` , uyumsuz şema türlerinin kabul edilmesini sağlar ve bunları aşağıdaki uygulamayla eşleyerek, <xref:System.Xml.Serialization.IXmlSerializable> dizisini sarmalayarak <xref:System.Xml.XmlNode> (yalnızca sınıf adı farklıdır).</span><span class="sxs-lookup"><span data-stu-id="11b35-491">Setting this option to `true` enables acceptance of non-conforming schema types and mapping them to the following implementation, <xref:System.Xml.Serialization.IXmlSerializable> wrapping an array of <xref:System.Xml.XmlNode> (only the class name differs).</span></span>

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

## <a name="datetimeoffset-serialization"></a><span data-ttu-id="11b35-492">DateTimeOffset serileştirme</span><span class="sxs-lookup"><span data-stu-id="11b35-492">DateTimeOffset Serialization</span></span>

<span data-ttu-id="11b35-493"><xref:System.DateTimeOffset>Temel bir tür olarak değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="11b35-493">The <xref:System.DateTimeOffset> is not treated as a primitive type.</span></span> <span data-ttu-id="11b35-494">Bunun yerine, iki bölümden oluşan karmaşık bir öğe olarak serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="11b35-494">Instead, it is serialized as a complex element with two parts.</span></span> <span data-ttu-id="11b35-495">İlk bölüm Tarih saatini temsil eder ve ikinci bölüm Tarih saatinden itibaren olan sapmayı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="11b35-495">The first part represents the date time, and the second part represents the offset from the date time.</span></span> <span data-ttu-id="11b35-496">Aşağıdaki kodda serileştirilmiş bir DateTimeOffset değeri örneği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="11b35-496">An example of a serialized DateTimeOffset value is shown in the following code.</span></span>

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

<span data-ttu-id="11b35-497">Şema aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="11b35-497">The schema is as follows.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="11b35-498">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="11b35-498">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- <xref:System.Runtime.Serialization.XsdDataContractImporter>
- [<span data-ttu-id="11b35-499">Veri Anlaşmalarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="11b35-499">Using Data Contracts</span></span>](using-data-contracts.md)

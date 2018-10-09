---
title: Veri Sözleşmesi Şema Başvurusu
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts [WCF], schema reference
ms.assetid: 9ebb0ebe-8166-4c93-980a-7c8f1f38f7c0
ms.openlocfilehash: 33661061e1a5db4f7826c1a8eca188f8c782b58f
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48873725"
---
# <a name="data-contract-schema-reference"></a><span data-ttu-id="f6e9b-102">Veri Sözleşmesi Şema Başvurusu</span><span class="sxs-lookup"><span data-stu-id="f6e9b-102">Data Contract Schema Reference</span></span>
<span data-ttu-id="f6e9b-103">Bu konu, XML Şeması (tarafından kullanılan XSD) alt açıklar <xref:System.Runtime.Serialization.DataContractSerializer> açıklayan ortak dil çalışma zamanı (CLR) için XML serileştirme türleri.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-103">This topic describes the subset of the XML Schema (XSD) used by <xref:System.Runtime.Serialization.DataContractSerializer> to describe common language runtime (CLR) types for XML serialization.</span></span>  
  
## <a name="datacontractserializer-mappings"></a><span data-ttu-id="f6e9b-104">DataContractSerializer eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="f6e9b-104">DataContractSerializer Mappings</span></span>  
 <span data-ttu-id="f6e9b-105">`DataContractSerializer` Meta verileri, meta veri uç noktası'nı kullanarak bir Windows Communication Foundation (WCF) hizmetinden dışarı aktardığınızda, CLR türleri için XSD eşler veya [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="f6e9b-105">The `DataContractSerializer` maps CLR types to XSD when metadata is exported from a Windows Communication Foundation (WCF) service using a metadata endpoint or the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="f6e9b-106">Daha fazla bilgi için [veri sözleşmesi serileştiricisi](../../../../docs/framework/wcf/feature-details/data-contract-serializer.md).</span><span class="sxs-lookup"><span data-stu-id="f6e9b-106">For more information, see [Data Contract Serializer](../../../../docs/framework/wcf/feature-details/data-contract-serializer.md).</span></span>  
  
 <span data-ttu-id="f6e9b-107">`DataContractSerializer` Ayrıca Web Hizmetleri Açıklama Dili (WSDL) veya XSD belgelere erişmek ve veri sözleşmeleri Hizmetleri veya istemciler için üretmek için Svcutil.exe kullanıldığında XSD CLR türleriyle eşleştirir.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-107">The `DataContractSerializer` also maps XSD to CLR types when Svcutil.exe is used to access Web Services Description Language (WSDL) or XSD documents and generate data contracts for services or clients.</span></span>  
  
 <span data-ttu-id="f6e9b-108">Bu belgede belirtilen gereksinimlere uygun XML Şeması Örnekleri kullanarak CLR türlerine eşlenebilir `DataContractSerializer`.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-108">Only XML Schema instances that conform to requirements stated in this document can be mapped to CLR types using `DataContractSerializer`.</span></span>  
  
### <a name="support-levels"></a><span data-ttu-id="f6e9b-109">Destek düzeyleri</span><span class="sxs-lookup"><span data-stu-id="f6e9b-109">Support Levels</span></span>  
 <span data-ttu-id="f6e9b-110">`DataContractSerializer` Aşağıdaki Destek düzeyleri için belirli bir XML Şeması özelliği sağlar:</span><span class="sxs-lookup"><span data-stu-id="f6e9b-110">The `DataContractSerializer` provides the following levels of support for a given XML Schema feature:</span></span>  
  
-   <span data-ttu-id="f6e9b-111">**Desteklenen**.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-111">**Supported**.</span></span> <span data-ttu-id="f6e9b-112">Bu özelliğin CLR türleri veya öznitelikleri (veya her ikisi de) kullanarak açık bir eşleme yoktur `DataContractSerializer`.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-112">There is explicit mapping from this feature to CLR types or attributes (or both) using `DataContractSerializer`.</span></span>  
  
-   <span data-ttu-id="f6e9b-113">**Yoksayılan**.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-113">**Ignored**.</span></span> <span data-ttu-id="f6e9b-114">Özelliği tarafından alınan şemalar izin `DataContractSerializer`, ancak kod oluşturma üzerinde hiçbir etkisi olmaz.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-114">The feature is allowed in schemas imported by the `DataContractSerializer`, but has no effect on code generation.</span></span>  
  
-   <span data-ttu-id="f6e9b-115">**Yasak**.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-115">**Forbidden**.</span></span> <span data-ttu-id="f6e9b-116">`DataContractSerializer` Özelliğini kullanarak bir şema almayı desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-116">The `DataContractSerializer` does not support importing a schema using the feature.</span></span> <span data-ttu-id="f6e9b-117">Örneğin, bu tür bir özelliği kullanan bir şema ile bir WSDL erişirken Svcutil.exe geri kullanarak döner <xref:System.Xml.Serialization.XmlSerializer> yerine.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-117">For example, Svcutil.exe, when accessing a WSDL with a schema that uses such a feature, falls back to using the <xref:System.Xml.Serialization.XmlSerializer> instead.</span></span> <span data-ttu-id="f6e9b-118">Bu, varsayılan olarak açıktır.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-118">This is by default.</span></span>  
  
## <a name="general-information"></a><span data-ttu-id="f6e9b-119">Genel bilgiler</span><span class="sxs-lookup"><span data-stu-id="f6e9b-119">General Information</span></span>  
  
-   <span data-ttu-id="f6e9b-120">Şema ad alanı anlatıldığı [XML Şeması](https://go.microsoft.com/fwlink/?LinkId=95475).</span><span class="sxs-lookup"><span data-stu-id="f6e9b-120">The schema namespace is described at [XML Schema](https://go.microsoft.com/fwlink/?LinkId=95475).</span></span> <span data-ttu-id="f6e9b-121">Bu belgede "xs" öneki kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-121">The prefix "xs" is used in this document.</span></span>  
  
-   <span data-ttu-id="f6e9b-122">Bir şema olmayan ad alanı ile herhangi bir özniteliği yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-122">Any attributes with a non-schema namespace are ignored.</span></span>  
  
-   <span data-ttu-id="f6e9b-123">Ek açıklamaları (olanlar dışında bu belgede açıklanan) göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-123">Any annotations (except for those described in this document) are ignored.</span></span>  
  
### <a name="xsschema-attributes"></a><span data-ttu-id="f6e9b-124">\<xs: Schema >: öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f6e9b-124">\<xs:schema>: attributes</span></span>  
  
|<span data-ttu-id="f6e9b-125">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f6e9b-125">Attribute</span></span>|<span data-ttu-id="f6e9b-126">DataContract</span><span class="sxs-lookup"><span data-stu-id="f6e9b-126">DataContract</span></span>|  
|---------------|------------------|  
|`attributeFormDefault`|<span data-ttu-id="f6e9b-127">Yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-127">Ignored.</span></span>|  
|`blockDefault`|<span data-ttu-id="f6e9b-128">Yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-128">Ignored.</span></span>|  
|`elementFormDefault`|<span data-ttu-id="f6e9b-129">Nitelenmelidir.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-129">Must be qualified.</span></span> <span data-ttu-id="f6e9b-130">Tüm öğeler için bir şema tarafından desteklenen nitelenmelidir `DataContractSerializer`.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-130">All elements must be qualified for a schema to be supported by `DataContractSerializer`.</span></span> <span data-ttu-id="f6e9b-131">Bu iki ayar tarafından gerçekleştirilebilir xs:schema/@elementFormDefault "tam" veya ayarlayarak xs:element/@form için "tam" her tek öğe bildiriminde.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-131">This can be accomplished by either setting xs:schema/@elementFormDefault to "qualified" or by setting xs:element/@form to "qualified" on each individual element declaration.</span></span>|  
|`finalDefault`|<span data-ttu-id="f6e9b-132">Yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-132">Ignored.</span></span>|  
|`Id`|<span data-ttu-id="f6e9b-133">Yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-133">Ignored.</span></span>|  
|`targetNamespace`|<span data-ttu-id="f6e9b-134">Desteklenen ve veri anlaşması ad alanıyla eşlendi.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-134">Supported and mapped to the data contract namespace.</span></span> <span data-ttu-id="f6e9b-135">Bu öznitelik belirtilmezse boş ad alanı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-135">If this attribute is not specified, the blank namespace is used.</span></span> <span data-ttu-id="f6e9b-136">Ayrılmış ad alanı olamaz `http://schemas.microsoft.com/2003/10/Serialization/`.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-136">Cannot be the reserved namespace `http://schemas.microsoft.com/2003/10/Serialization/`.</span></span>|  
|`version`|<span data-ttu-id="f6e9b-137">Yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-137">Ignored.</span></span>|  
  
### <a name="xsschema-contents"></a><span data-ttu-id="f6e9b-138">\<xs: Schema >: içeriği</span><span class="sxs-lookup"><span data-stu-id="f6e9b-138">\<xs:schema>: contents</span></span>  
  
|<span data-ttu-id="f6e9b-139">İçindekiler</span><span class="sxs-lookup"><span data-stu-id="f6e9b-139">Contents</span></span>|<span data-ttu-id="f6e9b-140">Şema</span><span class="sxs-lookup"><span data-stu-id="f6e9b-140">Schema</span></span>|  
|--------------|------------|  
|`include`|<span data-ttu-id="f6e9b-141">Desteklenen.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-141">Supported.</span></span> <span data-ttu-id="f6e9b-142">`DataContractSerializer` Xs destekler: içerir ve xs:import.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-142">`DataContractSerializer` supports xs:include and xs:import.</span></span> <span data-ttu-id="f6e9b-143">Ancak, Svcutil.exe sınırlar aşağıdaki `xs:include/@schemaLocation` ve `xs:import/@location` meta verileri bir yerel dosyadan yüklendiğinde başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-143">However, Svcutil.exe restricts following `xs:include/@schemaLocation` and `xs:import/@location` references when metadata is loaded from a local file.</span></span> <span data-ttu-id="f6e9b-144">Şema dosyalarını listesi aracılığıyla değil ve bir bant dışı mekanizması aracılığıyla geçirilmelidir `include` böyle bir durumda; `include`d şema belgeleri yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-144">The list of schema files must be passed through an out-of-band mechanism and not through `include` in this case; `include`d schema documents are ignored.</span></span>|  
|`redefine`|<span data-ttu-id="f6e9b-145">Yasak.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-145">Forbidden.</span></span> <span data-ttu-id="f6e9b-146">Kullanımını `xs:redefine` tarafından yasaklanmış `DataContractSerializer` güvenlik nedenleriyle: `x:redefine` gerektirir `schemaLocation` izlemelidir.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-146">The use of `xs:redefine` is forbidden by `DataContractSerializer` for security reasons: `x:redefine` requires `schemaLocation` to be followed.</span></span> <span data-ttu-id="f6e9b-147">Bazı durumlarda, DataContract kullanarak Svcutil.exe kullanımını kısıtlayan `schemaLocation`.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-147">In certain circumstances, Svcutil.exe using DataContract restricts use of `schemaLocation`.</span></span>|  
|`import`|<span data-ttu-id="f6e9b-148">Desteklenen.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-148">Supported.</span></span> <span data-ttu-id="f6e9b-149">`DataContractSerializer` destekleyen `xs:include` ve `xs:import`.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-149">`DataContractSerializer` supports `xs:include` and `xs:import`.</span></span> <span data-ttu-id="f6e9b-150">Ancak, Svcutil.exe sınırlar aşağıdaki `xs:include/@schemaLocation` ve `xs:import/@location` meta verileri bir yerel dosyadan yüklendiğinde başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-150">However, Svcutil.exe restricts following `xs:include/@schemaLocation` and `xs:import/@location` references when metadata is loaded from a local file.</span></span> <span data-ttu-id="f6e9b-151">Şema dosyalarını listesi aracılığıyla değil ve bir bant dışı mekanizması aracılığıyla geçirilmelidir `include` böyle bir durumda; `include`d şema belgeleri yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-151">The list of schema files must be passed through an out-of-band mechanism and not through `include` in this case; `include`d schema documents are ignored.</span></span>|  
|`simpleType`|<span data-ttu-id="f6e9b-152">Desteklenen.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-152">Supported.</span></span> <span data-ttu-id="f6e9b-153">Bkz: `xs:simpleType` bölümü.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-153">See the `xs:simpleType` section.</span></span>|  
|`complexType`|<span data-ttu-id="f6e9b-154">Desteklenen veri sözleşmeleri eşlenir.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-154">Supported, maps to data contracts.</span></span> <span data-ttu-id="f6e9b-155">Bkz: `xs:complexType` bölümü.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-155">See the `xs:complexType` section.</span></span>|  
|`group`|<span data-ttu-id="f6e9b-156">Yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-156">Ignored.</span></span> <span data-ttu-id="f6e9b-157">`DataContractSerializer` kullanımını desteklemiyor `xs:group`, `xs:attributeGroup`, ve `xs:attribute`.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-157">`DataContractSerializer` does not support use of `xs:group`, `xs:attributeGroup`, and `xs:attribute`.</span></span> <span data-ttu-id="f6e9b-158">Bu bildirimleri alt öğeleri dikkate alınmaz `xs:schema`, içinde başvurulmuş ancak `complexType` veya desteklenen diğer yapıları.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-158">These declarations are ignored as children of `xs:schema`, but cannot be referenced from within `complexType` or other supported constructs.</span></span>|  
|`attributeGroup`|<span data-ttu-id="f6e9b-159">Yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-159">Ignored.</span></span> <span data-ttu-id="f6e9b-160">`DataContractSerializer` kullanımını desteklemiyor `xs:group`, `xs:attributeGroup`, ve `xs:attribute`.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-160">`DataContractSerializer` does not support use of `xs:group`, `xs:attributeGroup`, and `xs:attribute`.</span></span> <span data-ttu-id="f6e9b-161">Bu bildirimleri alt öğeleri dikkate alınmaz `xs:schema`, içinde başvurulmuş ancak `complexType` veya desteklenen diğer yapıları.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-161">These declarations are ignored as children of `xs:schema`, but cannot be referenced from within `complexType` or other supported constructs.</span></span>|  
|`element`|<span data-ttu-id="f6e9b-162">Desteklenen.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-162">Supported.</span></span> <span data-ttu-id="f6e9b-163">Genel öğe bildirimi (hazırlanmış) bakın.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-163">See Global Element Declaration (GED).</span></span>|  
|`attribute`|<span data-ttu-id="f6e9b-164">Yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-164">Ignored.</span></span> <span data-ttu-id="f6e9b-165">`DataContractSerializer` kullanımını desteklemiyor `xs:group`, `xs:attributeGroup`, ve `xs:attribute`.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-165">`DataContractSerializer` does not support use of `xs:group`, `xs:attributeGroup`, and `xs:attribute`.</span></span> <span data-ttu-id="f6e9b-166">Bu bildirimleri alt öğeleri dikkate alınmaz `xs:schema`, içinde başvurulmuş ancak `complexType` veya desteklenen diğer yapıları.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-166">These declarations are ignored as children of `xs:schema`, but cannot be referenced from within `complexType` or other supported constructs.</span></span>|  
|`notation`|<span data-ttu-id="f6e9b-167">Yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-167">Ignored.</span></span>|  
  
## <a name="complex-types--xscomplextype"></a><span data-ttu-id="f6e9b-168">Karmaşık türler – \<xs:complexType ></span><span class="sxs-lookup"><span data-stu-id="f6e9b-168">Complex Types – \<xs:complexType></span></span>  
  
### <a name="general-information"></a><span data-ttu-id="f6e9b-169">Genel bilgiler</span><span class="sxs-lookup"><span data-stu-id="f6e9b-169">General Information</span></span>  
 <span data-ttu-id="f6e9b-170">Her bir karmaşık türü \<xs:complexType > bir veri sözleşmesine eşler.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-170">Each complex type \<xs:complexType> maps to a data contract.</span></span>  
  
### <a name="xscomplextype-attributes"></a><span data-ttu-id="f6e9b-171">\<xs:complexType >: öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f6e9b-171">\<xs:complexType>: attributes</span></span>  
  
|<span data-ttu-id="f6e9b-172">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f6e9b-172">Attribute</span></span>|<span data-ttu-id="f6e9b-173">Şema</span><span class="sxs-lookup"><span data-stu-id="f6e9b-173">Schema</span></span>|  
|---------------|------------|  
|`abstract`|<span data-ttu-id="f6e9b-174">False olmalıdır (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="f6e9b-174">Must be false (default).</span></span>|  
|`block`|<span data-ttu-id="f6e9b-175">Yasak.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-175">Forbidden.</span></span>|  
|`final`|<span data-ttu-id="f6e9b-176">Yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-176">Ignored.</span></span>|  
|`id`|<span data-ttu-id="f6e9b-177">Yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-177">Ignored.</span></span>|  
|`mixed`|<span data-ttu-id="f6e9b-178">False olmalıdır (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="f6e9b-178">Must be false (default).</span></span>|  
|`name`|<span data-ttu-id="f6e9b-179">Desteklenen ve veri anlaşması adına eşlenir.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-179">Supported and mapped to the data contract name.</span></span> <span data-ttu-id="f6e9b-180">Adında nokta varsa, bir iç türü için eşleme türü için girişiminde yapılır.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-180">If there are periods in the name, an attempt is made to map the type to an inner type.</span></span> <span data-ttu-id="f6e9b-181">Örneğin, adında bir karmaşık tür `A.B` veri anlaşması eşlenir tür veri anlaşması adına sahip bir türün bir iç türü `A`, ancak böyle bir veri türü yalnızca sözleşme yoksa.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-181">For example, a complex type named `A.B` maps to a data contract type that is an inner type of a type with the data contract name `A`, but only if such a data contract type exists.</span></span> <span data-ttu-id="f6e9b-182">Birden fazla iç içe geçme düzeyine mümkündür: Örneğin, `A.B.C` bir iç türünde olması gerekir, ancak yalnızca olabilir `A` ve `A.B` her ikisi de mevcut.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-182">More than one level of nesting is possible: for example, `A.B.C` can be an inner type, but only if `A` and `A.B` both exist.</span></span>|  
  
### <a name="xscomplextype-contents"></a><span data-ttu-id="f6e9b-183">\<xs:complexType >: içeriği</span><span class="sxs-lookup"><span data-stu-id="f6e9b-183">\<xs:complexType>: contents</span></span>  
  
|<span data-ttu-id="f6e9b-184">İçindekiler</span><span class="sxs-lookup"><span data-stu-id="f6e9b-184">Contents</span></span>|<span data-ttu-id="f6e9b-185">Şema</span><span class="sxs-lookup"><span data-stu-id="f6e9b-185">Schema</span></span>|  
|--------------|------------|  
|`simpleContent`|<span data-ttu-id="f6e9b-186">Uzantıları yasaktır.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-186">Extensions are forbidden.</span></span><br /><br /> <span data-ttu-id="f6e9b-187">Kısıtlama yalnızca verilir `anySimpleType`.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-187">Restriction is allowed only from `anySimpleType`.</span></span>|  
|`complexContent`|<span data-ttu-id="f6e9b-188">Desteklenen.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-188">Supported.</span></span> <span data-ttu-id="f6e9b-189">"Devralma" konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-189">See "Inheritance".</span></span>|  
|`group`|<span data-ttu-id="f6e9b-190">Yasak.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-190">Forbidden.</span></span>|  
|`all`|<span data-ttu-id="f6e9b-191">Yasak.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-191">Forbidden.</span></span>|  
|`choice`|<span data-ttu-id="f6e9b-192">Yasak</span><span class="sxs-lookup"><span data-stu-id="f6e9b-192">Forbidden</span></span>|  
|`sequence`|<span data-ttu-id="f6e9b-193">Desteklenen bir veri anlaşması veri üyeleri eşlenir.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-193">Supported, maps to data members of a data contract.</span></span>|  
|`attribute`|<span data-ttu-id="f6e9b-194">Yasak, bile kullanın (bir durumla) = "prohibited".</span><span class="sxs-lookup"><span data-stu-id="f6e9b-194">Forbidden, even if use="prohibited" (with one exception).</span></span> <span data-ttu-id="f6e9b-195">Yalnızca standart serileştirme Şema ad alanından isteğe bağlı öznitelikleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-195">Only optional attributes from the Standard Serialization Schema namespace are supported.</span></span> <span data-ttu-id="f6e9b-196">Programlama modeli veri anlaşması veri üyeleri eşlemeyin.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-196">They do not map to data members in the data contract programming model.</span></span> <span data-ttu-id="f6e9b-197">Şu anda yalnızca tek bir özniteliğe anlamı vardır ve ISerializable bölümde ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-197">Currently, only one such attribute has meaning and is discussed in the ISerializable section.</span></span> <span data-ttu-id="f6e9b-198">Diğerleri yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-198">All others are ignored.</span></span>|  
|`attributeGroup`|<span data-ttu-id="f6e9b-199">Yasak.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-199">Forbidden.</span></span> <span data-ttu-id="f6e9b-200">WCF v1 sürümdeki `DataContractSerializer` varlığını yoksayar `attributeGroup` içinde `xs:complexType`.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-200">In the WCF v1 release, `DataContractSerializer` ignores the presence of `attributeGroup` inside `xs:complexType`.</span></span>|  
|`anyAttribute`|<span data-ttu-id="f6e9b-201">Yasak.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-201">Forbidden.</span></span>|  
|<span data-ttu-id="f6e9b-202">(boş)</span><span class="sxs-lookup"><span data-stu-id="f6e9b-202">(empty)</span></span>|<span data-ttu-id="f6e9b-203">Bir veri anlaşması hiçbir veri üyeleri ile eşlenir.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-203">Maps to a data contract with no data members.</span></span>|  
  
### <a name="xssequence-in-a-complex-type-attributes"></a><span data-ttu-id="f6e9b-204">\<xs:Sequence > bir karmaşık türde: öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f6e9b-204">\<xs:sequence> in a complex type: attributes</span></span>  
  
|<span data-ttu-id="f6e9b-205">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f6e9b-205">Attribute</span></span>|<span data-ttu-id="f6e9b-206">Şema</span><span class="sxs-lookup"><span data-stu-id="f6e9b-206">Schema</span></span>|  
|---------------|------------|  
|`id`|<span data-ttu-id="f6e9b-207">Yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-207">Ignored.</span></span>|  
|`maxOccurs`|<span data-ttu-id="f6e9b-208">1 (varsayılan) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-208">Must be 1 (default).</span></span>|  
|`minOccurs`|<span data-ttu-id="f6e9b-209">1 (varsayılan) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-209">Must be 1 (default).</span></span>|  
  
### <a name="xssequence-in-a-complex-type-contents"></a><span data-ttu-id="f6e9b-210">\<xs:Sequence > bir karmaşık türde: içeriği</span><span class="sxs-lookup"><span data-stu-id="f6e9b-210">\<xs:sequence> in a complex type: contents</span></span>  
  
|<span data-ttu-id="f6e9b-211">İçindekiler</span><span class="sxs-lookup"><span data-stu-id="f6e9b-211">Contents</span></span>|<span data-ttu-id="f6e9b-212">Şema</span><span class="sxs-lookup"><span data-stu-id="f6e9b-212">Schema</span></span>|  
|--------------|------------|  
|`element`|<span data-ttu-id="f6e9b-213">Her örnek, bir veri üyesini eşler.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-213">Each instance maps to a data member.</span></span>|  
|`group`|<span data-ttu-id="f6e9b-214">Yasak.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-214">Forbidden.</span></span>|  
|`choice`|<span data-ttu-id="f6e9b-215">Yasak.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-215">Forbidden.</span></span>|  
|`sequence`|<span data-ttu-id="f6e9b-216">Yasak.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-216">Forbidden.</span></span>|  
|`any`|<span data-ttu-id="f6e9b-217">Yasak.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-217">Forbidden.</span></span>|  
|<span data-ttu-id="f6e9b-218">(boş)</span><span class="sxs-lookup"><span data-stu-id="f6e9b-218">(empty)</span></span>|<span data-ttu-id="f6e9b-219">Bir veri anlaşması hiçbir veri üyeleri ile eşlenir.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-219">Maps to a data contract with no data members.</span></span>|  
  
## <a name="elements--xselement"></a><span data-ttu-id="f6e9b-220">Öğeleri – \<xs:element ></span><span class="sxs-lookup"><span data-stu-id="f6e9b-220">Elements – \<xs:element></span></span>  
  
### <a name="general-information"></a><span data-ttu-id="f6e9b-221">Genel bilgiler</span><span class="sxs-lookup"><span data-stu-id="f6e9b-221">General Information</span></span>  
 <span data-ttu-id="f6e9b-222">`<xs:element>` şu bağlamlarda oluşabilir:</span><span class="sxs-lookup"><span data-stu-id="f6e9b-222">`<xs:element>` can occur in the following contexts:</span></span>  
  
-   <span data-ttu-id="f6e9b-223">İçinde ortaya çıkabilir bir `<xs:sequence>`, bir normal (koleksiyon dışı) veri anlaşması veri üyesi açıklar.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-223">It can occur within an `<xs:sequence>`, which describes a data member of a regular (non-collection) data contract.</span></span> <span data-ttu-id="f6e9b-224">Bu durumda, `maxOccurs` öznitelik 1 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-224">In this case, the `maxOccurs` attribute must be 1.</span></span> <span data-ttu-id="f6e9b-225">(0 değerine izin verilmez).</span><span class="sxs-lookup"><span data-stu-id="f6e9b-225">(A value of 0 is not allowed).</span></span>  
  
-   <span data-ttu-id="f6e9b-226">İçinde ortaya çıkabilir bir `<xs:sequence>`, bir koleksiyon veri anlaşması veri üyesi açıklar.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-226">It can occur within an `<xs:sequence>`, which describes a data member of a collection data contract.</span></span> <span data-ttu-id="f6e9b-227">Bu durumda, `maxOccurs` 1'den büyük veya "sınırsız" özniteliği olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-227">In this case, the `maxOccurs` attribute must be greater than 1 or "unbounded".</span></span>  
  
-   <span data-ttu-id="f6e9b-228">İçinde ortaya çıkabilir bir `<xs:schema>` bir genel öğe bildirimi (hazırlanmış) olarak.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-228">It can occur within an `<xs:schema>` as a Global Element Declaration (GED).</span></span>  
  
### <a name="xselement-with-maxoccurs1-within-an-xssequence-data-members"></a><span data-ttu-id="f6e9b-229">\<xs:Element > ile maxOccurs = 1 içinde bir \<xs:sequence > (veri üyeleri)</span><span class="sxs-lookup"><span data-stu-id="f6e9b-229">\<xs:element> with maxOccurs=1 within an \<xs:sequence> (Data Members)</span></span>  
  
|<span data-ttu-id="f6e9b-230">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f6e9b-230">Attribute</span></span>|<span data-ttu-id="f6e9b-231">Şema</span><span class="sxs-lookup"><span data-stu-id="f6e9b-231">Schema</span></span>|  
|---------------|------------|  
|`ref`|<span data-ttu-id="f6e9b-232">Yasak.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-232">Forbidden.</span></span>|  
|`name`|<span data-ttu-id="f6e9b-233">Desteklenen veri üye adına eşlenir.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-233">Supported, maps to the data member name.</span></span>|  
|`type`|<span data-ttu-id="f6e9b-234">Desteklenen veri üyesi eşlenir yazın.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-234">Supported, maps to the data member type.</span></span> <span data-ttu-id="f6e9b-235">Daha fazla bilgi için türü/temel eşleme bakın.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-235">For more information, see Type/primitive mapping.</span></span> <span data-ttu-id="f6e9b-236">Aksi takdirde belirtilen (ve anonim bir tür içermiyor), `xs:anyType` varsayılır.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-236">If not specified (and the element does not contain an anonymous type), `xs:anyType` is assumed.</span></span>|  
|`block`|<span data-ttu-id="f6e9b-237">Yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-237">Ignored.</span></span>|  
|`default`|<span data-ttu-id="f6e9b-238">Yasak.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-238">Forbidden.</span></span>|  
|`fixed`|<span data-ttu-id="f6e9b-239">Yasak.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-239">Forbidden.</span></span>|  
|`form`|<span data-ttu-id="f6e9b-240">Nitelenmelidir.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-240">Must be qualified.</span></span> <span data-ttu-id="f6e9b-241">Bu öznitelik aracılığıyla ayarlanabilir `elementFormDefault` üzerinde `xs:schema`.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-241">This attribute can be set through `elementFormDefault` on `xs:schema`.</span></span>|  
|`id`|<span data-ttu-id="f6e9b-242">Yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-242">Ignored.</span></span>|  
|`maxOccurs`|<span data-ttu-id="f6e9b-243">1.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-243">1</span></span>|  
|`minOccurs`|<span data-ttu-id="f6e9b-244">Eşlendiği <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> veri üyesi özelliği (`IsRequired` true olduğunda `minOccurs` 1'dir).</span><span class="sxs-lookup"><span data-stu-id="f6e9b-244">Maps to the <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> property of a data member (`IsRequired` is true when `minOccurs` is 1).</span></span>|  
|`nillable`|<span data-ttu-id="f6e9b-245">Tür eşlemesi etkiler.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-245">Affects type mapping.</span></span> <span data-ttu-id="f6e9b-246">Eşleme türü/temel bakın.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-246">See Type/primitive mapping.</span></span>|  
  
### <a name="xselement-with-maxoccurs1-within-an-xssequence-collections"></a><span data-ttu-id="f6e9b-247">\<xs:Element > ile maxOccurs > 1 içinde bir \<xs:sequence > (koleksiyonlar)</span><span class="sxs-lookup"><span data-stu-id="f6e9b-247">\<xs:element> with maxOccurs>1 within an \<xs:sequence> (Collections)</span></span>  
  
-   <span data-ttu-id="f6e9b-248">Eşleyen bir <xref:System.Runtime.Serialization.CollectionDataContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-248">Maps to a <xref:System.Runtime.Serialization.CollectionDataContractAttribute>.</span></span>  
  
-   <span data-ttu-id="f6e9b-249">Koleksiyon türlerini yalnızca xs: element'ine bir xs:sequence içinde izin verilir.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-249">In collection types, only one xs:element is allowed within an xs:sequence.</span></span>  
  
 <span data-ttu-id="f6e9b-250">Koleksiyonlar aşağıdaki türde olabilir:</span><span class="sxs-lookup"><span data-stu-id="f6e9b-250">Collections can be of the following types:</span></span>  
  
-   <span data-ttu-id="f6e9b-251">Normal koleksiyonları (örneğin, diziler).</span><span class="sxs-lookup"><span data-stu-id="f6e9b-251">Regular collections (for example, arrays).</span></span>  
  
-   <span data-ttu-id="f6e9b-252">Sözlük koleksiyonları (bir değer diğerine; eşleme Örneğin, bir <xref:System.Collections.Hashtable>).</span><span class="sxs-lookup"><span data-stu-id="f6e9b-252">Dictionary collections (mapping one value to another; for example, a <xref:System.Collections.Hashtable>).</span></span>  
  
-   <span data-ttu-id="f6e9b-253">Bir sözlük ve bir anahtar/değer çifti türünde bir dizi arasındaki tek fark oluşturulan programlama modelidir.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-253">The only difference between a dictionary and an array of a key/value pair type is in the generated programming model.</span></span> <span data-ttu-id="f6e9b-254">Verilen tür için bir sözlük koleksiyon olduğunu belirtmek için kullanılan bir şema ek açıklama mekanizması yoktur.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-254">There is a schema annotation mechanism that can be used to indicate that a given type is a dictionary collection.</span></span>  
  
 <span data-ttu-id="f6e9b-255">Kuralları `ref`, `block`, `default`, `fixed`, `form`, ve `id` öznitelikleri olan koleksiyon dışı çalışması için olanla aynıdır.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-255">The rules for the `ref`, `block`, `default`, `fixed`, `form`, and `id` attributes are the same as for the non-collection case.</span></span> <span data-ttu-id="f6e9b-256">Diğer öznitelikler aşağıdaki tabloda içerir.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-256">Other attributes include those in the following table.</span></span>  
  
|<span data-ttu-id="f6e9b-257">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f6e9b-257">Attribute</span></span>|<span data-ttu-id="f6e9b-258">Şema</span><span class="sxs-lookup"><span data-stu-id="f6e9b-258">Schema</span></span>|  
|---------------|------------|  
|`name`|<span data-ttu-id="f6e9b-259">Desteklenen eşlenir <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> özelliğinde `CollectionDataContractAttribute` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-259">Supported, maps to the <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> property in the `CollectionDataContractAttribute` attribute.</span></span>|  
|`type`|<span data-ttu-id="f6e9b-260">Desteklenen bir koleksiyonda depolanan türü eşlenir.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-260">Supported, maps to the type stored in the collection.</span></span>|  
|`maxOccurs`|<span data-ttu-id="f6e9b-261">1'den büyük veya "sınırsız".</span><span class="sxs-lookup"><span data-stu-id="f6e9b-261">Greater than 1 or "unbounded".</span></span> <span data-ttu-id="f6e9b-262">DC şema "sınırsız" kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-262">The DC schema should use "unbounded".</span></span>|  
|`minOccurs`|<span data-ttu-id="f6e9b-263">Yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-263">Ignored.</span></span>|  
|`nillable`|<span data-ttu-id="f6e9b-264">Tür eşlemesi etkiler.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-264">Affects type mapping.</span></span> <span data-ttu-id="f6e9b-265">Bu öznitelik sözlüğü koleksiyonlar için göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-265">This attribute is ignored for dictionary collections.</span></span>|  
  
### <a name="xselement-within-an-xsschema-global-element-declaration"></a><span data-ttu-id="f6e9b-266">\<xs:Element > içinde bir \<xs: Schema > Genel öğe bildirimi</span><span class="sxs-lookup"><span data-stu-id="f6e9b-266">\<xs:element> within an \<xs:schema> Global Element Declaration</span></span>  
  
-   <span data-ttu-id="f6e9b-267">Bir genel öğe bildirimi (bir şema türü olarak aynı ad ve ad alanı sahip veya anonim bir tür içinde kendisini tanımlayan hazırlanmış) türüyle ilişkili olduğu söylenir.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-267">A Global Element Declaration (GED) that has the same name and namespace as a type in schema, or that defines an anonymous type inside itself, is said to be associated with the type.</span></span>  
  
-   <span data-ttu-id="f6e9b-268">Şema dışarı aktarma: ilişkili GEDs her oluşturulan türü için hem basit hem de karmaşık oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-268">Schema export: associated GEDs are generated for every generated type, both simple and complex.</span></span>  
  
-   <span data-ttu-id="f6e9b-269">Seri durumundan çıkarma/seri hale getirme:, ilişkili GEDs kök öğe türü için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-269">Deserialization/serialization: associated GEDs are used as root elements for the type.</span></span>  
  
-   <span data-ttu-id="f6e9b-270">Şema içeri aktarma: ilişkili GEDs gerekli değildir ve (türleri tanımlamadığınız sürece) aşağıdaki kurallar izlerseniz göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-270">Schema import: associated GEDs are not required and are ignored if they follow the following rules (unless they define types).</span></span>  
  
|<span data-ttu-id="f6e9b-271">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f6e9b-271">Attribute</span></span>|<span data-ttu-id="f6e9b-272">Şema</span><span class="sxs-lookup"><span data-stu-id="f6e9b-272">Schema</span></span>|  
|---------------|------------|  
|`abstract`|<span data-ttu-id="f6e9b-273">İlişkili GEDs için false olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-273">Must be false for associated GEDs.</span></span>|  
|`block`|<span data-ttu-id="f6e9b-274">İçinde ilişkili GEDs alınamaz.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-274">Forbidden in associated GEDs.</span></span>|  
|`default`|<span data-ttu-id="f6e9b-275">İçinde ilişkili GEDs alınamaz.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-275">Forbidden in associated GEDs.</span></span>|  
|`final`|<span data-ttu-id="f6e9b-276">İlişkili GEDs için false olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-276">Must be false for associated GEDs.</span></span>|  
|`fixed`|<span data-ttu-id="f6e9b-277">İçinde ilişkili GEDs alınamaz.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-277">Forbidden in associated GEDs.</span></span>|  
|`id`|<span data-ttu-id="f6e9b-278">Yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-278">Ignored.</span></span>|  
|`name`|<span data-ttu-id="f6e9b-279">Desteklenen.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-279">Supported.</span></span> <span data-ttu-id="f6e9b-280">İlişkili GEDs tanımına bakın.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-280">See the definition of associated GEDs.</span></span>|  
|`nillable`|<span data-ttu-id="f6e9b-281">İlişkili GEDs için doğru olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-281">Must be true for associated GEDs.</span></span>|  
|`substitutionGroup`|<span data-ttu-id="f6e9b-282">İçinde ilişkili GEDs alınamaz.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-282">Forbidden in associated GEDs.</span></span>|  
|`type`|<span data-ttu-id="f6e9b-283">Desteklenen ve (anonim bir tür öğeyi içeren sürece) için ilişkili GEDs türüyle eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-283">Supported, and must match the associated type for associated GEDs (unless the element contains an anonymous type).</span></span>|  
  
### <a name="xselement-contents"></a><span data-ttu-id="f6e9b-284">\<xs:Element >: içeriği</span><span class="sxs-lookup"><span data-stu-id="f6e9b-284">\<xs:element>: contents</span></span>  
  
|<span data-ttu-id="f6e9b-285">İçindekiler</span><span class="sxs-lookup"><span data-stu-id="f6e9b-285">Contents</span></span>|<span data-ttu-id="f6e9b-286">Şema</span><span class="sxs-lookup"><span data-stu-id="f6e9b-286">Schema</span></span>|  
|--------------|------------|  
|`simpleType`|<span data-ttu-id="f6e9b-287">Supported.\*</span><span class="sxs-lookup"><span data-stu-id="f6e9b-287">Supported.\*</span></span>|  
|`complexType`|<span data-ttu-id="f6e9b-288">Supported.\*</span><span class="sxs-lookup"><span data-stu-id="f6e9b-288">Supported.\*</span></span>|  
|`unique`|<span data-ttu-id="f6e9b-289">Yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-289">Ignored.</span></span>|  
|`key`|<span data-ttu-id="f6e9b-290">Yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-290">Ignored.</span></span>|  
|`keyref`|<span data-ttu-id="f6e9b-291">Yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-291">Ignored.</span></span>|  
|<span data-ttu-id="f6e9b-292">(boş)</span><span class="sxs-lookup"><span data-stu-id="f6e9b-292">(blank)</span></span>|<span data-ttu-id="f6e9b-293">Desteklenen.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-293">Supported.</span></span>|  
  
 <span data-ttu-id="f6e9b-294">\* Kullanırken `simpleType` ve `complexType,` anonim türler için eşleme olduğundan, anonim olmayan türleri ile aynıdır, hiçbir anonim veri sözleşmeleri olmasını dışında ve böylece öğe adından türetilir oluşturulan bir adla adlandırılmış veri anlaşması oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-294">\* When using the `simpleType` and `complexType,` mapping for anonymous types is the same as for non-anonymous types, except that there is no anonymous data contracts, and so a named data contract is created, with a generated name derived from the element name.</span></span> <span data-ttu-id="f6e9b-295">Anonim türler için kuralları aşağıdaki listede verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="f6e9b-295">The rules for anonymous types are in the following list:</span></span>  
  
-   <span data-ttu-id="f6e9b-296">WCF uygulama Ayrıntısı: varsa `xs:element` adının nokta içermediğinden, dış veri anlaşması türü için bir iç türü anonim tür eşler.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-296">WCF implementation detail: If the `xs:element` name does not contain periods, the anonymous type maps to an inner type of the outer data contract type.</span></span> <span data-ttu-id="f6e9b-297">Adı bir nokta içeriyorsa, sonuçta elde edilen veri anlaşması türü bağımsızdır (iç bir tür değil).</span><span class="sxs-lookup"><span data-stu-id="f6e9b-297">If the name contains periods, the resulting data contract type is independent (not an inner type).</span></span>  
  
-   <span data-ttu-id="f6e9b-298">Oluşturulan veri sözleşmesi iç türü veri anlaşması adına bir nokta, öğe ve dize "Türü" adını dış türündeki adıdır.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-298">The generated data contract name of the inner type is the data contract name of the outer type followed by a period, the name of the element, and the string "Type".</span></span>  
  
-   <span data-ttu-id="f6e9b-299">İle bir veri anlaşması ad zaten var, adı benzersiz bir ad oluşturulana kadar "1", "2", "3", vb. eklenerek benzersiz yapılır.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-299">If a data contract with such a name already exists, the name is made unique by appending "1", "2", "3", and so on until a unique name is created.</span></span>  
  
## <a name="simple-types---xssimpletype"></a><span data-ttu-id="f6e9b-300">Basit türler - \<xs:simpleType ></span><span class="sxs-lookup"><span data-stu-id="f6e9b-300">Simple Types - \<xs:simpleType></span></span>  
  
### <a name="xssimpletype-attributes"></a><span data-ttu-id="f6e9b-301">\<xs:simpleType >: öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f6e9b-301">\<xs:simpleType>: attributes</span></span>  
  
|<span data-ttu-id="f6e9b-302">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f6e9b-302">Attribute</span></span>|<span data-ttu-id="f6e9b-303">Şema</span><span class="sxs-lookup"><span data-stu-id="f6e9b-303">Schema</span></span>|  
|---------------|------------|  
|`final`|<span data-ttu-id="f6e9b-304">Yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-304">Ignored.</span></span>|  
|`id`|<span data-ttu-id="f6e9b-305">Yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-305">Ignored.</span></span>|  
|`name`|<span data-ttu-id="f6e9b-306">Desteklenen veri eşlenir adı sözleşme.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-306">Supported, maps to the data contract name.</span></span>|  
  
### <a name="xssimpletype-contents"></a><span data-ttu-id="f6e9b-307">\<xs:simpleType >: içeriği</span><span class="sxs-lookup"><span data-stu-id="f6e9b-307">\<xs:simpleType>: contents</span></span>  
  
|<span data-ttu-id="f6e9b-308">İçindekiler</span><span class="sxs-lookup"><span data-stu-id="f6e9b-308">Contents</span></span>|<span data-ttu-id="f6e9b-309">Şema</span><span class="sxs-lookup"><span data-stu-id="f6e9b-309">Schema</span></span>|  
|--------------|------------|  
|`restriction`|<span data-ttu-id="f6e9b-310">Desteklenen.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-310">Supported.</span></span> <span data-ttu-id="f6e9b-311">Sabit listesi veri sözleşmeleri eşlenir.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-311">Maps to enumeration data contracts.</span></span> <span data-ttu-id="f6e9b-312">Bu öznitelik, numaralandırma desenle eşleşmez gözardı edilir.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-312">This attribute is ignored if it does not match the enumeration pattern.</span></span> <span data-ttu-id="f6e9b-313">Bkz: `xs:simpleType` kısıtlamaları bölümü.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-313">See the `xs:simpleType` restrictions section.</span></span>|  
|`list`|<span data-ttu-id="f6e9b-314">Desteklenen.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-314">Supported.</span></span> <span data-ttu-id="f6e9b-315">Bayrak sabit listesi veri sözleşmeleri eşlenir.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-315">Maps to flag enumeration data contracts.</span></span> <span data-ttu-id="f6e9b-316">Bkz: `xs:simpleType` bölümünde listelenir.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-316">See the `xs:simpleType` lists section.</span></span>|  
|`union`|<span data-ttu-id="f6e9b-317">Yasak.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-317">Forbidden.</span></span>|  
  
### <a name="xsrestriction"></a><span data-ttu-id="f6e9b-318">\<xs:restriction ></span><span class="sxs-lookup"><span data-stu-id="f6e9b-318">\<xs:restriction></span></span>  
  
-   <span data-ttu-id="f6e9b-319">Karmaşık tür kısıtlamalar için temel desteklenen = "`xs:anyType`".</span><span class="sxs-lookup"><span data-stu-id="f6e9b-319">Complex type restrictions are supported only for base="`xs:anyType`".</span></span>  
  
-   <span data-ttu-id="f6e9b-320">Basit türü kısıtlamalarını `xs:string` sahip olmayan herhangi bir kısıtlama modelleri dışındaki `xs:enumeration` numaralandırma veri sözleşmelerine eşlenir.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-320">Simple type restrictions of `xs:string` that do not have any restriction facets other than `xs:enumeration` are mapped to enumeration data contracts.</span></span>  
  
-   <span data-ttu-id="f6e9b-321">Tüm diğer basit tür kısıtlamaları, bunlar kısıtlama türlerine eşlenir.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-321">All other simple type restrictions are mapped to the types they restrict.</span></span> <span data-ttu-id="f6e9b-322">Örneğin, bir kısıtlaması `xs:int` gibi bir tamsayı değerine eşleyen `xs:int` kendisi yapar.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-322">For example, a restriction of `xs:int` maps to an integer, just as `xs:int` itself does.</span></span> <span data-ttu-id="f6e9b-323">Türü/temel eşleme ilkel tür eşlemesi hakkında daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-323">For more information about primitive type mapping, see Type/primitive mapping.</span></span>  
  
### <a name="xsrestriction-attributes"></a><span data-ttu-id="f6e9b-324">\<xs:restriction >: öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f6e9b-324">\<xs:restriction>: attributes</span></span>  
  
|<span data-ttu-id="f6e9b-325">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f6e9b-325">Attribute</span></span>|<span data-ttu-id="f6e9b-326">Şema</span><span class="sxs-lookup"><span data-stu-id="f6e9b-326">Schema</span></span>|  
|---------------|------------|  
|`base`|<span data-ttu-id="f6e9b-327">Desteklenen bir basit tür olmalıdır veya `xs:anyType`.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-327">Must be a supported simple type or `xs:anyType`.</span></span>|  
|`id`|<span data-ttu-id="f6e9b-328">Yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-328">Ignored.</span></span>|  
  
### <a name="xsrestriction-for-all-other-cases-contents"></a><span data-ttu-id="f6e9b-329">\<xs:restriction > diğer tüm durumlarda: içeriği</span><span class="sxs-lookup"><span data-stu-id="f6e9b-329">\<xs:restriction> for all other cases: contents</span></span>  
  
|<span data-ttu-id="f6e9b-330">İçindekiler</span><span class="sxs-lookup"><span data-stu-id="f6e9b-330">Contents</span></span>|<span data-ttu-id="f6e9b-331">Şema</span><span class="sxs-lookup"><span data-stu-id="f6e9b-331">Schema</span></span>|  
|--------------|------------|  
|`simpleType`|<span data-ttu-id="f6e9b-332">Varsa, desteklenen bir temel türünden türetilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-332">If present, must be derived from a supported primitive type.</span></span>|  
|`minExclusive`|<span data-ttu-id="f6e9b-333">Yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-333">Ignored.</span></span>|  
|`minInclusive`|<span data-ttu-id="f6e9b-334">Yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-334">Ignored.</span></span>|  
|`maxExclusive`|<span data-ttu-id="f6e9b-335">Yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-335">Ignored.</span></span>|  
|`maxInclusive`|<span data-ttu-id="f6e9b-336">Yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-336">Ignored.</span></span>|  
|`totalDigits`|<span data-ttu-id="f6e9b-337">Yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-337">Ignored.</span></span>|  
|`fractionDigits`|<span data-ttu-id="f6e9b-338">Yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-338">Ignored.</span></span>|  
|`length`|<span data-ttu-id="f6e9b-339">Yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-339">Ignored.</span></span>|  
|`minLength`|<span data-ttu-id="f6e9b-340">Yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-340">Ignored.</span></span>|  
|`maxLength`|<span data-ttu-id="f6e9b-341">Yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-341">Ignored.</span></span>|  
|`enumeration`|<span data-ttu-id="f6e9b-342">Yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-342">Ignored.</span></span>|  
|`whiteSpace`|<span data-ttu-id="f6e9b-343">Yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-343">Ignored.</span></span>|  
|`pattern`|<span data-ttu-id="f6e9b-344">Yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-344">Ignored.</span></span>|  
|<span data-ttu-id="f6e9b-345">(boş)</span><span class="sxs-lookup"><span data-stu-id="f6e9b-345">(blank)</span></span>|<span data-ttu-id="f6e9b-346">Desteklenen.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-346">Supported.</span></span>|  
  
## <a name="enumeration"></a><span data-ttu-id="f6e9b-347">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="f6e9b-347">Enumeration</span></span>  
  
### <a name="xsrestriction-for-enumerations-attributes"></a><span data-ttu-id="f6e9b-348">\<xs:restriction > Sabit listeleri için: öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f6e9b-348">\<xs:restriction> for enumerations: attributes</span></span>  
  
|<span data-ttu-id="f6e9b-349">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f6e9b-349">Attribute</span></span>|<span data-ttu-id="f6e9b-350">Şema</span><span class="sxs-lookup"><span data-stu-id="f6e9b-350">Schema</span></span>|  
|---------------|------------|  
|`base`|<span data-ttu-id="f6e9b-351">Varsa, olmalıdır `xs:string`.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-351">If present, must be `xs:string`.</span></span>|  
|`id`|<span data-ttu-id="f6e9b-352">Yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-352">Ignored.</span></span>|  
  
### <a name="xsrestriction-for-enumerations-contents"></a><span data-ttu-id="f6e9b-353">\<xs:restriction > Sabit listeleri için: içeriği</span><span class="sxs-lookup"><span data-stu-id="f6e9b-353">\<xs:restriction> for enumerations: contents</span></span>  
  
|<span data-ttu-id="f6e9b-354">İçindekiler</span><span class="sxs-lookup"><span data-stu-id="f6e9b-354">Contents</span></span>|<span data-ttu-id="f6e9b-355">Şema</span><span class="sxs-lookup"><span data-stu-id="f6e9b-355">Schema</span></span>|  
|--------------|------------|  
|`simpleType`|<span data-ttu-id="f6e9b-356">Varsa, bir sabit listesi kısıtlama veri anlaşması (Bu bölümde) tarafından desteklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-356">If present, must be an enumeration restriction supported by the data contract (this section).</span></span>|  
|`minExclusive`|<span data-ttu-id="f6e9b-357">Yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-357">Ignored.</span></span>|  
|`minInclusive`|<span data-ttu-id="f6e9b-358">Yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-358">Ignored.</span></span>|  
|`maxExclusive`|<span data-ttu-id="f6e9b-359">Yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-359">Ignored.</span></span>|  
|`maxInclusive`|<span data-ttu-id="f6e9b-360">Yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-360">Ignored.</span></span>|  
|`totalDigits`|<span data-ttu-id="f6e9b-361">Yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-361">Ignored.</span></span>|  
|`fractionDigits`|<span data-ttu-id="f6e9b-362">Yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-362">Ignored.</span></span>|  
|`length`|<span data-ttu-id="f6e9b-363">Yasak.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-363">Forbidden.</span></span>|  
|`minLength`|<span data-ttu-id="f6e9b-364">Yasak.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-364">Forbidden.</span></span>|  
|`maxLength`|<span data-ttu-id="f6e9b-365">Yasak.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-365">Forbidden.</span></span>|  
|`enumeration`|<span data-ttu-id="f6e9b-366">Desteklenen.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-366">Supported.</span></span> <span data-ttu-id="f6e9b-367">Sabit listesi "id" dikkate alınmaz ve "value" değeri sabit listesi veri anlaşması adına eşlenir.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-367">Enumeration "id" is ignored, and "value" maps to the value name in the enumeration data contract.</span></span>|  
|`whiteSpace`|<span data-ttu-id="f6e9b-368">Yasak.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-368">Forbidden.</span></span>|  
|`pattern`|<span data-ttu-id="f6e9b-369">Yasak.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-369">Forbidden.</span></span>|  
|<span data-ttu-id="f6e9b-370">(boş)</span><span class="sxs-lookup"><span data-stu-id="f6e9b-370">(empty)</span></span>|<span data-ttu-id="f6e9b-371">Desteklenir, boş bir numaralandırma türü eşlenir.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-371">Supported, maps to empty enumeration type.</span></span>|  
  
 <span data-ttu-id="f6e9b-372">Aşağıdaki kod, C# sabit listesi sınıfı gösterir.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-372">The following code shows a C# enumeration class.</span></span>  
  
```  
public enum MyEnum  
{  
   first = 3,  
   second = 4,  
   third =5  
```  
  
 <span data-ttu-id="f6e9b-373">}</span><span class="sxs-lookup"><span data-stu-id="f6e9b-373">}</span></span>  
  
 <span data-ttu-id="f6e9b-374">Aşağıdaki şemada Bu sınıf eşlendiği `DataContractSerializer`.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-374">This class maps to the following schema by the `DataContractSerializer`.</span></span> <span data-ttu-id="f6e9b-375">Sabit listesi değerleri 1'den başlatırsanız `xs:annotation` blokları oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-375">If enumeration values start from 1, `xs:annotation` blocks are not generated.</span></span>  
  
```xml  
<xs:simpleType name="MyEnum">  
<xs:restriction base="xs:string">  
 <xs:enumeration value="first">  
  <xs:annotation>  
   <xs:appinfo>  
    <EnumerationValue   
     xmlns="http://schemas.microsoft.com/2003/10/Serialization/">  
     3  
    </EnumerationValue>  
   </xs:appinfo>  
  </xs:annotation>  
 </xs:enumeration>  
 <xs:enumeration value="second">  
  <xs:annotation>  
   <xs:appinfo>  
    <EnumerationValue   
     xmlns="http://schemas.microsoft.com/2003/10/Serialization/">  
     4  
    </EnumerationValue>  
   </xs:appinfo>  
  </xs:annotation>  
 </xs:enumeration>  
</xs:restriction>  
</xs:simpleType>  
```  
  
### <a name="xslist"></a><span data-ttu-id="f6e9b-376">\<xs:list ></span><span class="sxs-lookup"><span data-stu-id="f6e9b-376">\<xs:list></span></span>  
 <span data-ttu-id="f6e9b-377">`DataContractSerializer` Haritalar Numaralandırma türleri ile işaretlenen `System.FlagsAttribute` için `xs:list` türetilen `xs:string`.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-377">`DataContractSerializer` maps enumeration types marked with `System.FlagsAttribute` to `xs:list` derived from `xs:string`.</span></span> <span data-ttu-id="f6e9b-378">Başka hiçbir `xs:list` çeşitlemeleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-378">No other `xs:list` variations are supported.</span></span>  
  
### <a name="xslist-attributes"></a><span data-ttu-id="f6e9b-379">\<xs:list >: öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f6e9b-379">\<xs:list>: attributes</span></span>  
  
|<span data-ttu-id="f6e9b-380">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f6e9b-380">Attribute</span></span>|<span data-ttu-id="f6e9b-381">Şema</span><span class="sxs-lookup"><span data-stu-id="f6e9b-381">Schema</span></span>|  
|---------------|------------|  
|`itemType`|<span data-ttu-id="f6e9b-382">Yasak.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-382">Forbidden.</span></span>|  
|`id`|<span data-ttu-id="f6e9b-383">Yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-383">Ignored.</span></span>|  
  
### <a name="xslist-contents"></a><span data-ttu-id="f6e9b-384">\<xs:list >: içeriği</span><span class="sxs-lookup"><span data-stu-id="f6e9b-384">\<xs:list>: contents</span></span>  
  
|<span data-ttu-id="f6e9b-385">İçindekiler</span><span class="sxs-lookup"><span data-stu-id="f6e9b-385">Contents</span></span>|<span data-ttu-id="f6e9b-386">Şema</span><span class="sxs-lookup"><span data-stu-id="f6e9b-386">Schema</span></span>|  
|--------------|------------|  
|`simpleType`|<span data-ttu-id="f6e9b-387">Kısıtlaması olmalıdır `xs:string` kullanarak `xs:enumeration` modeli.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-387">Must be restriction from `xs:string` using `xs:enumeration` facet.</span></span>|  
  
 <span data-ttu-id="f6e9b-388">Numaralandırma değeri 2 ilerleme (bayrakları için varsayılan) gücünü izlemiyorsa, değeri depolanan `xs:annotation/xs:appInfo/ser:EnumerationValue` öğesi.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-388">If enumeration value does not follow a power of 2 progression (default for Flags), the value is stored in the `xs:annotation/xs:appInfo/ser:EnumerationValue` element.</span></span>  
  
 <span data-ttu-id="f6e9b-389">Örneğin, aşağıdaki kod, bir numaralandırma türü işaretler.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-389">For example, the following code flags an enumeration type.</span></span>  
  
```  
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
  
 <span data-ttu-id="f6e9b-390">Bu tür, aşağıdaki şemanın eşler.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-390">This type maps to the following schema.</span></span>  
  
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
                <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Se  
rialization/">16</EnumerationValue>  
              </xs:appinfo>  
            </xs:annotation>  
          </xs:enumeration>  
          <xs:enumeration value="AuthWindowsLiveID">  
            <xs:annotation>  
              <xs:appinfo>  
                <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Se  
rialization/">64</EnumerationValue>  
              </xs:appinfo>  
            </xs:annotation>  
          </xs:enumeration>  
        </xs:restriction>  
      </xs:simpleType>  
    </xs:list>  
  </xs:simpleType>  
```  
  
## <a name="inheritance"></a><span data-ttu-id="f6e9b-391">Devralma</span><span class="sxs-lookup"><span data-stu-id="f6e9b-391">Inheritance</span></span>  
  
### <a name="general-rules"></a><span data-ttu-id="f6e9b-392">Genel kurallar</span><span class="sxs-lookup"><span data-stu-id="f6e9b-392">General rules</span></span>  
 <span data-ttu-id="f6e9b-393">Bir veri anlaşması başka bir veri sözleşme devralabilir.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-393">A data contract can inherit from another data contract.</span></span> <span data-ttu-id="f6e9b-394">Bu tür veri sözleşmeleri kullanarak uzantı türleri tarafından türetilmiş ve bir temel harita `<xs:extension>` XML Şeması yapısı.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-394">Such data contracts map to a base and are derived by extension types using the `<xs:extension>` XML Schema construct.</span></span>  
  
 <span data-ttu-id="f6e9b-395">Bir veri anlaşması bir koleksiyon veri anlaşması ' devralamaz.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-395">A data contract cannot inherit from a collection data contract.</span></span>  
  
 <span data-ttu-id="f6e9b-396">Örneğin, aşağıdaki kod, bir veri sözleşmedir.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-396">For example, the following code is a data contract.</span></span>  
  
```  
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
  
 <span data-ttu-id="f6e9b-397">Bu veri sözleşme aşağıdaki XML şema türü bildirimi için eşler.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-397">This data contract maps to the following XML Schema type declaration.</span></span>  
  
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
  
### <a name="xscomplexcontent-attributes"></a><span data-ttu-id="f6e9b-398">\<xs:complexContent >: öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f6e9b-398">\<xs:complexContent>: attributes</span></span>  
  
|<span data-ttu-id="f6e9b-399">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f6e9b-399">Attribute</span></span>|<span data-ttu-id="f6e9b-400">Şema</span><span class="sxs-lookup"><span data-stu-id="f6e9b-400">Schema</span></span>|  
|---------------|------------|  
|`id`|<span data-ttu-id="f6e9b-401">Yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-401">Ignored.</span></span>|  
|`mixed`|<span data-ttu-id="f6e9b-402">False olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-402">Must be false.</span></span>|  
  
### <a name="xscomplexcontent-contents"></a><span data-ttu-id="f6e9b-403">\<xs:complexContent >: içeriği</span><span class="sxs-lookup"><span data-stu-id="f6e9b-403">\<xs:complexContent>: contents</span></span>  
  
|<span data-ttu-id="f6e9b-404">İçindekiler</span><span class="sxs-lookup"><span data-stu-id="f6e9b-404">Contents</span></span>|<span data-ttu-id="f6e9b-405">Şema</span><span class="sxs-lookup"><span data-stu-id="f6e9b-405">Schema</span></span>|  
|--------------|------------|  
|`restriction`|<span data-ttu-id="f6e9b-406">Temel durumlar hariç, Yasak, = "`xs:anyType`".</span><span class="sxs-lookup"><span data-stu-id="f6e9b-406">Forbidden, except when base="`xs:anyType`".</span></span> <span data-ttu-id="f6e9b-407">İkinci içeriğini yerleştirmeye eşdeğer `xs:restriction` doğrudan kapsayıcı altına `xs:complexContent`.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-407">The latter is equivalent to placing the content of the `xs:restriction` directly under the container of the `xs:complexContent`.</span></span>|  
|`extension`|<span data-ttu-id="f6e9b-408">Desteklenen.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-408">Supported.</span></span> <span data-ttu-id="f6e9b-409">Veri anlaşma devralma eşlenir.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-409">Maps to data contract inheritance.</span></span>|  
  
### <a name="xsextension-in-xscomplexcontent-attributes"></a><span data-ttu-id="f6e9b-410">\<xs:extension> in \<xs:complexContent>: attributes</span><span class="sxs-lookup"><span data-stu-id="f6e9b-410">\<xs:extension> in \<xs:complexContent>: attributes</span></span>  
  
|<span data-ttu-id="f6e9b-411">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f6e9b-411">Attribute</span></span>|<span data-ttu-id="f6e9b-412">Şema</span><span class="sxs-lookup"><span data-stu-id="f6e9b-412">Schema</span></span>|  
|---------------|------------|  
|`id`|<span data-ttu-id="f6e9b-413">Yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-413">Ignored.</span></span>|  
|`base`|<span data-ttu-id="f6e9b-414">Desteklenen.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-414">Supported.</span></span> <span data-ttu-id="f6e9b-415">Bu tür öğesinden devralır eşlemeleri için temel veri anlaşması türü.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-415">Maps to the base data contract type that this type inherits from.</span></span>|  
  
### <a name="xsextension-in-xscomplexcontent-contents"></a><span data-ttu-id="f6e9b-416">\<xs:Extension > içinde \<xs:complexContent >: içeriği</span><span class="sxs-lookup"><span data-stu-id="f6e9b-416">\<xs:extension> in \<xs:complexContent>: contents</span></span>  
 <span data-ttu-id="f6e9b-417">Kuralları aynıdır `<xs:complexType>` içeriği.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-417">The rules are the same as for `<xs:complexType>` contents.</span></span>  
  
 <span data-ttu-id="f6e9b-418">Varsa bir `<xs:sequence>` sağlanır, kendi üyesi öğeleri eşlemek için türetilmiş veri anlaşması içinde mevcut olan ek veri üyeleri.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-418">If an `<xs:sequence>` is provided, its member elements map to additional data members that are present in the derived data contract.</span></span>  
  
 <span data-ttu-id="f6e9b-419">Türetilmiş bir tür bir öğe temel türde aynı ada sahip bir öğe içeriyorsa, benzersiz olması için oluşturulan bir ada sahip bir veri üyesinin yinelenen öğe bildirimi eşler.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-419">If a derived type contains an element with the same name as an element in a base type, the duplicate element declaration maps to a data member with a name that is generated to be unique.</span></span> <span data-ttu-id="f6e9b-420">Pozitif tamsayı veri üye adına ("Üye1", "üye2" vb.) eklenen benzersiz bir ad bulunana kadar.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-420">Positive integer numbers are added to the data member name ("member1", "member2", and so on) until a unique name is found.</span></span> <span data-ttu-id="f6e9b-421">Buna karşılık:</span><span class="sxs-lookup"><span data-stu-id="f6e9b-421">Conversely:</span></span>  
  
-   <span data-ttu-id="f6e9b-422">Bir temel veri sözleşmesi veri üyesi olarak aynı ada ve türe sahip bir veri üyesi türetilmiş veri anlaşması varsa `DataContractSerializer` türetilen türde de bu karşılık gelen öğe oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-422">If a derived data contract has a data member with the same name and type as a data member in a base data contract, `DataContractSerializer` generates this corresponding element in the derived type.</span></span>  
  
-   <span data-ttu-id="f6e9b-423">Temel veri anlaşması ancak farklı bir tür veri üyesi olarak aynı ada sahip bir veri üyesi türetilmiş veri anlaşması varsa `DataContractSerializer` türünde bir öğe ile bir şema alır `xs:anyType` hem türetilen tür bildirimleri, hem de temel türü.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-423">If a derived data contract has a data member with the same name as a data member in a base data contract but a different type, the `DataContractSerializer` imports a schema with an element of the type `xs:anyType` in both base type and derived type declarations.</span></span> <span data-ttu-id="f6e9b-424">Orijinal tür adının de korunur `xs:annotations/xs:appInfo/ser:ActualType/@Name`.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-424">The original type name is preserved in `xs:annotations/xs:appInfo/ser:ActualType/@Name`.</span></span>  
  
 <span data-ttu-id="f6e9b-425">Her iki Çeşitleme ile ilgili veri üyeleri bazında bağlıdır belirsiz bir içerik modeli, bir şemaya neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-425">Both variations may lead to a schema with an ambiguous content model, which depends on the order of the respective data members.</span></span>  
  
## <a name="typeprimitive-mapping"></a><span data-ttu-id="f6e9b-426">Tür/temel eşleme</span><span class="sxs-lookup"><span data-stu-id="f6e9b-426">Type/primitive mapping</span></span>  
 <span data-ttu-id="f6e9b-427">`DataContractSerializer` Temel türler için XML Şeması aşağıdaki eşlemeyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-427">The `DataContractSerializer` uses the following mapping for XML Schema primitive types.</span></span>  
  
|<span data-ttu-id="f6e9b-428">XSD türü</span><span class="sxs-lookup"><span data-stu-id="f6e9b-428">XSD type</span></span>|<span data-ttu-id="f6e9b-429">.NET türü</span><span class="sxs-lookup"><span data-stu-id="f6e9b-429">.NET type</span></span>|  
|--------------|---------------|  
|`anyType`|<span data-ttu-id="f6e9b-430"><xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-430"><xref:System.Object>.</span></span>|  
|`anySimpleType`|<span data-ttu-id="f6e9b-431"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-431"><xref:System.String>.</span></span>|  
|`duration`|<span data-ttu-id="f6e9b-432"><xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-432"><xref:System.TimeSpan>.</span></span>|  
|`dateTime`|<span data-ttu-id="f6e9b-433"><xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-433"><xref:System.DateTime>.</span></span>|  
|`dateTimeOffset`|<span data-ttu-id="f6e9b-434"><xref:System.DateTime> ve <xref:System.TimeSpan> kaydırmanın.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-434"><xref:System.DateTime> and <xref:System.TimeSpan> for the offset.</span></span> <span data-ttu-id="f6e9b-435">DateTimeOffset serileştirme aşağıya bakın.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-435">See DateTimeOffset Serialization below.</span></span>|  
|`time`|<span data-ttu-id="f6e9b-436"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-436"><xref:System.String>.</span></span>|  
|`date`|<span data-ttu-id="f6e9b-437"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-437"><xref:System.String>.</span></span>|  
|`gYearMonth`|<span data-ttu-id="f6e9b-438"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-438"><xref:System.String>.</span></span>|  
|`gYear`|<span data-ttu-id="f6e9b-439"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-439"><xref:System.String>.</span></span>|  
|`gMonthDay`|<span data-ttu-id="f6e9b-440"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-440"><xref:System.String>.</span></span>|  
|`gDay`|<span data-ttu-id="f6e9b-441"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-441"><xref:System.String>.</span></span>|  
|`gMonth`|<span data-ttu-id="f6e9b-442"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-442"><xref:System.String>.</span></span>|  
|`boolean`|<xref:System.Boolean>|  
|`base64Binary`|<span data-ttu-id="f6e9b-443"><xref:System.Byte> dizisi.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-443"><xref:System.Byte> array.</span></span>|  
|`hexBinary`|<span data-ttu-id="f6e9b-444"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-444"><xref:System.String>.</span></span>|  
|`float`|<span data-ttu-id="f6e9b-445"><xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-445"><xref:System.Single>.</span></span>|  
|`double`|<span data-ttu-id="f6e9b-446"><xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-446"><xref:System.Double>.</span></span>|  
|`anyURI`|<span data-ttu-id="f6e9b-447"><xref:System.Uri>.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-447"><xref:System.Uri>.</span></span>|  
|`QName`|<span data-ttu-id="f6e9b-448"><xref:System.Xml.XmlQualifiedName>.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-448"><xref:System.Xml.XmlQualifiedName>.</span></span>|  
|`string`|<span data-ttu-id="f6e9b-449"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-449"><xref:System.String>.</span></span>|  
|`normalizedString`|<span data-ttu-id="f6e9b-450"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-450"><xref:System.String>.</span></span>|  
|`token`|<span data-ttu-id="f6e9b-451"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-451"><xref:System.String>.</span></span>|  
|`language`|<span data-ttu-id="f6e9b-452"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-452"><xref:System.String>.</span></span>|  
|`Name`|<span data-ttu-id="f6e9b-453"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-453"><xref:System.String>.</span></span>|  
|`NCName`|<span data-ttu-id="f6e9b-454"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-454"><xref:System.String>.</span></span>|  
|`ID`|<span data-ttu-id="f6e9b-455"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-455"><xref:System.String>.</span></span>|  
|`IDREF`|<span data-ttu-id="f6e9b-456"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-456"><xref:System.String>.</span></span>|  
|`IDREFS`|<span data-ttu-id="f6e9b-457"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-457"><xref:System.String>.</span></span>|  
|`ENTITY`|<span data-ttu-id="f6e9b-458"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-458"><xref:System.String>.</span></span>|  
|`ENTITIES`|<span data-ttu-id="f6e9b-459"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-459"><xref:System.String>.</span></span>|  
|`NMTOKEN`|<span data-ttu-id="f6e9b-460"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-460"><xref:System.String>.</span></span>|  
|`NMTOKENS`|<span data-ttu-id="f6e9b-461"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-461"><xref:System.String>.</span></span>|  
|`decimal`|<span data-ttu-id="f6e9b-462"><xref:System.Decimal>.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-462"><xref:System.Decimal>.</span></span>|  
|`integer`|<span data-ttu-id="f6e9b-463"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-463"><xref:System.Int64>.</span></span>|  
|`nonPositiveInteger`|<span data-ttu-id="f6e9b-464"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-464"><xref:System.Int64>.</span></span>|  
|`negativeInteger`|<span data-ttu-id="f6e9b-465"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-465"><xref:System.Int64>.</span></span>|  
|`long`|<span data-ttu-id="f6e9b-466"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-466"><xref:System.Int64>.</span></span>|  
|`int`|<span data-ttu-id="f6e9b-467"><xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-467"><xref:System.Int32>.</span></span>|  
|`short`|<span data-ttu-id="f6e9b-468"><xref:System.Int16>.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-468"><xref:System.Int16>.</span></span>|  
|`Byte`|<span data-ttu-id="f6e9b-469"><xref:System.SByte>.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-469"><xref:System.SByte>.</span></span>|  
|`nonNegativeInteger`|<span data-ttu-id="f6e9b-470"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-470"><xref:System.Int64>.</span></span>|  
|`unsignedLong`|<span data-ttu-id="f6e9b-471"><xref:System.UInt64>.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-471"><xref:System.UInt64>.</span></span>|  
|`unsignedInt`|<span data-ttu-id="f6e9b-472"><xref:System.UInt32>.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-472"><xref:System.UInt32>.</span></span>|  
|`unsignedShort`|<span data-ttu-id="f6e9b-473"><xref:System.UInt16>.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-473"><xref:System.UInt16>.</span></span>|  
|`unsignedByte`|<span data-ttu-id="f6e9b-474"><xref:System.Byte>.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-474"><xref:System.Byte>.</span></span>|  
|`positiveInteger`|<span data-ttu-id="f6e9b-475"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-475"><xref:System.Int64>.</span></span>|  
  
## <a name="iserializable-types-mapping"></a><span data-ttu-id="f6e9b-476">Eşleme ISerializable türler</span><span class="sxs-lookup"><span data-stu-id="f6e9b-476">ISerializable types mapping</span></span>  
 <span data-ttu-id="f6e9b-477">İçinde [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sürüm 1.0, `ISerializable` Kalıcılık ya da veri aktarımı için nesneleri serileştirmek için genel bir mekanizma olarak kullanıma sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-477">In [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] version 1.0, `ISerializable` was introduced as a general mechanism to serialize objects for persistence or data transfer.</span></span> <span data-ttu-id="f6e9b-478">Kullanabileceğiniz birçok [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] türleri uygulayan `ISerializable` ve uygulamalar arasında geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-478">There are many [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] types that implement `ISerializable` and that can be passed between applications.</span></span> <span data-ttu-id="f6e9b-479">`DataContractSerializer` doğal olarak için destek sağlar `ISerializable` sınıfları.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-479">`DataContractSerializer` naturally provides support for `ISerializable` classes.</span></span> <span data-ttu-id="f6e9b-480">`DataContractSerializer` Eşler `ISerializable` uygulama şema türü, yalnızca QName türü tarafından (tam adı) değişir ve etkili bir şekilde özellik koleksiyonlarıdır.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-480">The `DataContractSerializer` maps `ISerializable` implementation schema types that differ only by the QName (qualified name) of the type and are effectively property collections.</span></span> <span data-ttu-id="f6e9b-481">Örneğin, `DataContractSerializer` eşler <xref:System.Exception> aşağıdaki XSD türüne `http://schemas.datacontract.org/2004/07/System` ad alanı.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-481">For example, the `DataContractSerializer` maps <xref:System.Exception> to the following XSD type in the `http://schemas.datacontract.org/2004/07/System` namespace.</span></span>  
  
```xml  
<xs:complexType name="Exception">  
 <xs:sequence>  
  <xs:any minOccurs="0" maxOccurs="unbounded"   
      namespace="##local" processContents="skip"/>  
 </xs:sequence>  
 <xs:attribute ref="ser:FactoryType"/>  
</xs:complexType>  
```  
  
 <span data-ttu-id="f6e9b-482">İsteğe bağlı öznitelik `ser:FactoryType` veri sözleşme serileştirme içinde bildirilen şema türü seri durumdan çıkarabiliyorsa bir Üreteç sınıfını başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-482">The optional attribute `ser:FactoryType` declared in the Data Contract Serialization schema references a factory class that can deserialize the type.</span></span> <span data-ttu-id="f6e9b-483">Fabrika sınıfı Bilinen türlerin koleksiyonuna bir parçası olarak `DataContractSerializer` kullanılan örnek.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-483">The factory class must be part of the known types collection of the `DataContractSerializer` instance being used.</span></span> <span data-ttu-id="f6e9b-484">Bilinen türler hakkında daha fazla bilgi için bkz: [veri sözleşme bilinen türleri](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="f6e9b-484">For more information about known types, see [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="datacontract-serialization-schema"></a><span data-ttu-id="f6e9b-485">DataContract serileştirme şeması</span><span class="sxs-lookup"><span data-stu-id="f6e9b-485">DataContract Serialization Schema</span></span>  
 <span data-ttu-id="f6e9b-486">Bir dizi Şemaları dışarı tarafından `DataContractSerializer` türleri, öğeleri ve bir özel veri sözleşme serileştirme ad öznitelikleri kullanın:</span><span class="sxs-lookup"><span data-stu-id="f6e9b-486">A number of schemas exported by the `DataContractSerializer` use types, elements, and attributes from a special Data Contract Serialization namespace:</span></span>  
  
 `http://schemas.microsoft.com/2003/10/Serialization`
  
 <span data-ttu-id="f6e9b-487">Eksiksiz bir veri sözleşme serileştirme şeması bildirimi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-487">The following is a complete Data Contract Serialization schema declaration.</span></span>  
  
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
  
 <span data-ttu-id="f6e9b-488">Aşağıdakiler dikkate alınmalıdır:</span><span class="sxs-lookup"><span data-stu-id="f6e9b-488">The following should be noted:</span></span>  
  
-   <span data-ttu-id="f6e9b-489">`ser:char` tür Unicode karakterlerini temsil etmek için sunulan <xref:System.Char>.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-489">`ser:char` is introduced to represent Unicode characters of type <xref:System.Char>.</span></span>  
  
-   <span data-ttu-id="f6e9b-490">`valuespace` , `xs:duration` Sıralı bir küme için daha az için eşlenebilir bir <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-490">The `valuespace` of `xs:duration` is reduced to an ordered set so that it can be mapped to a <xref:System.TimeSpan>.</span></span>  
  
-   <span data-ttu-id="f6e9b-491">`FactoryType` öğesinden türetilen türler dışarı şemalar kullanılır <xref:System.Runtime.Serialization.ISerializable>.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-491">`FactoryType` is used in schemas exported from types that are derived from <xref:System.Runtime.Serialization.ISerializable>.</span></span>  
  
## <a name="importing-non-datacontract-schemas"></a><span data-ttu-id="f6e9b-492">DataContract olmayan şemaları alma</span><span class="sxs-lookup"><span data-stu-id="f6e9b-492">Importing non-DataContract schemas</span></span>  
 <span data-ttu-id="f6e9b-493">`DataContractSerializer` sahip `ImportXmlTypes` seçeneği için uygun olmayan şemaları alma izni `DataContractSerializer` XSD profili (bkz <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> özelliği).</span><span class="sxs-lookup"><span data-stu-id="f6e9b-493">`DataContractSerializer` has the `ImportXmlTypes` option to allow import of schemas that do not conform to the `DataContractSerializer` XSD profile (see the <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> property).</span></span> <span data-ttu-id="f6e9b-494">Bu seçeneğin ayarlanması `true` kabul DSCP şema türleri ve bunları aşağıdaki uygulama için eşleme sağlayan <xref:System.Xml.Serialization.IXmlSerializable> dizisi sarmalama <xref:System.Xml.XmlNode> (yalnızca sınıf adını farklıdır).</span><span class="sxs-lookup"><span data-stu-id="f6e9b-494">Setting this option to `true` enables acceptance of non-conforming schema types and mapping them to the following implementation, <xref:System.Xml.Serialization.IXmlSerializable> wrapping an array of <xref:System.Xml.XmlNode> (only the class name differs).</span></span>  
  
```  
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
  
## <a name="datetimeoffset-serialization"></a><span data-ttu-id="f6e9b-495">DateTimeOffset seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="f6e9b-495">DateTimeOffset Serialization</span></span>  
 <span data-ttu-id="f6e9b-496"><xref:System.DateTimeOffset> Türü bir basit tür olarak işlenmez.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-496">The <xref:System.DateTimeOffset> is not treated as a primitive type.</span></span> <span data-ttu-id="f6e9b-497">Bunun yerine, bu iki bölümleri içeren karmaşık bir öğe olarak serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-497">Instead, it is serialized as a complex element with two parts.</span></span> <span data-ttu-id="f6e9b-498">İlk bölümü tarih saat ve ikinci bölümü, tarih saati uzaklığı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-498">The first part represents the date time, and the second part represents the offset from the date time.</span></span> <span data-ttu-id="f6e9b-499">Aşağıdaki kodda bir örneğini serileştirilmiş bir DateTimeOffset değer gösterilir.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-499">An example of a serialized DateTimeOffset value is shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="f6e9b-500">Şeması aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-500">The schema is as follows.</span></span>  
  
```xml  
<xs:schema targetNamespace="http://schemas.datacontract.org/2004/07/System">  
   <xs:complexType name="DateTimeOffset">  
      <xs:sequence minOccurs="1" maxOccurs="1">  
         <xs:element name="DateTime" type="xs:dateTime"  
         minOccurs="1" maxOccurs="1" />  
         <xs:elementname="OffsetMinutes" type="xs:short"  
         minOccurs="1" maxOccurs="1" />  
      </xs:sequence>  
   </xs:complexType>  
</xs:schema>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f6e9b-501">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f6e9b-501">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 <xref:System.Runtime.Serialization.XsdDataContractImporter>  
 [<span data-ttu-id="f6e9b-502">Veri Anlaşmalarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="f6e9b-502">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)

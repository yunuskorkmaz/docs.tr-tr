---
title: '&lt;Property&gt; Öğesi (.NET Yerel)'
ms.date: 03/30/2017
ms.assetid: ad4ba56d-3bcb-4c10-ba90-1cc66e2175a1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 47ed75d377814a740edece2b6a69e44acbd8ef0c
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45527717"
---
# <a name="ltpropertygt-element-net-native"></a><span data-ttu-id="ab75f-102">&lt;Property&gt; Öğesi (.NET Yerel)</span><span class="sxs-lookup"><span data-stu-id="ab75f-102">&lt;Property&gt; Element (.NET Native)</span></span>
<span data-ttu-id="ab75f-103">Çalışma zamanı yansıma ilkesini bir özellik için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="ab75f-103">Applies runtime reflection policy to a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab75f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ab75f-104">Syntax</span></span>  
  
```xml  
<Property Name="property_name"  
          Browse="policy_type"  
          Dynamic="policy_type"  
          Serialize="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ab75f-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ab75f-105">Attributes and Elements</span></span>  
 <span data-ttu-id="ab75f-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ab75f-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ab75f-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ab75f-107">Attributes</span></span>  
  
|<span data-ttu-id="ab75f-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ab75f-108">Attribute</span></span>|<span data-ttu-id="ab75f-109">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="ab75f-109">Attribute type</span></span>|<span data-ttu-id="ab75f-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ab75f-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="ab75f-111">Genel</span><span class="sxs-lookup"><span data-stu-id="ab75f-111">General</span></span>|<span data-ttu-id="ab75f-112">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="ab75f-112">Required attribute.</span></span> <span data-ttu-id="ab75f-113">Özellik adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ab75f-113">Specifies the property name.</span></span>|  
|`Browse`|<span data-ttu-id="ab75f-114">Yansıma</span><span class="sxs-lookup"><span data-stu-id="ab75f-114">Reflection</span></span>|<span data-ttu-id="ab75f-115">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="ab75f-115">Optional attribute.</span></span> <span data-ttu-id="ab75f-116">Hakkında bilgi için sorgulama veya özellik numaralandırma denetler, ancak çalışma zamanında herhangi bir dinamik erişim sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="ab75f-116">Controls querying for information about or enumerating the property but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="ab75f-117">Yansıma</span><span class="sxs-lookup"><span data-stu-id="ab75f-117">Reflection</span></span>|<span data-ttu-id="ab75f-118">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="ab75f-118">Optional attribute.</span></span> <span data-ttu-id="ab75f-119">Programlama. özelliği dinamik etkinleştirmek için çalışma zamanı erişimi denetler.</span><span class="sxs-lookup"><span data-stu-id="ab75f-119">Controls runtime access to the property to enable dynamic programming.</span></span> <span data-ttu-id="ab75f-120">Bu ilke, bir özellik ayarlanabilir veya çalışma zamanında dinamik olarak alınan olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="ab75f-120">This policy ensures that a property can be set or retrieved dynamically at run time.</span></span>|  
|`Serialize`|<span data-ttu-id="ab75f-121">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="ab75f-121">Serialization</span></span>|<span data-ttu-id="ab75f-122">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="ab75f-122">Optional attribute.</span></span> <span data-ttu-id="ab75f-123">Çalışma zamanı kitaplıkları gibi Newtonsoft JSON seri hale getirici tarafından serileştirilecek veya veri bağlama için kullanılacak tür örnekleri etkinleştirmek için bir özellik erişimi denetler.</span><span class="sxs-lookup"><span data-stu-id="ab75f-123">Controls runtime access to a property to enable type instances to be serialized by libraries such as the Newtonsoft JSON serializer or to be used for data binding.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="ab75f-124">Ad özniteliği</span><span class="sxs-lookup"><span data-stu-id="ab75f-124">Name attribute</span></span>  
  
|<span data-ttu-id="ab75f-125">Değer</span><span class="sxs-lookup"><span data-stu-id="ab75f-125">Value</span></span>|<span data-ttu-id="ab75f-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ab75f-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ab75f-127">*method_name*</span><span class="sxs-lookup"><span data-stu-id="ab75f-127">*method_name*</span></span>|<span data-ttu-id="ab75f-128">Özellik adı.</span><span class="sxs-lookup"><span data-stu-id="ab75f-128">The property name.</span></span> <span data-ttu-id="ab75f-129">Özelliğin türü üst öğe tarafından tanımlanan [ \<türü >](../../../docs/framework/net-native/type-element-net-native.md) veya [ \<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="ab75f-129">The type of the property is defined by the parent [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) or [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="ab75f-130">Diğer tüm öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ab75f-130">All other attributes</span></span>  
  
|<span data-ttu-id="ab75f-131">Değer</span><span class="sxs-lookup"><span data-stu-id="ab75f-131">Value</span></span>|<span data-ttu-id="ab75f-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ab75f-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ab75f-133">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="ab75f-133">*policy_setting*</span></span>|<span data-ttu-id="ab75f-134">Bu ilke türü özelliği için geçerli ayar.</span><span class="sxs-lookup"><span data-stu-id="ab75f-134">The setting to apply to this policy type for the property.</span></span> <span data-ttu-id="ab75f-135">Olası değerler `Auto`, `Excluded`, `Included`, ve `Required`.</span><span class="sxs-lookup"><span data-stu-id="ab75f-135">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="ab75f-136">Daha fazla bilgi için [çalışma zamanı yönerge İlkesi ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="ab75f-136">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ab75f-137">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ab75f-137">Child Elements</span></span>  
 <span data-ttu-id="ab75f-138">Yok.</span><span class="sxs-lookup"><span data-stu-id="ab75f-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ab75f-139">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ab75f-139">Parent Elements</span></span>  
  
|<span data-ttu-id="ab75f-140">Öğe</span><span class="sxs-lookup"><span data-stu-id="ab75f-140">Element</span></span>|<span data-ttu-id="ab75f-141">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ab75f-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ab75f-142">\<türü ></span><span class="sxs-lookup"><span data-stu-id="ab75f-142">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="ab75f-143">Yansıma İlkesi, bir tür ve tüm üyeleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="ab75f-143">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="ab75f-144">\<Typeınstantiation ></span><span class="sxs-lookup"><span data-stu-id="ab75f-144">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="ab75f-145">Yansıma ilkesini, oluşturulmuş bir genel türü ve tüm üyeleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="ab75f-145">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ab75f-146">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ab75f-146">Remarks</span></span>  
 <span data-ttu-id="ab75f-147">Bir özelliğin ilke açıkça tanımlı değilse, kendi üst öğenin çalışma zamanı ilkesini devralır.</span><span class="sxs-lookup"><span data-stu-id="ab75f-147">If a property's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab75f-148">Örnek</span><span class="sxs-lookup"><span data-stu-id="ab75f-148">Example</span></span>  
 <span data-ttu-id="ab75f-149">Aşağıdaki örnek, örneklemek için yansıtma kullanır. bir `Book` nesne ve özellik değerlerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="ab75f-149">The following example uses reflection to instantiate a `Book` object and display its property values.</span></span> <span data-ttu-id="ab75f-150">Projesi için özgün default.rd.xml dosyasını aşağıdaki gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="ab75f-150">The original default.rd.xml file for the project appears as follows:</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Namespace Name="LibraryApplications"  Browse="Required Public" >  
         <Type Name="Book"   Activate="All" />  
      </Namespace>  
   </Application>  
</Directives>  
```  
  
 <span data-ttu-id="ab75f-151">Dosya geçerli `All` değerini `Activate` İlkesi `Book` sınıf oluşturucuları yansıma aracılığıyla erişmesini sağlar sınıfını.</span><span class="sxs-lookup"><span data-stu-id="ab75f-151">The file applies the `All` value to the `Activate` policy for the `Book` class, which allows access to class constructors through reflection.</span></span> <span data-ttu-id="ab75f-152">`Browse` İlkesi `Book` sınıfı, kendi üst ad alanından devralınır.</span><span class="sxs-lookup"><span data-stu-id="ab75f-152">The `Browse` policy for the `Book` class is inherited from its parent namespace.</span></span> <span data-ttu-id="ab75f-153">Bu ayar `Required Public`, hangi kullanımınıza meta verileri çalışma zamanında.</span><span class="sxs-lookup"><span data-stu-id="ab75f-153">This is set to `Required Public`, which makes metadata available at runtime.</span></span>  
  
 <span data-ttu-id="ab75f-154">Örnek kaynak kodu verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ab75f-154">The following is the source code for the example.</span></span> <span data-ttu-id="ab75f-155">`outputBlock` Değişkenini temsil eder bir [TextBlock](https://msdn.microsoft.com/library/windows.ui.xaml.controls.textblock.aspx) denetimi.</span><span class="sxs-lookup"><span data-stu-id="ab75f-155">The `outputBlock` variable represents a [TextBlock](https://msdn.microsoft.com/library/windows.ui.xaml.controls.textblock.aspx) control.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/property1.cs#6)]  
  
 <span data-ttu-id="ab75f-156">Ancak, derleme ve bu örnek yürütme oluşturur bir [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) özel durum.</span><span class="sxs-lookup"><span data-stu-id="ab75f-156">However, compiling and executing this example throws a [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) exception.</span></span> <span data-ttu-id="ab75f-157">Meta veri yaptık olsa da `Book` türü kullanılabilir alamadık özellik alıcıları uygulamaları dinamik olarak kullanılabilir hale getirmek.</span><span class="sxs-lookup"><span data-stu-id="ab75f-157">Although we've made metadata for the `Book` type available, we've failed to make the implementations of the property getters available dynamically.</span></span> <span data-ttu-id="ab75f-158">Tarafından iki yoldan biriyle ya da Biz bu hatayı düzeltebilir:</span><span class="sxs-lookup"><span data-stu-id="ab75f-158">We can correct this error by either in one of two ways:</span></span>  
  
-   <span data-ttu-id="ab75f-159">tanımlayarak `Dynamic` İlkesi `Book` yazın, [ \<türü >](../../../docs/framework/net-native/type-element-net-native.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="ab75f-159">by defining the `Dynamic` policy for the `Book` type in its [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) element.</span></span>  
  
-   <span data-ttu-id="ab75f-160">İç içe bir ekleyerek [ \<özellik >](../../../docs/framework/net-native/property-element-net-native.md) default.rd.xml dosyanın aşağıdaki gibi alıcı çağırmak için istiyoruz her özellik için öğesi.</span><span class="sxs-lookup"><span data-stu-id="ab75f-160">By adding a nested [\<Property>](../../../docs/framework/net-native/property-element-net-native.md) element for each property whose getter we'd like to invoke, as the following default.rd.xml file does.</span></span>  
  
    ```xml  
    <Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
       <Application>  
          <Namespace Name="LibraryApplications"  Browse="Required Public" >  
             <Type Name="Book"   Activate="All" >  
                <Property Name="Title" Dynamic="Required" />  
                <Property Name="Author" Dynamic="Required" />  
                  <Property Name="ISBN" Dynamic="Required" />  
             </Type>  
          </Namespace>  
       </Application>  
    </Directives>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="ab75f-161">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ab75f-161">See Also</span></span>  
 [<span data-ttu-id="ab75f-162">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="ab75f-162">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="ab75f-163">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="ab75f-163">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [<span data-ttu-id="ab75f-164">Çalışma Zamanı Yönerge İlkesi Ayarları</span><span class="sxs-lookup"><span data-stu-id="ab75f-164">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)

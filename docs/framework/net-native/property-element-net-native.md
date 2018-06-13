---
title: '&lt;Property&gt; Öğesi (.NET Yerel)'
ms.date: 03/30/2017
ms.assetid: ad4ba56d-3bcb-4c10-ba90-1cc66e2175a1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8a857523b15631aa9c112c9c0d208d96b0ec0d4a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33396465"
---
# <a name="ltpropertygt-element-net-native"></a><span data-ttu-id="bfd61-102">&lt;Property&gt; Öğesi (.NET Yerel)</span><span class="sxs-lookup"><span data-stu-id="bfd61-102">&lt;Property&gt; Element (.NET Native)</span></span>
<span data-ttu-id="bfd61-103">Çalışma zamanı yansıma İlkesi bir özellik için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="bfd61-103">Applies runtime reflection policy to a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfd61-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bfd61-104">Syntax</span></span>  
  
```xml  
<Property Name="property_name"  
          Browse="policy_type"  
          Dynamic="policy_type"  
          Serialize="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bfd61-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="bfd61-105">Attributes and Elements</span></span>  
 <span data-ttu-id="bfd61-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bfd61-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bfd61-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bfd61-107">Attributes</span></span>  
  
|<span data-ttu-id="bfd61-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="bfd61-108">Attribute</span></span>|<span data-ttu-id="bfd61-109">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="bfd61-109">Attribute type</span></span>|<span data-ttu-id="bfd61-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bfd61-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="bfd61-111">Genel</span><span class="sxs-lookup"><span data-stu-id="bfd61-111">General</span></span>|<span data-ttu-id="bfd61-112">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="bfd61-112">Required attribute.</span></span> <span data-ttu-id="bfd61-113">Özellik adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="bfd61-113">Specifies the property name.</span></span>|  
|`Browse`|<span data-ttu-id="bfd61-114">Yansıma</span><span class="sxs-lookup"><span data-stu-id="bfd61-114">Reflection</span></span>|<span data-ttu-id="bfd61-115">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="bfd61-115">Optional attribute.</span></span> <span data-ttu-id="bfd61-116">Hakkında bilgi için sorgulama veya özellik numaralandırma kontrol eder, ancak herhangi bir dinamik erişim çalışma zamanında etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="bfd61-116">Controls querying for information about or enumerating the property but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="bfd61-117">Yansıma</span><span class="sxs-lookup"><span data-stu-id="bfd61-117">Reflection</span></span>|<span data-ttu-id="bfd61-118">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="bfd61-118">Optional attribute.</span></span> <span data-ttu-id="bfd61-119">Programlama dinamik etkinleştirmek için özellik çalışma zamanı erişimi kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="bfd61-119">Controls runtime access to the property to enable dynamic programming.</span></span> <span data-ttu-id="bfd61-120">Bu ilke, bir özellik ayarlanabilir veya çalışma zamanında dinamik olarak alınan olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="bfd61-120">This policy ensures that a property can be set or retrieved dynamically at run time.</span></span>|  
|`Serialize`|<span data-ttu-id="bfd61-121">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="bfd61-121">Serialization</span></span>|<span data-ttu-id="bfd61-122">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="bfd61-122">Optional attribute.</span></span> <span data-ttu-id="bfd61-123">Bir özellik türü örnekleri kitaplıklar gibi Newtonsoft JSON seri hale getirici tarafından seri hale veya veri bağlaması için kullanılmak üzere etkinleştirmek için çalışma zamanı erişimi kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="bfd61-123">Controls runtime access to a property to enable type instances to be serialized by libraries such as the Newtonsoft JSON serializer or to be used for data binding.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="bfd61-124">Ad özniteliği</span><span class="sxs-lookup"><span data-stu-id="bfd61-124">Name attribute</span></span>  
  
|<span data-ttu-id="bfd61-125">Değer</span><span class="sxs-lookup"><span data-stu-id="bfd61-125">Value</span></span>|<span data-ttu-id="bfd61-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bfd61-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="bfd61-127">*method_name*</span><span class="sxs-lookup"><span data-stu-id="bfd61-127">*method_name*</span></span>|<span data-ttu-id="bfd61-128">Özellik adı.</span><span class="sxs-lookup"><span data-stu-id="bfd61-128">The property name.</span></span> <span data-ttu-id="bfd61-129">Özelliğin türü üst tarafından tanımlanan [ \<türü >](../../../docs/framework/net-native/type-element-net-native.md) veya [ \<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="bfd61-129">The type of the property is defined by the parent [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) or [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="bfd61-130">Tüm diğer özniteliklerle</span><span class="sxs-lookup"><span data-stu-id="bfd61-130">All other attributes</span></span>  
  
|<span data-ttu-id="bfd61-131">Değer</span><span class="sxs-lookup"><span data-stu-id="bfd61-131">Value</span></span>|<span data-ttu-id="bfd61-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bfd61-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="bfd61-133">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="bfd61-133">*policy_setting*</span></span>|<span data-ttu-id="bfd61-134">Bu ilke türü özelliği için geçerli ayar.</span><span class="sxs-lookup"><span data-stu-id="bfd61-134">The setting to apply to this policy type for the property.</span></span> <span data-ttu-id="bfd61-135">Olası değerler şunlardır: `Auto`, `Excluded`, `Included`, ve `Required`.</span><span class="sxs-lookup"><span data-stu-id="bfd61-135">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="bfd61-136">Daha fazla bilgi için bkz: [çalışma zamanı yönerge İlkesi ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="bfd61-136">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bfd61-137">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="bfd61-137">Child Elements</span></span>  
 <span data-ttu-id="bfd61-138">Yok.</span><span class="sxs-lookup"><span data-stu-id="bfd61-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bfd61-139">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="bfd61-139">Parent Elements</span></span>  
  
|<span data-ttu-id="bfd61-140">Öğe</span><span class="sxs-lookup"><span data-stu-id="bfd61-140">Element</span></span>|<span data-ttu-id="bfd61-141">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bfd61-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bfd61-142">\<türü ></span><span class="sxs-lookup"><span data-stu-id="bfd61-142">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="bfd61-143">Yansıma ilke türü ve tüm üyeleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="bfd61-143">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="bfd61-144">\<Typeınstantiation ></span><span class="sxs-lookup"><span data-stu-id="bfd61-144">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="bfd61-145">Yansıma İlkesi, yapılandırılmış bir genel tür ve tüm üyeleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="bfd61-145">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bfd61-146">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bfd61-146">Remarks</span></span>  
 <span data-ttu-id="bfd61-147">Bir özelliğin İlkesi açıkça tanımlanmazsa, kendi üst öğesi, çalışma zamanı İlkesi devralır.</span><span class="sxs-lookup"><span data-stu-id="bfd61-147">If a property's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bfd61-148">Örnek</span><span class="sxs-lookup"><span data-stu-id="bfd61-148">Example</span></span>  
 <span data-ttu-id="bfd61-149">Aşağıdaki örnek örneği oluşturmak için yansıma kullanan bir `Book` nesne ve özellik değerlerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="bfd61-149">The following example uses reflection to instantiate a `Book` object and display its property values.</span></span> <span data-ttu-id="bfd61-150">Projesi için özgün default.rd.xml dosya şu şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="bfd61-150">The original default.rd.xml file for the project appears as follows:</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Namespace Name="LibraryApplications"  Browse="Required Public" >  
         <Type Name="Book"   Activate="All" />  
      </Namespace>  
   </Application>  
</Directives>  
```  
  
 <span data-ttu-id="bfd61-151">Dosyasının geçerli `All` değeri `Activate` için ilke `Book` sınıf oluşturucular yansıma aracılığıyla erişim sağlayan sınıf.</span><span class="sxs-lookup"><span data-stu-id="bfd61-151">The file applies the `All` value to the `Activate` policy for the `Book` class, which allows access to class constructors through reflection.</span></span> <span data-ttu-id="bfd61-152">`Browse` İçin ilke `Book` sınıfı, kendi üst ad alanından devralınır.</span><span class="sxs-lookup"><span data-stu-id="bfd61-152">The `Browse` policy for the `Book` class is inherited from its parent namespace.</span></span> <span data-ttu-id="bfd61-153">Bu ayar `Required Public`, hangi kullanılabilir hale getirir meta veri çalışma zamanında.</span><span class="sxs-lookup"><span data-stu-id="bfd61-153">This is set to `Required Public`, which makes metadata available at runtime.</span></span>  
  
 <span data-ttu-id="bfd61-154">Örneğin kaynak kodu verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="bfd61-154">The following is the source code for the example.</span></span> <span data-ttu-id="bfd61-155">`outputBlock` Değişkeni temsil eden bir [TextBlock](http://msdn.microsoft.com/library/windows.ui.xaml.controls.textblock.aspx) denetim.</span><span class="sxs-lookup"><span data-stu-id="bfd61-155">The `outputBlock` variable represents a [TextBlock](http://msdn.microsoft.com/library/windows.ui.xaml.controls.textblock.aspx) control.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/property1.cs#6)]  
  
 <span data-ttu-id="bfd61-156">Ancak, derleme ve bu örnek yürütme oluşturur bir [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) özel durum.</span><span class="sxs-lookup"><span data-stu-id="bfd61-156">However, compiling and executing this example throws a [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) exception.</span></span> <span data-ttu-id="bfd61-157">Meta veri yaptık rağmen `Book` kullanılabilen türü, alamadık özellik alıcıları uygulamaları dinamik olarak kullanılabilir hale getirmek.</span><span class="sxs-lookup"><span data-stu-id="bfd61-157">Although we've made metadata for the `Book` type available, we've failed to make the implementations of the property getters available dynamically.</span></span> <span data-ttu-id="bfd61-158">Biz bu hata ya da iki yoldan biriyle düzeltebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="bfd61-158">We can correct this error by either in one of two ways:</span></span>  
  
-   <span data-ttu-id="bfd61-159">tanımlayarak `Dynamic` için ilke `Book` yazın, [ \<türü >](../../../docs/framework/net-native/type-element-net-native.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="bfd61-159">by defining the `Dynamic` policy for the `Book` type in its [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) element.</span></span>  
  
-   <span data-ttu-id="bfd61-160">İç içe bir ekleyerek [ \<özelliği >](../../../docs/framework/net-native/property-element-net-native.md) aşağıdaki default.rd.xml dosya yaptığı gibi alıcı çağırmak için isteriz her özellik için öğesi.</span><span class="sxs-lookup"><span data-stu-id="bfd61-160">By adding a nested [\<Property>](../../../docs/framework/net-native/property-element-net-native.md) element for each property whose getter we'd like to invoke, as the following default.rd.xml file does.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bfd61-161">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bfd61-161">See Also</span></span>  
 [<span data-ttu-id="bfd61-162">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="bfd61-162">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="bfd61-163">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="bfd61-163">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [<span data-ttu-id="bfd61-164">Çalışma Zamanı Yönerge İlkesi Ayarları</span><span class="sxs-lookup"><span data-stu-id="bfd61-164">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)

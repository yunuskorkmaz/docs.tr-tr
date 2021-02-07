---
description: 'Daha fazla bilgi edinin: <Property> öğesi (.NET Native)'
title: <Property> Öğesi (.NET Native)
ms.date: 03/30/2017
ms.assetid: ad4ba56d-3bcb-4c10-ba90-1cc66e2175a1
ms.openlocfilehash: cd3c033fd2ce21b69ff0d8563f0782838f39b09f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738474"
---
# <a name="property-element-net-native"></a><span data-ttu-id="85d89-103">\<Property> Öğesi (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="85d89-103">\<Property> Element (.NET Native)</span></span>

<span data-ttu-id="85d89-104">Çalışma zamanı yansıtma ilkesini bir özelliğe uygular.</span><span class="sxs-lookup"><span data-stu-id="85d89-104">Applies runtime reflection policy to a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85d89-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="85d89-105">Syntax</span></span>  
  
```xml  
<Property Name="property_name"  
          Browse="policy_type"  
          Dynamic="policy_type"  
          Serialize="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="85d89-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="85d89-106">Attributes and Elements</span></span>  

 <span data-ttu-id="85d89-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="85d89-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="85d89-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="85d89-108">Attributes</span></span>  
  
|<span data-ttu-id="85d89-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="85d89-109">Attribute</span></span>|<span data-ttu-id="85d89-110">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="85d89-110">Attribute type</span></span>|<span data-ttu-id="85d89-111">Description</span><span class="sxs-lookup"><span data-stu-id="85d89-111">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="85d89-112">Genel</span><span class="sxs-lookup"><span data-stu-id="85d89-112">General</span></span>|<span data-ttu-id="85d89-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="85d89-113">Required attribute.</span></span> <span data-ttu-id="85d89-114">Özellik adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="85d89-114">Specifies the property name.</span></span>|  
|`Browse`|<span data-ttu-id="85d89-115">Yansıma</span><span class="sxs-lookup"><span data-stu-id="85d89-115">Reflection</span></span>|<span data-ttu-id="85d89-116">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="85d89-116">Optional attribute.</span></span> <span data-ttu-id="85d89-117">Özelliği hakkında bilgi sorgulamayı denetler, ancak çalışma zamanında herhangi bir dinamik erişimi etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="85d89-117">Controls querying for information about or enumerating the property but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="85d89-118">Yansıma</span><span class="sxs-lookup"><span data-stu-id="85d89-118">Reflection</span></span>|<span data-ttu-id="85d89-119">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="85d89-119">Optional attribute.</span></span> <span data-ttu-id="85d89-120">Dinamik programlamayı etkinleştirmek için özelliğe çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="85d89-120">Controls runtime access to the property to enable dynamic programming.</span></span> <span data-ttu-id="85d89-121">Bu ilke, bir özelliğin çalışma zamanında dinamik olarak ayarlanamayacağını veya alınamayacağını sağlar.</span><span class="sxs-lookup"><span data-stu-id="85d89-121">This policy ensures that a property can be set or retrieved dynamically at run time.</span></span>|  
|`Serialize`|<span data-ttu-id="85d89-122">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="85d89-122">Serialization</span></span>|<span data-ttu-id="85d89-123">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="85d89-123">Optional attribute.</span></span> <span data-ttu-id="85d89-124">Tür örneklerinin, Newtonsoft JSON serileştirici veya veri bağlama için kullanılması gibi kitaplıklar tarafından serileştirilmesi için bir özelliğe çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="85d89-124">Controls runtime access to a property to enable type instances to be serialized by libraries such as the Newtonsoft JSON serializer or to be used for data binding.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="85d89-125">Ad özniteliği</span><span class="sxs-lookup"><span data-stu-id="85d89-125">Name attribute</span></span>  
  
|<span data-ttu-id="85d89-126">Değer</span><span class="sxs-lookup"><span data-stu-id="85d89-126">Value</span></span>|<span data-ttu-id="85d89-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="85d89-127">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="85d89-128">*method_name*</span><span class="sxs-lookup"><span data-stu-id="85d89-128">*method_name*</span></span>|<span data-ttu-id="85d89-129">Özellik adı.</span><span class="sxs-lookup"><span data-stu-id="85d89-129">The property name.</span></span> <span data-ttu-id="85d89-130">Özelliğin türü üst [\<Type>](type-element-net-native.md) veya öğe tarafından tanımlanır [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="85d89-130">The type of the property is defined by the parent [\<Type>](type-element-net-native.md) or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="85d89-131">Diğer tüm öznitelikler</span><span class="sxs-lookup"><span data-stu-id="85d89-131">All other attributes</span></span>  
  
|<span data-ttu-id="85d89-132">Değer</span><span class="sxs-lookup"><span data-stu-id="85d89-132">Value</span></span>|<span data-ttu-id="85d89-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="85d89-133">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="85d89-134">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="85d89-134">*policy_setting*</span></span>|<span data-ttu-id="85d89-135">Özelliği için bu ilke türüne uygulanacak ayar.</span><span class="sxs-lookup"><span data-stu-id="85d89-135">The setting to apply to this policy type for the property.</span></span> <span data-ttu-id="85d89-136">Olası değerler şunlardır,, `Auto` `Excluded` `Included` ve `Required` .</span><span class="sxs-lookup"><span data-stu-id="85d89-136">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="85d89-137">Daha fazla bilgi için bkz. [çalışma zamanı yönergesi Ilke ayarları](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="85d89-137">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="85d89-138">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="85d89-138">Child Elements</span></span>  

 <span data-ttu-id="85d89-139">Yok.</span><span class="sxs-lookup"><span data-stu-id="85d89-139">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="85d89-140">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="85d89-140">Parent Elements</span></span>  
  
|<span data-ttu-id="85d89-141">Öğe</span><span class="sxs-lookup"><span data-stu-id="85d89-141">Element</span></span>|<span data-ttu-id="85d89-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="85d89-142">Description</span></span>|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="85d89-143">Yansıma ilkesini bir türe ve tüm üyelerine uygular.</span><span class="sxs-lookup"><span data-stu-id="85d89-143">Applies reflection policy to a type and all its members.</span></span>|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="85d89-144">Oluşturulan genel türe ve tüm üyelerine yansıma ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="85d89-144">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="85d89-145">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="85d89-145">Remarks</span></span>  

 <span data-ttu-id="85d89-146">Bir özelliğin İlkesi açıkça tanımlanmamışsa, üst öğesinin çalışma zamanı ilkesini devralır.</span><span class="sxs-lookup"><span data-stu-id="85d89-146">If a property's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="85d89-147">Örnek</span><span class="sxs-lookup"><span data-stu-id="85d89-147">Example</span></span>  

 <span data-ttu-id="85d89-148">Aşağıdaki örnek, bir nesnenin örneğini oluşturmak `Book` ve özellik değerlerini göstermek için yansıma kullanır.</span><span class="sxs-lookup"><span data-stu-id="85d89-148">The following example uses reflection to instantiate a `Book` object and display its property values.</span></span> <span data-ttu-id="85d89-149">Projenin özgün default.rd.xml dosyası şu şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="85d89-149">The original default.rd.xml file for the project appears as follows:</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Namespace Name="LibraryApplications"  Browse="Required Public" >  
         <Type Name="Book"   Activate="All" />  
      </Namespace>  
   </Application>  
</Directives>  
```  
  
 <span data-ttu-id="85d89-150">Dosya, `All` `Activate` `Book` yansıma aracılığıyla sınıf oluşturuculara erişime izin veren sınıfının ilkesine değeri uygular.</span><span class="sxs-lookup"><span data-stu-id="85d89-150">The file applies the `All` value to the `Activate` policy for the `Book` class, which allows access to class constructors through reflection.</span></span> <span data-ttu-id="85d89-151">`Browse`Sınıfın ilkesi, `Book` üst ad alanından devralınır.</span><span class="sxs-lookup"><span data-stu-id="85d89-151">The `Browse` policy for the `Book` class is inherited from its parent namespace.</span></span> <span data-ttu-id="85d89-152">Bu `Required Public` , meta verileri çalışma zamanında kullanılabilir hale getiren olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="85d89-152">This is set to `Required Public`, which makes metadata available at runtime.</span></span>  
  
 <span data-ttu-id="85d89-153">Örnek için kaynak kodu aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="85d89-153">The following is the source code for the example.</span></span> <span data-ttu-id="85d89-154">`outputBlock`Değişkeni bir denetimi temsil eder <xref:Windows.UI.Xaml.Controls.TextBlock> .</span><span class="sxs-lookup"><span data-stu-id="85d89-154">The `outputBlock` variable represents a <xref:Windows.UI.Xaml.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/property1.cs#6)]  
  
 <span data-ttu-id="85d89-155">Ancak, bu örneği derlemek ve yürütmek bir [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) özel durumu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="85d89-155">However, compiling and executing this example throws a [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) exception.</span></span> <span data-ttu-id="85d89-156">Kullanılabilir tür için meta veriler yaptığımız halde `Book` , özellik uygulamalarındaki uygulamaları dinamik olarak kullanılabilir hale geçirdik.</span><span class="sxs-lookup"><span data-stu-id="85d89-156">Although we've made metadata for the `Book` type available, we've failed to make the implementations of the property getters available dynamically.</span></span> <span data-ttu-id="85d89-157">Bu hatayı iki şekilde düzeltebiliriz:</span><span class="sxs-lookup"><span data-stu-id="85d89-157">We can correct this error by either in one of two ways:</span></span>  
  
- <span data-ttu-id="85d89-158">`Dynamic`öğesinde türü için ilkeyi tanımlayarak `Book` [\<Type>](type-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="85d89-158">by defining the `Dynamic` policy for the `Book` type in its [\<Type>](type-element-net-native.md) element.</span></span>  
  
- <span data-ttu-id="85d89-159">[\<Property>](property-element-net-native.md)Aşağıdaki default.rd.xml dosyası olduğundan, alıcı çağırmak istediğiniz her bir özellik için iç içe bir öğe ekleyerek.</span><span class="sxs-lookup"><span data-stu-id="85d89-159">By adding a nested [\<Property>](property-element-net-native.md) element for each property whose getter we'd like to invoke, as the following default.rd.xml file does.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="85d89-160">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="85d89-160">See also</span></span>

- [<span data-ttu-id="85d89-161">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="85d89-161">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="85d89-162">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="85d89-162">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="85d89-163">Çalışma Zamanı Yönerge İlkesi Ayarları</span><span class="sxs-lookup"><span data-stu-id="85d89-163">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)

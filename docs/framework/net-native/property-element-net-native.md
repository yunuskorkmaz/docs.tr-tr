---
title: <Property> öğesi (.NET Native)
ms.date: 03/30/2017
ms.assetid: ad4ba56d-3bcb-4c10-ba90-1cc66e2175a1
ms.openlocfilehash: b9bc89804a872dddf1a56c2a3dadc9c3df4f5fd1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128206"
---
# <a name="property-element-net-native"></a><span data-ttu-id="70cf1-102">\<Özellik > öğesi (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="70cf1-102">\<Property> Element (.NET Native)</span></span>
<span data-ttu-id="70cf1-103">Çalışma zamanı yansıtma ilkesini bir özelliğe uygular.</span><span class="sxs-lookup"><span data-stu-id="70cf1-103">Applies runtime reflection policy to a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70cf1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="70cf1-104">Syntax</span></span>  
  
```xml  
<Property Name="property_name"  
          Browse="policy_type"  
          Dynamic="policy_type"  
          Serialize="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="70cf1-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="70cf1-105">Attributes and Elements</span></span>  
 <span data-ttu-id="70cf1-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="70cf1-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="70cf1-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="70cf1-107">Attributes</span></span>  
  
|<span data-ttu-id="70cf1-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="70cf1-108">Attribute</span></span>|<span data-ttu-id="70cf1-109">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="70cf1-109">Attribute type</span></span>|<span data-ttu-id="70cf1-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="70cf1-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="70cf1-111">Genel</span><span class="sxs-lookup"><span data-stu-id="70cf1-111">General</span></span>|<span data-ttu-id="70cf1-112">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="70cf1-112">Required attribute.</span></span> <span data-ttu-id="70cf1-113">Özellik adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="70cf1-113">Specifies the property name.</span></span>|  
|`Browse`|<span data-ttu-id="70cf1-114">Yansıma</span><span class="sxs-lookup"><span data-stu-id="70cf1-114">Reflection</span></span>|<span data-ttu-id="70cf1-115">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="70cf1-115">Optional attribute.</span></span> <span data-ttu-id="70cf1-116">Özelliği hakkında bilgi sorgulamayı denetler, ancak çalışma zamanında herhangi bir dinamik erişimi etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="70cf1-116">Controls querying for information about or enumerating the property but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="70cf1-117">Yansıma</span><span class="sxs-lookup"><span data-stu-id="70cf1-117">Reflection</span></span>|<span data-ttu-id="70cf1-118">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="70cf1-118">Optional attribute.</span></span> <span data-ttu-id="70cf1-119">Dinamik programlamayı etkinleştirmek için özelliğe çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="70cf1-119">Controls runtime access to the property to enable dynamic programming.</span></span> <span data-ttu-id="70cf1-120">Bu ilke, bir özelliğin çalışma zamanında dinamik olarak ayarlanamayacağını veya alınamayacağını sağlar.</span><span class="sxs-lookup"><span data-stu-id="70cf1-120">This policy ensures that a property can be set or retrieved dynamically at run time.</span></span>|  
|`Serialize`|<span data-ttu-id="70cf1-121">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="70cf1-121">Serialization</span></span>|<span data-ttu-id="70cf1-122">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="70cf1-122">Optional attribute.</span></span> <span data-ttu-id="70cf1-123">Tür örneklerinin, Newtonsoft JSON serileştirici veya veri bağlama için kullanılması gibi kitaplıklar tarafından serileştirilmesi için bir özelliğe çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="70cf1-123">Controls runtime access to a property to enable type instances to be serialized by libraries such as the Newtonsoft JSON serializer or to be used for data binding.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="70cf1-124">Ad özniteliği</span><span class="sxs-lookup"><span data-stu-id="70cf1-124">Name attribute</span></span>  
  
|<span data-ttu-id="70cf1-125">Değer</span><span class="sxs-lookup"><span data-stu-id="70cf1-125">Value</span></span>|<span data-ttu-id="70cf1-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="70cf1-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="70cf1-127">*method_name*</span><span class="sxs-lookup"><span data-stu-id="70cf1-127">*method_name*</span></span>|<span data-ttu-id="70cf1-128">Özellik adı.</span><span class="sxs-lookup"><span data-stu-id="70cf1-128">The property name.</span></span> <span data-ttu-id="70cf1-129">Özelliğin türü, üst [\<türü >](type-element-net-native.md) veya [\<typeörneklemesi >](typeinstantiation-element-net-native.md) öğesi tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="70cf1-129">The type of the property is defined by the parent [\<Type>](type-element-net-native.md) or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="70cf1-130">Diğer tüm öznitelikler</span><span class="sxs-lookup"><span data-stu-id="70cf1-130">All other attributes</span></span>  
  
|<span data-ttu-id="70cf1-131">Değer</span><span class="sxs-lookup"><span data-stu-id="70cf1-131">Value</span></span>|<span data-ttu-id="70cf1-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="70cf1-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="70cf1-133">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="70cf1-133">*policy_setting*</span></span>|<span data-ttu-id="70cf1-134">Özelliği için bu ilke türüne uygulanacak ayar.</span><span class="sxs-lookup"><span data-stu-id="70cf1-134">The setting to apply to this policy type for the property.</span></span> <span data-ttu-id="70cf1-135">Olası değerler şunlardır `Auto`, `Excluded`, `Included`ve `Required`.</span><span class="sxs-lookup"><span data-stu-id="70cf1-135">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="70cf1-136">Daha fazla bilgi için bkz. [çalışma zamanı yönergesi Ilke ayarları](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="70cf1-136">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="70cf1-137">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="70cf1-137">Child Elements</span></span>  
 <span data-ttu-id="70cf1-138">Yok.</span><span class="sxs-lookup"><span data-stu-id="70cf1-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="70cf1-139">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="70cf1-139">Parent Elements</span></span>  
  
|<span data-ttu-id="70cf1-140">Öğe</span><span class="sxs-lookup"><span data-stu-id="70cf1-140">Element</span></span>|<span data-ttu-id="70cf1-141">Açıklama</span><span class="sxs-lookup"><span data-stu-id="70cf1-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="70cf1-142">\<türü ></span><span class="sxs-lookup"><span data-stu-id="70cf1-142">\<Type></span></span>](type-element-net-native.md)|<span data-ttu-id="70cf1-143">Yansıma ilkesini bir türe ve tüm üyelerine uygular.</span><span class="sxs-lookup"><span data-stu-id="70cf1-143">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="70cf1-144">\<Typeörneklemesi ></span><span class="sxs-lookup"><span data-stu-id="70cf1-144">\<TypeInstantiation></span></span>](typeinstantiation-element-net-native.md)|<span data-ttu-id="70cf1-145">Oluşturulan genel türe ve tüm üyelerine yansıma ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="70cf1-145">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="70cf1-146">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="70cf1-146">Remarks</span></span>  
 <span data-ttu-id="70cf1-147">Bir özelliğin İlkesi açıkça tanımlanmamışsa, üst öğesinin çalışma zamanı ilkesini devralır.</span><span class="sxs-lookup"><span data-stu-id="70cf1-147">If a property's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="70cf1-148">Örnek</span><span class="sxs-lookup"><span data-stu-id="70cf1-148">Example</span></span>  
 <span data-ttu-id="70cf1-149">Aşağıdaki örnek, `Book` nesnesini başlatmak ve özellik değerlerini göstermek için yansıma kullanır.</span><span class="sxs-lookup"><span data-stu-id="70cf1-149">The following example uses reflection to instantiate a `Book` object and display its property values.</span></span> <span data-ttu-id="70cf1-150">Projenin özgün varsayılan. RD. xml dosyası şu şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="70cf1-150">The original default.rd.xml file for the project appears as follows:</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Namespace Name="LibraryApplications"  Browse="Required Public" >  
         <Type Name="Book"   Activate="All" />  
      </Namespace>  
   </Application>  
</Directives>  
```  
  
 <span data-ttu-id="70cf1-151">Dosya, yansıma aracılığıyla sınıf oluşturuculara erişime izin veren `Book` sınıfı için `Activate` ilkesine `All` değerini uygular.</span><span class="sxs-lookup"><span data-stu-id="70cf1-151">The file applies the `All` value to the `Activate` policy for the `Book` class, which allows access to class constructors through reflection.</span></span> <span data-ttu-id="70cf1-152">`Book` sınıfının `Browse` ilkesi üst ad alanından devralınır.</span><span class="sxs-lookup"><span data-stu-id="70cf1-152">The `Browse` policy for the `Book` class is inherited from its parent namespace.</span></span> <span data-ttu-id="70cf1-153">Bu, meta verileri çalışma zamanında kullanılabilir hale getiren `Required Public`olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="70cf1-153">This is set to `Required Public`, which makes metadata available at runtime.</span></span>  
  
 <span data-ttu-id="70cf1-154">Örnek için kaynak kodu aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="70cf1-154">The following is the source code for the example.</span></span> <span data-ttu-id="70cf1-155">`outputBlock` değişkeni bir <xref:Windows.UI.Xaml.Controls.TextBlock> denetimini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="70cf1-155">The `outputBlock` variable represents a <xref:Windows.UI.Xaml.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/property1.cs#6)]  
  
 <span data-ttu-id="70cf1-156">Ancak, bu örneği derlemek ve yürütmek bir [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) özel durumu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="70cf1-156">However, compiling and executing this example throws a [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) exception.</span></span> <span data-ttu-id="70cf1-157">`Book` türü için meta veriler yaptığımız halde, özellik uygulamalarındaki uygulamaları dinamik olarak kullanılabilir hale geçirdik.</span><span class="sxs-lookup"><span data-stu-id="70cf1-157">Although we've made metadata for the `Book` type available, we've failed to make the implementations of the property getters available dynamically.</span></span> <span data-ttu-id="70cf1-158">Bu hatayı iki şekilde düzeltebiliriz:</span><span class="sxs-lookup"><span data-stu-id="70cf1-158">We can correct this error by either in one of two ways:</span></span>  
  
- <span data-ttu-id="70cf1-159">`Book` türü için `Dynamic` ilkesi tanımlayarak [\<türü >](type-element-net-native.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="70cf1-159">by defining the `Dynamic` policy for the `Book` type in its [\<Type>](type-element-net-native.md) element.</span></span>  
  
- <span data-ttu-id="70cf1-160">Aşağıdaki default. RD. xml dosyası gibi, alıcı çağırmak istediğiniz her bir özellik için iç içe [\<özelliği >](property-element-net-native.md) öğesi ekleyerek.</span><span class="sxs-lookup"><span data-stu-id="70cf1-160">By adding a nested [\<Property>](property-element-net-native.md) element for each property whose getter we'd like to invoke, as the following default.rd.xml file does.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="70cf1-161">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="70cf1-161">See also</span></span>

- [<span data-ttu-id="70cf1-162">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="70cf1-162">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="70cf1-163">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="70cf1-163">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="70cf1-164">Çalışma Zamanı Yönerge İlkesi Ayarları</span><span class="sxs-lookup"><span data-stu-id="70cf1-164">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)

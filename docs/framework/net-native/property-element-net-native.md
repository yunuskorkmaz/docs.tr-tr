---
title: <Property> Öğesi (.NET yerel)
ms.date: 03/30/2017
ms.assetid: ad4ba56d-3bcb-4c10-ba90-1cc66e2175a1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c29cbfbd1c84d267e129bf97d4e9126c772d06d6
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55279116"
---
# <a name="property-element-net-native"></a>\<Özellik > öğesi (.NET yerel)
Çalışma zamanı yansıma ilkesini bir özellik için geçerlidir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<Property Name="property_name"  
          Browse="policy_type"  
          Dynamic="policy_type"  
          Serialize="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Öznitelik türü|Açıklama|  
|---------------|--------------------|-----------------|  
|`Name`|Genel|Gerekli öznitelik. Özellik adını belirtir.|  
|`Browse`|Yansıma|İsteğe bağlı öznitelik. Hakkında bilgi için sorgulama veya özellik numaralandırma denetler, ancak çalışma zamanında herhangi bir dinamik erişim sağlamaz.|  
|`Dynamic`|Yansıma|İsteğe bağlı öznitelik. Programlama. özelliği dinamik etkinleştirmek için çalışma zamanı erişimi denetler. Bu ilke, bir özellik ayarlanabilir veya çalışma zamanında dinamik olarak alınan olmasını sağlar.|  
|`Serialize`|Serileştirme|İsteğe bağlı öznitelik. Çalışma zamanı kitaplıkları gibi Newtonsoft JSON seri hale getirici tarafından serileştirilecek veya veri bağlama için kullanılacak tür örnekleri etkinleştirmek için bir özellik erişimi denetler.|  
  
## <a name="name-attribute"></a>Ad özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*method_name*|Özellik adı. Özelliğin türü üst öğe tarafından tanımlanan [ \<türü >](../../../docs/framework/net-native/type-element-net-native.md) veya [ \<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) öğesi.|  
  
## <a name="all-other-attributes"></a>Diğer tüm öznitelikler  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*policy_setting*|Bu ilke türü özelliği için geçerli ayar. Olası değerler `Auto`, `Excluded`, `Included`, ve `Required`. Daha fazla bilgi için [çalışma zamanı yönerge İlkesi ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<türü >](../../../docs/framework/net-native/type-element-net-native.md)|Yansıma İlkesi, bir tür ve tüm üyeleri için geçerlidir.|  
|[\<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Yansıma ilkesini, oluşturulmuş bir genel türü ve tüm üyeleri için geçerlidir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir özelliğin ilke açıkça tanımlı değilse, kendi üst öğenin çalışma zamanı ilkesini devralır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, örneklemek için yansıtma kullanır. bir `Book` nesne ve özellik değerlerini görüntüler. Projesi için özgün default.rd.xml dosyasını aşağıdaki gibi görünür:  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Namespace Name="LibraryApplications"  Browse="Required Public" >  
         <Type Name="Book"   Activate="All" />  
      </Namespace>  
   </Application>  
</Directives>  
```  
  
 Dosya geçerli `All` değerini `Activate` İlkesi `Book` sınıf oluşturucuları yansıma aracılığıyla erişmesini sağlar sınıfını. `Browse` İlkesi `Book` sınıfı, kendi üst ad alanından devralınır. Bu ayar `Required Public`, hangi kullanımınıza meta verileri çalışma zamanında.  
  
 Örnek kaynak kodu verilmiştir. `outputBlock` Değişkenini temsil eder bir <xref:Windows.UI.Xaml.Controls.TextBlock> denetimi.  
  
 [!code-csharp[ProjectN_Reflection#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/property1.cs#6)]  
  
 Ancak, derleme ve bu örnek yürütme oluşturur bir [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) özel durum. Meta veri yaptık olsa da `Book` türü kullanılabilir alamadık özellik alıcıları uygulamaları dinamik olarak kullanılabilir hale getirmek. Tarafından iki yoldan biriyle ya da Biz bu hatayı düzeltebilir:  
  
-   tanımlayarak `Dynamic` İlkesi `Book` yazın, [ \<türü >](../../../docs/framework/net-native/type-element-net-native.md) öğesi.  
  
-   İç içe bir ekleyerek [ \<özellik >](../../../docs/framework/net-native/property-element-net-native.md) default.rd.xml dosyanın aşağıdaki gibi alıcı çağırmak için istiyoruz her özellik için öğesi.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [Çalışma Zamanı Yönerge Öğeleri](../../../docs/framework/net-native/runtime-directive-elements.md)
- [Çalışma Zamanı Yönerge İlkesi Ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md)

---
title: <Property>Öğesi (.NET Native)
ms.date: 03/30/2017
ms.assetid: ad4ba56d-3bcb-4c10-ba90-1cc66e2175a1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 54daf15c593327bf3255f40f6eb6931ffc8bd3c6
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049305"
---
# <a name="property-element-net-native"></a>\<Özellik > öğesi (.NET Native)
Çalışma zamanı yansıtma ilkesini bir özelliğe uygular.  
  
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
|`Browse`|Yansıma|İsteğe bağlı öznitelik. Özelliği hakkında bilgi sorgulamayı denetler, ancak çalışma zamanında herhangi bir dinamik erişimi etkinleştirmez.|  
|`Dynamic`|Yansıma|İsteğe bağlı öznitelik. Dinamik programlamayı etkinleştirmek için özelliğe çalışma zamanı erişimini denetler. Bu ilke, bir özelliğin çalışma zamanında dinamik olarak ayarlanamayacağını veya alınamayacağını sağlar.|  
|`Serialize`|Serileştirme|İsteğe bağlı öznitelik. Tür örneklerinin, Newtonsoft JSON serileştirici veya veri bağlama için kullanılması gibi kitaplıklar tarafından serileştirilmesi için bir özelliğe çalışma zamanı erişimini denetler.|  
  
## <a name="name-attribute"></a>Ad özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*method_name*|Özellik adı. Özelliğin türü, üst [ \<tür >](type-element-net-native.md) veya [ \<typeörneklemesi >](typeinstantiation-element-net-native.md) öğesi tarafından tanımlanır.|  
  
## <a name="all-other-attributes"></a>Diğer tüm öznitelikler  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*policy_setting*|Özelliği için bu ilke türüne uygulanacak ayar. Olası değerler şunlardır `Auto` `Excluded` `Required`, ,ve.`Included` Daha fazla bilgi için bkz. [çalışma zamanı yönergesi Ilke ayarları](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Tür >](type-element-net-native.md)|Yansıma ilkesini bir türe ve tüm üyelerine uygular.|  
|[\<Typeörneklemesi >](typeinstantiation-element-net-native.md)|Oluşturulan genel türe ve tüm üyelerine yansıma ilkesi uygular.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir özelliğin İlkesi açıkça tanımlanmamışsa, üst öğesinin çalışma zamanı ilkesini devralır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir `Book` nesnenin örneğini oluşturmak ve özellik değerlerini göstermek için yansıma kullanır. Projenin özgün varsayılan. RD. xml dosyası şu şekilde görünür:  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Namespace Name="LibraryApplications"  Browse="Required Public" >  
         <Type Name="Book"   Activate="All" />  
      </Namespace>  
   </Application>  
</Directives>  
```  
  
 Dosya, yansıma aracılığıyla `All` sınıf oluşturuculara erişime `Activate` izin veren `Book` sınıfının ilkesine değeri uygular. `Book` Sınıfın ilkesi, üst ad alanından devralınır. `Browse` Bu, meta verileri `Required Public`çalışma zamanında kullanılabilir hale getiren olarak ayarlanır.  
  
 Örnek için kaynak kodu aşağıda verilmiştir. `outputBlock` Değişkeni bir<xref:Windows.UI.Xaml.Controls.TextBlock> denetimi temsil eder.  
  
 [!code-csharp[ProjectN_Reflection#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/property1.cs#6)]  
  
 Ancak, bu örneği derlemek ve yürütmek bir [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) özel durumu oluşturur. Kullanılabilir `Book` tür için meta veriler yaptığımız halde, özellik uygulamalarındaki uygulamaları dinamik olarak kullanılabilir hale geçirdik. Bu hatayı iki şekilde düzeltebiliriz:  
  
- tür `Dynamic` için`Book` [ilke tanımlayarak >öğesi.\<](type-element-net-native.md)  
  
- Aşağıdaki default. RD. xml dosyası gibi, alıcısı çağırmak istediğimiz her bir özellik için iç içe [ \<bir özellik >](property-element-net-native.md) öğesi ekleyerek.  
  
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

- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](runtime-directives-rd-xml-configuration-file-reference.md)
- [Çalışma Zamanı Yönerge Öğeleri](runtime-directive-elements.md)
- [Çalışma Zamanı Yönerge İlkesi Ayarları](runtime-directive-policy-settings.md)

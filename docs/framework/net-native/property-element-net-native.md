---
title: <Property>Öğesi (.NET Native)
ms.date: 03/30/2017
ms.assetid: ad4ba56d-3bcb-4c10-ba90-1cc66e2175a1
ms.openlocfilehash: b9bc89804a872dddf1a56c2a3dadc9c3df4f5fd1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128206"
---
# <a name="property-element-net-native"></a>\<Property>Öğesi (.NET Native)
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
|*method_name*|Özellik adı. Özelliğin türü üst [\<Type>](type-element-net-native.md) veya öğe tarafından tanımlanır [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .|  
  
## <a name="all-other-attributes"></a>Diğer tüm öznitelikler  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*policy_setting*|Özelliği için bu ilke türüne uygulanacak ayar. Olası değerler şunlardır,, `Auto` `Excluded` `Included` ve `Required` . Daha fazla bilgi için bkz. [çalışma zamanı yönergesi Ilke ayarları](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|Yansıma ilkesini bir türe ve tüm üyelerine uygular.|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|Oluşturulan genel türe ve tüm üyelerine yansıma ilkesi uygular.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir özelliğin İlkesi açıkça tanımlanmamışsa, üst öğesinin çalışma zamanı ilkesini devralır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir nesnenin örneğini oluşturmak `Book` ve özellik değerlerini göstermek için yansıma kullanır. Projenin özgün varsayılan. RD. xml dosyası şu şekilde görünür:  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Namespace Name="LibraryApplications"  Browse="Required Public" >  
         <Type Name="Book"   Activate="All" />  
      </Namespace>  
   </Application>  
</Directives>  
```  
  
 Dosya, `All` `Activate` `Book` yansıma aracılığıyla sınıf oluşturuculara erişime izin veren sınıfının ilkesine değeri uygular. `Browse`Sınıfın ilkesi, `Book` üst ad alanından devralınır. Bu `Required Public` , meta verileri çalışma zamanında kullanılabilir hale getiren olarak ayarlanır.  
  
 Örnek için kaynak kodu aşağıda verilmiştir. `outputBlock`Değişkeni bir denetimi temsil eder <xref:Windows.UI.Xaml.Controls.TextBlock> .  
  
 [!code-csharp[ProjectN_Reflection#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/property1.cs#6)]  
  
 Ancak, bu örneği derlemek ve yürütmek bir [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) özel durumu oluşturur. Kullanılabilir tür için meta veriler yaptığımız halde `Book` , özellik uygulamalarındaki uygulamaları dinamik olarak kullanılabilir hale geçirdik. Bu hatayı iki şekilde düzeltebiliriz:  
  
- `Dynamic`öğesinde türü için ilkeyi tanımlayarak `Book` [\<Type>](type-element-net-native.md) .  
  
- [\<Property>](property-element-net-native.md)Aşağıdaki default. RD. xml dosyası gibi, alıcı çağırmak istediğimiz her bir özellik için iç içe bir öğe ekleyerek.  
  
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

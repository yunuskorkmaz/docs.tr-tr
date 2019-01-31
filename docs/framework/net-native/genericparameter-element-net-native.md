---
title: <GenericParameter> Öğesi (.NET yerel)
ms.date: 03/30/2017
ms.assetid: cbd49732-3615-49a5-a900-f96947cdc3e6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: db9876727244d528ec3b7f1c3c9875bb5ca645b5
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55257778"
---
# <a name="genericparameter-element-net-native"></a>\<GenericParameter > öğesi (.NET yerel)
İlke bir genel tür veya yöntemin parametre türü için geçerlidir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<GenericParameter Name="generic_parameter_name"  
                  Activate="policy_type"  
                  Browse="policy_type"  
                  Dynamic="policy_type"  
                  Serialize="policy_type"  
                  DataContractSerializer="policy_type"  
                  DataContractJsonSerializer="policy_type"  
                  XmlSerializer="policy_type"  
                  MarshalObject="policy_type"  
                  MarshalDelegate="policy_type"  
                  MarshalStructure="policy_type"  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Öznitelik türü|Açıklama|  
|---------------|--------------------|-----------------|  
|`Name`|Genel|Gerekli öznitelik. Genel parametre adı. Örneğin, Genel temsilci <xref:System.Func%603>, değerini `Name` özniteliktir "TResult" temsilcinin dönüş değeri için çalışma zamanı ilkesini uygulamak için.|  
|`Activate`|Yansıma|İsteğe bağlı öznitelik. Oluşturucular örneklerinin etkinleştirmesi için çalışma zamanı erişimi denetler.|  
|`Browse`|Yansıma|İsteğe bağlı öznitelik. Program öğeleri hakkında bilgi için sorgulama kontrol eder, ancak herhangi bir çalışma zamanı erişim sağlamaz.|  
|`Dynamic`|Yansıma|İsteğe bağlı öznitelik. Dinamik programlama etkinleştirmek için Oluşturucular, yöntemler, alanlar, özellikler ve olaylar, tüm tür üyelerini, çalışma zamanı erişimi denetler.|  
|`Serialize`|Serileştirme|İsteğe bağlı öznitelik. Oluşturucular, alanları ve tür örnekleri sıralanabilir ve kitaplıkları gibi Newtonsoft JSON seri hale getirici tarafından serisi etkinleştirmek için özellikler, çalışma zamanı erişimi denetler.|  
|`DataContractSerializer`|Serileştirme|İsteğe bağlı öznitelik. Denetimleri İlkesi kullanan Serileştirmenin <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> sınıfı.|  
|`DataContractJsonSerializer`|Serileştirme|İsteğe bağlı öznitelik. İlke kullanan bir JSON serileştirme denetleyen <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> sınıfı.|  
|`XmlSerializer`|Serileştirme|İsteğe bağlı öznitelik. İlke kullanan bir XML serileştirme denetleyen <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> sınıfı.|  
|`MarshalObject`|Birlikte çalışma|İsteğe bağlı öznitelik. Windows çalışma zamanı ve COM başvuru türlerini hazırlama denetimleri İlkesi|  
|`MarshalDelegate`|Birlikte çalışma|İsteğe bağlı öznitelik. Yerel kod için işlev işaretçileri olarak temsilci türleri hazırlama için ilke denetler.|  
|`MarshalStructure`|Birlikte çalışma|İsteğe bağlı öznitelik. Yerel kod için değer türlerini hazırlama için ilke denetler.|  
  
## <a name="name-attribute"></a>Ad özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*generic_parameter_name*|Gerekli öznitelik. Genel tür parametre adı. Örneğin, Genel temsilci <xref:System.Func%603>, *generic_parameter_name* "TResult" değerini çalışma zamanı İlkesi temsilcinin dönüş değeri için geçerlidir.|  
  
## <a name="all-other-attributes"></a>Diğer tüm öznitelikler  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*policy_setting*|Bu ilke türü için geçerli ayar. Olası değerler `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, ve `Required All`. Daha fazla bilgi için [çalışma zamanı yönerge İlkesi ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Yöntem >](../../../docs/framework/net-native/method-element-net-native.md)|Çalışma zamanı yansıma ilkesini yapıcıya veya yönteme için geçerlidir.|  
|[\<türü >](../../../docs/framework/net-native/type-element-net-native.md)|Bir sınıf veya yapı gibi belirli bir tür için çalışma zamanı yansıma ilkesini uygular.|  
  
## <a name="remarks"></a>Açıklamalar  
 `<GenericParameter>` Ya da bir alt öğedir [ \<yöntemi >](../../../docs/framework/net-native/method-element-net-native.md) veya [ \<türü >](../../../docs/framework/net-native/type-element-net-native.md) öğesi olan bir belirli genel tür parametresi için ilkeyi uygulamak için kullanılır genel tür veya yöntem İmzasındaki adı belirtildi.  
  
 `<GenericParameter>` Öğesi, seri hale getiricileri genişletme ile kullanıldığında en kullanışlıdır. Aşağıdaki örnekte `<GenericParameter>` ilke türü için geçerli öğe `T` NewtonSoft JSON seri hale getirici'nın çağrılarında [JsonConvert.DeserializeObject\<T > (dize)](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonConvert_DeserializeObject__1.htm) yöntemi aşırı yüklemeleri.  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Type Name="Newtonsoft.Json.JsonConvert" >  
      <Method Name="DeserializeObject{T}">  
         <GenericParameter Name="T" Serialize="Required All" />  
      </Method>  
   </Type>  
</Directives>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.
- [\<Yöntem > öğesi](../../../docs/framework/net-native/method-element-net-native.md)
- [\<Türü > öğesi](../../../docs/framework/net-native/type-element-net-native.md)
- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [Çalışma Zamanı Yönerge İlkesi Ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
- [Çalışma Zamanı Yönerge Öğeleri](../../../docs/framework/net-native/runtime-directive-elements.md)

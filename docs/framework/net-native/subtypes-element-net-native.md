---
title: "&lt;Subtypes&gt; Öğesi (.NET Yerel)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb854070-248b-46cf-9dab-c322e2b4d624
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 39b46386c6861b6a8c2824a0055d4122ec0523c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltsubtypesgt-element-net-native"></a>&lt;Subtypes&gt; Öğesi (.NET Yerel)
Çalışma zamanı ilkesi içeren türünden devralınan tüm sınıflar için geçerlidir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<Subtypes Activate="policy_type"  
          Browse="policy_type"  
          Dynamic="policy_type"  
          Serialize="policy_type"   
          DataContractSerializer="policy_setting"  
          DataContractJsonSerializer="policy_setting"  
          XmlSerializer="policy_setting"  
          MarshalObject="policy_setting"  
          MarshalDelegate="policy_setting"  
          MarshalStructure="policy_setting" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Öznitelik türü|Açıklama|  
|---------------|--------------------|-----------------|  
|`Activate`|Yansıma|İsteğe bağlı öznitelik. Oluşturucular örneklerinin etkinleştirmesi için çalışma zamanı erişimi kontrol eder.|  
|`Browse`|Yansıma|İsteğe bağlı öznitelik. Program öğeleri hakkında bilgi için sorgulama kontrol eder, ancak herhangi bir çalışma zamanı erişim sağlamaz.|  
|`Dynamic`|Yansıma|İsteğe bağlı öznitelik. Dinamik programlama etkinleştirmek için Oluşturucular, yöntemleri, alanları, özellikleri ve olayları dahil tüm tür üyeleri, çalışma zamanı erişimi kontrol eder.|  
|`Serialize`|Serileştirme|İsteğe bağlı öznitelik. Oluşturucular, alanları ve seri hale getirilmiş ve kitaplıklar gibi Newtonsoft JSON seri hale getirici tarafından seri türü örnekleri etkinleştirmek için özellikleri, çalışma zamanı erişimi denetler.|  
|`DataContractSerializer`|Serileştirme|İsteğe bağlı öznitelik. Denetimleri kullanan serileştirme için ilke <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> sınıfı.|  
|`DataContractJsonSerializer`|Serileştirme|İsteğe bağlı öznitelik. Denetimleri kullanan JSON serileştirmesi için ilke <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> sınıfı.|  
|`XmlSerializer`|Serileştirme|İsteğe bağlı öznitelik. Denetimleri kullanan XML serileştirme için ilke <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> sınıfı.|  
|`MarshalObject`|Birlikte çalışma|İsteğe bağlı öznitelik. Başvuru türleri Windows çalışma zamanı ve COM hazırlama denetimlerini İlkesi|  
|`MarshalDelegate`|Birlikte çalışma|İsteğe bağlı öznitelik. Yerel kod için işlev işaretçileri olarak temsilci türleri hazırlama için ilke denetler.|  
|`MarshalStructure`|Birlikte çalışma|İsteğe bağlı öznitelik. Değer türleri yerel koda hazırlama için ilke denetler.|  
  
## <a name="all-attributes"></a>Tüm öznitelikleri  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*policy_setting*|Bu ilke türü için geçerli ayar. Olası değerler şunlardır: `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, ve `Required All`. Daha fazla bilgi için bkz: [çalışma zamanı yönerge İlkesi ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Türü >](../../../docs/framework/net-native/type-element-net-native.md)|Yansıma ilke türü ve tüm üyeleri için geçerlidir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `<Subtypes>` Öğesi türünü içeren tüm alt ilke uygulanır. Türetilmiş türler ve temel sınıflarına farklı ilkeleri uygulamak istediğinizde kullanın.  
  
 En az birinin mevcut olması gereken rağmen yansıma, seri hale getirme ve birlikte çalışma özniteliklerini tüm isteğe bağlıdır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek adlı bir sınıf tanımlar `BaseClass` ve adlı bir alt sınıfı `Derived1`.  
  
 [!code-csharp[ProjectN_Reflection#4](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/subtypes.cs#4)]  
  
 Aşağıdaki kodda gösterildiği gibi çalışma zamanı yönergeleri açıkça kümeleri dosya `Dynamic` ve `Activate` ilkelerini `BaseClass` için `Excluded`. Bu, nesne türü nedeniyle `BaseClass` dinamik olarak veya çağrıların ne kadar başlatılamaz `BaseClass` sınıfı oluşturucusu. Ancak, `<Subtypes>` öğesi türetilmiş sınıfları sağlar `BaseClass` dinamik olarak ve kendi sınıf oluşturucular çağrıları aracılığıyla örneğinin oluşturulması için.  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
   <Assembly Name="*Application*" Dynamic="Required All" />  
     <Type Name="Examples.Libraries.BaseClass" Activate ="Excluded" Dynamic="Excluded" >  
        <Subtypes Activate="Public" Dynamic ="Public"/>  
     </Type>  
  </Application>  
</Directives>  
```  
  
 Nedeniyle `<Subtypes>` yönergesi, başlatır aşağıdaki kod bir `Derived1` çağırarak dinamik olarak örneği <xref:System.Activator.CreateInstance%28System.Type%29?displayProperty=nameWithType> yöntemi başarıyla yürütür.  Burada bloğu değişkeni, bir <xref:System.Windows.Controls.TextBlock> boş bir Windows mağazası uygulaması nesne.  
  
 [!code-csharp[ProjectN_Reflection#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/subtypes.cs#5)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [\<Tür > öğesi](../../../docs/framework/net-native/type-element-net-native.md)  
 [Çalışma zamanı yönergeleri (rd.xml) yapılandırma dosyası başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [Çalışma zamanı yönerge öğeleri](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [Çalışma zamanı yönerge İlkesi ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md)

---
title: "&lt;Property&gt; Öğesi (.NET Yerel)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad4ba56d-3bcb-4c10-ba90-1cc66e2175a1
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d41e05c39f8483cc668962c53534bb531a8007ed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltpropertygt-element-net-native"></a>&lt;Property&gt; Öğesi (.NET Yerel)
Çalışma zamanı yansıma İlkesi bir özellik için geçerlidir.  
  
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
|`Browse`|Yansıma|İsteğe bağlı öznitelik. Hakkında bilgi için sorgulama veya özellik numaralandırma kontrol eder, ancak herhangi bir dinamik erişim çalışma zamanında etkinleştirmez.|  
|`Dynamic`|Yansıma|İsteğe bağlı öznitelik. Programlama dinamik etkinleştirmek için özellik çalışma zamanı erişimi kontrol eder. Bu ilke, bir özellik ayarlanabilir veya çalışma zamanında dinamik olarak alınan olmasını sağlar.|  
|`Serialize`|Serileştirme|İsteğe bağlı öznitelik. Bir özellik türü örnekleri kitaplıklar gibi Newtonsoft JSON seri hale getirici tarafından seri hale veya veri bağlaması için kullanılmak üzere etkinleştirmek için çalışma zamanı erişimi kontrol eder.|  
  
## <a name="name-attribute"></a>Ad özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*method_name*|Özellik adı. Özelliğin türü üst tarafından tanımlanan [ \<türü >](../../../docs/framework/net-native/type-element-net-native.md) veya [ \<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) öğesi.|  
  
## <a name="all-other-attributes"></a>Tüm diğer özniteliklerle  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*policy_setting*|Bu ilke türü özelliği için geçerli ayar. Olası değerler şunlardır: `Auto`, `Excluded`, `Included`, ve `Required`. Daha fazla bilgi için bkz: [çalışma zamanı yönerge İlkesi ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Türü >](../../../docs/framework/net-native/type-element-net-native.md)|Yansıma ilke türü ve tüm üyeleri için geçerlidir.|  
|[\<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Yansıma İlkesi, yapılandırılmış bir genel tür ve tüm üyeleri için geçerlidir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir özelliğin İlkesi açıkça tanımlanmazsa, kendi üst öğesi, çalışma zamanı İlkesi devralır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek örneği oluşturmak için yansıma kullanan bir `Book` nesne ve özellik değerlerini görüntüler. Projesi için özgün default.rd.xml dosya şu şekilde görünür:  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Namespace Name="LibraryApplications"  Browse="Required Public" >  
         <Type Name="Book"   Activate="All" />  
      </Namespace>  
   </Application>  
</Directives>  
```  
  
 Dosyasının geçerli `All` değeri `Activate` için ilke `Book` sınıf oluşturucular yansıma aracılığıyla erişim sağlayan sınıf. `Browse` İçin ilke `Book` sınıfı, kendi üst ad alanından devralınır. Bu ayar `Required Public`, hangi kullanılabilir hale getirir meta veri çalışma zamanında.  
  
 Örneğin kaynak kodu verilmiştir. `outputBlock` Değişkeni temsil eden bir [TextBlock](http://msdn.microsoft.com/library/windows.ui.xaml.controls.textblock.aspx) denetim.  
  
 [!code-csharp[ProjectN_Reflection#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/property1.cs#6)]  
  
 Ancak, derleme ve bu örnek yürütme oluşturur bir [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) özel durum. Meta veri yaptık rağmen `Book` kullanılabilen türü, alamadık özellik alıcıları uygulamaları dinamik olarak kullanılabilir hale getirmek. Biz bu hata ya da iki yoldan biriyle düzeltebilirsiniz:  
  
-   tanımlayarak `Dynamic` için ilke `Book` yazın, [ \<türü >](../../../docs/framework/net-native/type-element-net-native.md) öğesi.  
  
-   İç içe bir ekleyerek [ \<özelliği >](../../../docs/framework/net-native/property-element-net-native.md) aşağıdaki default.rd.xml dosya yaptığı gibi alıcı çağırmak için isteriz her özellik için öğesi.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çalışma zamanı yönergeleri (rd.xml) yapılandırma dosyası başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [Çalışma zamanı yönerge öğeleri](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [Çalışma zamanı yönerge İlkesi ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md)

---
title: <Subtypes>Eleman (.NET Yerel)
ms.date: 03/30/2017
ms.assetid: fb854070-248b-46cf-9dab-c322e2b4d624
ms.openlocfilehash: bb719449f3769c5dbbde6d05efdb865c18bb4ab2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180931"
---
# <a name="subtypes-element-net-native"></a>\<Element> Alt Türleri (.NET Yerli)
İçerme türünden devralınan tüm sınıflara çalışma zamanı ilkesi uygular.  
  
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
|`Activate`|Yansıma|İsteğe bağlı öznitelik. Örneklerin etkinleştirilmesini etkinleştirmek için çalışan zamanında kuruculara erişimi denetler.|  
|`Browse`|Yansıma|İsteğe bağlı öznitelik. Program öğeleri hakkında bilgi için sorgu denetimleri, ancak herhangi bir çalışma zamanı erişim etkinleştirmez.|  
|`Dynamic`|Yansıma|İsteğe bağlı öznitelik. Dinamik programlamayı etkinleştirmek için oluşturucular, yöntemler, alanlar, özellikler ve olaylar dahil olmak üzere tüm tür üyelerine çalışma zamanı erişimi denetler.|  
|`Serialize`|Serileştirme|İsteğe bağlı öznitelik. Newtonsoft JSON serileştiricisi gibi kitaplıklar tarafından seri hale getirilecek ve deserialized türü örnekleri etkinleştirmek için, yapıcılar, alanlar ve özelliklere çalışma zamanı erişimi denetler.|  
|`DataContractSerializer`|Serileştirme|İsteğe bağlı öznitelik. Sınıfı kullanan serileştirme ilkesini <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> denetler.|  
|`DataContractJsonSerializer`|Serileştirme|İsteğe bağlı öznitelik. Sınıfı kullanan JSON serileştirme <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> ilkesini denetler.|  
|`XmlSerializer`|Serileştirme|İsteğe bağlı öznitelik. Sınıfı kullanan XML serileştirme <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> ilkesini denetler.|  
|`MarshalObject`|Interop|İsteğe bağlı öznitelik. Başvuru türlerini Windows Runtime ve COM'a göre mareşalleme ilkesini denetler.|  
|`MarshalDelegate`|Interop|İsteğe bağlı öznitelik. Temsilci türlerini işlev işaretçisi olarak yerel koda göre işaretetmek için ilkeyi denetler.|  
|`MarshalStructure`|Interop|İsteğe bağlı öznitelik. Değer türlerini yerel koda göre mareşalleştirmek için ilkeyi denetler.|  
  
## <a name="all-attributes"></a>Tüm öznitelikler  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*policy_setting*|Bu ilke türüne uygulanacak ayar. Olası değerler `All` `Auto`, `Excluded` `Public`, `PublicAndInternal` `Required Public`, `Required PublicAndInternal`, `Required All`, , , ve . Daha fazla bilgi için [Runtime Yönergesi İlke Ayarları'na](runtime-directive-policy-settings.md)bakın.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Tip>](type-element-net-native.md)|Yansıma ilkesini bir türe ve tüm üyelerine uygular.|  
  
## <a name="remarks"></a>Açıklamalar  
 Öğe, `<Subtypes>` içerdiği türünün tüm alt türlerine ilke uygular. Türemiş türlere ve bunların temel sınıflarına farklı ilkeler uygulamak istediğinizde kullanırsınız.  
  
 Yansıma, serileştirme ve interop öznitelikleri isteğe bağlıdır, ancak en az birinin bulunması gerekir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, adlı `BaseClass` bir sınıf ve `Derived1`bir alt sınıf adlı tanımlar.  
  
 [!code-csharp[ProjectN_Reflection#4](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/subtypes.cs#4)]  
  
 Aşağıdaki kodda gösterildiği gibi, çalışma zamanı yönergeleri dosyası `Dynamic` `Activate` açıkça ayarlar `BaseClass` `Excluded`ve ilkeleri için . Bu nedenle, tür `BaseClass` nesneleri dinamik olarak veya `BaseClass` sınıf oluşturucuya yapılan çağrılarla anında alınamaz. Ancak, `<Subtypes>` öğe, türetilen `BaseClass` sınıfların dinamik olarak anında ve sınıf yapıcılarına yapılan çağrılar yoluyla oluşturulmasını sağlar.  
  
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
  
 `<Subtypes>` Yönerge nedeniyle, <xref:System.Activator.CreateInstance%28System.Type%29?displayProperty=nameWithType> yöntemi çağırarak bir `Derived1` örneği dinamik olarak anında sağlayan aşağıdaki kod başarılı bir şekilde yürütülür.  Buradaki blok değişkeni <xref:System.Windows.Controls.TextBlock> boş bir Windows Mağazası uygulamasındaki bir nesnedir.  
  
 [!code-csharp[ProjectN_Reflection#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/subtypes.cs#5)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [\<> Öğesi Yazın](type-element-net-native.md)
- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](runtime-directives-rd-xml-configuration-file-reference.md)
- [Çalışma Zamanı Yönerge Öğeleri](runtime-directive-elements.md)
- [Çalışma Zamanı Yönerge İlkesi Ayarları](runtime-directive-policy-settings.md)

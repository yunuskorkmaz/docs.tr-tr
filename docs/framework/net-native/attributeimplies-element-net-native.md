---
title: <AttributeImplies>Eleman (.NET Yerel)
ms.date: 03/30/2017
ms.assetid: 82db7193-a860-418b-84fc-fff2fdf2e025
ms.openlocfilehash: 2ab1fdc71bc43f61f69a0d9b7bea7acb35e14ea5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181059"
---
# <a name="attributeimplies-element-net-native"></a>\<Öznitelik> Öğe (.NET Yerli) Anlamına Gelir
İçerdeki öznitelik uygulanan kod öğeleri için ilke tanımlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<AttributeImplies Activate="policy_type"  
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
 Öğe `<AttributeImplies>` türü bir öznitelik (yani, bir sınıf türetilmiş) <xref:System.Attribute?displayProperty=nameWithType>ise öğe kullanılır. Öznitelik belirli bir program öğesine uygulanırsa, `<AttributeImplies>` öğe tarafından tanımlanan ilke bu program öğesine uygulanır.  
  
 Yansıma, serileştirme ve interop öznitelikleri isteğe bağlıdır, ancak en az birinin bulunması gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [\<> Öğesi Yazın](type-element-net-native.md)
- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](runtime-directives-rd-xml-configuration-file-reference.md)
- [Çalışma Zamanı Yönerge Öğeleri](runtime-directive-elements.md)
- [Çalışma Zamanı Yönerge İlkesi Ayarları](runtime-directive-policy-settings.md)

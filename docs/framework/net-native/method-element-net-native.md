---
title: <Method> Öğesi (.NET yerel)
ms.date: 03/30/2017
ms.assetid: 348b49e5-589d-4eb2-a597-d6ff60ab52d1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9fdc4441a8a11df5427badfaea95edb0abe52bde
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61867125"
---
# <a name="method-element-net-native"></a>\<Yöntem > öğesi (.NET yerel)
Çalışma zamanı yansıma ilkesini yapıcıya veya yönteme için geçerlidir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<Method Name="method_name"  
        Signature="method_signature"  
        Browse="policy_type"  
        Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Öznitelik türü|Açıklama|  
|---------------|--------------------|-----------------|  
|`Name`|Genel|Gerekli öznitelik. Yöntem adını belirtir.|  
|`Signature`|Genel|İsteğe bağlı öznitelik. Yöntem imzası belirtir. Birden çok parametre varsa, bunların virgülle ayrılır. Örneğin, aşağıdaki `<Method>` öğe tanımlar için ilke <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29> yöntemi.<br /><br /> `<Type Name="System.DateTime">    <Method Name="ToString" Signature="System.String,System.IFormatProvider"            Dynamic="Required" /> </Type>`<br /><br /> Öznitelik yoksa, çalışma zamanı yönerge yöntemin tüm aşırı yüklemeler için geçerlidir.|  
|`Browse`|Yansıma|İsteğe bağlı öznitelik. Hakkında bilgi için sorgulama veya bir yöntem numaralandırma kontrol eder, ancak herhangi bir dinamik çağrı çalışma zamanında etkinleştirmez.|  
|`Dynamic`|Yansıma|İsteğe bağlı öznitelik. Programlama. bir oluşturucu veya dinamik olarak etkinleştirme yöntemi çalışma zamanı erişimi denetler. Bu ilke, çalışma zamanında dinamik olarak çağrılabilir üyesi sağlar.|  
  
## <a name="name-attribute"></a>Ad özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*method_name*|Yöntem adı. Yöntem türü üst öğe tarafından tanımlanan [ \<türü >](../../../docs/framework/net-native/type-element-net-native.md) veya [ \<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) öğesi.|  
  
## <a name="signature-attribute"></a>İmza özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*method_signature*|Yöntem imzası form parametre türleri. Birden çok parametre, örneğin, virgülle ayrılır `"System.String,System.Int32,System.Int32)"`. Parametre türü adları, tam olarak nitelenmiş olmalıdır.|  
  
## <a name="all-other-attributes"></a>Diğer tüm öznitelikler  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*policy_setting*|Bu ilke türü için geçerli ayar. Olası değerler `Auto`, `Excluded`, `Included`, ve `Required`. Daha fazla bilgi için [çalışma zamanı yönerge İlkesi ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Parametresi >](../../../docs/framework/net-native/parameter-element-net-native.md)|Bir yönteme geçirilen bağımsız değişken türü ilke uygulanır.|  
|[\<GenericParameter >](../../../docs/framework/net-native/genericparameter-element-net-native.md)|İlke bir genel tür veya yöntemin parametre türü için geçerlidir.|  
|[\<Impliestype >](../../../docs/framework/net-native/impliestype-element-net-native.md)|İlke bu ilkeyi içeren tarafından temsil edilen yönteme uygulanmış bir türe geçerlidir `<Method>` öğesi.|  
|[\<TypeParameter >](../../../docs/framework/net-native/typeparameter-element-net-native.md)|Tarafından temsil edilen bir türün ilkenin uygulanacağı bir <xref:System.Type> bir yönteme geçirilen bağımsız değişken.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<türü >](../../../docs/framework/net-native/type-element-net-native.md)|Yansıma İlkesi, bir tür ve tüm üyeleri için geçerlidir.|  
|[\<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Yansıma ilkesini, oluşturulmuş bir genel türü ve tüm üyeleri için geçerlidir.|  
  
## <a name="remarks"></a>Açıklamalar  
 A `<Method>` öğesi bir genel yöntem, ilke kendi ilkesi olmayan tüm örneklemesi için geçerlidir.  
  
 Kullanabileceğiniz `Signature` belirli yöntemi aşırı yüklemesini yönelik ilke belirtmek için özniteliği. Aksi takdirde `Signature` özniteliği eksik olduğundan, çalışma zamanı yönerge yöntemin tüm aşırı yüklemeler için geçerlidir.  
  
 Kullanarak çalışma zamanı yansıma ilkesini bir oluşturucu tanımlayamaz `<Method>` öğesi. Bunun yerine, `Activate` özniteliği [ \<derleme >](../../../docs/framework/net-native/assembly-element-net-native.md), [ \<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md), [ \<türü >](../../../docs/framework/net-native/type-element-net-native.md), veya [ \<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) öğesi.  
  
## <a name="example"></a>Örnek  
 `Stringify` Yöntemidir aşağıdaki örnekte bir nesneyi dize gösterimine dönüştürmek için yansıtma kullanır. genel amaçlı bir biçimlendirme yöntemi. Nesnenin varsayılan çağırma yanı sıra `ToString` yöntemi yöntemi üretebilir biçimlendirilmiş Sonuç dizesini bir nesnenin geçirerek `ToString` yöntemi bir biçim dizesi bir <xref:System.IFormatProvider> uygulama veya her ikisi de. Biri de çağırabilirsiniz <xref:System.Convert.ToString%2A?displayProperty=nameWithType> aşırı birkaç ikili, onaltılık veya sekizlik gösterimine dönüştürür.  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 `Stringify` Yöntemi, aşağıdaki gibi kod tarafından çağrılabilir:  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 Ancak, .NET Native ile derlendiğinde, örnek bir özel durum sayısı çalışma zamanında oluşturabilecek dahil olmak üzere <xref:System.NullReferenceException> ve [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) özel durumlar, bu gerçekleşir çünkü `Stringify` yöntemi dinamik olarak .NET Framework sınıf kitaplığındaki temel türlerin biçimlendirme öncelikle desteklemeye yöneliktir. Ancak, meta verilerinin varsayılan yönergeleri dosyası tarafından erişilebilir değildir. Ancak, hatta meta verilerinin kullanılabilir olduğunda, örnek oluşturur. [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) özel durumları çünkü uygun `ToString` uygulamaları sahip olan dahil yerel kodda.  
  
 Bu özel durumların tüm kullanılarak kaldırılabilir [ \<türü >](../../../docs/framework/net-native/type-element-net-native.md) olan meta veri varsa ve ekleyerek olmalıdır türleri tanımlamak için `<Method>` yöntemi aşırı yüklemeleri uygulanmasını sağlamak için öğeleri çağrılabilen dinamik olarak da mevcuttur. Bu özel durumları ortadan kaldırır ve hatasız yürütmek örnek sağlayan default.rd.xml dosyası verilmiştir.  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
     <Assembly Name="*Application*" Dynamic="Required All" />  
  
     <Type Name = "System.Convert" Browse="Required Public" Dynamic="Required Public" >  
        <Method Name="ToString"    Dynamic ="Required" />  
     </Type>  
     <Type Name="System.Double" Browse="Required Public">  
        <Method Name="ToString" Dynamic="Required" />  
     </Type>  
     <Type Name ="System.Int32" Browse="Required Public" >  
        <Method Name="ToString" Dynamic="Required" />  
     </Type>  
     <Type Name ="System.Int64" Browse="Required Public" >  
        <Method Name="ToString" Dynamic="Required" />  
     </Type>  
     <Namespace Name="System" >  
        <Type Name="Byte" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="DateTime" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="Decimal" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="Guid" Browse ="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="Int16" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="SByte" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="Single" Browse="Required Public" >  
          <Method Name="ToString" Dynamic="Required" />           
        </Type>  
        <Type Name="TimeSpan" Browse="Required Public" >  
          <Method Name="ToString" Dynamic="Required" />           
        </Type>  
        <Type Name="UInt16" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="UInt32" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="UInt64" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
     </Namespace>  
  </Application>  
</Directives>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [Çalışma Zamanı Yönerge Öğeleri](../../../docs/framework/net-native/runtime-directive-elements.md)
- [Çalışma Zamanı Yönerge İlkesi Ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
- [\<Methodınstantiation > öğesi](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)

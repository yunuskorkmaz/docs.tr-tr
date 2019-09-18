---
title: <Method>Öğesi (.NET Native)
ms.date: 03/30/2017
ms.assetid: 348b49e5-589d-4eb2-a597-d6ff60ab52d1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d741f51abf02f4bfda2b007efd4c859027e54d9b
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049586"
---
# <a name="method-element-net-native"></a>\<Metot > öğesi (.NET Native)
Çalışma zamanı yansıtma ilkesini bir oluşturucuya veya yöntemine uygular.  
  
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
|`Signature`|Genel|İsteğe bağlı öznitelik. Yöntem imzasını belirtir. Birden çok parametre varsa, bunlar virgülle ayrılır. Örneğin, aşağıdaki `<Method>` öğe <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29> yöntemi için ilkeyi tanımlar.<br /><br /> `<Type Name="System.DateTime">    <Method Name="ToString" Signature="System.String,System.IFormatProvider"            Dynamic="Required" /> </Type>`<br /><br /> Öznitelik yoksa, çalışma zamanı yönergesi metodun tüm aşırı yüklemeleri için geçerlidir.|  
|`Browse`|Yansıma|İsteğe bağlı öznitelik. Bir yöntem hakkında bilgi sorgulama veya bir yöntemi numaralandırma, ancak çalışma zamanında dinamik çağırma etkinleştirmeyin.|  
|`Dynamic`|Yansıma|İsteğe bağlı öznitelik. Dinamik programlamayı etkinleştirmek için bir oluşturucuya veya yönteme çalışma zamanı erişimini denetler. Bu ilke, bir üyenin çalışma zamanında dinamik olarak çağrılabilir olmasını sağlar.|  
  
## <a name="name-attribute"></a>Ad özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*method_name*|Yöntem adı. Metodun türü, üst [ \<tür >](type-element-net-native.md) veya [ \<typeörneklemesi >](typeinstantiation-element-net-native.md) öğesi tarafından tanımlanır.|  
  
## <a name="signature-attribute"></a>Signature özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*method_signature*|Yöntem imzasını oluşturan parametre türleri. Birden çok parametre virgüllerle ayrılır, örneğin, `"System.String,System.Int32,System.Int32)"`. Parametre türü adları tam olarak nitelenmelidir.|  
  
## <a name="all-other-attributes"></a>Diğer tüm öznitelikler  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*policy_setting*|Bu ilke türüne uygulanacak ayar. Olası değerler şunlardır `Auto` `Excluded` `Required`, ,ve.`Included` Daha fazla bilgi için bkz. [çalışma zamanı yönergesi Ilke ayarları](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Parametre >](parameter-element-net-native.md)|Bir yönteme geçirilen bağımsız değişkenin türüne ilke uygular.|  
|[\<GenericParameter >](genericparameter-element-net-native.md)|İlkeyi genel bir türün veya yöntemin parametre türüne uygular.|  
|[\<Impliestype >](impliestype-element-net-native.md)|İlke, kapsayan `<Method>` öğe tarafından temsil edilen yönteme uygulanmışsa, ilkeyi bir türe uygular.|  
|[\<TypeParameter >](typeparameter-element-net-native.md)|Bir yönteme geçirilen <xref:System.Type> bağımsız değişkenle temsil edilen türe ilke uygular.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Tür >](type-element-net-native.md)|Yansıma ilkesini bir türe ve tüm üyelerine uygular.|  
|[\<Typeörneklemesi >](typeinstantiation-element-net-native.md)|Oluşturulan genel türe ve tüm üyelerine yansıma ilkesi uygular.|  
  
## <a name="remarks"></a>Açıklamalar  
 Genel `<Method>` yöntemin bir öğesi, kendi ilkesi olmayan tüm örneklemelerde ilkesini uygular.  
  
 Belirli bir yöntem aşırı `Signature` yüklemesi için ilkeyi belirtmek üzere özniteliğini kullanabilirsiniz. Aksi halde, özniteliği yoksa, çalışma zamanı yönergesi metodun tüm aşırı yüklemeleri için geçerlidir. `Signature`  
  
 `<Method>` Öğesini kullanarak bir Oluşturucu için çalışma zamanı yansıtma ilkesini tanımlayamazsınız. `Activate` Bunun yerine, [ \<derleme >](assembly-element-net-native.md), [ \<ad alanı >](namespace-element-net-native.md), [ \<tür >](type-element-net-native.md)veya [ \<typeörneklemesi >](typeinstantiation-element-net-native.md) öğesi özniteliğini kullanın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki `Stringify` örnekteki yöntem, bir nesneyi dize gösterimine dönüştürmek için yansıma kullanan genel amaçlı bir biçimlendirme yöntemidir. Nesnenin varsayılan `ToString` metodunu çağırmanın yanı sıra, yöntemi bir `ToString` nesnenin yöntemini bir biçim dizesi, bir <xref:System.IFormatProvider> uygulama veya her ikisi geçirerek, biçimlendirilen bir sonuç dizesi üretebilir. Ayrıca, bir sayıyı ikili, onaltılı <xref:System.Convert.ToString%2A?displayProperty=nameWithType> veya sekizli gösterimine dönüştüren aşırı yüklemelerin birini çağırabilir.  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 `Stringify` Yöntemi, aşağıdaki gibi kodla çağrılabilir:  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 Ancak, .NET Native ile derlendiğinde, örnek, çalışma zamanında, ve [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) özel durumları dahil <xref:System.NullReferenceException> olmak üzere bir dizi özel durum oluşturabilir, `Stringify` bunun nedeni yöntemin öncelikle .NET Framework sınıf kitaplığındaki temel türleri dinamik olarak biçimlendirmeyi destekler. Ancak, meta verileri varsayılan yönergeler dosyası tarafından kullanılamaz. Ancak meta verileri kullanılabilir duruma getirilse de, uygun `ToString` uygulamalar yerel koda dahil olmadığından, örnek [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) özel durumları oluşturur.  
  
 Bu özel durumlar, meta verileri bulunması gereken türleri tanımlamak için [ \<tür >](type-element-net-native.md) öğesi kullanılarak ve çağrılabilir yöntem aşırı yüklemelerinin uygulanmasını sağlamak için öğe ekleyerek `<Method>` ortadan kaldırılabilir. dinamik olarak da mevcuttur. Aşağıda, bu özel durumları ortadan kaldıran ve örneğin hatasız yürütülmesine izin veren default. RD. xml dosyası verilmiştir.  
  
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

- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](runtime-directives-rd-xml-configuration-file-reference.md)
- [Çalışma Zamanı Yönerge Öğeleri](runtime-directive-elements.md)
- [Çalışma Zamanı Yönerge İlkesi Ayarları](runtime-directive-policy-settings.md)
- [\<Methodörneklemesi > öğesi](methodinstantiation-element-net-native.md)

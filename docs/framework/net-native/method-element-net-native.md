---
title: <Method>Eleman (.NET Yerel)
ms.date: 03/30/2017
ms.assetid: 348b49e5-589d-4eb2-a597-d6ff60ab52d1
ms.openlocfilehash: 8db32c660846b4f4071fff2a40c760a3d1ef2489
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180985"
---
# <a name="method-element-net-native"></a>\<Yöntem> Elemanı (.NET Yerli)
Bir oluşturucuya veya yönteme çalışma zamanı yansıtma ilkesi uygular.  
  
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
|`Signature`|Genel|İsteğe bağlı öznitelik. Yöntem imzasını belirtir. Birden çok parametre varsa, virgülle ayrılırlar. Örneğin, aşağıdaki `<Method>` öğe <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29> yöntem için ilke tanımlar.<br /><br /> `<Type Name="System.DateTime">    <Method Name="ToString" Signature="System.String,System.IFormatProvider"            Dynamic="Required" /> </Type>`<br /><br /> Öznitelik yoksa, çalışma zamanı yönergesi yöntemin tüm aşırı yükleri için geçerlidir.|  
|`Browse`|Yansıma|İsteğe bağlı öznitelik. Bir yöntem hakkında bilgi için sorgulamayı veya bir yöntemin sayısalasını denetler, ancak çalışma zamanında dinamik bir çağrıyı etkinleştirmez.|  
|`Dynamic`|Yansıma|İsteğe bağlı öznitelik. Dinamik programlamayı etkinleştirmek için bir oluşturucuya veya yönteme çalışma zamanı erişimini denetler. Bu ilke, bir üyenin çalışma zamanında dinamik olarak çağrılmasını sağlar.|  
  
## <a name="name-attribute"></a>Ad özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*method_name*|Yöntem adı. Yöntemin türü ana [ \<Type>](type-element-net-native.md) veya [ \<TypeInstantiation>](typeinstantiation-element-net-native.md) öğesi tarafından tanımlanır.|  
  
## <a name="signature-attribute"></a>İmza özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*method_signature*|Yöntem imzasını oluşturan parametre türleri. Birden çok parametre virgülle `"System.String,System.Int32,System.Int32)"`ayrılır, örneğin. Parametre türü adları tam nitelikli olmalıdır.|  
  
## <a name="all-other-attributes"></a>Diğer tüm öznitelikler  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*policy_setting*|Bu ilke türüne uygulanacak ayar. Olası değerler `Auto` `Excluded`, `Included`, `Required`, ve . Daha fazla bilgi için [Runtime Yönergesi İlke Ayarları'na](runtime-directive-policy-settings.md)bakın.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Parametre>](parameter-element-net-native.md)|Bir yönteme geçirilen bağımsız değişken türüne ilke uygular.|  
|[\<Genel Parametre>](genericparameter-element-net-native.md)|Genel bir tür veya yöntemin parametre türüne ilke uygular.|  
|[\<ImpliesType>](impliestype-element-net-native.md)|Bu ilke, içeren `<Method>` öğe tarafından temsil edilen yönteme uygulanmışsa, bir türe ilke uygular.|  
|[\<TipParametre>](typeparameter-element-net-native.md)|Bir yönteme geçirilen bir <xref:System.Type> bağımsız değişken tarafından temsil edilen türe ilke uygular.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Tip>](type-element-net-native.md)|Yansıma ilkesini bir türe ve tüm üyelerine uygular.|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|Yapılı genel bir türe ve tüm üyelerine yansıma ilkesi uygular.|  
  
## <a name="remarks"></a>Açıklamalar  
 Genel `<Method>` bir yöntemin bir öğesi, ilkesini kendi ilkesi olmayan tüm anlık iletilere uygular.  
  
 Belirli bir `Signature` yöntem aşırı yüklemesi için ilke belirtmek için öznitelik kullanabilirsiniz. Aksi takdirde, `Signature` öznitelik yoksa, çalışma zamanı yönergesi yöntemin tüm aşırı yükleri için geçerlidir.  
  
 `<Method>` Öğeyi kullanarak bir oluşturucu için çalışma zamanı yansıtma ilkesini tanımlayamazsınız. Bunun yerine, `Activate` [ \<Derleme>, ](assembly-element-net-native.md) [ \<Namespace>, ](namespace-element-net-native.md) [ \<Type>](type-element-net-native.md)veya [ \<TypeInstantiation>](typeinstantiation-element-net-native.md) öğesiözeğini kullanın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki `Stringify` örnekteki yöntem, bir nesneyi dize gösterimine dönüştürmek için yansımayı kullanan genel amaçlı bir biçimlendirme yöntemidir. Nesnenin varsayılan `ToString` yöntemini çağırmaya ek olarak, yöntem, nesnenin `ToString` yöntemini biçimlendirme dizesi, <xref:System.IFormatProvider> uygulama veya her ikisini birden geçirerek biçimlendirilmiş bir sonuç dizesi üretebilir. Ayrıca, bir sayıyı <xref:System.Convert.ToString%2A?displayProperty=nameWithType> ikili, heksadesibel veya sekizli gösterimine dönüştüren aşırı yüklerden birini de çağırabilir.  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 Yöntem `Stringify` aşağıdaki gibi kod la çağrılabilir:  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 Ancak, .NET Native ile derlendiğinde, örnek çalışma zamanında bir dizi özel <xref:System.NullReferenceException> durum atabilir, ve [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) özel durumlar da dahil olmak üzere, yöntem öncelikle .NET Framework Class Kitaplığı'ndaki ilkel türleri dinamik olarak biçimlendirmeyi desteklemek için tasarlandığından bu `Stringify` oluşur. Ancak, meta verileri varsayılan yönergeler dosyası tarafından kullanılamaz. Ancak, meta verileri kullanılabilir hale getirilse bile, uygun `ToString` uygulamalar yerel koda dahil edilmediğinden, örnek Eksik [RuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) özel durumlarını atar.  
  
 Bu özel durumlar, meta verileri bulunması gereken türleri tanımlamak için [ \<Type>](type-element-net-native.md) öğesi kullanılarak `<Method>` ve dinamik olarak çağrılabilen yöntem aşırı yüklemelerinin uygulanmasının da mevcut olduğundan emin olmak için öğeler eklenerek ortadan kaldırılabilir. Aşağıda, bu özel durumları ortadan kaldıran ve örneğin hatasız yürütülmesine izin veren default.rd.xml dosyası verilmiştir.  
  
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
- [\<MethodInstantiation> Elementi](methodinstantiation-element-net-native.md)

---
title: <Method> öğesi (.NET Native)
ms.date: 03/30/2017
ms.assetid: 348b49e5-589d-4eb2-a597-d6ff60ab52d1
ms.openlocfilehash: 7b0e77e6dea29cbd5218ab3f6f992002efd51656
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128342"
---
# <a name="method-element-net-native"></a>\<yöntemi > öğesi (.NET Native)
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
|`Signature`|Genel|İsteğe bağlı öznitelik. Yöntem imzasını belirtir. Birden çok parametre varsa, bunlar virgülle ayrılır. Örneğin, aşağıdaki `<Method>` öğesi <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29> yöntemi için ilkeyi tanımlar.<br /><br /> `<Type Name="System.DateTime">    <Method Name="ToString" Signature="System.String,System.IFormatProvider"            Dynamic="Required" /> </Type>`<br /><br /> Öznitelik yoksa, çalışma zamanı yönergesi metodun tüm aşırı yüklemeleri için geçerlidir.|  
|`Browse`|Yansıma|İsteğe bağlı öznitelik. Bir yöntem hakkında bilgi sorgulama veya bir yöntemi numaralandırma, ancak çalışma zamanında dinamik çağırma etkinleştirmeyin.|  
|`Dynamic`|Yansıma|İsteğe bağlı öznitelik. Dinamik programlamayı etkinleştirmek için bir oluşturucuya veya yönteme çalışma zamanı erişimini denetler. Bu ilke, bir üyenin çalışma zamanında dinamik olarak çağrılabilir olmasını sağlar.|  
  
## <a name="name-attribute"></a>Ad özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*method_name*|Yöntem adı. Metodun türü, üst [\<türü >](type-element-net-native.md) veya [\<typeörneklemesi >](typeinstantiation-element-net-native.md) öğesi tarafından tanımlanır.|  
  
## <a name="signature-attribute"></a>Signature özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*method_signature*|Yöntem imzasını oluşturan parametre türleri. Birden çok parametre virgüllerle ayrılır, örneğin `"System.String,System.Int32,System.Int32)"`. Parametre türü adları tam olarak nitelenmelidir.|  
  
## <a name="all-other-attributes"></a>Diğer tüm öznitelikler  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*policy_setting*|Bu ilke türüne uygulanacak ayar. Olası değerler şunlardır `Auto`, `Excluded`, `Included`ve `Required`. Daha fazla bilgi için bkz. [çalışma zamanı yönergesi Ilke ayarları](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<parametresi >](parameter-element-net-native.md)|Bir yönteme geçirilen bağımsız değişkenin türüne ilke uygular.|  
|[\<GenericParameter >](genericparameter-element-net-native.md)|İlkeyi genel bir türün veya yöntemin parametre türüne uygular.|  
|[\<ımpliestype >](impliestype-element-net-native.md)|İlke, kapsayan `<Method>` öğesi tarafından temsil edilen yönteme uygulanmışsa, ilkeyi bir türe uygular.|  
|[\<TypeParameter >](typeparameter-element-net-native.md)|Bir yönteme geçirilen <xref:System.Type> bağımsız değişkeniyle temsil edilen türe ilke uygular.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<türü >](type-element-net-native.md)|Yansıma ilkesini bir türe ve tüm üyelerine uygular.|  
|[\<Typeörneklemesi >](typeinstantiation-element-net-native.md)|Oluşturulan genel türe ve tüm üyelerine yansıma ilkesi uygular.|  
  
## <a name="remarks"></a>Açıklamalar  
 Genel yöntemin `<Method>` öğesi, kendi ilkesi olmayan tüm örneklemelerde ilkesini uygular.  
  
 Belirli bir yöntem aşırı yüklemesi için ilkeyi belirtmek üzere `Signature` özniteliğini kullanabilirsiniz. Aksi takdirde, `Signature` özniteliği yoksa, çalışma zamanı yönergesi metodun tüm aşırı yüklemeleri için geçerlidir.  
  
 `<Method>` öğesini kullanarak bir Oluşturucu için çalışma zamanı yansıtma ilkesini tanımlayamazsınız. Bunun yerine [\<bütünleştirilmiş kod >](assembly-element-net-native.md)`Activate` özniteliğini, [\<ad alanı >](namespace-element-net-native.md), [\<tür >](type-element-net-native.md)veya [\<typeörneklemesi >](typeinstantiation-element-net-native.md) öğesini kullanın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekteki `Stringify` yöntemi, bir nesneyi dize gösterimine dönüştürmek için yansıma kullanan genel amaçlı bir biçimlendirme yöntemidir. Nesnenin varsayılan `ToString` yöntemini çağırmaya ek olarak, yöntemi bir nesnenin `ToString` yöntemini bir biçim dizesi, bir <xref:System.IFormatProvider> uygulama veya her ikisini geçirerek, biçimli bir sonuç dizesi üretebilir. Ayrıca, bir sayıyı ikili, onaltılı veya sekizli gösterimine dönüştüren <xref:System.Convert.ToString%2A?displayProperty=nameWithType> aşırı yüklerden birini çağırabilir.  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 `Stringify` yöntemi aşağıdaki gibi kodla çağrılabilir:  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 Ancak, .NET Native ile derlendiğinde, örnek, çalışma zamanında <xref:System.NullReferenceException> ve [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) özel durumları dahil olmak üzere bir dizi özel durum oluşturabilir, bu durum `Stringify` yönteminin öncelikle desteklenmesini amaçladığı için oluşur .NET Framework sınıf kitaplığındaki temel türleri dinamik olarak biçimlendirme. Ancak, meta verileri varsayılan yönergeler dosyası tarafından kullanılamaz. Ancak meta verileri kullanılabilir duruma getirilse de, uygun `ToString` uygulamaları yerel koda dahil olmadığından, örnek [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) özel durumları oluşturur.  
  
 Bu özel durumlar, meta verileri bulunması gereken türleri tanımlamak için [\<türü >](type-element-net-native.md) öğesi kullanılarak ve dinamik olarak çağrılabilen yöntem aşırı yüklemelerinin uygulanmasını sağlamak için `<Method>` öğeleri ekleyerek ortadan kaldırılabilir. görüntülemeyen. Aşağıda, bu özel durumları ortadan kaldıran ve örneğin hatasız yürütülmesine izin veren default. RD. xml dosyası verilmiştir.  
  
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

---
title: "&lt;Method&gt; Öğesi (.NET Yerel)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 348b49e5-589d-4eb2-a597-d6ff60ab52d1
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c6d70fd560cb7b164460eb3882cac88ed733d788
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltmethodgt-element-net-native"></a>&lt;Method&gt; Öğesi (.NET Yerel)
Çalışma zamanı yansıma ilke oluşturucunun ya da yöntemi için geçerlidir.  
  
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
|`Signature`|Genel|İsteğe bağlı öznitelik. Yöntem imzası belirtir. Birden çok parametre varsa, bunların virgülle ayrılır. Örneğin, aşağıdaki `<Method>` öğesi tanımlar için ilke <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29> yöntemi.<br /><br /> `<Type Name="System.DateTime">    <Method Name="ToString" Signature="System.String,System.IFormatProvider"            Dynamic="Required" /> </Type>`<br /><br /> Öznitelik olmazsa, çalışma zamanı yönerge yöntemi tüm aşırı yüklemeleri için geçerlidir.|  
|`Browse`|Yansıma|İsteğe bağlı öznitelik. Hakkında bilgi için sorgulama veya bir yöntem numaralandırma kontrol eder, ancak çalışma zamanında dinamik herhangi çağırma etkinleştirmez.|  
|`Dynamic`|Yansıma|İsteğe bağlı öznitelik. Programlama Oluşturucusu veya dinamik etkinleştirmek için yöntemi çalışma zamanı erişimi kontrol eder. Bu ilke üyesi çalışma zamanında dinamik olarak çağrılabilir sağlar.|  
  
## <a name="name-attribute"></a>Ad özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*method_name*|Yöntem adı. Yöntem türü üst tarafından tanımlanan [ \<türü >](../../../docs/framework/net-native/type-element-net-native.md) veya [ \<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) öğesi.|  
  
## <a name="signature-attribute"></a>İmza özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*method_signature*|Yöntem imzası form parametre türleri. Birden çok parametre, örneğin, virgülle ayrılır `"System.String,System.Int32,System.Int32)"`. Parametre türü adları tam olarak nitelenmiş olmalıdır.|  
  
## <a name="all-other-attributes"></a>Tüm diğer özniteliklerle  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*policy_setting*|Bu ilke türü için geçerli ayar. Olası değerler şunlardır: `Auto`, `Excluded`, `Included`, ve `Required`. Daha fazla bilgi için bkz: [çalışma zamanı yönerge İlkesi ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Parametresi >](../../../docs/framework/net-native/parameter-element-net-native.md)|Bir yönteme geçirilen bağımsız değişken türü ilke uygulanır.|  
|[\<GenericParameter >](../../../docs/framework/net-native/genericparameter-element-net-native.md)|İlke genel türü veya yöntemi parametresinin türü için geçerlidir.|  
|[\<Impliestype >](../../../docs/framework/net-native/impliestype-element-net-native.md)|Bu ilkeyi içeren tarafından temsil edilen yöntem uygulandıysa İlkesi bir türü için geçerlidir `<Method>` öğesi.|  
|[\<TypeParameter >](../../../docs/framework/net-native/typeparameter-element-net-native.md)|Tarafından temsil edilen türü ilkenin uygulandığı bir <xref:System.Type> yöntemi için bağımsız değişken geçirildi.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Türü >](../../../docs/framework/net-native/type-element-net-native.md)|Yansıma ilke türü ve tüm üyeleri için geçerlidir.|  
|[\<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Yansıma İlkesi, yapılandırılmış bir genel tür ve tüm üyeleri için geçerlidir.|  
  
## <a name="remarks"></a>Açıklamalar  
 A `<Method>` genel yöntem öğesinin kendi ilke olmayan tüm örneklemesi kendi ilke uygulanır.  
  
 Kullanabileceğiniz `Signature` belirli yöntemi aşırı yüklemesini ilkesini belirtmek için öznitelik. Aksi halde, eğer `Signature` özniteliği yoksa, çalışma zamanı yönerge yöntemi tüm aşırı yüklemeleri için geçerlidir.  
  
 Kullanarak bir oluşturucu için çalışma zamanı yansıma İlkesi tanımlayamazsınız `<Method>` öğesi. Bunun yerine, kullanın `Activate` özniteliği [ \<derleme >](../../../docs/framework/net-native/assembly-element-net-native.md), [ \<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md), [ \<türü >](../../../docs/framework/net-native/type-element-net-native.md), veya [ \<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) öğesi.  
  
## <a name="example"></a>Örnek  
 `Stringify` Yöntemidir aşağıdaki örnekte, dize gösterimi bir nesneyi dönüştürmek için yansıma kullanan genel amaçlı bir biçimlendirme yöntemi. Nesnenin varsayılan çağıran yanı sıra `ToString` yöntemi, yöntem oluşturabilirsiniz biçimlendirilmiş Sonuç dizesini bir nesnenin geçirerek `ToString` yöntemi bir biçim dizesi bir <xref:System.IFormatProvider> uygulaması ya da her ikisini de. Aşağıdakilerden birini de işleyememesi <xref:System.Convert.ToString%2A?displayProperty=nameWithType> bir sayı, ikili, onaltılık veya sekizlik gösterimine dönüştürür aşırı.  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 `Stringify` Yöntemi, aşağıdaki gibi kod tarafından çağrılabilir:  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 Ancak, .NET yerel ile derlendiğinde örnek bir özel durum sayısı çalışma zamanında atabilirsiniz dahil olmak üzere <xref:System.NullReferenceException> ve [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) özel durumlar, bu oluşur çünkü `Stringify` yöntemi dinamik olarak .NET Framework Sınıf Kitaplığı'nda ilkel türler biçimlendirme öncelikle desteklemeye yönelik. Ancak, bunların meta verilerini varsayılan yönergeleri dosyası tarafından kullanılabilir hale getirilir değil. Hatta kendi meta veriler kullanılabilir olduğunda, ancak örnek oluşturur [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) özel durumlar için uygun `ToString` uygulamaları sahip olan dahil yerel kodda.  
  
 Bu özel durumlar tüm kullanarak Kaldırılabilir [ \<türü >](../../../docs/framework/net-native/type-element-net-native.md) , meta verileri, mevcut ve ekleyerek olmalıdır türlerini tanımlamak üzere öğesi `<Method>` yöntemi aşırı uyarlamasını emin olmak için öğeleri çağrılabilir dinamik olarak da mevcuttur. Bu özel durumları ortadan kaldırır ve hatasız yürütmek örnek sağlayan default.rd.xml dosya verilmiştir.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çalışma zamanı yönergeleri (rd.xml) yapılandırma dosyası başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [Çalışma zamanı yönerge öğeleri](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [Çalışma zamanı yönerge İlkesi ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md)  
 [\<Methodınstantiation > öğesi](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)

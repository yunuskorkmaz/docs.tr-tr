---
title: Yansıma ve Genel Türler
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- generics [.NET Framework], reflection emit
- reflection emit, generic types
- reflection, generic types
- type arguments
- generics [.NET Framework], reflection
- viewing type information
- type information, viewing
- types, generic
- type parameters
ms.assetid: f7180fc5-dd41-42d4-8a8e-1b34288e06de
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a45ef91eba38223270a04cff2f00c30decb019f1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793126"
---
# <a name="reflection-and-generic-types"></a>Yansıma ve Genel Türler
<a name="top"></a> Bakış açısıyla yansıma, genel bir tür bir sıradan tür arasındaki fark (genel tür tanımı değilse) genel bir tür ile tür parametreleri kümesini ilişkilendirildiğinizden olduğu veya tür bağımsız değişkenleri (oluşturulan bir tür ise). Genel yöntem, aynı şekilde sıradan bir yönteminden farklıdır.  
  
 Yansıma, genel türler ve yöntemlerin nasıl işlediğini anlamak için iki anahtarı vardır:  
  
- Genel tür tanımları ve genel yöntem tanımlarını tür parametreleri örnekleri tarafından temsil edilen <xref:System.Type> sınıfı.  
  
    > [!NOTE]
    >  Çoğu özellikleri ve yöntemleri <xref:System.Type> farklı davranışa sahip olduğunda bir <xref:System.Type> nesnesi bir genel tür parametresini temsil eder. Bu farklılıklar, özellik ve yöntem konularındaki belgelenmiştir. Örneğin, <xref:System.Type.IsAutoClass%2A> ve <xref:System.Type.DeclaringType%2A>. Ayrıca, yalnızca geçerli olduğunda bazı üyeleri olan bir <xref:System.Type> nesnesi bir genel tür parametresini temsil eder. Örneğin, <xref:System.Type.GetGenericTypeDefinition%2A>.  
  
- Örneği, <xref:System.Type> sonra tür parametreleri (için genel tür tanımları) veya tür bağımsız değişkenleri (için oluşturulan türler) temsil eden bir tür dizisi içeren bir genel türü temsil eder. Aynı örneğini geçerlidir <xref:System.Reflection.MethodInfo> genel bir yöntemi temsil eden sınıf.  
  
 Yansıma yöntemlerini sağlar <xref:System.Type> ve <xref:System.Reflection.MethodInfo> tür parametreleri dizisi erişmek ve örneği olup olmadığını belirlemek için izin <xref:System.Type> bir tür parametresi veya gerçek bir türü temsil eder.  
  
 Örneğin, burada bahsedilen yöntemler gösteren kodu görmek [nasıl yapılır: İnceleme ve örnek oluşturma yansıma ile genel türleri](../../../docs/framework/reflection-and-codedom/how-to-examine-and-instantiate-generic-types-with-reflection.md).  
  
 Aşağıdaki tartışmaya terminolojisi genel türler, tür parametreleri ve bağımsız değişkenler arasındaki farkı gibi konusunda ve açık veya kapalı oluşturulan türler varsayar. Daha fazla bilgi için [genel türler](../../../docs/standard/generics/index.md).  
  
 Bu genel bakış aşağıdaki bölümlerden oluşur:  
  
- [Bu, bir genel tür veya yöntemin mi?](#is_this_a_generic_type_or_method)  
  
- [Kapalı genel türler oluşturma](#generating_closed_generic_types)  
  
- [Tür bağımsız değişkeni ve tür parametreleri İnceleme](#examining_type_arguments)  
  
- [Okuduğunuzda](#invariants)  
  
- [İlgili Konular](#related_topics)  
  
<a name="is_this_a_generic_type_or_method"></a>   
## <a name="is-this-a-generic-type-or-method"></a>Bu, bir genel tür veya yöntemin mi?  
 Bilinmeyen bir tür örneği tarafından temsil edilen incelemek için yansıma kullanırken <xref:System.Type>, kullanın <xref:System.Type.IsGenericType%2A> bilinmeyen tür genel olup olmadığını belirlemek için özellik. Döndürür `true` tür genel ise. Benzer şekilde, bir örneği tarafından temsil edilen bir bilinmeyen yöntem incelediğinizde <xref:System.Reflection.MethodInfo> sınıfı, kullanın <xref:System.Reflection.MethodBase.IsGenericMethod%2A> yöntemi genel olup olmadığını belirlemek için özellik.  
  
### <a name="is-this-a-generic-type-or-method-definition"></a>Bu, bir genel tür veya yöntem tanımını mi?  
 Kullanma <xref:System.Type.IsGenericTypeDefinition%2A> belirlemek için özellik olup olmadığını bir <xref:System.Type> nesnesini gösteren bir genel tür tanımı ve kullanımı <xref:System.Reflection.MethodBase.IsGenericMethodDefinition%2A> belirlemek için yöntemi olup olmadığını bir <xref:System.Reflection.MethodInfo> bir genel yöntem tanımını temsil eder.  
  
 Genel tür ve yöntem tanımlarını instantiable türleri oluşturulduğu şablonlardır. Genel türleri .NET Framework sınıf kitaplığında gibi <xref:System.Collections.Generic.Dictionary%602>, genel tür tanımlar.  
  
### <a name="is-the-type-or-method-open-or-closed"></a>Tür veya yöntem açık veya kapalı?  
 Her kapsayan türden tüm tür parametreleri de dahil olmak üzere tüm tür parametreleri için instantiable türleri yapıştırıyorsanız, bir genel tür veya yöntemin kapalı. Kapalıysa bir genel türün bir örneği yalnızca oluşturabilirsiniz. <xref:System.Type.ContainsGenericParameters%2A?displayProperty=nameWithType> Özelliği döndürür `true` bir tür açık değilse. Yöntemleri için <xref:System.Reflection.MethodBase.ContainsGenericParameters%2A?displayProperty=nameWithType> yöntem aynı işlevi gerçekleştirir.  
  
 [Başa dön](#top)  
  
<a name="generating_closed_generic_types"></a>   
## <a name="generating-closed-generic-types"></a>Kapalı genel türler oluşturma  
 Bir genel tür veya yöntem tanımını aldıktan sonra kullanmak <xref:System.Type.MakeGenericType%2A> kapalı genel tür yöntemini veya <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A> yöntemi oluşturmak için bir <xref:System.Reflection.MethodInfo> kapalı bir obecnou metodu.  
  
### <a name="getting-the-generic-type-or-method-definition"></a>Genel tür veya yöntem tanımını alma  
 Bir açık genel tür veya bir genel tür veya yöntem tanımını yöntemi varsa, örnekleri oluşturulamıyor ve eksik tür parametrelerini sağlayamazsınız. Genel bir türün veya yöntemin tanımı olmalıdır. Kullanım <xref:System.Type.GetGenericTypeDefinition%2A> genel tür tanımı elde etmek için yöntemi veya <xref:System.Reflection.MethodInfo.GetGenericMethodDefinition%2A> genel yöntem tanımının elde etmek için yöntemi.  
  
 Örneğin, bir <xref:System.Type> nesnesini temsil eden `Dictionary<int, string>` (`Dictionary(Of Integer, String)` Visual Basic'te) ve türü oluşturmak istediğiniz `Dictionary<string, MyClass>`, kullanabileceğiniz <xref:System.Type.GetGenericTypeDefinition%2A> almak için yöntemi bir <xref:System.Type> temsil eden `Dictionary<TKey, TValue>` ve ardından <xref:System.Type.MakeGenericType%2A> üretmek için yöntemi bir <xref:System.Type> temsil eden `Dictionary<int, MyClass>`.  
  
 Genel bir tür değil bir açık genel tür örneği için "Tür parametresi veya tür bağımsız değişkeni" bölümüne bakın.  
  
 [Başa dön](#top)  
  
<a name="examining_type_arguments"></a>   
## <a name="examining-type-arguments-and-type-parameters"></a>Tür bağımsız değişkeni ve tür parametreleri İnceleme  
 Kullanma <xref:System.Type.GetGenericArguments%2A?displayProperty=nameWithType> dizisi elde etmek için yöntemi <xref:System.Type> tür parametreleri veya genel bir türün tür bağımsız değişkenleri temsil eden ve nesneleri <xref:System.Reflection.MethodInfo.GetGenericArguments%2A?displayProperty=nameWithType> yöntemi genel yöntem için de aynısını yapın.  
  
 Sonra bildiğiniz bir <xref:System.Type> nesnesini temsil eden bir tür parametresi, yansıma yanıtlarını alabileceğiniz çok sayıda başka sorularınız vardır. Tür parametresi'nın kaynak ve konumunu kısıtlamaları belirleyebilirsiniz.  
  
### <a name="type-parameter-or-type-argument"></a>Tür parametresi veya tür bağımsız değişkeni  
 Dizinin belirli bir öğesi bir tür parametresi veya tür bağımsız değişkeni olup olmadığını belirlemek için <xref:System.Type.IsGenericParameter%2A> özelliği. <xref:System.Type.IsGenericParameter%2A> Özelliği `true` öğesi bir tür parametresi ise.  
  
 Bu durumda tür bağımsız değişkeni tür parametreleri ve karışımı vardır, genel tür tanımı olmadan genel bir tür açık olabilir. Örneğin, aşağıdaki kodda, sınıf `D` ilk tür parametresi koyarak tarafından oluşturulan bir tür türetilen `D` ikinci tür parametresi için `B`.  
  
```csharp  
class B<T, U> {}  
class D<V, W> : B<int, V> {}  
```  
  
```vb  
Class B(Of T, U)  
End Class  
Class D(Of V, W)  
    Inherits B(Of Integer, V)  
End Class  
```  
  
```cpp  
generic<typename T, typename U> ref class B {};  
generic<typename V, typename W> ref class D : B<int, V> {};  
```  
  
 Edinirseniz, bir <xref:System.Type> nesnesini temsil eden `D<V, W>` ve <xref:System.Type.BaseType%2A> sonuç türünü temel almak için özellik `type B<int, V>` açık, ancak bir genel tür tanımı değil.  
  
### <a name="source-of-a-generic-parameter"></a>Genel parametre kaynağı  
 Genel tür parametresi, İncelemekte olduğunuz türü, kapsayan türün veya genel yöntem gelebilir. Genel tür parametre kaynağı aşağıdaki şekilde belirleyebilirsiniz:  
  
- İlk olarak, <xref:System.Type.DeclaringMethod%2A> tür parametresi, genel bir yöntemi gelen olup olmadığını belirlemek için özellik. Özellik değeri null başvuru değilse (`Nothing` Visual Basic'te), kaynağın genel bir yöntem ise.  
  
- Kaynağı bir genel yöntem değil kullanırsanız <xref:System.Type.DeclaringType%2A> genel tür genel tür parametresi belirlemek için özellik ait.  
  
 Tür parametresi, genel bir yönteme ait değilse <xref:System.Type.DeclaringType%2A> özelliği ilgisizdir genel yöntem bildirilen tür döndürür.  
  
### <a name="position-of-a-generic-parameter"></a>Genel parametre konumu  
 Nadir durumlarda, tür parametresi türü parametre listesini bildirmek sınıfıyla konumunu belirlemek gereklidir. Örneğin, sahip olduğunuz varsayalım. bir <xref:System.Type> nesnesini temsil eden `B<int, V>` önceki örnekten türü. <xref:System.Type.GetGenericArguments%2A> Yöntemi listesini tür bağımsız değişkenlerini ve incelediğinizde, size `V` kullanabileceğiniz <xref:System.Type.DeclaringMethod%2A> ve <xref:System.Type.DeclaringType%2A> nereden geldiğini bulmak için özellikleri. Ardından <xref:System.Type.GenericParameterPosition%2A> özelliği burada tanımlanan tür parametresi listesi içindeki konumu belirlemek için. Bu örnekte, `V` 0 (sıfır) burada tanımlanan tür parametresi listesi konumundadır.  
  
### <a name="base-type-and-interface-constraints"></a>Temel türü ve arabirim kısıtlamaları  
 Kullanım <xref:System.Type.GetGenericParameterConstraints%2A> temel türü bir tür parametresi kısıtlaması ve arabirimi kısıtlamaları elde etmek için yöntemi. Dizinin öğeleri sırası önemli değildir. Bir arabirim türü ise bir arabirim kısıtlaması bir öğeyi temsil eder.  
  
### <a name="generic-parameter-attributes"></a>Genel parametre öznitelikleri  
 <xref:System.Type.GenericParameterAttributes%2A> Özellik alımları bir <xref:System.Reflection.GenericParameterAttributes> varyansını (Kovaryans veya kontravaryans) ve özel bir tür parametresi kısıtlamaları belirten değer.  
  
#### <a name="covariance-and-contravariance"></a>Kovaryans ve Kontravaryans  
 Bir tür parametresi birlikte değişken olduğu veya değişken karşıtı belirlemek için uygulama <xref:System.Reflection.GenericParameterAttributes.VarianceMask?displayProperty=nameWithType> için maske <xref:System.Reflection.GenericParameterAttributes> tarafından döndürülen değer <xref:System.Type.GenericParameterAttributes%2A> özelliği. Sonuç ise <xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>, tür parametresi sabit. Bkz: [Kovaryans ve kontravaryans](../../../docs/standard/generics/covariance-and-contravariance.md).  
  
#### <a name="special-constraints"></a>Özel kısıtlamalar  
 Özel bir tür parametresi kısıtlamaları belirlemek için uygulama <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=nameWithType> için maske <xref:System.Reflection.GenericParameterAttributes> tarafından döndürülen değer <xref:System.Type.GenericParameterAttributes%2A> özelliği. Sonuç ise <xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>, hiçbir özel sınırlamalar vardır. Bir başvuru türü, NULL olmayan bir değer türü olması ve varsayılan bir oluşturucuya sahip olması için bir tür parametresi kısıtlı olabilir.  
  
 [Başa dön](#top)  
  
<a name="invariants"></a>   
## <a name="invariants"></a>Okuduğunuzda  
 Yansıma genel türler için genel koşulları ilişkin sabit koşulların tablo için bkz: <xref:System.Type.IsGenericType%2A?displayProperty=nameWithType>. Bkz: Genel metotlar için ilgili ek koşullar için <xref:System.Reflection.MethodBase.IsGenericMethod%2A?displayProperty=nameWithType>.  
  
 [Başa dön](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Nasıl yapılır: İnceleme ve yansıma ile genel türleri örnek oluşturma](../../../docs/framework/reflection-and-codedom/how-to-examine-and-instantiate-generic-types-with-reflection.md)|Özellikleri ve yöntemleri kullanmayı gösterir <xref:System.Type> ve <xref:System.Reflection.MethodInfo> genel türleri İnceleme.|  
|[Genel Türler](../../../docs/standard/generics/index.md)|Genel türler özelliğini ve .NET Framework içinde nasıl desteklendiği açıklanmaktadır.|  
|[Nasıl yapılır: Yansıma ile genel tür tanımlama yayma](../../../docs/framework/reflection-and-codedom/how-to-define-a-generic-type-with-reflection-emit.md)|Yansıma kullanmayı gösterir yayma dinamik derlemelerde genel türler oluşturmak için.|  
|[Tür Bilgilerini Görüntüleme](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)|Açıklar <xref:System.Type> sınıfı ve nasıl kullanılacağını örneklendiren kod örnekleri sağlar <xref:System.Type> Oluşturucular, yöntemler, alanlar, özellikler ve olaylar hakkında bilgi almak için çeşitli yansıma sınıfları ile.|

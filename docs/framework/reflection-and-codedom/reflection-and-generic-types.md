---
title: "Yansıma ve Genel Türler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 99d8da622b23a98b8a48ad6fcdb82c270d24ed22
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="reflection-and-generic-types"></a>Yansıma ve Genel Türler
<a name="top"></a>Yansıma point of görünümünü genel bir tür bir sıradan türü arasındaki fark (genel tür tanımında ise) genel bir tür ile türü parametreleri kümesini ilişkili olduğunu olan veya tür bağımsız değişkenleri (yapılandırılmış bir tür ise). Genel yöntem aynı şekilde bir sıradan yönteminden farklıdır.  
  
 Genel türler ve yöntemleri yansıma nasıl işlediğini anlamak için iki anahtar vardır:  
  
-   Genel tür tanımları ve genel yöntem tanımlarını tür parametrelerini örneği tarafından temsil edilen <xref:System.Type> sınıfı.  
  
    > [!NOTE]
    >  Birçok özellikleri ve yöntemleri <xref:System.Type> farklı davranışa sahip olduğunda bir <xref:System.Type> nesnesini temsil eden bir genel tür parametresi. Bu farklılıklar, özellik ve yöntem konularında belgelenmiştir. Örneğin, <xref:System.Type.IsAutoClass%2A> ve <xref:System.Type.DeclaringType%2A>. Ayrıca, bazı yalnızca olduğunda geçerlidir üyeleridir bir <xref:System.Type> nesnesini temsil eden bir genel tür parametresi. Örneğin, <xref:System.Type.GetGenericTypeDefinition%2A>.  
  
-   Bir örneği varsa <xref:System.Type> tür parametreleri (için genel tür tanımları) veya tür bağımsız değişkenleri (oluşturulan türler) temsil eden türleri dizisi içerir sonra genel bir tür temsil eder. Aynı örneği geçerlidir <xref:System.Reflection.MethodInfo> genel yöntem temsil eden sınıf.  
  
 Yansıma yöntemlerini sağlar <xref:System.Type> ve <xref:System.Reflection.MethodInfo> olanak tanıyacak şekilde tür parametreleri dizisi erişmek ve örneği olup olmadığını belirlemek için <xref:System.Type> bir tür parametresi veya gerçek bir türü temsil eder.  
  
 Örneğin bkz: Burada bahsedilen yöntemler gösteren kodu [nasıl yapılır: inceleyin ve Instantiate genel türleri yansıma ile](../../../docs/framework/reflection-and-codedom/how-to-examine-and-instantiate-generic-types-with-reflection.md).  
  
 Aşağıdaki tartışma türü parametreler ve bağımsız değişkenler arasındaki farkı gibi genel türler terminolojisi aşina ve açık veya kapalı oluşturulan türler varsayar. Daha fazla bilgi için bkz: [genel türler](../../../docs/standard/generics/index.md).  
  
 Bu genel bakışta, aşağıdaki bölümlerden oluşur:  
  
-   [Bu genel türü veya yöntemi mi?](#is_this_a_generic_type_or_method)  
  
-   [Kapalı genel türleri oluşturma](#generating_closed_generic_types)  
  
-   [Tür bağımsız değişkenleri ve tür parametreleri İnceleme](#examining_type_arguments)  
  
-   [İnvariants](#invariants)  
  
-   [İlgili Konular](#related_topics)  
  
<a name="is_this_a_generic_type_or_method"></a>   
## <a name="is-this-a-generic-type-or-method"></a>Bu genel türü veya yöntemi mi?  
 Bir örneği tarafından temsil edilen bilinmeyen bir türe incelemek için yansıma kullandığınızda <xref:System.Type>, kullanın <xref:System.Type.IsGenericType%2A> bilinmeyen tür genel olup olmadığını belirlemek için özellik. Döndürdüğü `true` tür genel ise. Benzer şekilde, bir örneği tarafından temsil edilen bir bilinmeyen yöntem incelediğinizde <xref:System.Reflection.MethodInfo> sınıfı, kullanın <xref:System.Reflection.MethodInfo.IsGenericMethod%2A> yöntemi genel olup olmadığını belirlemek için özellik.  
  
### <a name="is-this-a-generic-type-or-method-definition"></a>Bu, bir genel tür veya yöntem tanımını mi?  
 Kullanmak <xref:System.Type.IsGenericTypeDefinition%2A> belirlemek için özellik isteyip bir <xref:System.Type> nesnesini temsil eden bir genel tür tanımı ve kullanımı <xref:System.Reflection.MethodInfo.IsGenericMethodDefinition%2A> belirlemek amacıyla yöntemi olup olmadığını bir <xref:System.Reflection.MethodInfo> genel yöntem tanımını temsil eder.  
  
 Genel tür ve yöntemi tanımları instantiable türleri oluşturulduğu şablonlarıdır. Genel türleri .NET Framework Sınıf Kitaplığı'nda gibi <xref:System.Collections.Generic.Dictionary%602>, genel tür tanımlar.  
  
### <a name="is-the-type-or-method-open-or-closed"></a>Türü veya yöntemi açık veya kapalı?  
 İnstantiable türleri tüm kapsayan türlerinin tüm tür parametreleri de dahil olmak üzere tüm türü parametreleri için değiştirilen durumunda bir genel türü veya yöntemi kapalı. Kapalıysa, yalnızca genel bir tür örneği oluşturabilirsiniz. <xref:System.Type.ContainsGenericParameters%2A?displayProperty=nameWithType> Özelliği döndürür `true` türü açıksa. Yöntemleri için <xref:System.Reflection.MethodInfo.ContainsGenericParameters%2A?displayProperty=nameWithType> yöntemi aynı işlevi gerçekleştirir.  
  
 [Başa dön](#top)  
  
<a name="generating_closed_generic_types"></a>   
## <a name="generating-closed-generic-types"></a>Kapalı genel türleri oluşturma  
 Genel tür ya da yöntem tanımını olduktan sonra kullanmak <xref:System.Type.MakeGenericType%2A> kapalı genel bir tür oluşturmak için yöntemi veya <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A> yöntemi oluşturmak için bir <xref:System.Reflection.MethodInfo> kapalı bir genel yöntem için.  
  
### <a name="getting-the-generic-type-or-method-definition"></a>Genel tür veya yöntem tanımını alma  
 Bir açık genel tür ya da bir genel tür veya yöntem tanımını yöntemi varsa, örnekleri oluşturulamıyor ve eksik tür parametrelerini sağlayamazsınız. Genel bir tür ya da yöntem tanımı olması gerekir. Kullanım <xref:System.Type.GetGenericTypeDefinition%2A> genel tür tanımı elde etmek için yöntemi veya <xref:System.Reflection.MethodInfo.GetGenericMethodDefinition%2A> genel yöntem tanımını elde etmek için yöntemi.  
  
 Örneğin, bir <xref:System.Type> nesnesini temsil eden `Dictionary<int, string>` (`Dictionary(Of Integer, String)` Visual Basic'te) ve türü oluşturmak istediğiniz `Dictionary<string, MyClass>`, kullanabileceğiniz <xref:System.Type.GetGenericTypeDefinition%2A> almak için yöntemi bir <xref:System.Type> temsil eden `Dictionary<TKey, TValue>` ve ardından <xref:System.Type.MakeGenericType%2A> yöntemini üretmeye bir <xref:System.Type> temsil eden `Dictionary<int, MyClass>`.  
  
 Genel bir tür olmayan açık genel tür örneği için "Tür parametresi veya tür bağımsız değişkeni" bölümüne bakın.  
  
 [Başa dön](#top)  
  
<a name="examining_type_arguments"></a>   
## <a name="examining-type-arguments-and-type-parameters"></a>Tür bağımsız değişkenleri ve tür parametreleri İnceleme  
 Kullanmak <xref:System.Type.GetGenericArguments%2A?displayProperty=nameWithType> bir dizi elde etmek için yöntemi <xref:System.Type> tür parametreleri veya genel bir tür, tür bağımsız değişkenleri temsil eder ve kullanan nesneleri <xref:System.Reflection.MethodInfo.GetGenericArguments%2A?displayProperty=nameWithType> genel yöntem aynı gerçekleştirmek için yöntem.  
  
 Öğrendikten sonra bir <xref:System.Type> nesnesini temsil eden bir tür parametresi, yansıma birçok ek sorusu vardır. Türü parametrenin kaynağı, konumunu ve kendi kısıtlamaları belirleyebilirsiniz.  
  
### <a name="type-parameter-or-type-argument"></a>Tür parametresi veya tür bağımsız değişkeni  
 Dizinin belirli bir öğesine bir tür parametresi veya tür bağımsız değişkeni olup olmadığını belirlemek için <xref:System.Type.IsGenericParameter%2A> özelliği. <xref:System.Type.IsGenericParameter%2A> Özelliği `true` öğesi bir tür parametresi ise.  
  
 Genel tür tanımında olmadan genel bir tür açık olabilir, bu durumda, tür bağımsız değişkenleri ve tür parametreleri bir karışımını sahiptir. Örneğin, aşağıdaki kodda sınıf `D` ilk tür parametresi değiştirerek tarafından oluşturulan bir türü türetilen `D` ikinci tür parametresi için `B`.  
  
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
  
 Elde varsa bir <xref:System.Type> nesnesini temsil eden `D<V, W>` ve <xref:System.Type.BaseType%2A> elde edilen türünü temel almak için özellik `type B<int, V>` açık, ancak genel tür tanımı değil.  
  
### <a name="source-of-a-generic-parameter"></a>Genel bir parametrenin kaynağı  
 Genel tür parametresi, İncelemekte olduğunuz türü, kendilerini kapsayan türle veya genel yöntem gelebilir. Genel tür parametresi kaynak gibi belirleyebilirsiniz:  
  
-   İlk olarak, kullanın <xref:System.Type.DeclaringMethod%2A> tür parametresi bir genel yöntemden gelen olup olmadığını belirlemek için özellik. Özellik değeri null bir başvuru değilse (`Nothing` Visual Basic'te), sonra kaynak genel bir yöntemdir.  
  
-   Kaynak genel yöntem değil kullanırsanız <xref:System.Type.DeclaringType%2A> genel tür genel tür parametresi belirlemek için özellik ait.  
  
 Tür parametresi genel bir yönteme aitse <xref:System.Type.DeclaringType%2A> özelliği ilgisiz genel yöntemini bildirdi türü döndürür.  
  
### <a name="position-of-a-generic-parameter"></a>Genel bir parametreye konumu  
 Nadir durumlarda, kendi bildiren sınıfı türü parametre listesi bir tür parametresi konumunu belirlemek gereklidir. Örneğin, sahip olduğunuz varsayalım bir <xref:System.Type> nesnesini temsil eden `B<int, V>` önceki örnekten türü. <xref:System.Type.GetGenericArguments%2A> Yöntemi, tür bağımsız değişkenleri ve, incelediğinizde listesini verir `V` kullanabileceğiniz <xref:System.Type.DeclaringMethod%2A> ve <xref:System.Type.DeclaringType%2A> nerede alanından gelir bulmak için özellikler. Daha sonra kullanabilirsiniz <xref:System.Type.GenericParameterPosition%2A> türü parametre listesine içindeki onu tanımlandığı konumunu belirlemek için özellik. Bu örnekte, `V` 0 (sıfır), tanımlandığı türü parametre listesinde konumundadır.  
  
### <a name="base-type-and-interface-constraints"></a>Temel türü ve arabirim kısıtlamaları  
 Kullanım <xref:System.Type.GetGenericParameterConstraints%2A> temel türü bir tür parametresi kısıtlaması ve arabirim kısıtlamaları elde etmek için yöntemi. Dizideki öğeler sırası önemli değildir. Bir arabirim türü ise bir arabirim kısıtlaması bir öğeyi temsil eder.  
  
### <a name="generic-parameter-attributes"></a>Genel parametre öznitelikleri  
 <xref:System.Type.GenericParameterAttributes%2A> Özelliği alır bir <xref:System.Reflection.GenericParameterAttributes> varyansı (Kovaryans veya değişken karşıtı) ve özel bir tür parametresi kısıtlamaları belirten değer.  
  
#### <a name="covariance-and-contravariance"></a>Kovaryans ve Kontravaryans  
 Olup bir tür parametresi birlikte değişkendir veya karşıtı belirlemek için uygulama <xref:System.Reflection.GenericParameterAttributes.VarianceMask?displayProperty=nameWithType> için maske <xref:System.Reflection.GenericParameterAttributes> tarafından döndürülen değer <xref:System.Type.GenericParameterAttributes%2A> özelliği. Sonuç ise <xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>, tür parametresi değişmez. Bkz: [Kovaryans ve kontravaryans](../../../docs/standard/generics/covariance-and-contravariance.md).  
  
#### <a name="special-constraints"></a>Özel kısıtlamalar  
 Özel bir tür parametresi kısıtlamaları belirlemek için uygulama <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=nameWithType> için maske <xref:System.Reflection.GenericParameterAttributes> tarafından döndürülen değer <xref:System.Type.GenericParameterAttributes%2A> özelliği. Sonuç ise <xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>, hiçbir özel sınırlamalar vardır. Tür parametresi, başvuru türünde bir null değer türü olabilir ve varsayılan bir oluşturucuya sahip olmasını kısıtlanabilir.  
  
 [Başa dön](#top)  
  
<a name="invariants"></a>   
## <a name="invariants"></a>İnvariants  
 Yansıma genel türleri için genel koşulları değişmez koşullarını tablo için bkz: <xref:System.Type.IsGenericType%2A?displayProperty=nameWithType>. Genel yöntemler için ilgili ek koşullar için bkz: <xref:System.Reflection.MethodInfo.IsGenericMethod%2A?displayProperty=nameWithType>.  
  
 [Başa dön](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Nasıl yapılır: inceleyin ve yansıma ile genel türleri örneği](../../../docs/framework/reflection-and-codedom/how-to-examine-and-instantiate-generic-types-with-reflection.md)|Özellikleri ve yöntemleri kullanmayı gösterir <xref:System.Type> ve <xref:System.Reflection.MethodInfo> genel türler incelemek için.|  
|[Genel türler](../../../docs/standard/generics/index.md)|Genel türler özellik ve .NET Framework nasıl desteklediği açıklanır.|  
|[Nasıl yapılır: yansıma ile genel tür tanımlama yayma](../../../docs/framework/reflection-and-codedom/how-to-define-a-generic-type-with-reflection-emit.md)|Yansıma kullanmayı gösterir dinamik derlemelerde genel türleri oluşturmak için yayma.|  
|[Tür bilgilerini görüntüleme](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)|Açıklar <xref:System.Type> sınıfı ve nasıl kullanılacağını gösteren kod örnekleri sağlar <xref:System.Type> Oluşturucular, yöntemleri, alanları, özellikleri ve olayları hakkında bilgi edinmek için çeşitli yansıma sınıflarla.|

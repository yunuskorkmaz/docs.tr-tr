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
ms.openlocfilehash: ce40a54e82e95f41247db525110c510e3d83031e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045924"
---
# <a name="reflection-and-generic-types"></a>Yansıma ve Genel Türler
<a name="top"></a>Yansıma görünüm noktasından, genel bir tür ve sıradan bir tür arasındaki fark, genel bir türün bir tür parametreleri kümesiyle (genel tür tanımı ise) veya tür bağımsız değişkenlerine (oluşturulmuş bir tür ise) ilişkilendirilme türüdür. Genel bir yöntem aynı şekilde sıradan bir yöntemden farklıdır.  
  
 Yansımanın genel türleri ve yöntemleri nasıl işlediğini anlamak için iki anahtar vardır:  
  
- Genel tür tanımlarının ve genel yöntem tanımlarının tür parametreleri, <xref:System.Type> sınıfının örnekleri tarafından temsil edilir.  
  
    > [!NOTE]
    > <xref:System.Type> Bir<xref:System.Type> nesne genel bir tür parametresini temsil ettiğinde birçok özellik ve yönteminin farklı davranışları vardır. Bu farklılıklar, özellik ve Yöntem konularında belgelenmiştir. Örneğin, bkz <xref:System.Type.IsAutoClass%2A> . ve <xref:System.Type.DeclaringType%2A>. Ayrıca, bazı üyeler yalnızca bir <xref:System.Type> nesne genel tür parametresini temsil ettiğinde geçerlidir. Örneğin, bkz <xref:System.Type.GetGenericTypeDefinition%2A>.  
  
- Bir örneği <xref:System.Type> bir genel türü temsil ediyorsa, tür parametrelerini (genel tür tanımları için) veya tür bağımsız değişkenlerini (oluşturulmuş türler için) temsil eden bir tür dizisi içerir. Aynı, bir genel yöntemi temsil eden <xref:System.Reflection.MethodInfo> sınıfının bir örneğinin aynısıdır.  
  
 Yansıma, ve türü <xref:System.Type> parametre <xref:System.Reflection.MethodInfo> dizisine erişmenize izin veren ve bir örneğinin bir tür parametresini mi yoksa gerçek bir türü mi <xref:System.Type> temsil ettiğini tespit eden ve ' nin yöntemlerini sağlar.  
  
 Örneğin, burada ele alınan yöntemleri gösteren kod için bkz [. nasıl yapılır: Yansıma](how-to-examine-and-instantiate-generic-types-with-reflection.md)ile genel türleri Inceleyin ve örnek oluşturun.  
  
 Aşağıdaki tartışmada, tür parametreleri ve bağımsız değişkenler ile açık veya kapalı oluşturulmuş türler arasındaki fark gibi genel türlerde terminoloji hakkında bilgi sahibi olduğu varsayılır. Daha fazla bilgi için bkz. [Genel türler](../../standard/generics/index.md).  
  
 Bu genel bakış aşağıdaki bölümlerden oluşur:  
  
- [Bu genel bir tür veya yöntem mi?](#is_this_a_generic_type_or_method)  
  
- [Kapalı genel türler üretiliyor](#generating_closed_generic_types)  
  
- [Tür bağımsız değişkenleri ve tür parametreleri inceleniyor](#examining_type_arguments)  
  
- [Invaryantlar](#invariants)  
  
- [İlgili konular](#related_topics)  
  
<a name="is_this_a_generic_type_or_method"></a>   
## <a name="is-this-a-generic-type-or-method"></a>Bu genel bir tür veya yöntem mi?  
 Bir örneği <xref:System.Type>tarafından temsil edilen bilinmeyen bir türü incelemek için yansıma kullandığınızda, bilinmeyen türün genel olup olmadığını <xref:System.Type.IsGenericType%2A> anlamak için özelliğini kullanın. Türün genel `true` olup olmadığını döndürür. Benzer şekilde, <xref:System.Reflection.MethodInfo> sınıfının bir örneğiyle temsil edilen bilinmeyen bir yöntemi incelediğinizde, yöntemin genel olup olmadığını anlamak için <xref:System.Reflection.MethodBase.IsGenericMethod%2A> özelliğini kullanın.  
  
### <a name="is-this-a-generic-type-or-method-definition"></a>Bu genel bir tür veya yöntem tanımıdır mi?  
 Bir nesnenin genel bir tür <xref:System.Reflection.MethodBase.IsGenericMethodDefinition%2A> tanımını temsil edip etmediğini anlamak için <xref:System.Reflection.MethodInfo> özelliğinikullanınvebirgenelyöntemtanımınıtemsiledipetmediğinianlamakiçinyönteminikullanın.<xref:System.Type.IsGenericTypeDefinition%2A> <xref:System.Type>  
  
 Genel tür ve yöntem tanımları, instantiable türlerin oluşturulduğu şablonlardır. .NET Framework sınıf kitaplığındaki <xref:System.Collections.Generic.Dictionary%602>genel türler genel tür tanımlardır.  
  
### <a name="is-the-type-or-method-open-or-closed"></a>Tür veya yöntem açık veya kapalı mı?  
 Tüm kapsayan türlerin tür parametreleri de dahil olmak üzere, instantiable türleri tüm tür parametreleri için kullanılıyorsa, genel tür veya yöntem kapalıdır. Yalnızca kapalıysa bir genel türün örneğini oluşturabilirsiniz. Bir tür açıksa `true` , özelliğidöndürür.<xref:System.Type.ContainsGenericParameters%2A?displayProperty=nameWithType> Yöntemler <xref:System.Reflection.MethodBase.ContainsGenericParameters%2A?displayProperty=nameWithType> için yöntem aynı işlevi gerçekleştirir.  
  
 [Başa dön](#top)  
  
<a name="generating_closed_generic_types"></a>   
## <a name="generating-closed-generic-types"></a>Kapalı genel türler üretiliyor  
 Genel bir tür veya yöntem tanımınız olduktan sonra, kapalı bir <xref:System.Type.MakeGenericType%2A> genel tür oluşturmak için yöntemini <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A> veya kapalı bir genel yöntem <xref:System.Reflection.MethodInfo> için oluşturmak için yöntemini kullanın.  
  
### <a name="getting-the-generic-type-or-method-definition"></a>Genel tür veya yöntem tanımını alma  
 Genel tür veya yöntem tanımı olmayan açık bir genel tür veya yönteminiz varsa, bunun örneklerini oluşturamazsınız ve eksik olan tür parametrelerini sağlayamazsınız. Genel bir tür veya yöntem tanımınız olmalıdır. Genel tür tanımını <xref:System.Reflection.MethodInfo.GetGenericMethodDefinition%2A> veya genel yöntem tanımını elde etmek için yöntemini almak için yönteminikullanın.<xref:System.Type.GetGenericTypeDefinition%2A>  
  
 Örneğin <xref:System.Type> , öğesini temsil eden `Dictionary<int, string>` bir nesneniz varsa (`Dictionary(Of Integer, String)` Visual Basic) ve `Dictionary<string, MyClass>`türü <xref:System.Type.GetGenericTypeDefinition%2A> oluşturmak istiyorsanız, bir <xref:System.Type> temsil `Dictionary<TKey, TValue>` ve sonra bir <xref:System.Type.MakeGenericType%2A> <xref:System.Type> temsil oluşturmakiçinyönteminikullanın.`Dictionary<int, MyClass>`  
  
 Genel tür olmayan bir açık genel tür örneği için, bu konunun devamındaki "tür parametresi veya tür bağımsız değişkeni" başlığına bakın.  
  
 [Başa dön](#top)  
  
<a name="examining_type_arguments"></a>   
## <a name="examining-type-arguments-and-type-parameters"></a>Tür bağımsız değişkenleri ve tür parametreleri inceleniyor  
 Bir genel <xref:System.Type>türüntür parametrelerini veya tür bağımsız değişkenlerini temsil eden bir nesne dizisi elde etmek için <xref:System.Type.GetGenericArguments%2A?displayProperty=nameWithType> yöntemini kullanın ve bir genel yöntem için aynı yapmak için yöntemini kullanın. <xref:System.Reflection.MethodInfo.GetGenericArguments%2A?displayProperty=nameWithType>  
  
 Bir <xref:System.Type> nesnenin bir tür parametresini temsil ettiğini öğrendikten sonra, birçok ek soru yansıması yanıt verebilir. Tür parametresinin kaynağını, konumunu ve kısıtlamalarını tespit edebilirsiniz.  
  
### <a name="type-parameter-or-type-argument"></a>Tür parametresi veya tür bağımsız değişkeni  
 Dizinin belirli bir öğesinin bir tür parametresi mi yoksa bir tür bağımsız değişkeni mi olduğunu anlamak için <xref:System.Type.IsGenericParameter%2A> özelliğini kullanın. <xref:System.Type.IsGenericParameter%2A> Özelliği,`true` öğe bir tür parametresidir.  
  
 Genel bir tür, genel tür tanımı olmadan açılabilir, bu durumda tür bağımsız değişkenleri ve tür parametrelerinin karışımı vardır. Örneğin, aşağıdaki kodda, sınıfının `D` ikinci tür parametresi `D` `B`için ilk tür parametresi yerine oluşturulan bir türden türetilir.  
  
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
  
 <xref:System.Type> Temsil eden `D<V, W>` bir nesne elde ediyorsanız ve temel türünü <xref:System.Type.BaseType%2A> elde etmek için özelliğini kullanırsanız, sonuç `type B<int, V>` açık olur ancak genel bir tür tanımı değildir.  
  
### <a name="source-of-a-generic-parameter"></a>Genel parametre kaynağı  
 Genel bir tür parametresi, incelentiğiniz türden, kapsayan türden veya genel bir yöntemden gelebilir. Genel tür parametresinin kaynağını şu şekilde belirleyebilirsiniz:  
  
- İlk olarak, Type <xref:System.Type.DeclaringMethod%2A> parametresinin genel bir yöntemden geldiğini öğrenmek için özelliğini kullanın. Özellik değeri null bir başvuru değilse (`Nothing` Visual Basic), kaynak genel bir yöntemdir.  
  
- Kaynak genel bir yöntem değilse, genel tür parametresinin ait olduğu <xref:System.Type.DeclaringType%2A> genel türü öğrenmek için özelliğini kullanın.  
  
 Tür parametresi genel bir yönteme aitse, <xref:System.Type.DeclaringType%2A> özelliği genel yöntemini belirten, ilgisiz olan türü döndürür.  
  
### <a name="position-of-a-generic-parameter"></a>Genel parametre konumu  
 Nadir durumlarda, bir tür parametresinin konumunu bildirme sınıfının tür parametresi listesinde belirlenmesi gerekir. Örneğin, yukarıdaki örnekteki <xref:System.Type> `B<int, V>` türü temsil eden bir nesneniz olduğunu varsayalım. Yöntemi size bağımsız değişkenlerin bir listesini verir ve ne zaman `V` geldiğini saptamak için <xref:System.Type.DeclaringMethod%2A> ve <xref:System.Type.DeclaringType%2A> özelliklerini kullanabilirsiniz. <xref:System.Type.GetGenericArguments%2A> Daha sonra özelliği, <xref:System.Type.GenericParameterPosition%2A> tanımlı olduğu tür parametresi listesindeki konumunu tespit etmek için kullanabilirsiniz. Bu örnekte, `V` tanımlanan tür parametresi listesinde 0 (sıfır) konumunda olur.  
  
### <a name="base-type-and-interface-constraints"></a>Temel tür ve arabirim kısıtlamaları  
 Bir tür parametresinin temel tür kısıtlamasını ve arabirim kısıtlamalarını almak için yönteminikullanın.<xref:System.Type.GetGenericParameterConstraints%2A> Dizi öğelerinin sırası önemli değildir. Bir öğesi arabirim türü ise arabirim kısıtlamasını temsil eder.  
  
### <a name="generic-parameter-attributes"></a>Genel parametre öznitelikleri  
 Özelliği, varyansı ( <xref:System.Reflection.GenericParameterAttributes> Kovaryans veya değişken varyans) ve bir tür parametresinin özel kısıtlamalarını gösteren bir değer alır. <xref:System.Type.GenericParameterAttributes%2A>  
  
#### <a name="covariance-and-contravariance"></a>Kovaryans ve Kontravaryans  
 Bir tür parametresinin birlikte değişken veya değişken karşıtı olduğunu anlamak için, <xref:System.Reflection.GenericParameterAttributes.VarianceMask?displayProperty=nameWithType> maskesini <xref:System.Reflection.GenericParameterAttributes> <xref:System.Type.GenericParameterAttributes%2A> özelliği tarafından döndürülen değere uygulayın. Sonuç ise <xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>tür parametresi sabit olur. Bkz. [Kovaryans ve değişken varyansı](../../standard/generics/covariance-and-contravariance.md).  
  
#### <a name="special-constraints"></a>Özel kısıtlamalar  
 Bir tür parametresinin özel kısıtlamalarını öğrenmek için, <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=nameWithType> maskesini <xref:System.Reflection.GenericParameterAttributes> <xref:System.Type.GenericParameterAttributes%2A> özelliği tarafından döndürülen değere uygulayın. Sonuç ise <xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>özel bir kısıtlama yoktur. Bir tür parametresi, bir başvuru türü, null yapılamayan bir değer türü ve parametresiz bir oluşturucuya sahip olacak şekilde kısıtlanabilir.  
  
 [Başa dön](#top)  
  
<a name="invariants"></a>   
## <a name="invariants"></a>Invaryantlar  
 Genel türler için yansıma içinde ortak terimler için sabit koşulların bir tablosu için, bkz <xref:System.Type.IsGenericType%2A?displayProperty=nameWithType>. Genel yöntemlerle ilgili ek terimler için bkz <xref:System.Reflection.MethodBase.IsGenericMethod%2A?displayProperty=nameWithType>.  
  
 [Başa dön](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Nasıl yapılır: Yansıma ile genel türleri İnceleme ve örnek oluşturma](how-to-examine-and-instantiate-generic-types-with-reflection.md)|Genel türleri incelemek için <xref:System.Type> ve <xref:System.Reflection.MethodInfo> özelliklerinin ve yöntemlerinin nasıl kullanılacağını gösterir.|  
|[Genel Türler](../../standard/generics/index.md)|Genel türler özelliğini ve .NET Framework nasıl desteklendiğini açıklar.|  
|[Nasıl yapılır: Yansıma Yayma ile genel bir tür tanımlama](how-to-define-a-generic-type-with-reflection-emit.md)|Dinamik derlemelerde genel türler oluşturmak için yansıma yayma 'nın nasıl kullanılacağını gösterir.|  
|[Tür Bilgilerini Görüntüleme](viewing-type-information.md)|Sınıfını açıklar ve oluşturucular, Yöntemler, alanlar, Özellikler ve olaylar <xref:System.Type> hakkında bilgi edinmek için çeşitli yansıma sınıflarıyla birlikte nasıl kullanılacağını gösteren kod örnekleri sağlar. <xref:System.Type>|

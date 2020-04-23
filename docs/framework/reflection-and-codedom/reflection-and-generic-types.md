---
title: Yansıma ve Genel Türler
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
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
ms.openlocfilehash: 4894b5cc64dca431c8d05b638847dd6cb7017bde
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180489"
---
# <a name="reflection-and-generic-types"></a>Yansıma ve Genel Türler
Yansıma görünüm noktasından, genel bir tür ve sıradan bir tür arasındaki fark, genel bir türün bir tür parametreleri kümesiyle (genel tür tanımı ise) veya tür bağımsız değişkenlerine (oluşturulmuş bir tür ise) ilişkilendirilme türüdür. Genel bir yöntem aynı şekilde sıradan bir yöntemden farklıdır.  
  
 Yansımanın genel türleri ve yöntemleri nasıl işlediğini anlamak için iki anahtar vardır:  
  
- Genel tür tanımlarının ve genel yöntem tanımlarının tür parametreleri, <xref:System.Type> sınıfının örnekleri tarafından temsil edilir.  
  
    > [!NOTE]
    > Bir <xref:System.Type> nesne genel bir tür <xref:System.Type> parametresini temsil ettiğinde birçok özellik ve yönteminin farklı davranışları vardır. Bu farklılıklar, özellik ve Yöntem konularında belgelenmiştir. Örneğin, bkz <xref:System.Type.IsAutoClass%2A> . ve <xref:System.Type.DeclaringType%2A>. Ayrıca, bazı üyeler yalnızca bir <xref:System.Type> nesne genel tür parametresini temsil ettiğinde geçerlidir. Örneğin, bkz <xref:System.Type.GetGenericTypeDefinition%2A>..  
  
- Bir örneği bir genel <xref:System.Type> türü temsil ediyorsa, tür parametrelerini (genel tür tanımları için) veya tür bağımsız değişkenlerini (oluşturulmuş türler için) temsil eden bir tür dizisi içerir. Aynı, bir genel yöntemi temsil eden <xref:System.Reflection.MethodInfo> sınıfının bir örneğinin aynısıdır.  
  
 Yansıma, ve türü <xref:System.Type> parametre <xref:System.Reflection.MethodInfo> dizisine erişmenize izin veren ve bir örneğinin bir tür parametresini mi yoksa gerçek bir türü mi <xref:System.Type> temsil ettiğini tespit eden ve ' nin yöntemlerini sağlar.  
  
 Burada ele alınan yöntemleri gösteren kod için bkz. [nasıl yapılır: yansıma Ile genel türleri İnceleme ve örnek oluşturma](how-to-examine-and-instantiate-generic-types-with-reflection.md).  
  
 Aşağıdaki tartışmada, tür parametreleri ve bağımsız değişkenler ile açık veya kapalı oluşturulmuş türler arasındaki fark gibi genel türlerde terminoloji hakkında bilgi sahibi olduğu varsayılır. Daha fazla bilgi için bkz. [Genel türler](../../standard/generics/index.md).  

## <a name="is-this-a-generic-type-or-method"></a>Bu genel bir tür veya yöntem mi?  
 Bir örneği tarafından temsil edilen bilinmeyen bir türü incelemek için yansıma kullandığınızda <xref:System.Type>, bilinmeyen türün genel olup olmadığını <xref:System.Type.IsGenericType%2A> anlamak için özelliğini kullanın. Türün genel `true` olup olmadığını döndürür. Benzer şekilde, <xref:System.Reflection.MethodInfo> sınıfının bir örneğiyle temsil edilen bilinmeyen bir yöntemi incelediğinizde, yöntemin genel olup olmadığını anlamak için <xref:System.Reflection.MethodBase.IsGenericMethod%2A> özelliğini kullanın.  
  
### <a name="is-this-a-generic-type-or-method-definition"></a>Bu genel bir tür veya yöntem tanımıdır mi?  
 Bir <xref:System.Type.IsGenericTypeDefinition%2A> <xref:System.Type> nesnenin genel bir tür tanımını temsil edip etmediğini anlamak için özelliğini kullanın ve bir <xref:System.Reflection.MethodBase.IsGenericMethodDefinition%2A> <xref:System.Reflection.MethodInfo> genel yöntem tanımını temsil edip etmediğini anlamak için yöntemini kullanın.  
  
 Genel tür ve yöntem tanımları, instantiable türlerin oluşturulduğu şablonlardır. .NET Framework sınıf kitaplığındaki <xref:System.Collections.Generic.Dictionary%602>genel türler genel tür tanımlardır.  
  
### <a name="is-the-type-or-method-open-or-closed"></a>Tür veya yöntem açık veya kapalı mı?  
 Tüm kapsayan türlerin tür parametreleri de dahil olmak üzere, instantiable türleri tüm tür parametreleri için kullanılıyorsa, genel tür veya yöntem kapalıdır. Yalnızca kapalıysa bir genel türün örneğini oluşturabilirsiniz. Bir <xref:System.Type.ContainsGenericParameters%2A?displayProperty=nameWithType> tür açıksa `true` , özelliği döndürür. Yöntemler için <xref:System.Reflection.MethodBase.ContainsGenericParameters%2A?displayProperty=nameWithType> Yöntem aynı işlevi gerçekleştirir.

## <a name="generating-closed-generic-types"></a>Kapalı genel türler üretiliyor  
 Genel bir tür veya yöntem tanımınız olduktan sonra, kapalı bir <xref:System.Type.MakeGenericType%2A> genel tür oluşturmak için yöntemini veya kapalı bir genel <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A> Yöntem <xref:System.Reflection.MethodInfo> için oluşturmak için yöntemini kullanın.  
  
### <a name="getting-the-generic-type-or-method-definition"></a>Genel tür veya yöntem tanımını alma  
 Genel tür veya yöntem tanımı olmayan açık bir genel tür veya yönteminiz varsa, bunun örneklerini oluşturamazsınız ve eksik olan tür parametrelerini sağlayamazsınız. Genel bir tür veya yöntem tanımınız olmalıdır. Genel tür <xref:System.Type.GetGenericTypeDefinition%2A> tanımını veya genel yöntem tanımını elde etmek için <xref:System.Reflection.MethodInfo.GetGenericMethodDefinition%2A> yöntemini almak için yöntemini kullanın.  
  
 Örneğin <xref:System.Type> , öğesini temsil eden `Dictionary<int, string>` bir nesneniz varsa (`Dictionary(Of Integer, String)` Visual Basic) ve türü `Dictionary<string, MyClass>`oluşturmak istiyorsanız, bir temsil almak <xref:System.Type.GetGenericTypeDefinition%2A> <xref:System.Type> için yöntemini kullanabilirsiniz `Dictionary<TKey, TValue>` ve sonra bir <xref:System.Type.MakeGenericType%2A> <xref:System.Type> temsil `Dictionary<int, MyClass>`oluşturmak için yöntemini kullanabilirsiniz.  
  
 Genel tür olmayan bir açık genel tür örneği için, bu konunun devamındaki "tür parametresi veya tür bağımsız değişkeni" başlığına bakın.

## <a name="examining-type-arguments-and-type-parameters"></a>Tür bağımsız değişkenleri ve tür parametreleri inceleniyor  
 Bir genel <xref:System.Type.GetGenericArguments%2A?displayProperty=nameWithType> türün tür parametrelerini veya tür bağımsız <xref:System.Type> değişkenlerini temsil eden bir nesne dizisi elde etmek için yöntemini kullanın ve bir genel yöntem için aynı <xref:System.Reflection.MethodInfo.GetGenericArguments%2A?displayProperty=nameWithType> yapmak için yöntemini kullanın.  
  
 Bir <xref:System.Type> nesnenin bir tür parametresini temsil ettiğini öğrendikten sonra, birçok ek soru yansıması yanıt verebilir. Tür parametresinin kaynağını, konumunu ve kısıtlamalarını tespit edebilirsiniz.  
  
### <a name="type-parameter-or-type-argument"></a>Tür parametresi veya tür bağımsız değişkeni  
 Dizinin belirli bir öğesinin bir tür parametresi mi yoksa bir tür bağımsız değişkeni mi olduğunu anlamak için <xref:System.Type.IsGenericParameter%2A> özelliğini kullanın. <xref:System.Type.IsGenericParameter%2A> Özelliği `true` , öğe bir tür parametresidir.  
  
 Genel bir tür, genel tür tanımı olmadan açılabilir, bu durumda tür bağımsız değişkenleri ve tür parametrelerinin karışımı vardır. Örneğin, aşağıdaki kodda, sınıfının `D` ikinci tür parametresi `D` için ilk tür parametresi yerine oluşturulan bir türden türetilir. `B`  
  
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
 Nadir durumlarda, bir tür parametresinin konumunu bildirme sınıfının tür parametresi listesinde belirlenmesi gerekir. Örneğin, yukarıdaki örnekteki <xref:System.Type> `B<int, V>` türü temsil eden bir nesneniz olduğunu varsayalım. <xref:System.Type.GetGenericArguments%2A> Yöntemi size bağımsız değişkenlerin bir listesini verir ve ne zaman `V` geldiğini saptamak için <xref:System.Type.DeclaringMethod%2A> ve <xref:System.Type.DeclaringType%2A> özelliklerini kullanabilirsiniz. Daha sonra özelliği, <xref:System.Type.GenericParameterPosition%2A> tanımlı olduğu tür parametresi listesindeki konumunu tespit etmek için kullanabilirsiniz. Bu örnekte, `V` tanımlanan tür parametresi listesinde 0 (sıfır) konumunda olur.  
  
### <a name="base-type-and-interface-constraints"></a>Temel tür ve arabirim kısıtlamaları  
 Bir tür <xref:System.Type.GetGenericParameterConstraints%2A> parametresinin temel tür kısıtlamasını ve arabirim kısıtlamalarını almak için yöntemini kullanın. Dizi öğelerinin sırası önemli değildir. Bir öğesi arabirim türü ise arabirim kısıtlamasını temsil eder.  
  
### <a name="generic-parameter-attributes"></a>Genel parametre öznitelikleri  
 <xref:System.Type.GenericParameterAttributes%2A> Özelliği, varyansı ( <xref:System.Reflection.GenericParameterAttributes> Kovaryans veya değişken varyans) ve bir tür parametresinin özel kısıtlamalarını gösteren bir değer alır.  
  
#### <a name="covariance-and-contravariance"></a>Kovaryans ve Kontravaryans  
 Bir tür parametresinin birlikte değişken veya değişken karşıtı olduğunu anlamak için, <xref:System.Reflection.GenericParameterAttributes.VarianceMask?displayProperty=nameWithType> maskesini <xref:System.Reflection.GenericParameterAttributes> <xref:System.Type.GenericParameterAttributes%2A> özelliği tarafından döndürülen değere uygulayın. Sonuç ise <xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>tür parametresi sabit olur. Bkz. [Kovaryans ve değişken varyansı](../../standard/generics/covariance-and-contravariance.md).  
  
#### <a name="special-constraints"></a>Özel kısıtlamalar  
 Bir tür parametresinin özel kısıtlamalarını öğrenmek için, <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=nameWithType> maskesini <xref:System.Reflection.GenericParameterAttributes> <xref:System.Type.GenericParameterAttributes%2A> özelliği tarafından döndürülen değere uygulayın. Sonuç ise <xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>özel bir kısıtlama yoktur. Bir tür parametresi, bir başvuru türü, null yapılamayan bir değer türü ve parametresiz bir oluşturucuya sahip olacak şekilde kısıtlanabilir.

## <a name="invariants"></a>Invaryantlar  
 Genel türler için yansıma içinde ortak terimler için sabit koşulların bir tablosu için, bkz <xref:System.Type.IsGenericType%2A?displayProperty=nameWithType>.. Genel yöntemlerle ilgili ek terimler için bkz <xref:System.Reflection.MethodBase.IsGenericMethod%2A?displayProperty=nameWithType>..  

## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Nasıl yapılır: Yansıma ile Genel Türleri İnceleme ve Örnek Oluşturma](how-to-examine-and-instantiate-generic-types-with-reflection.md)|Genel türleri incelemek için <xref:System.Type> ve <xref:System.Reflection.MethodInfo> özelliklerinin ve yöntemlerinin nasıl kullanılacağını gösterir.|  
|[Genel Türler](../../standard/generics/index.md)|Genel türler özelliğini ve .NET Framework nasıl desteklendiğini açıklar.|  
|[Nasıl yapılır: Yansıma Yayma ile Genel Tür Tanımlama](how-to-define-a-generic-type-with-reflection-emit.md)|Dinamik derlemelerde genel türler oluşturmak için yansıma yayma 'nın nasıl kullanılacağını gösterir.|  
|[Tür Bilgilerini Görüntüleme](viewing-type-information.md)|<xref:System.Type> Sınıfını açıklar ve oluşturucular, Yöntemler, alanlar, Özellikler ve olaylar <xref:System.Type> hakkında bilgi edinmek için çeşitli yansıma sınıflarıyla birlikte nasıl kullanılacağını gösteren kod örnekleri sağlar.|

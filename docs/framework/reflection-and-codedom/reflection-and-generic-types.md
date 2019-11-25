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
ms.openlocfilehash: 0a7d38c8177aa8f2c5f45dcc62a0ae6e5aaca2a7
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975445"
---
# <a name="reflection-and-generic-types"></a>Yansıma ve Genel Türler
Yansıma görünüm noktasından, genel bir tür ve sıradan bir tür arasındaki fark, genel bir türün bir tür parametreleri kümesiyle (genel tür tanımı ise) veya tür bağımsız değişkenlerine (oluşturulmuş bir tür ise) ilişkilendirilme türüdür. Genel bir yöntem aynı şekilde sıradan bir yöntemden farklıdır.  
  
 Yansımanın genel türleri ve yöntemleri nasıl işlediğini anlamak için iki anahtar vardır:  
  
- Genel tür tanımlarının ve genel yöntem tanımlarının tür parametreleri <xref:System.Type> sınıfının örnekleri tarafından temsil edilir.  
  
    > [!NOTE]
    > Bir <xref:System.Type> nesnesi genel bir tür parametresini temsil ettiğinde <xref:System.Type> birçok özellik ve yöntemi farklı davranışa sahiptir. Bu farklılıklar, özellik ve Yöntem konularında belgelenmiştir. Örneğin, bkz. <xref:System.Type.IsAutoClass%2A> ve <xref:System.Type.DeclaringType%2A>. Ayrıca, bazı üyeler yalnızca bir <xref:System.Type> nesnesi genel bir tür parametresini temsil ettiğinde geçerlidir. Örneğin, bkz. <xref:System.Type.GetGenericTypeDefinition%2A>.  
  
- Bir <xref:System.Type> örneği genel bir türü temsil ediyorsa, tür parametrelerini (genel tür tanımları için) veya tür bağımsız değişkenlerini (oluşturulmuş türler için) temsil eden bir tür dizisi içerir. Aynı, bir genel yöntemi temsil eden <xref:System.Reflection.MethodInfo> sınıfının bir örneğinin aynısıdır.  
  
 Yansıma, tür parametrelerinin dizisine erişmenize izin veren <xref:System.Type> ve <xref:System.Reflection.MethodInfo> ve bir <xref:System.Type> örneğinin bir tür parametresini mi yoksa gerçek bir türü mi temsil ettiğini tespit etmek için yöntemler sağlar.  
  
 Burada ele alınan yöntemleri gösteren kod için bkz. [nasıl yapılır: yansıma Ile genel türleri İnceleme ve örnek oluşturma](how-to-examine-and-instantiate-generic-types-with-reflection.md).  
  
 Aşağıdaki tartışmada, tür parametreleri ve bağımsız değişkenler ile açık veya kapalı oluşturulmuş türler arasındaki fark gibi genel türlerde terminoloji hakkında bilgi sahibi olduğu varsayılır. Daha fazla bilgi için bkz. [Genel türler](../../standard/generics/index.md).  

## <a name="is-this-a-generic-type-or-method"></a>Bu genel bir tür veya yöntem mi?  
 Bir <xref:System.Type>örneğiyle temsil edilen bilinmeyen bir türü incelemek için yansıma kullandığınızda, bilinmeyen türün genel olup olmadığını anlamak için <xref:System.Type.IsGenericType%2A> özelliğini kullanın. Tür genel ise `true` döndürür. Benzer şekilde, <xref:System.Reflection.MethodInfo> sınıfının bir örneğiyle temsil edilen bilinmeyen bir yöntemi incelediğinizde, yöntemin genel olup olmadığını anlamak için <xref:System.Reflection.MethodBase.IsGenericMethod%2A> özelliğini kullanın.  
  
### <a name="is-this-a-generic-type-or-method-definition"></a>Bu genel bir tür veya yöntem tanımıdır mi?  
 Bir <xref:System.Type> nesnesinin genel tür tanımını temsil edip etmediğini anlamak için <xref:System.Type.IsGenericTypeDefinition%2A> özelliğini kullanın ve bir <xref:System.Reflection.MethodInfo> genel yöntem tanımını temsil edip etmediğini anlamak için <xref:System.Reflection.MethodBase.IsGenericMethodDefinition%2A> metodunu kullanın.  
  
 Genel tür ve yöntem tanımları, instantiable türlerin oluşturulduğu şablonlardır. .NET Framework sınıf kitaplığındaki <xref:System.Collections.Generic.Dictionary%602>gibi genel türler genel tür tanımlardır.  
  
### <a name="is-the-type-or-method-open-or-closed"></a>Tür veya yöntem açık veya kapalı mı?  
 Tüm kapsayan türlerin tür parametreleri de dahil olmak üzere, instantiable türleri tüm tür parametreleri için kullanılıyorsa, genel tür veya yöntem kapalıdır. Yalnızca kapalıysa bir genel türün örneğini oluşturabilirsiniz. <xref:System.Type.ContainsGenericParameters%2A?displayProperty=nameWithType> özelliği, bir tür açıksa `true` döndürür. Yöntemler için <xref:System.Reflection.MethodBase.ContainsGenericParameters%2A?displayProperty=nameWithType> yöntemi aynı işlevi gerçekleştirir.   

## <a name="generating-closed-generic-types"></a>Kapalı genel türler üretiliyor  
 Genel bir tür veya yöntem tanımınız olduktan sonra, kapalı bir genel yöntem için bir <xref:System.Reflection.MethodInfo> oluşturmak üzere kapalı bir genel tür veya <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A> yöntemi oluşturmak için <xref:System.Type.MakeGenericType%2A> yöntemini kullanın.  
  
### <a name="getting-the-generic-type-or-method-definition"></a>Genel tür veya yöntem tanımını alma  
 Genel tür veya yöntem tanımı olmayan açık bir genel tür veya yönteminiz varsa, bunun örneklerini oluşturamazsınız ve eksik olan tür parametrelerini sağlayamazsınız. Genel bir tür veya yöntem tanımınız olmalıdır. Genel tür tanımını almak için <xref:System.Type.GetGenericTypeDefinition%2A> yöntemini veya genel yöntem tanımını elde etmek için <xref:System.Reflection.MethodInfo.GetGenericMethodDefinition%2A> metodunu kullanın.  
  
 Örneğin, `Dictionary<int, string>` temsil eden bir <xref:System.Type> nesneniz varsa (Visual Basic 'de`Dictionary(Of Integer, String)`) ve türü `Dictionary<string, MyClass>`oluşturmak istiyorsanız <xref:System.Type.GetGenericTypeDefinition%2A> öğesini temsil eden bir <xref:System.Type> almak için `Dictionary<TKey, TValue>` yöntemini kullanarak <xref:System.Type.MakeGenericType%2A> temsil eden bir <xref:System.Type> üretebilirsiniz.  
  
 Genel tür olmayan bir açık genel tür örneği için, bu konunun devamındaki "tür parametresi veya tür bağımsız değişkeni" başlığına bakın.   

## <a name="examining-type-arguments-and-type-parameters"></a>Tür bağımsız değişkenleri ve tür parametreleri inceleniyor  
 Bir genel türün tür parametrelerini veya tür bağımsız değişkenlerini temsil eden <xref:System.Type> nesnelerinin bir dizisini almak için <xref:System.Type.GetGenericArguments%2A?displayProperty=nameWithType> yöntemini kullanın ve bir genel yöntem için aynı yapmak için <xref:System.Reflection.MethodInfo.GetGenericArguments%2A?displayProperty=nameWithType> metodunu kullanın.  
  
 Bir <xref:System.Type> nesnesinin bir tür parametresini temsil ettiğini öğrendikten sonra, yansıma Yanıtlayabildiğiniz pek çok ek soruya sahip olursunuz. Tür parametresinin kaynağını, konumunu ve kısıtlamalarını tespit edebilirsiniz.  
  
### <a name="type-parameter-or-type-argument"></a>Tür parametresi veya tür bağımsız değişkeni  
 Dizinin belirli bir öğesinin bir tür parametresi mi yoksa bir tür bağımsız değişkeni mi olduğunu anlamak için <xref:System.Type.IsGenericParameter%2A> özelliğini kullanın. <xref:System.Type.IsGenericParameter%2A> özelliği, öğe bir tür parametresi ise `true`.  
  
 Genel bir tür, genel tür tanımı olmadan açılabilir, bu durumda tür bağımsız değişkenleri ve tür parametrelerinin karışımı vardır. Örneğin, aşağıdaki kodda, sınıf `D`, `B`ikinci tür parametresi için `D` ilk tür parametresini değiştirerek oluşturulan bir türden türetilir.  
  
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
  
 `D<V, W>` temsil eden bir <xref:System.Type> nesnesi elde ediyorsanız ve temel türünü almak için <xref:System.Type.BaseType%2A> özelliğini kullanırsanız, sonuçta elde edilen `type B<int, V>` açıktır, ancak genel bir tür tanımı değildir.  
  
### <a name="source-of-a-generic-parameter"></a>Genel parametre kaynağı  
 Genel bir tür parametresi, incelentiğiniz türden, kapsayan türden veya genel bir yöntemden gelebilir. Genel tür parametresinin kaynağını şu şekilde belirleyebilirsiniz:  
  
- İlk olarak, tür parametresinin genel bir yöntemden geldiğini öğrenmek için <xref:System.Type.DeclaringMethod%2A> özelliğini kullanın. Özellik değeri null bir başvuru değilse (Visual Basic`Nothing`), kaynak genel bir yöntemdir.  
  
- Kaynak genel bir yöntem değilse, genel tür parametresinin ait olduğu genel türü öğrenmek için <xref:System.Type.DeclaringType%2A> özelliğini kullanın.  
  
 Tür parametresi genel bir yönteme aitse, <xref:System.Type.DeclaringType%2A> özelliği genel yöntemini belirten, ilgisiz olan türü döndürür.  
  
### <a name="position-of-a-generic-parameter"></a>Genel parametre konumu  
 Nadir durumlarda, bir tür parametresinin konumunu bildirme sınıfının tür parametresi listesinde belirlenmesi gerekir. Örneğin, yukarıdaki örnekteki `B<int, V>` türünü temsil eden bir <xref:System.Type> nesneniz olduğunu varsayalım. <xref:System.Type.GetGenericArguments%2A> yöntemi size bağımsız değişkenlerin bir listesini sağlar ve `V` incelediğinizde <xref:System.Type.DeclaringMethod%2A> ve <xref:System.Type.DeclaringType%2A> özelliklerini kullanarak nereden geldiğini bulabilir. Daha sonra <xref:System.Type.GenericParameterPosition%2A> özelliğini kullanarak, tanımlı olduğu tür parametresi listesindeki konumunu belirleyebilirsiniz. Bu örnekte, `V` tanımlandığı tür parametresi listesinde 0 (sıfır) konumunda olur.  
  
### <a name="base-type-and-interface-constraints"></a>Temel tür ve arabirim kısıtlamaları  
 Bir tür parametresinin temel tür kısıtlamasını ve arabirim kısıtlamalarını almak için <xref:System.Type.GetGenericParameterConstraints%2A> yöntemini kullanın. Dizi öğelerinin sırası önemli değildir. Bir öğesi arabirim türü ise arabirim kısıtlamasını temsil eder.  
  
### <a name="generic-parameter-attributes"></a>Genel parametre öznitelikleri  
 <xref:System.Type.GenericParameterAttributes%2A> özelliği, varyansı (Kovaryans veya değişken varyans) ve bir tür parametresinin özel kısıtlamalarını gösteren bir <xref:System.Reflection.GenericParameterAttributes> değeri alır.  
  
#### <a name="covariance-and-contravariance"></a>Kovaryans ve Kontravaryans  
 Bir tür parametresinin birlikte değişken veya değişken karşıtı olup olmadığını öğrenmek için, <xref:System.Reflection.GenericParameterAttributes.VarianceMask?displayProperty=nameWithType> maskesini <xref:System.Type.GenericParameterAttributes%2A> özelliği tarafından döndürülen <xref:System.Reflection.GenericParameterAttributes> değerine uygulayın. Sonuç <xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>, tür parametresi sabit olur. Bkz. [Kovaryans ve değişken varyansı](../../standard/generics/covariance-and-contravariance.md).  
  
#### <a name="special-constraints"></a>Özel kısıtlamalar  
 Bir tür parametresinin özel kısıtlamalarını öğrenmek için, <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=nameWithType> maskesini <xref:System.Type.GenericParameterAttributes%2A> özelliği tarafından döndürülen <xref:System.Reflection.GenericParameterAttributes> değerine uygulayın. Sonuç <xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>, özel kısıtlama yoktur. Bir tür parametresi, bir başvuru türü, null yapılamayan bir değer türü ve parametresiz bir oluşturucuya sahip olacak şekilde kısıtlanabilir.    

## <a name="invariants"></a>Invaryantlar  
 Genel türler için yansımayla ilgili yaygın koşullara yönelik sabit koşulların bir tablosu için bkz. <xref:System.Type.IsGenericType%2A?displayProperty=nameWithType>. Genel yöntemlerle ilgili ek terimler için bkz. <xref:System.Reflection.MethodBase.IsGenericMethod%2A?displayProperty=nameWithType>.  

## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Nasıl yapılır: Yansıma ile Genel Türleri İnceleme ve Örnek Oluşturma](how-to-examine-and-instantiate-generic-types-with-reflection.md)|Genel türleri incelemek için <xref:System.Type> ve <xref:System.Reflection.MethodInfo> özelliklerinin ve yöntemlerinin nasıl kullanılacağını gösterir.|  
|[Genel Türler](../../standard/generics/index.md)|Genel türler özelliğini ve .NET Framework nasıl desteklendiğini açıklar.|  
|[Nasıl yapılır: Yansıma Yayma ile Genel Tür Tanımlama](how-to-define-a-generic-type-with-reflection-emit.md)|Dinamik derlemelerde genel türler oluşturmak için yansıma yayma 'nın nasıl kullanılacağını gösterir.|  
|[Tür Bilgilerini Görüntüleme](viewing-type-information.md)|<xref:System.Type> sınıfını açıklar ve oluşturucular, Yöntemler, alanlar, Özellikler ve olaylar hakkında bilgi edinmek için <xref:System.Type> çeşitli yansıma sınıflarıyla nasıl kullanacağınızı gösteren kod örnekleri sağlar.|

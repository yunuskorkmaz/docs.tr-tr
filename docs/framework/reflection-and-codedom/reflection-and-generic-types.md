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
Yansıma açısından bakıldığında, genel bir tür ile sıradan bir tür arasındaki fark, genel bir tür türü yle bir dizi tür parametresini (genel bir tür tanımı ysa) veya tür bağımsız değişkenleri (oluşturulmuş bir türse) ilişkilendirmiş olmasıdır. Genel bir yöntem aynı şekilde sıradan bir yöntemfarklıdır.  
  
 Yansımanın genel türleri ve yöntemleri nasıl işleyeceğini anlamak için iki anahtar vardır:  
  
- Genel tür tanımlarının ve genel yöntem tanımlarının tür parametreleri <xref:System.Type> sınıfın örnekleritarafından temsil edilir.  
  
    > [!NOTE]
    > Bir <xref:System.Type> nesne genel <xref:System.Type> bir tür parametresini temsil ettiğinde birçok özellik ve yöntem farklı davranışa sahiptir. Bu farklılıklar özellik ve yöntem konularında belgelenmiştir. Örneğin, bkz <xref:System.Type.IsAutoClass%2A> <xref:System.Type.DeclaringType%2A>ve . Buna ek olarak, bazı üyeler <xref:System.Type> yalnızca bir nesne genel bir tür parametresini temsil ettiğinde geçerlidir. Örneğin, bkz. <xref:System.Type.GetGenericTypeDefinition%2A>  
  
- Genel bir <xref:System.Type> türü temsil eden bir örneği varsa, tür parametrelerini (genel tür tanımları için) veya tür bağımsız değişkenlerini (yapılandırılan türler için) temsil eden bir dizi tür içerir. Aynı genel bir yöntemi temsil <xref:System.Reflection.MethodInfo> eden sınıfın bir örneği için de geçerlidir.  
  
 Yansıma, tür <xref:System.Type> <xref:System.Reflection.MethodInfo> parametreleri dizisine erişmenizi ve bir tür parametresini <xref:System.Type> mi yoksa gerçek bir türü mü temsil ettiğini belirlemenize olanak tanıyan yöntemler sağlar.  
  
 Örneğin burada tartışılan yöntemleri gösteren kod, [bkz.](how-to-examine-and-instantiate-generic-types-with-reflection.md)  
  
 Aşağıdaki tartışma, tür parametreleri ve bağımsız değişkenler ve açık veya kapalı yapılandırılan türler arasındaki fark gibi genel jenerik terminolojisine aşinalığı varsayar. Daha fazla bilgi için [Genel Bilgiler'e](../../standard/generics/index.md)bakın.  

## <a name="is-this-a-generic-type-or-method"></a>Bu Genel Bir Tür mü yoksa Yöntem mi?  
 Bilinmeyen bir türü incelemek için yansımayı <xref:System.Type>kullandığınızda, bilinmeyen <xref:System.Type.IsGenericType%2A> türde genel olup olmadığını belirlemek için özelliği kullanın. Tür `true` genelse döndürür. Benzer şekilde, <xref:System.Reflection.MethodInfo> sınıfın bir örneği tarafından temsil edilen bilinmeyen bir <xref:System.Reflection.MethodBase.IsGenericMethod%2A> yöntemi incelediğinizde, yöntemin genel olup olmadığını belirlemek için özelliği kullanın.  
  
### <a name="is-this-a-generic-type-or-method-definition"></a>Bu Genel Bir Tür mü yoksa Yöntem Tanımı mı?  
 Bir <xref:System.Type.IsGenericTypeDefinition%2A> <xref:System.Type> nesnenin genel bir tür tanımını temsil edip <xref:System.Reflection.MethodBase.IsGenericMethodDefinition%2A> etmediğini belirlemek <xref:System.Reflection.MethodInfo> için özelliği kullanın ve genel bir yöntem tanımını temsil edip etmediğini belirlemek için yöntemi kullanın.  
  
 Genel tür ve yöntem tanımları, anında oluşturulabilir türlerin oluşturulduğu şablonlardır. .NET Framework sınıf kitaplığındaki genel <xref:System.Collections.Generic.Dictionary%602>türler, genel tür tanımlarıdır.  
  
### <a name="is-the-type-or-method-open-or-closed"></a>Tür veya Yöntem Açık mı kapalı mı?  
 Anlık türleri, tüm çevreleyen türlerin tüm tür parametreleri de dahil olmak üzere tüm tür parametreleri için değiştirilmişse, genel bir tür veya yöntem kapatılır. Yalnızca kapalıysa genel bir tür örneği oluşturabilirsiniz. Bir <xref:System.Type.ContainsGenericParameters%2A?displayProperty=nameWithType> tür `true` açıksa özellik döndürür. Yöntemler için <xref:System.Reflection.MethodBase.ContainsGenericParameters%2A?displayProperty=nameWithType> yöntem aynı işlevi gerçekleştirir.

## <a name="generating-closed-generic-types"></a>Kapalı Genel Türler Oluşturma  
 Genel bir tür veya yöntem tanımına <xref:System.Type.MakeGenericType%2A> sahip olduktan sonra, kapalı <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A> genel bir <xref:System.Reflection.MethodInfo> tür veya kapalı genel bir yöntem için bir yöntem oluşturmak için yöntem kullanın.  
  
### <a name="getting-the-generic-type-or-method-definition"></a>Genel Tür veya Yöntem Tanımıalma  
 Genel bir tür veya yöntem tanımı olmayan açık bir genel tür veya yöntem varsa, bunun örneklerini oluşturamazsınız ve eksik olan tür parametrelerini sağlayamazsınız. Genel bir tür veya yöntem tanımına sahip olmalısınız. Genel <xref:System.Type.GetGenericTypeDefinition%2A> yöntem tanımını elde etmek <xref:System.Reflection.MethodInfo.GetGenericMethodDefinition%2A> için genel tür tanımını veya yöntemi elde etmek için yöntemi kullanın.  
  
 Örneğin, <xref:System.Type> (Visual `Dictionary<int, string>` `Dictionary(Of Integer, String)` Basic'te) temsil eden bir nesneniz varsa `Dictionary<string, MyClass>`ve türü oluşturmak <xref:System.Type.GetGenericTypeDefinition%2A> istiyorsanız, <xref:System.Type> bir `Dictionary<TKey, TValue>` temsil almak <xref:System.Type.MakeGenericType%2A> için yöntemi <xref:System.Type> kullanabilir `Dictionary<int, MyClass>`ve sonra bir temsil oluşturmak için yöntemi kullanabilirsiniz.  
  
 Genel bir tür olmayan açık genel bir tür örneği için, bu konunun daha sonra "Parametre veya Tür Bağımsız Değişkeni Yazın" bölümüne bakın.

## <a name="examining-type-arguments-and-type-parameters"></a>Tip Bağımsız Değişkenleri ve Tip Parametrelerinin İncelenmesi  
 Genel <xref:System.Type.GetGenericArguments%2A?displayProperty=nameWithType> bir türdeki tür <xref:System.Type> parametrelerini veya tür bağımsız değişkenlerini temsil eden <xref:System.Reflection.MethodInfo.GetGenericArguments%2A?displayProperty=nameWithType> bir nesne dizisi elde etmek için yöntemi kullanın ve genel bir yöntem için aynı yöntemi yapmak için yöntemi kullanın.  
  
 Bir <xref:System.Type> nesnenin bir tür parametresini temsil ettiğini bildiğinizde, yansımanın yanıtlanabileceği birçok ek soru vardır. Tür parametresinin kaynağını, konumunu ve kısıtlamalarını belirleyebilirsiniz.  
  
### <a name="type-parameter-or-type-argument"></a>Tür Parametresi veya Tür Bağımsız Değişkeni  
 Dizinin belirli bir öğesinin bir tür parametresi mi yoksa <xref:System.Type.IsGenericParameter%2A> tür bağımsız değişkeni mi olduğunu belirlemek için özelliği kullanın. Özellik, <xref:System.Type.IsGenericParameter%2A> `true` öğenin bir tür parametresi olmasıdır.  
  
 Genel bir tür, genel bir tür tanımı olmadan açılabilir ve bu durumda tür bağımsız değişkenleri ve tür parametreleri karışımı vardır. Örneğin, aşağıdaki kodda sınıf, `D` `D` `B`ikinci tür parametresi için ilk tür parametresini ikame ederek oluşturulan bir türden türe  
  
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
  
 Temel türünü <xref:System.Type> elde etmek `D<V, W>` için <xref:System.Type.BaseType%2A> özelliği temsil eden bir nesne `type B<int, V>` elde ederseniz ve kullanırsanız, ortaya çıkan açık, ancak genel bir tür tanımı değildir.  
  
### <a name="source-of-a-generic-parameter"></a>Genel Parametrenin Kaynağı  
 Genel bir tür parametresi, incelediğiniz türden, çevreleyen bir türden veya genel bir yöntemden gelebilir. Genel tür parametresinin kaynağını aşağıdaki gibi belirleyebilirsiniz:  
  
- İlk olarak, <xref:System.Type.DeclaringMethod%2A> tür parametresinin genel bir yöntemden gelip gelmediğini belirlemek için özelliği kullanın. Özellik değeri null bir başvuru`Nothing` değilse (Visual Basic'te), kaynak genel bir yöntemdir.  
  
- Kaynak genel bir yöntem değilse, <xref:System.Type.DeclaringType%2A> genel tür parametresinin ait olduğu genel türü belirlemek için özelliği kullanın.  
  
 Tür parametresi genel bir yönteme <xref:System.Type.DeclaringType%2A> aitse, özellik, alakasız olan genel yöntemi bildiren türü döndürür.  
  
### <a name="position-of-a-generic-parameter"></a>Genel Parametrenin Konumu  
 Nadir durumlarda, bir tür parametresinin konumunu, bildirim sınıfının tür parametre listesinde belirlemek gerekir. Örneğin, önceki örnekten <xref:System.Type> `B<int, V>` türü temsil eden bir nesneniz olduğunu varsayalım. Yöntem <xref:System.Type.GetGenericArguments%2A> size tür bağımsız değişkenlerin bir listesini `V` verir ve <xref:System.Type.DeclaringMethod%2A> <xref:System.Type.DeclaringType%2A> incelediğinizde nereden geldiğini keşfetmek için bu ve özellikleri kullanabilirsiniz. Daha sonra, <xref:System.Type.GenericParameterPosition%2A> tanımlandığı tür parametre listesindekonumunu belirlemek için özelliği kullanabilirsiniz. Bu örnekte, `V` tanımlandığı tür parametre listesinde 0 (sıfır) konumundadır.  
  
### <a name="base-type-and-interface-constraints"></a>Temel Tür ve Arayüz Kısıtlamaları  
 Bir <xref:System.Type.GetGenericParameterConstraints%2A> tür parametresinin taban türü kısıtlamasını ve arabirim kısıtlamalarını elde etmek için yöntemi kullanın. Dizinin öğelerinin sırası önemli değildir. Bir öğe, arabirim türüyse arabirim kısıtlaması temsil eder.  
  
### <a name="generic-parameter-attributes"></a>Genel Parametre Öznitelikleri  
 Özellik <xref:System.Type.GenericParameterAttributes%2A> varyans (covariance veya contravariance) ve bir tür parametre özel kısıtlamaları gösteren bir <xref:System.Reflection.GenericParameterAttributes> değer alır.  
  
#### <a name="covariance-and-contravariance"></a>Kovaryans ve Kontravaryans  
 Bir tür parametresinin eşdeğişken mi yoksa zıt <xref:System.Reflection.GenericParameterAttributes.VarianceMask?displayProperty=nameWithType> değişken <xref:System.Reflection.GenericParameterAttributes> mi olduğunu belirlemek <xref:System.Type.GenericParameterAttributes%2A> için maskeyi özellik tarafından döndürülen değere uygulayın. Sonuç <xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>ise, tür parametresi değişmez. [Bkz. Covariance ve Contravariance](../../standard/generics/covariance-and-contravariance.md).  
  
#### <a name="special-constraints"></a>Özel Kısıtlamalar  
 Bir tür parametresinin özel kısıtlamalarını belirlemek <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=nameWithType> için <xref:System.Reflection.GenericParameterAttributes> maskeyi özellik tarafından <xref:System.Type.GenericParameterAttributes%2A> döndürülen değere uygulayın. Sonuç <xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>varsa, özel kısıtlamalar yoktur. Bir tür parametresi başvuru türü, nullable olmayan değer türü ve parametresiz bir oluşturucu olması için sınırlandırılabilir.

## <a name="invariants"></a>Invariants  
 Genel türler için yansımada ortak terimler için değişmez koşulların bir tablosu için bkz. <xref:System.Type.IsGenericType%2A?displayProperty=nameWithType> Genel yöntemlerle ilgili ek <xref:System.Reflection.MethodBase.IsGenericMethod%2A?displayProperty=nameWithType>koşullar için bkz.  

## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Nasıl yapılır: Yansıma ile Genel Türleri İnceleme ve Örnek Oluşturma](how-to-examine-and-instantiate-generic-types-with-reflection.md)|Genel türlerin özelliklerini ve yöntemlerinin nasıl kullanılacağını <xref:System.Type> ve <xref:System.Reflection.MethodInfo> inceleyeceğini gösterir.|  
|[Genel Türler](../../standard/generics/index.md)|Genel özellikler özelliğini ve .NET Framework'de nasıl desteklenirlerini açıklar.|  
|[Nasıl yapılır: Yansıma Yayma ile Genel Tür Tanımlama](how-to-define-a-generic-type-with-reflection-emit.md)|Dinamik derlemelerde genel türler oluşturmak için yansıma yayımı nın nasıl kullanılacağını gösterir.|  
|[Tür Bilgilerini Görüntüleme](viewing-type-information.md)|<xref:System.Type> Sınıfı açıklar ve oluşturucular, yöntemler, alanlar, özellikler ve olaylar hakkında bilgi edinmek için çeşitli yansıma sınıflarıyla nasıl kullanılacağını <xref:System.Type> gösteren kod örnekleri sağlar.|

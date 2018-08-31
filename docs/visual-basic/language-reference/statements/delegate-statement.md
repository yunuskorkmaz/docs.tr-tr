---
title: Delegate deyimi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Delegate
helpviewer_keywords:
- delegate keyword [Visual Basic]
- Delegate statement [Visual Basic]
ms.assetid: f799c518-0817-40cc-ad0b-4da846fdba57
ms.openlocfilehash: 4718c0a6e332d644a7f54c79246df95f841058d0
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2018
ms.locfileid: "43258489"
---
# <a name="delegate-statement"></a>Delegate Deyimi
Bir temsilci bildirmek için kullanılır. Temsilci başvurduğu bir başvuru türüdür bir `Shared` türü veya bir nesnenin bir örnek yöntemi için yöntem. Parametre ve dönüş türleri eşleşen her türlü yordam, bu temsilci sınıfı örneğini oluşturmak için kullanılabilir. Yordamı, temsilci örneği aracılığıyla sonra bir daha sonra çağrılabilir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
[ <attrlist> ] [ accessmodifier ] _  
[ Shadows ] Delegate [ Sub | Function ] name [( Of typeparamlist )] [([ parameterlist ])] [ As type ]  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`attrlist`|İsteğe bağlı. Bu temsilci için geçerli olan özniteliklerin listesi. Birden çok öznitelik virgülle ayrılır. İçine almalısınız [öznitelik listesi](../../../visual-basic/language-reference/statements/attribute-list.md) açılı ayraçlar içinde ("`<`"ve"`>`").|  
|`accessmodifier`|İsteğe bağlı. Hangi kod temsilci erişip belirtir. Aşağıdakilerden biri olabilir:<br /><br /> - [Genel](../../../visual-basic/language-reference/modifiers/public.md). Temsilci bildirir öğesi erişebilen herhangi bir kod da erişebilirsiniz.<br />-   [Korumalı](../../../visual-basic/language-reference/modifiers/protected.md). Temsilcinin sınıfı veya türetilmiş bir sınıf içinde tek bir kod da erişebilirsiniz.<br />-   [Arkadaş](../../../visual-basic/language-reference/modifiers/friend.md). Yalnızca aynı derlemedeki kod temsilci erişebilirsiniz.<br />- [Özel](../../../visual-basic/language-reference/modifiers/private.md). Yalnızca temsilci bildirir öğe içindeki kod, erişebilir.<br /><br /> - [Korumalı Friend](../../language-reference/modifiers/protected-friend.md) yalnızca temsilci temsilcinin sınıfın, türetilmiş bir sınıf veya aynı derleme içinde kod erişebilir. <br />- [Özel korumalı](../../language-reference/modifiers/private-protected.md) yalnızca temsilci temsilcinin sınıfı veya türetilmiş sınıf içinde aynı bütünleştirilmiş kod erişebilir. |  
|`Shadows`|İsteğe bağlı. Bu temsilci redeclares ve bir programlama aynı adlı bir öğeyi veya taban sınıfında aşırı yüklenmiş bir öğe kümesini gizler gösterir. Bildirilen öğe herhangi bir türden başka bir tür ile gölge.<br /><br /> Gölgeli öğe, dışında gölgeleme öğesi erişilemez olduğu gelen gölgeleri türetilmiş sınıf içinde kullanılamaz. Örneğin, bir `Private` öğesi bir temel sınıf öğesi, erişim iznine sahip olmayan kod gölgeliyor `Private` öğe temel sınıf öğe yerine erişir.|  
|`Sub`|İsteğe bağlı, ancak ya da `Sub` veya `Function` yer almalıdır. Bu yordam bir temsilci olarak bildirir `Sub` bir değer döndürmeyen bir yordam.|  
|`Function`|İsteğe bağlı, ancak ya da `Sub` veya `Function` yer almalıdır. Bu yordam bir temsilci olarak bildirir `Function` bir değer döndüren yordam.|  
|`name`|Gerekli. Name temsilci türü; Standart değişken adlandırma kurallarını izler.|  
|`typeparamlist`|İsteğe bağlı. Bu temsilci için tür parametreleri listesi. Birden çok tür parametrelerine virgülle ayrılır. İsteğe bağlı olarak, her tür parametresi değişken kullanarak bildirilebilir `In` ve `Out` genel değiştiriciler. İçine almalısınız [tür listesi](../../../visual-basic/language-reference/statements/type-list.md) parantez içinde ve onunla `Of` anahtar sözcüğü.|  
|`parameterlist`|İsteğe bağlı. Bunu çağrıldığında yordamına geçirilen parametrelerin listesi. İçine almalısınız [parametre listesi](../../../visual-basic/language-reference/statements/parameter-list.md) parantez içinde.|  
|`type`|Belirtirseniz gerekli bir `Function` yordamı. Dönüş değerinin veri türü.|  
  
## <a name="remarks"></a>Açıklamalar  
 `Delegate` Bildirimi temsilci sınıfını parametre ve dönüş türleri tanımlar. Eşleşen parametreler ve dönüş türleri ile her türlü yordam, bu temsilci sınıfı örneğini oluşturmak için kullanılabilir. Yordam sonra daha sonra temsilci örneği aracılığıyla temsilcinin çağırarak çağrılabilir `Invoke` yöntemi.  
  
 Temsilciler, ad alanı, modül, sınıf veya yapı düzeyinde ancak değil bir yordam içinde bildirilebilir.  
  
 Her bir temsilci sınıfı nesne yöntemi belirtimi geçirilen bir oluşturucu tanımlar. Bir temsilci Oluşturucu için bağımsız değişken bir yöntem veya lambda ifadesi bir başvuru olmalıdır.  
  
 Bir yönteme başvuru belirtmek için aşağıdaki sözdizimini kullanın:  
  
 `AddressOf` [`expression`.]`methodname`  
  
 Derleme zamanı türü `expression` bir sınıf veya bir yöntem imzası olan, temsilci sınıfı imzası eşleşen belirtilen adı içeren bir arabirim adı olmalıdır. `methodname` Paylaşılan bir yöntemine ya da bir örnek yöntemi olabilir. `methodname` Sınıfının varsayılan yöntemi temsilci oluşturmak olsa bile, isteğe bağlı değil.  
  
 Bir lambda ifadesini belirtmek için aşağıdaki sözdizimini kullanın:  
  
 `Function` ([`parm` Olarak `type`, `parm2` olarak `type2`,...]) `expression`  
  
 İşlev imzası temsilci türüyle eşleşmelidir. Lambda ifadeleri hakkında daha fazla bilgi için bkz. [Lambda ifadeleri](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 Temsilciler hakkında daha fazla bilgi için bkz. [Temsilciler](../../../visual-basic/programming-guide/language-features/delegates/index.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `Delegate` iki sayının üzerinde çalışan ve bir sayı döndüren bir temsilci bildirmeniz deyimi. `DelegateTest` Yöntemi bu tür bir temsilci örneğini alır ve numarası çiftleri üzerinde çalışılacak kullanır.  
  
 [!code-vb[VbVbalrDelegates#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/delegate-statement_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [AddressOf İşleci](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [,](../../../visual-basic/language-reference/statements/of-clause.md)  
 [Temsilciler](../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [Nasıl yapılır: Genel Bir Sınıf Kullanma](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [Visual Basic'de genel türler](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Kovaryans ve Kontravaryans](../../programming-guide/concepts/covariance-contravariance/index.md)  
 [İçinde](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)  
 [Çıkış](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)

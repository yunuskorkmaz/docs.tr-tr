---
title: Delegate Deyimi
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Delegate
helpviewer_keywords:
- delegate keyword [Visual Basic]
- Delegate statement [Visual Basic]
ms.assetid: f799c518-0817-40cc-ad0b-4da846fdba57
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7e79a261f74cbc7aa067af63629e31bedf65d163
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="delegate-statement"></a>Delegate Deyimi
Bir temsilci bildirmek için kullanılır. Bir temsilci başvurduğu bir başvuru türü olan bir `Shared` yöntemi türü veya örnek yöntemi nesnenin. Parametre ve dönüş türleri eşleşen herhangi bir yordam, bu temsilci sınıfının bir örneğini oluşturmak için kullanılabilir. Yordam sonra yoluyla temsilci örnek daha sonra çağrılabilir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
[ <attrlist> ] [ accessmodifier ] _  
[ Shadows ] Delegate [ Sub | Function ] name [( Of typeparamlist )] [([ parameterlist ])] [ As type ]  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`attrlist`|İsteğe bağlı. Bu temsilciye uygulamak öznitelikler listesi. Birden çok öznitelik virgülle ayrılır. İçine almalısınız [öznitelik listesi](../../../visual-basic/language-reference/statements/attribute-list.md) açılı ayraç ("`<`"ve"`>`").|  
|`accessmodifier`|İsteğe bağlı. Hangi kod temsilci erişip belirtir. Aşağıdakilerden biri olabilir:<br /><br /> -   [Ortak](../../../visual-basic/language-reference/modifiers/public.md). Temsilci bildirir öğesi erişebilmeniz için herhangi bir kod da erişebilirsiniz.<br />-   [Korumalı](../../../visual-basic/language-reference/modifiers/protected.md). Yalnızca kodunu temsilcinin sınıf veya türetilmiş bir sınıf içinde erişebilir.<br />-   [Arkadaş](../../../visual-basic/language-reference/modifiers/friend.md). Yalnızca aynı bütünleştirilmiş kod içinde kod temsilci erişebilir.<br />-   [Özel](../../../visual-basic/language-reference/modifiers/private.md). Yalnızca kod temsilci bildirir öğesi içinde erişebilir.<br /><br /> Belirleyebileceğiniz `Protected Friend` temsilcinin sınıfı, türetilmiş bir sınıf ya da aynı bütünleştirilmiş kodundan erişim sağlamak için.|  
|`Shadows`|İsteğe bağlı. Bu temsilci redeclares ve bir aynı adlı programlama öğesi ya da bir taban sınıf içinde aşırı yüklenmiş öğelerin gizler gösterir. Bildirilen öğe herhangi bir tür başka herhangi bir tür ile gölge.<br /><br /> Gölgeli bir öğe, dışında gölgeleme öğesi erişilemez olduğu gelen shadows türetilmiş sınıf içinde kullanılamaz. Örneğin, varsa bir `Private` öğesi shadows erişim izni yok kod bir temel sınıf öğesi `Private` öğe temel sınıf öğesi yerine erişir.|  
|`Sub`|İsteğe bağlı, ancak ya da `Sub` veya `Function` görünmesi gerekir. Bu yordam bir temsilci olarak bildirir `Sub` bir değer döndürmüyor yordamı.|  
|`Function`|İsteğe bağlı, ancak ya da `Sub` veya `Function` görünmesi gerekir. Bu yordam bir temsilci olarak bildirir `Function` yordamı bir değer döndürür.|  
|`name`|Gerekli. Temsilci türünün adı; Standart değişken adlandırma kuralları izler.|  
|`typeparamlist`|İsteğe bağlı. Bu temsilci için tür parametrelerinin listesi. Birden çok tür parametreleri virgülle ayrılır. İsteğe bağlı olarak, her tür parametre değişken kullanarak bildirilebilir `In` ve `Out` genel değiştiricileri. İçine almalısınız [türü listesinde](../../../visual-basic/language-reference/statements/type-list.md) parantez içinde ve onunla tanıtmak `Of` anahtar sözcüğü.|  
|`parameterlist`|İsteğe bağlı. Bunu çağrıldığında yordamına geçirilen parametre listesi. İçine almalısınız [parametre listesi](../../../visual-basic/language-reference/statements/parameter-list.md) parantez içinde.|  
|`type`|Belirtirseniz gerekli bir `Function` yordamı. Dönüş değeri veri türü.|  
  
## <a name="remarks"></a>Açıklamalar  
 `Delegate` Deyimi bir temsilci sınıf parametre ve dönüş türlerini tanımlar. Parametreler ve dönüş türleri eşleşen herhangi bir yordam, bu temsilci sınıfının bir örneğini oluşturmak için kullanılabilir. Yordam sonra daha sonra temsilci örneği yoluyla temsilcinin çağırarak çağrılabilir `Invoke` yöntemi.  
  
 Temsilciler ad alanı, modül, sınıf veya yapı düzeyinde ancak bir yordam içinde değil bildirilebilir.  
  
 Her temsilci sınıfı nesne yöntemi belirtimi geçirilen bir oluşturucu tanımlar. Temsilci oluşturucu bağımsız değişken bir yöntem ya da bir lambda ifadesi başvuru olması gerekir.  
  
 Bir yöntem başvuru belirtmek için aşağıdaki sözdizimini kullanın:  
  
 `AddressOf` [`expression`.]`methodname`  
  
 Derleme zamanı türünü `expression` bir sınıf veya bir yöntemi, imza eşleşen temsilci sınıfı imza belirtilen adını içeren bir arabirim adı olması gerekir. `methodname` Paylaştırılmış yöntem veya örnek yöntemi olabilir. `methodname` Sınıfının varsayılan yöntemi için bir temsilci oluşturmak olsa bile isteğe bağlı değildir.  
  
 Lambda ifadesi belirtmek için aşağıdaki sözdizimini kullanın:  
  
 `Function`([`parm` Olarak `type`, `parm2` olarak `type2`,...])`expression`  
  
 İşlev imzası temsilci türüyle eşleşmelidir. Lambda ifadeleri hakkında daha fazla bilgi için bkz: [Lambda ifadeleri](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 Temsilciler hakkında daha fazla bilgi için bkz: [Temsilciler](../../../visual-basic/programming-guide/language-features/delegates/index.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır `Delegate` iki numaralarında işletim ve bir sayı döndüren bir temsilci bildirmek için deyimi. `DelegateTest` Yöntemi bu tür bir temsilci örneği alır ve numarası çiftleri üzerinde çalışması için kullanır.  
  
 [!code-vb[VbVbalrDelegates#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/delegate-statement_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [AddressOf işleci](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [,](../../../visual-basic/language-reference/statements/of-clause.md)  
 [Temsilciler](../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [Nasıl yapılır: genel bir sınıf kullanma](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [Visual Basic'de genel türler](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Kovaryans ve kontravaryans](../../programming-guide/concepts/covariance-contravariance/index.md)  
 [İçinde](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)  
 [Çıkışı](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)

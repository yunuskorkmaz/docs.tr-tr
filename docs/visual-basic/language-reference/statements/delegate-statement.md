---
title: Temsilci ekstresi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Delegate
helpviewer_keywords:
- delegate keyword [Visual Basic]
- Delegate statement [Visual Basic]
ms.assetid: f799c518-0817-40cc-ad0b-4da846fdba57
ms.openlocfilehash: 4a8260da4d2224551de71fd54f734007c7fa214f
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583451"
---
# <a name="delegate-statement"></a>Delegate Deyimi
Bir temsilciyi bildirmek için kullanılır. Temsilci, bir türün `Shared` yöntemine veya bir nesnenin örnek metoduna başvuran bir başvuru türüdür. Bu temsilci sınıfının bir örneğini oluşturmak için eşleşen parametre ve dönüş türleri olan herhangi bir yordam kullanılabilir. Yordam daha sonra temsilci örneği aracılığıyla çağrılabilir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
[ <attrlist> ] [ accessmodifier ] _  
[ Shadows ] Delegate [ Sub | Function ] name [( Of typeparamlist )] [([ parameterlist ])] [ As type ]  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`attrlist`|İsteğe bağlı. Bu temsilci için uygulanan özniteliklerin listesi. Birden çok öznitelik virgülle ayrılır. [Öznitelik listesini](../../../visual-basic/language-reference/statements/attribute-list.md) açılı ayraç içine almalısınız ("`<`" ve "`>`").|  
|`accessmodifier`|İsteğe bağlı. Temsilciye erişebilecek kodu belirtir. Aşağıdakilerden biri olabilir:<br /><br /> - [genel](../../../visual-basic/language-reference/modifiers/public.md). Temsilciyi bildiren öğeye erişebilen tüm kodlar buna erişebilir.<br />-   [korumalı](../../../visual-basic/language-reference/modifiers/protected.md). Yalnızca temsilcinin sınıfı veya türetilmiş bir sınıf içindeki kodlar buna erişebilir.<br />-   [arkadaş](../../../visual-basic/language-reference/modifiers/friend.md). Temsilciye yalnızca aynı derleme içindeki kod erişebilir.<br />[özel](../../../visual-basic/language-reference/modifiers/private.md)- . Yalnızca temsilciyi bildiren öğesi içindeki kod erişebilir.<br /><br /> yalnızca temsilcinin sınıfı, türetilmiş bir sınıf veya aynı derleme içindeki[korunan arkadaş](../../language-reference/modifiers/protected-friend.md) kodu -  temsilciye erişebilir. <br />yalnızca temsilcinin sınıfı içindeki veya aynı derlemede bulunan türetilmiş bir sınıftaki[özel korumalı](../../language-reference/modifiers/private-protected.md) kod -  temsilciye erişebilir. |  
|`Shadows`|İsteğe bağlı. Bu temsilcinin, bir temel sınıfta aynı adlı programlama öğesi veya aşırı yüklenmiş öğeler kümesi tarafından yeniden bildirdiğini ve gizlediğini belirtir. Herhangi bir tür tanımlanmış öğeyi başka bir tür ile gölgelendirebilmeniz gerekir.<br /><br /> Gölgelendirilmiş bir öğe, gölgeleme öğesinin erişilemez olması dışında, kendisini gölgelendirilebilen türetilmiş sınıfın içinden kullanılamaz. Örneğin, bir `Private` öğesi bir temel sınıf öğesini göltikten sonra, `Private` öğesine erişim izni olmayan kod bunun yerine temel sınıf öğesine erişir.|  
|`Sub`|İsteğe bağlı, ancak `Sub` ya da `Function` görünmelidir. Bu yordamı bir değer döndürmeyen `Sub` bir yöntem olarak bildirir.|  
|`Function`|İsteğe bağlı, ancak `Sub` ya da `Function` görünmelidir. Bu yordamı bir değer döndüren bir temsilci `Function` yordamı olarak bildirir.|  
|`name`|Gerekli. Temsilci türünün adı; Standart değişken adlandırma kurallarını izler.|  
|`typeparamlist`|İsteğe bağlı. Bu temsilcinin tür parametrelerinin listesi. Birden çok tür parametresi virgülle ayrılır. İsteğe bağlı olarak, her tür parametresi `In` ve `Out` genel değiştiriciler kullanılarak değişken olarak bildirilemez. [Tür listesini](../../../visual-basic/language-reference/statements/type-list.md) parantez içine almalısınız ve bunu `Of` anahtar sözcüğüyle birlikte vermelisiniz.|  
|`parameterlist`|İsteğe bağlı. Çağrıldığında yordama geçirilen parametrelerin listesi. [Parametre listesini](../../../visual-basic/language-reference/statements/parameter-list.md) parantez içine almalısınız.|  
|`type`|Bir `Function` yordamı belirtirseniz gereklidir. Dönüş değerinin veri türü.|  
  
## <a name="remarks"></a>Açıklamalar  
 @No__t_0 ifade, bir temsilci sınıfının parametresini ve dönüş türlerini tanımlar. Bu temsilci sınıfının bir örneğini oluşturmak için, eşleşen parametreleri ve dönüş türlerini içeren herhangi bir yordam kullanılabilir. Daha sonra yordam, temsilcinin `Invoke` yöntemi çağırarak temsilci örneği aracılığıyla çağrılabilir.  
  
 Temsilciler ad alanı, modül, sınıf veya yapı düzeyinde bildirilebilecek, ancak bir yordam içinde bildirilemez.  
  
 Her temsilci sınıfı, bir nesne yönteminin belirtimini geçen bir oluşturucuyu tanımlar. Bir temsilci oluşturucusuna bağımsız değişken bir yönteme veya bir lambda ifadesine başvuru olmalıdır.  
  
 Bir yönteme başvuru belirtmek için aşağıdaki sözdizimini kullanın:  
  
 `AddressOf` [`expression`.] `methodname`  
  
 @No__t_0 derleme zamanı türü, imzası temsilci sınıfının imzasıyla eşleşen belirtilen adda bir yöntemi içeren bir sınıfın veya arabirimin adı olmalıdır. @No__t_0, paylaşılan bir yöntem ya da bir örnek yöntemi olabilir. Sınıfının varsayılan yöntemi için bir temsilci oluştursanız bile `methodname` isteğe bağlı değildir.  
  
 Bir lambda ifadesi belirtmek için aşağıdaki sözdizimini kullanın:  
  
 `Function` ([`parm` as `type`, `parm2` as `type2`,...])  `expression`  
  
 İşlevin imzası, temsilci türü ile aynı olmalıdır. Lambda ifadeleri hakkında daha fazla bilgi için bkz. [lambda ifadeleri](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 Temsilciler hakkında daha fazla bilgi için bkz. [Temsilciler](../../../visual-basic/programming-guide/language-features/delegates/index.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, iki sayı üzerinde çalışan ve bir sayı döndüren bir temsilciyi bildirmek için `Delegate` bildirimini kullanır. @No__t_0 yöntemi bu tür bir temsilcinin örneğini alır ve sayı çiftleri üzerinde çalışmak için onu kullanır.  
  
 [!code-vb[VbVbalrDelegates#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#14)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [AddressOf İşleci](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Durumunu](../../../visual-basic/language-reference/statements/of-clause.md)
- [Temsilciler](../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Nasıl yapılır: Genel Bir Sınıf Kullanma](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [Visual Basic genel türler](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Kovaryans ve Kontravaryans](../../programming-guide/concepts/covariance-contravariance/index.md)
- ['Ndaki](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
- [Dışı](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)

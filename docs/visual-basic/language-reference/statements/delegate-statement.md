---
title: Delegate Deyimi
ms.date: 07/20/2015
f1_keywords:
- vb.Delegate
helpviewer_keywords:
- delegate keyword [Visual Basic]
- Delegate statement [Visual Basic]
ms.assetid: f799c518-0817-40cc-ad0b-4da846fdba57
ms.openlocfilehash: 29de4c174273c3c6c0d4f0cea1ee6dc254a1339b
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866654"
---
# <a name="delegate-statement"></a>Delegate Deyimi

Bir temsilciyi bildirmek için kullanılır. Temsilci, `Shared` bir türün yöntemine veya bir nesnenin örnek metoduna başvuran bir başvuru türüdür. Bu temsilci sınıfının bir örneğini oluşturmak için eşleşen parametre ve dönüş türleri olan herhangi bir yordam kullanılabilir. Yordam daha sonra temsilci örneği aracılığıyla çağrılabilir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
[ <attrlist> ] [ accessmodifier ] _  
[ Shadows ] Delegate [ Sub | Function ] name [( Of typeparamlist )] [([ parameterlist ])] [ As type ]  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`attrlist`|İsteğe bağlı. Bu temsilci için uygulanan özniteliklerin listesi. Birden çok öznitelik virgülle ayrılır. [Öznitelik listesini](attribute-list.md) açılı ayraçlar (" `<` " ve " `>` ") içine almalısınız.|  
|`accessmodifier`|İsteğe bağlı. Temsilciye erişebilecek kodu belirtir. Aşağıdakilerden biri olabilir:<br /><br /> - [Genel](../modifiers/public.md). Temsilciyi bildiren öğeye erişebilen tüm kodlar buna erişebilir.<br />-   [Korunuyor](../modifiers/protected.md). Yalnızca temsilcinin sınıfı veya türetilmiş bir sınıf içindeki kodlar buna erişebilir.<br />-   [Arkadaş](../modifiers/friend.md). Temsilciye yalnızca aynı derleme içindeki kod erişebilir.<br />- [Özel](../modifiers/private.md). Yalnızca temsilciyi bildiren öğesi içindeki kod erişebilir.<br /><br /> - [Korumalı arkadaş](../modifiers/protected-friend.md) Yalnızca temsilcinin sınıfının, türetilmiş bir sınıfın veya aynı derlemenin içindeki kodların temsilciye erişimi olabilir. <br />- [Özel korumalı](../modifiers/private-protected.md) Yalnızca temsilcinin sınıfı içindeki veya aynı derlemede bulunan türetilmiş bir sınıftaki kod temsilciye erişebilir. |  
|`Shadows`|İsteğe bağlı. Bu temsilcinin, bir temel sınıfta aynı adlı programlama öğesi veya aşırı yüklenmiş öğeler kümesi tarafından yeniden bildirdiğini ve gizlediğini belirtir. Herhangi bir tür tanımlanmış öğeyi başka bir tür ile gölgelendirebilmeniz gerekir.<br /><br /> Gölgelendirilmiş bir öğe, gölgeleme öğesinin erişilemez olması dışında, kendisini gölgelendirilebilen türetilmiş sınıfın içinden kullanılamaz. Örneğin, bir öğe bir `Private` temel sınıf öğesini gölerse, öğesine erişim izni olmayan kod, `Private` bunun yerine temel sınıf öğesine erişir.|  
|`Sub`|İsteğe bağlı, ancak ya da `Sub` `Function` görünür olmalıdır. Bu yordamı `Sub` bir değer döndürmeyen bir temsilci yordamı olarak bildirir.|  
|`Function`|İsteğe bağlı, ancak ya da `Sub` `Function` görünür olmalıdır. Bu yordamı `Function` bir değer döndüren temsilci yordamı olarak bildirir.|  
|`name`|Gereklidir. Temsilci türünün adı; Standart değişken adlandırma kurallarını izler.|  
|`typeparamlist`|İsteğe bağlı. Bu temsilcinin tür parametrelerinin listesi. Birden çok tür parametresi virgülle ayrılır. İsteğe bağlı olarak, her tür parametresi `In` ve genel değiştiriciler kullanılarak değişken olarak bildirilemez `Out` . [Tür listesini](type-list.md) parantez içine almalısınız ve anahtar sözcüğü ile birlikte tanıtmalısınız `Of` .|  
|`parameterlist`|İsteğe bağlı. Çağrıldığında yordama geçirilen parametrelerin listesi. [Parametre listesini](parameter-list.md) parantez içine almalısınız.|  
|`type`|Bir yordam belirtirseniz gereklidir `Function` . Dönüş değerinin veri türü.|  
  
## <a name="remarks"></a>Açıklamalar  

 `Delegate`İfade, bir temsilci sınıfının parametresini ve dönüş türlerini tanımlar. Bu temsilci sınıfının bir örneğini oluşturmak için, eşleşen parametreleri ve dönüş türlerini içeren herhangi bir yordam kullanılabilir. Daha sonra yordam, temsilcinin yöntemi çağırarak temsilci örneği aracılığıyla çağrılabilir `Invoke` .  
  
 Temsilciler ad alanı, modül, sınıf veya yapı düzeyinde bildirilebilecek, ancak bir yordam içinde bildirilemez.  
  
 Her temsilci sınıfı, bir nesne yönteminin belirtimini geçen bir oluşturucuyu tanımlar. Bir temsilci oluşturucusuna bağımsız değişken bir yönteme veya bir lambda ifadesine başvuru olmalıdır.  
  
 Bir yönteme başvuru belirtmek için aşağıdaki sözdizimini kullanın:  
  
 `AddressOf` [`expression`.]`methodname`  
  
 ' In derleme zamanı türü, `expression` imzası temsilci sınıfının imzasıyla eşleşen belirtilen adda bir yöntemi içeren bir sınıfın veya arabirimin adı olmalıdır. , `methodname` Paylaşılan bir yöntem ya da bir örnek yöntemi olabilir. `methodname`Sınıfının varsayılan yöntemi için bir temsilci oluştursanız bile, bu isteğe bağlı değildir.  
  
 Bir lambda ifadesi belirtmek için aşağıdaki sözdizimini kullanın:  
  
 `Function` ([ `parm` As `type` , `parm2` as `type2` ,...]) `expression`  
  
 İşlevin imzası, temsilci türü ile aynı olmalıdır. Lambda ifadeleri hakkında daha fazla bilgi için bkz. [lambda ifadeleri](../../programming-guide/language-features/procedures/lambda-expressions.md).  
  
 Temsilciler hakkında daha fazla bilgi için bkz. [Temsilciler](../../programming-guide/language-features/delegates/index.md).  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, `Delegate` iki sayı üzerinde çalışan ve bir sayı döndüren bir temsilciyi bildirmek için bildirimini kullanır. `DelegateTest`Yöntemi bu tür bir temsilcinin örneğini alır ve sayı çiftleri üzerinde çalışmak için onu kullanır.  
  
 [!code-vb[VbVbalrDelegates#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#14)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [AddressOf İşleci](../operators/addressof-operator.md)
- [Durumunu](of-clause.md)
- [Temsilciler](../../programming-guide/language-features/delegates/index.md)
- [Nasıl yapılır: Genel Bir Sınıf Kullanma](../../programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [Visual Basic genel türler](../../programming-guide/language-features/data-types/generic-types.md)
- [Kovaryans ve değişken sapması](../../programming-guide/concepts/covariance-contravariance/index.md)
- [İçinde](../modifiers/in-generic-modifier.md)
- [Dışı](../modifiers/out-generic-modifier.md)

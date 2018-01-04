---
title: "CType İşlevi (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.CType
helpviewer_keywords:
- expression conversion results
- explicit data type conversions [Visual Basic]
- CType function
- conversions [Visual Basic], expression
ms.assetid: dd4b29e7-6fa1-428c-877e-69955420bb72
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d804ce75929592675068fdc434a1ba7429fa5373
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="ctype-function-visual-basic"></a>CType İşlevi (Visual Basic)
Belirtilen veri türü, nesne, yapısı, sınıf veya arabirim için açıkça bir ifade dönüştürmenin sonucunu döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
CType(expression, typename)  
```  
  
## <a name="parts"></a>Bölümler  
 `expression`  
 Herhangi bir geçerli ifade. Varsa değerini `expression` tarafından izin verilen aralığın dışında `typename`, Visual Basic bir özel durum oluşturur.  
  
 `typename`  
 Yasal içinde herhangi bir ifade bir `As` yan tümcesinde bir `Dim` deyimi, diğer bir deyişle, tüm veri türü, nesne, yapısı, sınıf veya arabirimi adı.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!TIP]
>  Tür dönüştürme gerçekleştirmek için aşağıdaki işlevler de kullanabilirsiniz:  
>   
>  -   Dönüşüm işlevleri gibi yazın `CByte`, `CDbl`, ve `CInt` belirli bir veri türüne dönüştürme gerçekleştirin. Daha fazla bilgi için bkz: [tür dönüştürme işlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md).  
> -   [DirectCast işleci](../../../visual-basic/language-reference/operators/directcast-operator.md) veya [TryCast işleci](../../../visual-basic/language-reference/operators/trycast-operator.md). Bu işleçlere bir tür devralınmalıdır veya diğer tür gerektirir. Değerinden biraz daha iyi performans sağlayabilirsiniz `CType` ve ondan dönüştürülürken `Object` veri türü.  
  
 `CType`dönüştürme kodu ifadeyi hesaplar kodun bir parçası olduğu anlamına gelir derlenmiş satır içi olur. Dönüştürme gerçekleştirmek için hiçbir yordam adlı çünkü bazı durumlarda, kodu daha hızlı çalışır.  
  
 Hiçbir dönüştürme tanımlanmış olması durumunda `expression` için `typename` (örneğin, `Integer` için `Date`), Visual Basic derleme zamanı hata iletisini görüntüler.  
  
 Çalışma zamanında bir dönüştürme başarısız olursa, uygun özel durum oluşur. Daraltma dönüştürme başarısız olursa, bir <xref:System.OverflowException> en yaygın sonucudur. Dönüştürme tanımsızsa bir <xref:System.InvalidCastException> içinde oluşturulur. Örneğin, bu durum `expression` türü `Object` ve çalışma zamanı türü için dönüştürme `typename`.  
  
 Veri türü `expression` veya `typename` bir sınıf ya da tanımladığınız, yapısı, tanımlayabilirsiniz `CType` sınıf veya yapı bir dönüşüm işleci olarak. Böylece `CType` gibi davranan bir *işleci aşırı*. Bunu yaparsanız, sınıf veya yapı atılabilen özel durumlar dahil olmak üzere, gelen ve dönüşümler davranışını kontrol edebilirsiniz.  
  
## <a name="overloading"></a>Aşırı Yükleme  
 `CType` İşleci ayrıca aşırı yüklenebilir bir sınıf veya kodunuzu dışında tanımlanmış yapısı. Kodunuz için veya böyle bir sınıf veya yapı dönüştürür, davranışını anladığınızdan emin olun, `CType` işleci. Daha fazla bilgi için bkz: [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="converting-dynamic-objects"></a>Dinamik nesneler dönüştürme  
 Tür dönüştürmeleri dinamik nesnelerin kullanan kullanıcı tanımlı dinamik dönüşümler tarafından gerçekleştirilen <xref:System.Dynamic.DynamicObject.TryConvert%2A> veya <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A> yöntemleri. Dinamik nesnelerle çalışıyorsanız kullanmak <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> dinamik Nesne dönüştürmek için yöntem.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır `CType` bir ifadeyi dönüştürmek için işlevi `Single` veri türü.  
  
 [!code-vb[VbVbalrFunctions#24](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/ctype-function_1.vb)]  
  
 Ek örnekler için bkz: [dolaylı ve açık dönüştürmeler](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.OverflowException>  
 <xref:System.InvalidCastException>  
 [Tür Dönüştürme İşlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Dönüştürme İşlevleri](../../../visual-basic/language-reference/functions/conversion-functions.md)  
 [Operator Deyimi](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Nasıl yapılır: Dönüştürme İşleci Tanımlama](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)  
 [.NET Framework'te tür dönüştürme](../../../standard/base-types/type-conversion.md)

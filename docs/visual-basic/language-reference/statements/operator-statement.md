---
title: Operator Deyimi
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.operator
helpviewer_keywords:
- operators [Visual Basic]
- procedures [Visual Basic], operator
- Narrowing keyword [Visual Basic], conversion operators
- Visual Basic code, operators
- Widening keyword [Visual Basic], conversion operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- overloaded operators [Visual Basic]
- operator overloading
- operator procedures
- Operator statement [Visual Basic]
- CType function [Visual Basic], Operator statement
ms.assetid: b12ec4af-1ad7-4a17-865b-c5ee96320ae5
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1b6be45fd0a606f43c14d57f3f8ae0955f256ba6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="operator-statement"></a>Operator Deyimi
İşleç simgesi, işlenen ve bir işleç yordamı tanımlayan bir sınıf veya yapı kodu bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
[ <attrlist> ] Public [ Overloads ] Shared [ Shadows ] [ Widening | Narrowing ]   
Operator operatorsymbol ( operand1 [, operand2 ]) [ As [ <attrlist> ] type ]  
    [ statements ]  
    [ statements ]  
    Return returnvalue  
    [ statements ]  
End Operator  
```  
  
## <a name="parts"></a>Bölümler  
 `attrlist`  
 İsteğe bağlı. Bkz: [öznitelik listesi](../../../visual-basic/language-reference/statements/attribute-list.md).  
  
 `Public`  
 Gerekli. Bu işleç yordamı sahip olduğunu gösterir [ortak](../../../visual-basic/language-reference/modifiers/public.md) erişim.  
  
 `Overloads`  
 İsteğe bağlı. Bkz: [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md).  
  
 `Shared`  
 Gerekli. Bu işleç yordamı olduğunu gösteren bir [paylaşılan](../../../visual-basic/language-reference/modifiers/shared.md) yordamı.  
  
 `Shadows`  
 İsteğe bağlı. Bkz: [gölgeleri](../../../visual-basic/language-reference/modifiers/shadows.md).  
  
 `Widening`  
 Belirtmediğiniz sürece bir dönüşüm işleci için gerekli `Narrowing`. Bu işleç yordamı tanımladığına gösteren bir [Widening](../../../visual-basic/language-reference/modifiers/widening.md) dönüştürme. "Genişletme ve daraltma dönüşümleri" Bu yardım sayfasına bakın.  
  
 `Narrowing`  
 Belirtmediğiniz sürece bir dönüşüm işleci için gerekli `Widening`. Bu işleç yordamı tanımladığına gösteren bir [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md) dönüştürme. "Genişletme ve daraltma dönüşümleri" Bu yardım sayfasına bakın.  
  
 `operatorsymbol`  
 Gerekli. Simge veya bu işleç yordamı tanımlar işleci tanıtıcısı.  
  
 `operand1`  
 Gerekli. Ad ve (bir dönüşüm işleci dahil) birli işleç tek işlenen ya da bir ikili işlecinin sol işleneni türü.  
  
 `operand2`  
 İkili işleçler için gereklidir. Ad ve sağ işleneni, ikili işleç türü.  
  
 `operand1`ve `operand2` aşağıdaki söz dizimini ve bölümleri vardır:  
  
 `[ ByVal ] operandname [ As operandtype ]`  
  
|Bölümü|Açıklama|  
|----------|-----------------|  
|`ByVal`|İsteğe bağlı, ancak geçirme mekanizması olmalıdır [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).|  
|`operandname`|Gerekli. Bu işlenen temsil eden değişkeninin adı. Bkz: [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`operandtype`|İsteğe bağlı sürece `Option Strict` olan `On`. Bu işlenen veri türü.|  
  
 `type`  
 İsteğe bağlı sürece `Option Strict` olan `On`. İşleç yordamı değerinin veri türü döndürür.  
  
 `statements`  
 İsteğe bağlı. İşleç yordamı çalışan ifadeler bloğu.  
  
 `returnvalue`  
 Gerekli. İşleç yordamı çağırma koda döndüren değer.  
  
 `End``Operator`  
 Gerekli. Bu işleç yordamı tanımı sonlandırır.  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanabileceğiniz `Operator` yalnızca bir sınıf veya yapı içinde. Yani *bildirimi bağlam* bir işleç bir kaynak dosya, ad alanı, modülü, arabirim, yordam veya blok olamaz. Daha fazla bilgi için bkz: [bildirim bağlamları ve varsayılan erişim düzeyleri](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Tüm işleçler olmalıdır `Public Shared`. Belirtemeyeceğiniz `ByRef`, `Optional`, veya `ParamArray` ya da işlenen için.  
  
 Dönüş değeri tutmak için işlecin veya tanımlayıcısı'nı kullanamazsınız. Kullanmalısınız `Return` deyimi ve onu bir değer belirtmelisiniz. Herhangi bir sayıda `Return` deyimleri yordamda herhangi bir yerinde görünebilir.  
  
 Bu şekilde bir işleci tanımlama çağrılır *İşleç aşırı yüklemesi*, kullandığınız olup olmadığına bakılmaksızın `Overloads` anahtar sözcüğü. Aşağıdaki tabloda, tanımlayabileceğiniz işleçleri listeler.  
  
|Tür|İşleçler|  
|----------|---------------|  
|Birli|`+`, `-`, `IsFalse`, `IsTrue`, `Not`|  
|İkili|`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`|  
|Dönüştürme (tekli)|`CType`|  
  
 Unutmayın `=` işlecidir ikili listesinde atama işleci karşılaştırma işleci.  
  
 Tanımladığınızda `CType`, ya da belirtmeniz gerekir `Widening` veya `Narrowing`.  
  
## <a name="matched-pairs"></a>Eşleşen çiftleri  
 Belirli işleçleri eşleşen çiftleri tanımlamanız gerekir. Bu tür bir çifti ya da işleç tanımlarsanız, diğeri de tanımlamanız gerekir. Eşleşen çiftleri şunlardır:  
  
-   `=`ve`<>`  
  
-   `>`ve`<`  
  
-   `>=`ve`<=`  
  
-   `IsTrue`ve`IsFalse`  
  
## <a name="data-type-restrictions"></a>Veri türü kısıtlamaları  
 Tanımladığınız her işleci üzerinde tanımladığınız sınıf veya yapı kapsaması gerekir. Bu sınıf veya yapı için aşağıdakilerin veri türü olarak görüntülenirler anlamına gelir:  
  
-   Birli işleç işlenen.  
  
-   En az biri ikili işlecinin işlenenleri.  
  
-   İşlenen veya bir dönüşüm işleci dönüş türü.  
  
 Belirli işleçleri ek veri kısıtlamaları gibi türü vardır:  
  
-   Tanımlarsanız `IsTrue` ve `IsFalse` işleçleri, bunların her ikisi de döndürmelidir `Boolean` türü.  
  
-   Tanımlarsanız `<<` ve `>>` işleçleri, bunların her ikisini de belirtmelisiniz `Integer` yazın `operandtype` , `operand2`.  
  
 Dönüş türü ya da işlenen türü için karşılık gelen gerekmez. Örneğin, bir karşılaştırma işleci gibi `=` veya `<>` döndürebilir `Boolean` hiçbiri işleneni olsa bile `Boolean`.  
  
## <a name="logical-and-bitwise-operators"></a>Mantıksal ve bit düzeyinde işleçler  
 `And`, `Or`, `Not`, Ve `Xor` işleçleri Visual Basic'de mantıksal ve bit düzeyinde işlemleri gerçekleştirebilir. Ancak, bu işleçlere birini bir sınıf veya yapı tanımlarsanız, yalnızca kendi Bitsel işlemi tanımlayabilirsiniz.  
  
 Tanımlayamazsınız `AndAlso` işleciyle doğrudan bir `Operator` deyimi. Ancak, kullanabileceğiniz `AndAlso` aşağıdaki koşullar karşılamış varsa:  
  
-   Tanımladığınız `And` için kullanmak istediğiniz aynı işlenen türlerinde `AndAlso`.  
  
-   Tanımınız `And` üzerinde tanımladığınız, sınıf veya yapı aynı türü döndürür.  
  
-   Tanımladığınız `IsFalse` üzerinde tanımladığınız sınıf veya yapı işlecinin `And`.  
  
 Benzer şekilde, kullanabileceğiniz `OrElse` tanımlanmış durumunda `Or` aynı işlenen üzerinde sınıf veya yapı ve dönüş türüyle tanımladığınız `IsTrue` sınıf veya yapı üzerinde.  
  
## <a name="widening-and-narrowing-conversions"></a>Genişletme ve Daraltma Dönüşümleri  
 A *dönüştürme genişletme* çalışma zamanında her zaman başarılı ancak bir *dönüştürme daraltma* çalışma zamanında başarısız olabilir. Daha fazla bilgi için bkz: [Widening ve daraltma dönüşümleri](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
 Bir dönüştürme yordamı olmasını bildirirseniz `Widening`, yordam kodunuzun hatalarını oluşturmalıdır değil. Aşağıdaki anlamına gelir:  
  
-   Her zaman türünde geçerli bir değer döndürmelidir `type`.  
  
-   Tüm olası özel durumları ve diğer hata durumlarını işlemelidir.  
  
-   Tüm hata döndürür çağırır yordamları işlemelidir.  
  
 Bir dönüştürme yordamı başarısız olabilir olasılığı yok veya onun işlenmeyen bir özel duruma neden olabilir, olmasını bildirmelidir `Narrowing`.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde `Operator` işleç yordamları için içeren bir yapı özetini tanımlamak için deyimi `And`, `Or`, `IsFalse`, ve `IsTrue` işleçler. `And`ve `Or` türünde iki işlenen herbiri `abc` ve dönüş türü `abc`. `IsFalse`ve `IsTrue` türü tek bir işlenen herbiri `abc` ve geri dönüp `Boolean`. Bu tanımları kullanılacak çağıran kodu izin `And`, `AndAlso`, `Or`, ve `OrElse` türündeki işlenenler ile `abc`.  
  
 [!code-vb[VbVbalrStatements#44](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/operator-statement_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IsFalse işleci](../../../visual-basic/language-reference/operators/isfalse-operator.md)  
 [IsTrue işleci](../../../visual-basic/language-reference/operators/istrue-operator.md)  
 [Genişletme](../../../visual-basic/language-reference/modifiers/widening.md)  
 [Daraltma](../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [Genişletme ve daraltma dönüşümleri](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [İşleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)  
 [Nasıl yapılır: bir işleci tanımlama](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [Nasıl yapılır: bir dönüşüm işleci tanımlama](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)  
 [Nasıl yapılır: bir işleç yordamı çağırma](../../../visual-basic/programming-guide/language-features/procedures/how-to-call-an-operator-procedure.md)  
 [Nasıl yapılır: işleçleri tanımlayan bir sınıf kullanma](../../../visual-basic/programming-guide/language-features/procedures/how-to-use-a-class-that-defines-operators.md)

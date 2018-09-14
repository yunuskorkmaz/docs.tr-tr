---
title: Operator deyimi (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 69dea99cf71bd1e091116e54e244abfca291ffdb
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45589449"
---
# <a name="operator-statement"></a>Operator Deyimi
Operatör sembolünü, işlenenleri ve bir sınıf ya da yapı üzerinde bir işleç yordamı tanımlayan kodu bildirir.  
  
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
 Gerekli. Bu işleç yordamı sahip olduğunu gösterir [genel](../../../visual-basic/language-reference/modifiers/public.md) erişim.  
  
 `Overloads`  
 İsteğe bağlı. Bkz: [aşırı](../../../visual-basic/language-reference/modifiers/overloads.md).  
  
 `Shared`  
 Gerekli. Bu işleç yordamı olduğunu belirten bir [paylaşılan](../../../visual-basic/language-reference/modifiers/shared.md) yordamı.  
  
 `Shadows`  
 İsteğe bağlı. Bkz: [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).  
  
 `Widening`  
 Siz belirtmediğiniz sürece, bir dönüştürme işleci için gerekli `Narrowing`. Bu işleç yordamı tanımlayan gösteren bir [Widening](../../../visual-basic/language-reference/modifiers/widening.md) dönüştürme. "Genişletme ve daraltma dönüştürmeleri" Bu Yardım sayfasında bakın.  
  
 `Narrowing`  
 Siz belirtmediğiniz sürece, bir dönüştürme işleci için gerekli `Widening`. Bu işleç yordamı tanımlayan gösteren bir [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md) dönüştürme. "Genişletme ve daraltma dönüştürmeleri" Bu Yardım sayfasında bakın.  
  
 `operatorsymbol`  
 Gerekli. Simge veya bu işleç yordamı tanımlar işlecin tanımlayıcısı.  
  
 `operand1`  
 Gerekli. Adı ve tek bir işlenen (dönüştürme işleci dahil) birli işleç veya sol işleneni, ikili işleç türü.  
  
 `operand2`  
 İkili işleçler için gereklidir. Bir ikili işlecinin sağ işleneninin türü ve adı.  
  
 `operand1` ve `operand2` aşağıdaki söz dizimini ve bölümleri vardır:  
  
 `[ ByVal ] operandname [ As operandtype ]`  
  
|Bölümü|Açıklama|  
|----------|-----------------|  
|`ByVal`|İsteğe bağlı, ancak geçirme mekanizması olmalıdır [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).|  
|`operandname`|Gerekli. Bu işlenen temsil eden değişkenin adı. Bkz: [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`operandtype`|İsteğe bağlı sürece `Option Strict` olduğu `On`. Bu işlenen veri türü.|  
  
 `type`  
 İsteğe bağlı sürece `Option Strict` olduğu `On`. İşleç yordamı değerinin veri türü döndürür.  
  
 `statements`  
 İsteğe bağlı. İşleç yordamı çalıştıran bir deyimler bloğunu.  
  
 `returnvalue`  
 Gerekli. İşleç yordamı çağırma koda döndürür. değer.  
  
 `End``Operator`  
 Gerekli. Bu işleç yordamı tanımını sonlandırır.  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanabileceğiniz `Operator` yalnızca bir sınıf veya yapı içinde. Başka bir deyişle *bildirim içeriğinin* operatörün bir kaynak dosyası, ad alanı, modülü, arabirim, yordam veya blok olamayacağı için. Daha fazla bilgi için [bildirim bağlamları ve varsayılan erişim düzeyleri](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Tüm işleçler olmalıdır `Public Shared`. Belirtemezsiniz `ByRef`, `Optional`, veya `ParamArray` iki işlenenden için.  
  
 Dönüş değerini tutmak için işlecin veya tanımlayıcısı'nı kullanamazsınız. Kullanmalısınız `Return` ifadesi ve bir değer belirtmeniz gerekir. Herhangi bir sayıda `Return` deyimleri yordamda herhangi bir yerinde görünebilir.  
  
 Bu şekilde bir işleci tanımlama çağrılır *İşleç aşırı yüklemesi*, kullandığınız olup olmadığını `Overloads` anahtar sözcüğü. Aşağıdaki tabloda, tanımlayabileceğiniz işleçleri listelenmektedir.  
  
|Tür|İşleçler|  
|----------|---------------|  
|Birli|`+`, `-`, `IsFalse`, `IsTrue`, `Not`|  
|İkili|`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`|  
|Dönüştürme (tekli)|`CType`|  
  
 Unutmayın `=` işlecidir ikili listesinde karşılaştırma işleci atama işleci.  
  
 Tanımladığınızda `CType`, belirtmeli `Widening` veya `Narrowing`.  
  
## <a name="matched-pairs"></a>Eşleşen çiftleri  
 Belirli işleçleri eşleşen çiftleri tanımlamanız gerekir. Böyle bir çifti ya da işleç tanımlarsanız, diğeri de tanımlamanız gerekir. Eşleşen çiftleri şunlardır:  
  
-   `=` ve `<>`  
  
-   `>` ve `<`  
  
-   `>=` ve `<=`  
  
-   `IsTrue` ve `IsFalse`  
  
## <a name="data-type-restrictions"></a>Veri türü kısıtlamaları  
 Tanımladığınız her işleci üzerinde tanımladığınız sınıf veya yapı kapsaması gerekir. Başka bir deyişle, sınıf veya yapı aşağıdaki veri türünde yer almalıdır:  
  
-   Birli işleç işleneni.  
  
-   En az bir ikili işlecinin işlenenleri.  
  
-   İşlenen veya bir dönüştürme işlecinin dönüş türü.  
  
 Belirli operatörün ek veri kısıtlamaları, aşağıdaki gibi yazın:  
  
-   Tanımlarsanız `IsTrue` ve `IsFalse` işleçleri, bunların her ikisi de döndürmelidir `Boolean` türü.  
  
-   Tanımlarsanız `<<` ve `>>` işleçleri, bunların her ikisini de belirtmelisiniz `Integer` yazın `operandtype` , `operand2`.  
  
 İki işlenenden türüne karşılık gelen dönüş türü yok. Örneğin, bir karşılaştırma işleci gibi `=` veya `<>` döndürebilir `Boolean` iki işlenenin olsa bile `Boolean`.  
  
## <a name="logical-and-bitwise-operators"></a>Mantıksal ve bit düzeyinde işleçler  
 `And`, `Or`, `Not`, Ve `Xor` işleçleri Visual Basic'de mantıksal ve bit düzeyinde işlemleri gerçekleştirebilir. Ancak, bu işleçler birini bir sınıf veya yapı tanımlarsanız, yalnızca, bit düzeyinde işlem tanımlayabilirsiniz.  
  
 Tanımlanamaz `AndAlso` işleci ile doğrudan bir `Operator` deyimi. Ancak, kullanabileceğiniz `AndAlso` aşağıdaki koşulların yerine getirilmesini varsa:  
  
-   Tanımladığınız `And` için kullanmak istediğiniz aynı işlenen türlerinde `AndAlso`.  
  
-   Tanımınız `And` üzerinde tanımladığınız, sınıf veya yapı aynı türü döndürür.  
  
-   Tanımladığınız `IsFalse` üzerinde tanımladığınız sınıf ya da yapı üzerinde operatör `And`.  
  
 Benzer şekilde, kullanabileceğiniz `OrElse` tanımladıysanız, `Or` sınıf veya yapı ve size dönüş türüyle aynı işlenenlerde tanımladığınız `IsTrue` sınıf veya yapı.  
  
## <a name="widening-and-narrowing-conversions"></a>Genişletme ve Daraltma Dönüşümleri  
 A *dönüştürme genişletme* çalışma zamanında, her zaman başarılı ancak bir *daraltma dönüştürmesi* çalışma zamanında başarısız olabilir. Daha fazla bilgi için [Widening ve daraltma dönüşümleri](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
 Bir dönüştürme yordamı olmasını bildirirseniz `Widening`, yordam kodunuzun hatalarını oluşturmamanız gerekir. Aşağıdaki anlamına gelir:  
  
-   Her zaman geçerli bir değer türü döndürmelidir `type`.  
  
-   Tüm olası özel durumları ve diğer hata durumlarını işlemelidir.  
  
-   Bu çağrı yaptığı tüm yordamları bir hata döndürür işlemesi gerekir.  
  
 Bir dönüştürme yordamı başarısız olabilir bir olasılık yoktur veya onun işlenmeyen bir özel durum neden olabilir, olmasını bildirmelidir `Narrowing`.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde `Operator` deyimi için işleç yordamları içeren bir yapının ana hatlarını tanımlayacak `And`, `Or`, `IsFalse`, ve `IsTrue` işleçleri. `And` ve `Or` her iki işleneni de türü ele `abc` ve dönüş türü `abc`. `IsFalse` ve `IsTrue` türünde tek bir işlenen herbiri `abc` ve dönüş `Boolean`. Çağıran kod kullanmak bu tanımları izin `And`, `AndAlso`, `Or`, ve `OrElse` türündeki işlenenler ile `abc`.  
  
 [!code-vb[VbVbalrStatements#44](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/operator-statement_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IsFalse İşleci](../../../visual-basic/language-reference/operators/isfalse-operator.md)  
 [IsTrue İşleci](../../../visual-basic/language-reference/operators/istrue-operator.md)  
 [Widening](../../../visual-basic/language-reference/modifiers/widening.md)  
 [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [Genişletme ve Daraltma Dönüştürmeleri](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [İşleç Yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)  
 [Nasıl yapılır: İşleç Tanımlama](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [Nasıl yapılır: Dönüştürme İşleci Tanımlama](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)  
 [Nasıl yapılır: Bir İşleç Yordamı Çağırma](../../../visual-basic/programming-guide/language-features/procedures/how-to-call-an-operator-procedure.md)  
 [Nasıl yapılır: İşleçleri Tanımlayan Bir Sınıf Kullanma](../../../visual-basic/programming-guide/language-features/procedures/how-to-use-a-class-that-defines-operators.md)

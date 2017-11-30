---
title: "Visual Basic'de Değişken Bildirimi"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], declaring
- member variables [Visual Basic], declarations
- Dim statement [Visual Basic], variable declaration
- declaring variables [Visual Basic]
- variables [Visual Basic], scope
- variables [Visual Basic], data types
- data types [Visual Basic], variable declarations
- lifetime [Visual Basic], variables
- variables [Visual Basic], lifetime
- access levels [Visual Basic], variables
- scope [Visual Basic], declaration statements
- variables [Visual Basic], access level
- local variables [Visual Basic], declarations
- scope [Visual Basic], variables
ms.assetid: d8f10226-92b1-480f-9f53-df377b2d7e15
caps.latest.revision: "31"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7f7b924aed1da7db816aa5c11239e301428770b7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="variable-declaration-in-visual-basic"></a>Visual Basic'de Değişken Bildirimi
Ad ve özelliklerini belirtmek için bir değişken bildirin. Değişken bildirimi deyimi [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md). Konumuna ve içeriği değişkenin özellikleri belirler.  
  
 Değişken adlandırma kuralları ve hususlar için bkz: [bildirilen öğe adları](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
## <a name="declaration-levels"></a>Bildirim düzeyleri  
  
### <a name="local-and-member-variables"></a>Yerel ve üye değişkenleri  
 A *yerel değişken* bir yordam içinde bildirilen biridir. A *üye değişkeni* üyesi olan bir [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] yazın; sınıf, yapı veya modül içinde ancak bu sınıf, yapı veya modülü iç herhangi bir yordam içinde değil modülü düzeyinde bildirilmedi.  
  
### <a name="shared-and-instance-variables"></a>Paylaşılan ve örnek değişkenleri  
 Sınıf veya yapı olsun veya olmasın, paylaşılan üzerinde bir üye değişkenine kategorisini bağlıdır. İle bildirilirse [paylaşılan](../../../../visual-basic/language-reference/modifiers/shared.md) olmasından anahtar sözcüğü bir *paylaşılan değişken*, ve sınıf veya yapı tüm örnekleri arasında paylaşılan tek bir kopya bulunmaktadır.  
  
 Aksi durumda olduğu bir *örnek değişkeni*, ve sınıf veya yapı her örneği için ayrı bir kopyası oluşturulur. Belirli bir örnek değişkeni kopyasını yalnızca örneği sınıf veya yapı içinde oluşturulduğu için kullanılabilir. Diğer örneklerini sınıf veya yapı örnek değişkeninde bir kopyasını bağımsızdır.  
  
## <a name="declaring-data-type"></a>Veri türü bildirme  
 [Olarak](../../../../visual-basic/language-reference/statements/as-clause.md) bildirim deyiminin yan tümcesinde veri türü veya nesne türü bildirme değişkenin tanımlamanıza izin verir. Şu türler için bir değişken belirtebilirsiniz:  
  
-   Başlangıç veri türü, gibi `Boolean`, `Long`, veya`Decimal`  
  
-   Bir dizi ya da yapısı gibi bir bileşik veri türü  
  
-   Bir nesne türü ya da uygulamanızı veya başka bir uygulama tanımlı sınıfı  
  
-   A [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] gibi sınıfı <xref:System.Windows.Forms.Label> veya<xref:System.Windows.Forms.TextBox>  
  
-   Arabirim türü, gibi <xref:System.IComparable> veya<xref:System.IDisposable>  
  
 Veri türü yinelemek zorunda kalmadan bir deyim birkaç değişkenleri bildirebilirsiniz. Değişkenleri aşağıdaki deyimlerinde `i`, `j`, ve `k` türü olarak bildirilmiş `Integer`, `l` ve `m` olarak `Long`, ve `x` ve `y` olarak`Single`:  
  
```  
Dim i, j, k As Integer  
' All three variables in the preceding statement are declared as Integer.  
Dim l, m As Long, x, y As Single  
' In the preceding statement, l and m are Long, x and y are Single.  
```  
  
 Veri türleri hakkında daha fazla bilgi için bkz: [veri türleri](../../../../visual-basic/programming-guide/language-features/data-types/index.md). Nesneleri hakkında daha fazla bilgi için bkz: [nesneler ve sınıflar](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) ve [bileşenlerle programlama](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3).  
  
## <a name="local-type-inference"></a>Yerel Tür Arabirimi  
 *Tür çıkarımı* olmadan bildirilen yerel değişkenleri veri türlerini belirlemek için kullanılan bir `As` yan tümcesi. Derleyici başlatma ifade türü değişkeninden türü oluşturur. Bu, açıkça bir türü bildirmeden değişkenleri bildirin olanak sağlar. Aşağıdaki örnekte, her ikisi de `num1` ve `num2` tamsayı olarak kesin türü belirtilmiş.  
  
 [!code-vb[VbVbalrTypeInference#1](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/variable-declaration_1.vb)]  
  
 Yerel türü çıkarımı kullanmak istiyorsanız, `Option Infer` ayarlanmalıdır `On`. Daha fazla bilgi için bkz: [yerel türü çıkarımı](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) ve [Option Infer deyimi](../../../../visual-basic/language-reference/statements/option-infer-statement.md).  
  
## <a name="characteristics-of-declared-variables"></a>Bildirilen değişkenlerin özellikleri  
 *Ömrü* bir değişken süre hangi BT sırasında kullanılmak üzere kullanılabilir. Genel olarak, (yordamı veya sınıfı gibi) bildirir öğesi var olmaya devam eder sürece bir değişken mevcut. Değişkenini içeren öğe ömür varolan devam gerekmez, bildiriminde özel bir şey yapmanız gerekmez. Değişkenini içeren kendi öğesinin daha uzun var olmaya devam gerekiyorsa içerebilir `Static` veya `Shared` anahtar sözcük, `Dim` deyimi. Daha fazla bilgi için bkz: [Visual Basic'de ömür](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md).  
  
 *Kapsam* bir değişken adı niteleme olmadan başvurduğu tüm kod kümesidir. Bir değişkenin kapsamını burada bildirilmeden tarafından belirlenir. Belirli bir bölgede bulunan koduna adlarını nitelemek gerek kalmadan bu bölgede tanımlanan değişkenler kullanabilirsiniz. Daha fazla bilgi için bkz: [Visual Basic'de kapsam](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).  
  
 Bir değişkenin *erişim düzeyine* erişmek için izne sahip code uzantı'dır. Bu erişim değiştiricisi tarafından belirlenir (gibi [ortak](../../../../visual-basic/language-reference/modifiers/public.md) veya [özel](../../../../visual-basic/language-reference/modifiers/private.md)) kullandığınız `Dim` deyimi. Daha fazla bilgi için bkz: [erişim düzeyini Visual Basic'te](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: yeni değişken oluşturma](../../../../visual-basic/programming-guide/language-features/variables/how-to-create-a-new-variable.md)  
 [Nasıl yapılır: içine ve dışına bir değişken veri taşıma](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md)  
 [Veri türleri](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Korumalı](../../../../visual-basic/language-reference/modifiers/protected.md)  
 [Arkadaş](../../../../visual-basic/language-reference/modifiers/friend.md)  
 [Statik](../../../../visual-basic/language-reference/modifiers/static.md)  
 [Bildirilen öğe özellikleri](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [Yerel tür çıkarımı](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Option Infer deyimi](../../../../visual-basic/language-reference/statements/option-infer-statement.md)

---
title: Module Deyimi
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- Module
- vb.Module
helpviewer_keywords:
- modules, classes
- modules
- Module statement [Visual Basic]
- modules, declaring
- standard modules
- classes [Visual Basic], vs. modules
- declarations [Visual Basic], modules
ms.assetid: a1243afc-14a5-45df-95d5-51118aeac362
caps.latest.revision: 24
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 51f8fd063449c072a69cdffd9f6ce2a96cc3f68c
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="module-statement"></a>Module Deyimi
Bir modül adını bildirir ve tanımını değişkenleri, özellikleri, olayları ve modülü oluşur yordamları sunar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb 
[ <attributelist> ] [ accessmodifier ]  Module name  
    [ statements ]  
End Module  
```  
  
## <a name="parts"></a>Bölümler  
 `attributelist`  
 İsteğe bağlı. Bkz: [öznitelik listesi](../../../visual-basic/language-reference/statements/attribute-list.md).  
  
 `accessmodifier`  
 İsteğe bağlı. Aşağıdakilerden biri olabilir:  
  
-   [Public](../../../visual-basic/language-reference/modifiers/public.md)  
  
-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
 Bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 `name`  
 Gerekli. Bu modül adı. Bkz: [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
 `statements`  
 İsteğe bağlı. Değişkenleri, özellikleri, olayları, yordamlar ve bu modülün iç içe geçmiş türler tanımlamak deyimleri.  
  
 `End Module`  
 Sonlandırır `Module` tanımı.  
  
## <a name="remarks"></a>Açıklamalar  
 A `Module` deyimi, ad alanı bir başvuru türü tanımlar. A *Modülü* (bazen adlı bir *standart modül*) benzer bir sınıf, ancak bazı önemli farklılıklar. Her modül tam olarak bir örnek var ve oluşturulamaz veya bir değişkenine atanan gerekmez. Modülleri devralma desteklemez veya arabirimlerini. Bir modül bildirimi bir *türü* bir sınıf veya yapı herkese açık — bir modül veri türüne sahip bir programlama öğesi bildiremezsiniz.  
  
 Kullanabileceğiniz `Module` yalnızca ad alanı düzeyinde. Yani *bildirimi bağlam* bir modül kaynak dosya veya ad alanı olmalı ve bir sınıf, yapı, modülü, arabirimi, yordamı veya blok olamaz. Bir modül herhangi bir tür veya başka bir modül içinde iç içe yerleştirilemez. Daha fazla bilgi için bkz: [bildirim bağlamları ve varsayılan erişim düzeyleri](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Bir modül programınız olarak aynı yaşam süresi vardır. Üyeleri tüm olduğundan `Shared`, ayrıca sahip oldukları yaşam süreleri, program eşit.  
  
 Modülleri varsayılan [arkadaş](../../../visual-basic/language-reference/modifiers/friend.md) erişim. Erişim değiştiricileri ile erişim düzeylerine göre ayarlayabilirsiniz. Daha fazla bilgi için bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 Örtük olarak bir modül tüm üyeleri olan `Shared`.  
  
## <a name="classes-and-modules"></a>Sınıfları ve modülleri  
 Benzer şekilde bu öğelere sahip, ancak de önemli bazı farklar vardır.  
  
-   **Terminolojisi.** Visual Basic önceki sürümlerini tanıması modülleri iki tür: *sınıf modülleri* (.cls dosyaları) ve *Standart modüller* (.bas dosyaları). Bunlar geçerli sürümü çağırır *sınıfları* ve *modülleri*sırasıyla.  
  
-   **Paylaşılan üyeler.** Bir sınıf üyesi paylaşılan olup veya örnek üyesine kontrol edebilirsiniz.  
  
-   **Nesne yönü.** Nesne odaklı sınıfları, ancak modüller değildir. Bu nedenle yalnızca sınıfları nesneler olarak oluşturulabilir. Daha fazla bilgi için bkz: [nesneler ve sınıflar](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).  
  
## <a name="rules"></a>Kurallar  
  
-   **Değiştirici.** Tüm modül örtük olarak üyeleridir [paylaşılan](../../../visual-basic/language-reference/modifiers/shared.md). Kullanamazsınız `Shared` bildirme üyesi ve herhangi bir üyenin paylaşılan durum değiştirilemiyor, anahtar sözcük.  
  
-   **Devralma.** Bir modül herhangi bir türünden dışında devral olamaz <xref:System.Object>, tüm modüllerine devralır. Özellikle, bir modül başka bir devralma olamaz.  
  
     Kullanamazsınız [Inherits deyimi](../../../visual-basic/language-reference/statements/inherits-statement.md) belirtmek için bir modül tanımında bile <xref:System.Object>.  
  
-   **Varsayılan özellik.** Bir modüldeki herhangi bir varsayılan özellik tanımlayamazsınız. Daha fazla bilgi için bkz: [varsayılan](../../../visual-basic/language-reference/modifiers/default.md).  
  
## <a name="behavior"></a>Davranış  
  
-   **Erişim düzeyi.** Bir modül her üye kendi erişim düzeyi ile bildirebilir. Modül üyeleri için varsayılan değer [ortak](../../../visual-basic/language-reference/modifiers/public.md) erişim, değişkenleri ve sabitleri dışında varsayılan [özel](../../../visual-basic/language-reference/modifiers/private.md) erişim. Bir modül daha üyeleri birden sınırlı erişimi Belirtilen modül erişim düzeyi önceliklidir.  
  
-   **Kapsamı.** Kendi ad boyunca kapsamdaki bir modüldür.  
  
     Her modül üye kapsamını tüm modülüdür. Tüm üyeler uygulanabilecek bildirimi *yazın yükseltme*, kapsamlarına modülü içeren ad alanına yükseltilmesi neden olur. Daha fazla bilgi için bkz: [tür yükseltme](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).  
  
-   **Niteliğe.** Bir projede birden fazla modülü sahip olabilir ve iki veya daha fazla modüllerinde aynı ada sahip üye bildirebilirsiniz. Ancak, başvuru dışında bu modül ise böyle bir üyesi uygun modül adı ile herhangi bir referans nitelemeniz gerekir. Daha fazla bilgi için bkz: [bildirilmiş öğelere başvurular](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
## <a name="example"></a>Örnek  
 [!code-vb[VbVbalrStatements#69](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/module-statement_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Class Deyimi](../../../visual-basic/language-reference/statements/class-statement.md)  
 [Namespace Deyimi](../../../visual-basic/language-reference/statements/namespace-statement.md)  
 [Structure Deyimi](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Interface Deyimi](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Tür Yükseltme](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)

---
title: "Tür Yükseltme (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- declared elements [Visual Basic], scope
- visibility [Visual Basic], declared elements
- Partial keyword [Visual Basic], unexpected results with type promotion
- scope [Visual Basic], declared elements
- scope [Visual Basic], Visual Basic
- type promotion
- declared elements [Visual Basic], visibility
ms.assetid: 035eeb15-e4c5-4288-ab3c-6bd5d22f7051
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f3a55c023afe7afe96f862f0b3cbbdb03a15b902
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="type-promotion-visual-basic"></a>Tür Yükseltme (Visual Basic)
Bir modül programlama öğesinde bildirirken [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kapsamı modülü içeren ad alanına yükseltir. Bu olarak bilinir *yazın yükseltme*.  
  
 Aşağıdaki örnek, bir modül iskelet tanımının ve bu modül iki üyeleri gösterir.  
  
 [!code-vb[VbVbalrDeclaredElements#1](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_1.vb)]  
  
 İçinde `projModule`, programlama Modül düzeyinde bildirilen öğeler için yükseltilen `projNamespace`. Önceki örnekte, `basicEnum` ve `innerClass` öne, ancak `numberSub` Modül düzeyinde bildirilmediğinden değildir.  
  
## <a name="effect-of-type-promotion"></a>Tür promosyonu etkisi  
 Tür promosyonu etkisini niteliğe dize modül adını içermesi gerekmez ' dir. Aşağıdaki örnekte iki yordam önceki örnekte çağrılar.  
  
 [!code-vb[VbVbalrDeclaredElements#2](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_2.vb)]  
  
 Önceki örnekte, ilk çağrıda tam nitelenmiş dizelerini kullanır. Ancak, bu tür yükseltme nedeniyle gerekli değildir. İkinci çağrı da erişir modülün üyeleri dahil etmeden `projModule` niteliğe dizelerde.  
  
## <a name="defeat-of-type-promotion"></a>Tür promosyonu zorluğunu  
 Tür promosyonu ad alanı aynı ada sahip bir üye modülü üyesi olarak zaten varsa, bu modülü üyenin engellenmediğinden. Aşağıdaki örnek, bir numaralandırma ve aynı ad alanı içindeki bir modül iskelet tanımını gösterir.  
  
 [!code-vb[VbVbalrDeclaredElements#3](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_3.vb)]  
  
 Önceki örnekte [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] sınıfı yükseltemezsiniz `abc` için `thisNameSpace` zaten bir numaralandırma ad alanı düzeyinde aynı ada sahip olduğundan. Erişim için `abcSub`, tam nitelenmiş dize kullanmalısınız `thisNamespace.thisModule.abc.abcSub`. Ancak, sınıf `xyz` hala yükseltilir ve dosyaya erişebildiğinizi `xyzSub` kısa niteliğe dizesiyle `thisNamespace.xyz.xyzSub`.  
  
### <a name="defeat-of-type-promotion-for-partial-types"></a>Tür promosyonu kısmi türler için zorluğunu  
 Bir sınıf veya yapı bir modül içinde kullanıyorsa [kısmi](../../../../visual-basic/language-reference/modifiers/partial.md) anahtar sözcüğü, tür yükseltme Bu sınıf veya yapı, için otomatik olarak engellenmediğinden aynı ada sahip bir üye ad alanına sahip olup olmadığına bakılmaksızın. Modülü diğer öğeleri için tür yükseltme hala uygundur.  
  
 **Sonuçları.** Tür promosyonu kısmi tanımının zorluğunu beklenmeyen sonuçlara ve hatta derleyici hataları neden olabilir. Aşağıdaki örnekte, biri olan bir modül içinde bir sınıfın iskelet kısmi tanımlarını gösterir.  
  
 [!code-vb[VbVbalrDeclaredElements#4](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_4.vb)]  
  
 Önceki örnekte, iki kısmi tanımlarını birleştirmek için derleyici Geliştirici bekleyebilirsiniz `sampleClass`. Ancak, derleyici kısmi tanımının içinde yükseltme dikkate almaz `sampleModule`. Sonuç olarak, iki farklı ve ayrıdır sınıf derlemeye çalışır, her ikisi de adlı `sampleClass` ancak farklı nitelik yolları.  
  
 Yalnızca tam yollarına aynı zaman derleyici kısmi tanımları birleştirir.  
  
## <a name="recommendations"></a>Önerileri  
 Aşağıdaki öneriler iyi bir programlama uygulama temsil eder.  
  
-   **Benzersiz adlar.** Programlama öğelerine adlandırma üzerinde tam denetime sahip olduğunuzda, her zaman benzersiz adlar her yerde kullanmak iyi bir fikir değil. Aynı ek niteliğe gerektirir ve kodunuzu okumak daha zor hale getirebilir. Bunlar ayrıca Zarif hataları ve beklenmeyen sonuçlara yol açabilir.  
  
-   **Tam nitelenmiş.** Modüller ve diğer öğeleri aynı ad ile çalışırken, güvenli bir yaklaşım her zaman tam nitelenmiş için tüm programlama öğeleri kullanmaktır. Tür promosyonu modülü üyesi için engellenmediğinden ise ve tam olarak bu üyede uygun değil, farklı bir programlama öğesi yanlışlıkla erişebilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Module deyimi](../../../../visual-basic/language-reference/statements/module-statement.md)  
 [Namespace deyimi](../../../../visual-basic/language-reference/statements/namespace-statement.md)  
 [Kısmi](../../../../visual-basic/language-reference/modifiers/partial.md)  
 [Visual Basic'de kapsam](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)  
 [Nasıl yapılır: bir değişkenin kapsamını denetleme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)  
 [Bildirilmiş öğelere başvurular](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)

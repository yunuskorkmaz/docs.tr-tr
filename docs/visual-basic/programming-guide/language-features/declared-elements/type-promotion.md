---
title: Tür Yükseltme (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic], scope
- visibility [Visual Basic], declared elements
- Partial keyword [Visual Basic], unexpected results with type promotion
- scope [Visual Basic], declared elements
- scope [Visual Basic], Visual Basic
- type promotion
- declared elements [Visual Basic], visibility
ms.assetid: 035eeb15-e4c5-4288-ab3c-6bd5d22f7051
ms.openlocfilehash: f7ac6bfb944da8bd50e035ba97b2b513176dc661
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61973309"
---
# <a name="type-promotion-visual-basic"></a>Tür Yükseltme (Visual Basic)
Modül içindeki bir programlama öğesi bildirdiğinizde, Visual Basic modülü içeren ad alanı kapsamında yükseltir. Bu olarak bilinir *türü promosyon*.  
  
 Aşağıdaki örnek, bir modül iskelet tanımını ve bu modül iki üyeleri gösterir.  
  
 [!code-vb[VbVbalrDeclaredElements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#1)]  
  
 İçinde `projModule`, programlama Modül düzeyinde bildirilen öğeler için yükseltilen `projNamespace`. Önceki örnekte `basicEnum` ve `innerClass` yükseltilir, ancak `numberSub` Modül düzeyinde bildirilmediğinden değildir.  
  
## <a name="effect-of-type-promotion"></a>Tür promosyonu etkisi  
 Tür promosyonu etkisini nitelik dize modül adını içerecek şekilde gerekmeyen ' dir. Aşağıdaki örnek önceki örnekte iki yordam çağrıları yapar.  
  
 [!code-vb[VbVbalrDeclaredElements#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#2)]  
  
 Önceki örnekte, ilk çağrı, tam nitelenmiş dizeleri kullanır. Ancak, bu tür yükseltme nedeniyle gerekli değildir. İkinci çağrı da erişir modülün üyeleri dahil etmeden `projModule` nitelik Dizelerdeki.  
  
## <a name="defeat-of-type-promotion"></a>Tür yükseltme zorluğunu  
 Tür yükseltme, ad alanı aynı ada sahip bir üye modülü üye olarak zaten varsa, bu modül üyenin engellenmediğinden. Aşağıdaki örnek, bir numaralandırma ve aynı ad alanı içinde bir modül bir çatı tanımı gösterilmektedir.  
  
 [!code-vb[VbVbalrDeclaredElements#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#3)]  
  
 Önceki örnekte, Visual Basic sınıf düzeyine yükseltilemiyor `abc` için `thisNameSpace` zaten var olduğundan ad alanı düzeyinde aynı ada sahip bir sabit listesi. Erişim için `abcSub`, tam nitelenmiş dize kullanmalısınız `thisNamespace.thisModule.abc.abcSub`. Ancak, sınıf `xyz` hala yükseltilir ve erişebileceğiniz `xyzSub` kısa nitelik dize ile `thisNamespace.xyz.xyzSub`.  
  
### <a name="defeat-of-type-promotion-for-partial-types"></a>Kısmi türler için tür yükseltme zorluğunu  
 Bir sınıf veya yapı içinde bir modül kullanıyorsa [kısmi](../../../../visual-basic/language-reference/modifiers/partial.md) anahtar sözcüğü, tür yükseltme, bu sınıf veya yapı için otomatik olarak engellenmediğinden aynı ada sahip bir üye ad alanına sahip olup olmadığını. Diğer öğeleri modüldeki tür yükseltme için yine de uygundur.  
  
 **Sonuçları.** Tür promosyonu kısmi tanımı, zorluğunu, beklenmeyen sonuçlar ve hatta derleyici hataları neden olabilir. Aşağıdaki örnek, bir sınıfın biri içinde bir modül olan iskelet kısmi tanımları gösterir.  
  
 [!code-vb[VbVbalrDeclaredElements#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#4)]  
  
 Önceki örnekte, geliştiricinin iki kısmi tanımlarını birleştirmek için derleyici beklenebilir `sampleClass`. Ancak, derleyici kısmi tanım içinde promosyon düşünmez `sampleModule`. Sonuç olarak, iki ayrı ve farklı sınıflar derlemek çalışır, hem adlandırılmış `sampleClass` ancak farklı nitelik yolları.  
  
 Yalnızca tam yollarının aynı olduğunda derleyici kısmi tanımları birleştirir.  
  
## <a name="recommendations"></a>Öneriler  
 Aşağıdaki öneriler, iyi bir programlama uygulama temsil eder.  
  
- **Benzersiz adları.** Programlama öğelerine adlandırma üzerinde tam denetime sahiptir, bu her zaman her yerde benzersiz adlar kullanacak şekilde iyi bir fikirdir. Aynı adlara ek onay gerektirir ve kodunuzun okunmasını zorlaştırabilir. Bunlar ayrıca ince hatalar ve beklenmeyen sonuçlara yol açabilir.  
  
- **Tam nitelenmiş.** Modüller ve diğer öğeleri aynı ad ile çalışırken, güvenli bir yaklaşım her zaman tam nitelenmiş için tüm programlama öğeleri kullanmaktır. Tür promosyonu modülü üyesi engellenmediğinden ve tam olarak bu üyede nitelendirmeyin, yanlışlıkla farklı bir programlama öğesine erişebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Module Deyimi](../../../../visual-basic/language-reference/statements/module-statement.md)
- [Namespace Deyimi](../../../../visual-basic/language-reference/statements/namespace-statement.md)
- [Partial](../../../../visual-basic/language-reference/modifiers/partial.md)
- [Visual Basic'de kapsam](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [Nasıl yapılır: Bir değişkenin kapsamını denetleme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)
- [Bildirilmiş Öğelere Başvurular](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)

---
title: Tür Yükseltme
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
ms.openlocfilehash: 6c28ca22e96616ff09e147400bfdb2adb922ff0e
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085808"
---
# <a name="type-promotion-visual-basic"></a>Tür Yükseltme (Visual Basic)

Bir modülde programlama öğesi bildirdiğinizde Visual Basic kapsamını modülünü içeren ad alanına yükseltir. Bu, *tür yükseltmesi*olarak bilinir.  
  
 Aşağıdaki örnek, bir modülün iskelet tanımını ve bu modülün iki üyesini gösterir.  
  
 [!code-vb[VbVbalrDeclaredElements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#1)]  
  
 İçinde `projModule` , modül düzeyinde belirtilen programlama öğeleri ' e yükseltilir `projNamespace` . Önceki örnekte `basicEnum` ve `innerClass` yükseltilmekte, ancak `numberSub` modül düzeyinde bildirilmemiş olduğundan, değildir.  
  
## <a name="effect-of-type-promotion"></a>Yükseltme türü etkisi  

 Yükseltme türünün etkisi, bir nitelik dizesinin modül adını içermesi gerekmez. Aşağıdaki örnek, önceki örnekteki yordama iki çağrı yapar.  
  
 [!code-vb[VbVbalrDeclaredElements#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#2)]  
  
 Yukarıdaki örnekte, ilk çağrı bütün nitelik dizelerini kullanır. Ancak, tür yükseltmesi nedeniyle bu gerekli değildir. İkinci çağrı Ayrıca, nitelik dizelerine dahil etmeden modülün üyelerine erişir `projModule` .  
  
## <a name="defeat-of-type-promotion"></a>Tür promosyonu  

 Ad alanı zaten bir modül üyesiyle aynı ada sahip bir üyeye sahipse, bu modül üyesi için yükseltme yapılır yazın. Aşağıdaki örnek, bir numaralandırma ve aynı ad uzayı içindeki bir modülün iskelet tanımını gösterir.  
  
 [!code-vb[VbVbalrDeclaredElements#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#3)]  
  
 Yukarıdaki örnekte, `abc` `thisNameSpace` ad alanı düzeyinde aynı ada sahip bir sabit listesi olduğundan, Visual Basic sınıfını öğesine yükseltemezsiniz. Erişmek için `abcSub` tam niteleme dizesini kullanmanız gerekir `thisNamespace.thisModule.abc.abcSub` . Ancak, sınıf `xyz` hala yükseltilir ve `xyzSub` daha kısa nitelik dizesiyle erişebilirsiniz `thisNamespace.xyz.xyzSub` .  
  
### <a name="defeat-of-type-promotion-for-partial-types"></a>Kısmi türler için tür promosyonu  

 Modül içindeki bir sınıf veya yapı [kısmi](../../../language-reference/modifiers/partial.md) anahtar sözcüğünü kullanıyorsa, ad alanının aynı ada sahip bir üyeye sahip olup olmadığına bakılmaksızın, bu sınıf veya yapı için otomatik olarak tür yükseltmesi yapılır. Modüldeki diğer öğeler de tür yükseltme için uygun değildir.  
  
 **Larının.** Kısmi bir tanımın tür promosyonu, beklenmedik sonuçlara ve hatta derleyici hatalarına neden olabilir. Aşağıdaki örnek, bir sınıfının bir modül içinde olan bir sınıfın iskelet kısmi tanımlarını gösterir.  
  
 [!code-vb[VbVbalrDeclaredElements#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#4)]  
  
 Yukarıdaki örnekte, geliştirici derleyicinin iki kısmi tanımını birleştirme işlemini bekleyebilir `sampleClass` . Ancak derleyici, içindeki kısmi Tanım için yükseltmeyi göz önünde bulundurmaz `sampleModule` . Sonuç olarak, hem adında hem de `sampleClass` farklı nitelik yollarıyla birlikte iki ayrı ve farklı sınıf derlemeye çalışır.  
  
 Derleyici, kısmi tanımları yalnızca kendi tam yolları özdeş olduğunda birleştirir.  
  
## <a name="recommendations"></a>Öneriler  

 Aşağıdaki öneriler iyi programlama uygulamasını temsil etmektedir.  
  
- **Benzersiz adlar.** Programlama öğelerinin adlandırılması üzerinde tam denetime sahip olduğunuzda her yerde benzersiz adların kullanılması her zaman iyi bir fikirdir. Aynı adlar ek nitelik gerektirir ve kodunuzun okunmasını daha zor hale getirir. Ayrıca, hafif hatalara ve beklenmedik sonuçlara yol açabilir.  
  
- **Tam nitelik.** Aynı ad alanındaki modüller ve diğer öğelerle çalışırken, en güvenli yaklaşım tüm programlama öğeleri için her zaman tam niteliğin kullanılması. Tür promosyonu bir modül üyesi için ertelendirilürse ve bu üyeyi tamamen nitelemeniz durumunda farklı bir programlama öğesine yanlışlıkla erişebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Module Deyimi](../../../language-reference/statements/module-statement.md)
- [Namespace Deyimi](../../../language-reference/statements/namespace-statement.md)
- [Kısmi](../../../language-reference/modifiers/partial.md)
- [Visual Basic'de Kapsam](scope.md)
- [Nasıl yapılır: Bir Değişkenin Kapsamını Denetleme](how-to-control-the-scope-of-a-variable.md)
- [Bildirilmiş Öğelere Başvurular](references-to-declared-elements.md)

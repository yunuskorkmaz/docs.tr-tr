---
title: With...End With Deyimi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.With
helpviewer_keywords:
- With keyword [Visual Basic]
- loop structures [Visual Basic], and With...End With statements
- execution [Visual Basic], on object
- instructions, repeating
- With...End With statements [Visual Basic]
- With statement [Visual Basic]
- With statement [Visual Basic], nesting
- objects [Visual Basic], accessing
- With block
- End keyword [Visual Basic], With...End With statements
ms.assetid: 340d5fbb-4f43-48ec-a024-80843c137817
ms.openlocfilehash: a3762e3bf0978feeb1155f8cc8249a77f0a497df
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54535275"
---
# <a name="withend-with-statement-visual-basic"></a>With...End With Deyimi (Visual Basic)
Deyimlerin, nesne veya yapı üyelerine erişim sağlarken basitleştirilmiş bir sözdizimi kullanabilmesi için sürekli olarak tek bir nesneye veya yapıya başvuran bir dizi deyim yürütür.  Bir yapı kullanırken yalnızca üyelerinin değerlerini okuyabilir veya çağırma yöntemlerinin ve kullanılan bir yapının üyelerine değer atamak çalışırsanız hata alırsınız bir `With...End With` deyimi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
With objectExpression  
    [ statements ]  
End With  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`objectExpression`|Gerekli. Nesne olarak değerlendirilen bir ifade. İfade rasgele karmaşık olabilir ve yalnızca bir kez değerlendirilir. İfade, basit türler de dahil olmak üzere herhangi bir veri türü olarak değerlendirilebilir.|  
|`statements`|İsteğe bağlı. Bir veya daha fazla deyim arasında `With` ve `End With` öğesinin değerlendirilmesiyle oluşturulan bir nesnenin üyelerine başvuruda `objectExpression`.|  
|`End With`|Gerekli. Tanımını sonlandırır `With` blok.|  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanarak `With...End With`, nesnenin adını birçok kez belirtmeden belirtilen bir nesne üzerinde bir dizi deyim gerçekleştirebilirsiniz. İçinde bir `With` deyim bloğunu belirtebileceğiniz bir nokta ile başlayan nesnenin bir üyesi olarak `With` deyim nesnesi varmış.  
  
 Örneğin, tek bir nesnede birden çok özelliklerini değiştirmek için özellik atama deyimlerini içine yerleştirin. `With...End With` nesnesine yalnızca bir kez her özellik ataması için bir kez yerine başvuran bloğu.  
  
 Kodunuzu birden fazla deyimde aynı nesneye erişirse, aşağıdaki faydaları kullanarak elde `With` deyimi:  
  
-   Karmaşık ifadenin üyelerine birden çok kez başvuruda bulunmak için sonucu geçici bir değişkene atamanıza veya karmaşık ifadeyi birden çok kez değerlendirmenize gerek yoktur.  
  
-   Yinelenen niteleyici ifadeleri ortadan kaldırarak kodunuzu daha okunur hale getirirsiniz.  
  
 Veri türü `objectExpression` gibi herhangi bir sınıf veya yapı türü veya hatta bir Visual Basic basit türü olabilir `Integer`.  Varsa `objectExpression` sonuçları dışında herhangi bir nesne, yalnızca üyelerinin değerlerini okuyabilir veya çağırma yöntemlerinin ve kullanılan bir yapının üyelerine değer atamak çalışırsanız hata alırsınız bir `With...End With` deyimi.  Aynı hata, yapı döndüren ve hemen erişilen ve bir değer gibi işlev sonucunun bir üyesine atanmış bir yöntemi çağırdığınız alma budur `GetAPoint().x = 1`.  İki durumda da sorun şudur: Yapı yalnızca çağrı yığınında mevcuttur ve değiştirilmiş bir yapı üyesinin bu durumlarda, programdaki diğer herhangi bir kodun değişikliği gözlemleyebileceği şekilde bir konuma yazabilmesinin hiçbir yolu yoktur.  
  
 `objectExpression` Bloğuna girişte bir kez değerlendirilir. Atayamazsınız `objectExpression` içinden `With` blok.  
  
 İçinde bir `With` bloğu bunları nitelemeden yalnızca belirtilen nesnenin özellikleri ve yöntemleri erişebilirsiniz. Diğer nesnelerin yöntemlerini ve özelliklerini kullanabilirsiniz, ancak bunları nesne adlarıyla nitelemeniz gerekir.  
  
 Bir yerleştirebilirsiniz `With...End With` deyimi içinde başka bir. İç içe geçmiş `With...End With` deyimleri için başvurulan nesneler bağlamdan açık değilse kafa karıştırıcı olabilir. Bir dış bir nesne için tam bir başvuru sağlamalısınız `With` nesne bir iç başvuruluyor, block `With` blok.  
  
 Dal oluşturamazsınız bir `With` deyim bloğuna bloğun dışından.  
  
 Blok bir döngü içermediği sürece deyimler yalnızca bir kez çalışır. Farklı türlerde denetim yapılarını iç içe yerleştirebilirsiniz. Daha fazla bilgi için [iç içe geçmiş denetim yapıları](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
> [!NOTE]
>  Kullanabileceğiniz `With` anahtar sözcüğünü nesne başlatıcılarda da. Daha fazla bilgi ve örnekler için bkz. [nesne başlatıcıları: Adlandırılmış ve anonim türler](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) ve [anonim türler](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
>   
>  Kullanıyorsanız, bir `With` blok özelliklerle veya alanlarla hemen kullanmanızın, bir nesnenin yalnızca başlatmak için bir nesne Başlatıcı kullanmayı düşünün.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, her `With` blok, tek bir nesne üzerinde bir dizi deyim yürütür.  
  
 [!code-vb[VbVbalrWithStatement#2](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/with-end-with-statement_1.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek Yuvalar `With…End With` deyimleri. İç içe içinde `With` deyimi, sözdizimi içteki nesneye başvurur.  
  
 [!code-vb[VbVbalrWithStatement#1](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/with-end-with-statement_2.vb)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Collections.Generic.List%601>
- [İç İçe Geçmiş Denetim Yapıları](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Nesne başlatıcıları: Adlandırılmış ve anonim türler](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Anonim Tipler](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)

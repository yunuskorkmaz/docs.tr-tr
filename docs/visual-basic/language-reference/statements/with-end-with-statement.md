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
ms.openlocfilehash: 3d26932c23299c6fbcb53b1389abd7694f529eef
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963323"
---
# <a name="withend-with-statement-visual-basic"></a>With...End With Deyimi (Visual Basic)
Deyimlerin, nesne veya yapı üyelerine erişim sağlarken basitleştirilmiş bir sözdizimi kullanabilmesi için sürekli olarak tek bir nesneye veya yapıya başvuran bir dizi deyim yürütür.  Bir yapı kullanırken, yalnızca üye değerlerini okuyabilir veya yöntemleri çağırabilir ve bir `With...End With` bildirimde kullanılan bir yapının üyelerine değer atamaya çalışırsanız hata alırsınız.  
  
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
|`statements`|İsteğe bağlı. `objectExpression`Ve `With` arasındakibirveyadahafazladeyim,değerlendirmesitarafındanüretilenbirnesneninüyelerinebaşvurabilir.`End With`|  
|`End With`|Gerekli. `With` Bloğunun tanımını sonlandırır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanarak `With...End With`, nesnenin adını birden çok kez belirtmeden belirtilen bir nesne üzerinde bir dizi deyim gerçekleştirebilirsiniz. Bir `With` ifade bloğunda, bir nokta ile başlayan nesnenin bir üyesini, `With` ifade nesnesi önünde olduğu gibi belirtebilirsiniz.  
  
 Örneğin, tek bir nesnedeki birden çok özelliği değiştirmek için, özellik atama deyimlerini, her özellik ataması için `With...End With` bir kez olmak yerine, nesneye yalnızca bir kez başvuruda bulunan bloğun içine yerleştirin.  
  
 Kodunuz birden çok deyimde aynı nesneye erişirse, şu avantajları kullanarak `With` aşağıdaki avantajları elde edersiniz:  
  
- Karmaşık ifadenin üyelerine birden çok kez başvuruda bulunmak için sonucu geçici bir değişkene atamanıza veya karmaşık ifadeyi birden çok kez değerlendirmenize gerek yoktur.  
  
- Yinelenen niteleyici ifadeleri ortadan kaldırarak kodunuzu daha okunur hale getirirsiniz.  
  
 Veri türü `objectExpression` herhangi bir sınıf veya yapı türü ya da gibi Visual Basic bir öğesel tür `Integer`olabilir.  Bir `objectExpression` nesne dışında bir işlem sonucu varsa, yalnızca üyelerinin değerlerini okuyabilir veya yöntemleri çağırabilir ve bir `With...End With` bildirimde kullanılan bir yapının üyelerine değer atamaya çalışırsanız hata alırsınız.  Bu, bir yapı döndüren ve hemen erişilen ve işlevin sonucunun `GetAPoint().x = 1`bir üyesine değer atayan bir yöntemi çağırdıysanız elde ettiğiniz hatadır.  İki durumda da sorun şudur: Yapı yalnızca çağrı yığınında mevcuttur ve değiştirilmiş bir yapı üyesinin bu durumlarda, programdaki diğer herhangi bir kodun değişikliği gözlemleyebileceği şekilde bir konuma yazabilmesinin hiçbir yolu yoktur.  
  
 , `objectExpression` Bloğa giriş yapıldığında bir kez değerlendirilir. Bloğunu`With` bloğunun içinden yeniden `objectExpression` atayamazsınız.  
  
 Bir `With` blok içinde, yalnızca belirtilen nesnenin yöntemlerine ve özelliklerine uygun olmayan şekilde erişebilirsiniz. Diğer nesnelerin yöntemlerini ve özelliklerini kullanabilirsiniz, ancak bunları nesne adlarıyla nitelemeniz gerekir.  
  
 Bir `With...End With` ifadeyi diğerinin içine yerleştirebilirsiniz. Başvurulan `With...End With` nesneler bağlamdan temizlenmemişse iç içe geçmiş deyimler kafa karıştırıcı olabilir. Nesneye bir iç `With` `With` blok içinden başvuruluyorsa, bir dış bloktaki bir nesneye tam nitelikli bir başvuru sağlamanız gerekir.  
  
 Blok dışından bir `With` ifade bloğuna dal oluşturamazsınız.  
  
 Blok bir döngü içermediği sürece deyimler yalnızca bir kez çalışır. Farklı türlerde denetim yapılarını iç içe yerleştirebilirsiniz. Daha fazla bilgi için bkz. [Iç Içe denetim yapıları](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
> [!NOTE]
> `With` Anahtar sözcüğünü ayrıca nesne başlatıcılarda da kullanabilirsiniz. Daha fazla bilgi ve örnek için bkz [. nesne başlatıcıları: Adlandırılmış ve anonim türler](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) ve [anonim türler](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
>   
>  Yalnızca yeni örneklediğiniz nesnenin `With` özelliklerini veya alanlarını başlatmak için bir blok kullanıyorsanız, bunun yerine bir nesne Başlatıcısı kullanmayı düşünün.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, her `With` bir blok tek bir nesne üzerinde bir dizi deyim yürütür.  
  
 [!code-vb[VbVbalrWithStatement#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrwithstatement/vb/mainwindow.xaml.vb#2)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek with `With…End With` deyimleri. İç içe geçmiş `With` bildiriminde sözdizimi, iç nesneye başvurur.  
  
 [!code-vb[VbVbalrWithStatement#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrwithstatement/vb/mainwindow.xaml.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic.List%601>
- [İç İçe Geçmiş Denetim Yapıları](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Nesne başlatıcıları: Adlandırılmış ve anonim türler](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Anonim Tipler](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)

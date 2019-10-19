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
ms.openlocfilehash: 3da04b85865389a2b4466b78091ff28529346269
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582249"
---
# <a name="withend-with-statement-visual-basic"></a>With...End With Deyimi (Visual Basic)

Deyimlerin, nesne veya yapı üyelerine erişim sağlarken basitleştirilmiş bir sözdizimi kullanabilmesi için sürekli olarak tek bir nesneye veya yapıya başvuran bir dizi deyim yürütür.  Bir yapı kullanırken, yalnızca üye değerlerini okuyabilir veya yöntemleri çağırabilir ve bir `With...End With` bildiriminde kullanılan bir yapının üyelerine değer atamaya çalışırsanız hata alırsınız.

## <a name="syntax"></a>Sözdizimi

```vb
With objectExpression
    [ statements ]
End With
```

## <a name="parts"></a>Bölümler

|Terim|Tanım|
|---|---|
|`objectExpression`|Gerekli. Nesne olarak değerlendirilen bir ifade. İfade rasgele karmaşık olabilir ve yalnızca bir kez değerlendirilir. İfade, basit türler de dahil olmak üzere herhangi bir veri türü olarak değerlendirilebilir.|
|`statements`|İsteğe bağlı. @No__t_2 değerlendirmesi tarafından üretilen bir nesnenin üyelerine başvurabilen `With` ve `End With` arasındaki bir veya daha fazla deyim.|
|`End With`|Gerekli. @No__t_0 bloğunun tanımını sonlandırır.|

## <a name="remarks"></a>Açıklamalar

@No__t_0 kullanarak, nesnenin adını birden çok kez belirtmeden belirtilen bir nesne üzerinde bir dizi deyim gerçekleştirebilirsiniz. Bir `With` bildiri bloğunda, bir noktayla başlayan nesnenin bir üyesini, `With` deyimin nesnesi önünde olduğu gibi belirtebilirsiniz.

Örneğin, tek bir nesnedeki birden çok özelliği değiştirmek için, özellik atama deyimlerini, her özellik ataması için bir kez olmak yerine, nesneye yalnızca bir kez başvuruda bulunan `With...End With` bloğunun içine yerleştirin.

Kodunuz birden çok deyimde aynı nesneye erişirse, `With` deyimini kullanarak aşağıdaki avantajları elde edersiniz:

- Karmaşık ifadenin üyelerine birden çok kez başvuruda bulunmak için sonucu geçici bir değişkene atamanıza veya karmaşık ifadeyi birden çok kez değerlendirmenize gerek yoktur.

- Yinelenen niteleyici ifadeleri ortadan kaldırarak kodunuzu daha okunur hale getirirsiniz.

@No__t_0 veri türü herhangi bir sınıf veya yapı türü veya hatta `Integer` gibi bir Visual Basic elemensel tür olabilir.  @No__t_0 bir nesneden farklı bir şekilde sonuçlanırsa, yalnızca üyelerinin değerlerini okuyabilir veya yöntemleri çağırabilir ve bir `With...End With` bildiriminde kullanılan bir yapının üyelerine değer atamaya çalışırsanız hata alırsınız.  Bu, bir yapı döndüren ve hemen erişilen ve işlevin sonucunun bir üyesine değer atayan, `GetAPoint().x = 1` gibi bir yöntemi çağırdıysanız elde ettiğiniz hatadır.  İki durumda da sorun şudur: Yapı yalnızca çağrı yığınında mevcuttur ve değiştirilmiş bir yapı üyesinin bu durumlarda, programdaki diğer herhangi bir kodun değişikliği gözlemleyebileceği şekilde bir konuma yazabilmesinin hiçbir yolu yoktur.

@No__t_0, bloğa giriş yapıldığında bir kez değerlendirilir. @No__t_0 `With` bloğunun içinden yeniden atayamazsınız.

@No__t_0 bloğu içinde, yalnızca belirtilen nesnenin yöntemlerine ve özelliklerine bunları nitelemeden erişebilirsiniz. Diğer nesnelerin yöntemlerini ve özelliklerini kullanabilirsiniz, ancak bunları nesne adlarıyla nitelemeniz gerekir.

Bir `With...End With` deyiminizi başka bir şekilde yerleştirebilirsiniz. Başvurulan nesneler bağlamdan temizlenmemişse iç içe `With...End With` deyimleri kafa karıştırıcı olabilir. Nesneye bir iç `With` bloğunun başvurduğu zaman bir dıştaki `With` bloğunda bir nesneye tam bir başvuru sağlamanız gerekir.

Bloğunun dışından `With` bir ifade bloğuna dallandırma yapamazsınız.

Blok bir döngü içermediği sürece deyimler yalnızca bir kez çalışır. Farklı türlerde denetim yapılarını iç içe yerleştirebilirsiniz. Daha fazla bilgi için bkz. [Iç Içe denetim yapıları](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).

> [!NOTE]
> Nesne başlatıcılarda `With` anahtar sözcüğünü de kullanabilirsiniz. Daha fazla bilgi ve örnek için bkz. [nesne başlatıcıları: adlandırılmış ve anonim türler](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) ve [anonim türler](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).
>
> Yalnızca yeni örneklediğiniz bir nesnenin özelliklerini veya alanlarını başlatmak için bir `With` bloğu kullanıyorsanız, bunun yerine bir nesne Başlatıcısı kullanmayı düşünün.

## <a name="example"></a>Örnek

Aşağıdaki örnekte, her `With` bloğu tek bir nesne üzerinde bir dizi deyim yürütür.

[!code-vb[VbVbalrWithStatement#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrwithstatement/vb/mainwindow.xaml.vb#2)]

## <a name="example"></a>Örnek

Aşağıdaki örnek `With…End With` deyimlerini ifade etti. İç içe `With` bildiriminde sözdizimi, iç nesneye başvurur.

[!code-vb[VbVbalrWithStatement#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrwithstatement/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic.List%601>
- [İç İçe Geçmiş Denetim Yapıları](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Nesne Başlatıcıları: Adlandırılmış ve Anonim Tipler](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Anonim Tipler](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)

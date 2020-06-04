---
title: With...End With Deyimi
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
ms.openlocfilehash: 50f3bd0c6e96254274b429794901e2e4ac719ad0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401387"
---
# <a name="withend-with-statement-visual-basic"></a>With...End With Deyimi (Visual Basic)

Deyimlerin, nesne veya yapı üyelerine erişim sağlarken basitleştirilmiş bir sözdizimi kullanabilmesi için sürekli olarak tek bir nesneye veya yapıya başvuran bir dizi deyim yürütür.  Bir yapı kullanırken, yalnızca üye değerlerini okuyabilir veya yöntemleri çağırabilir ve bir bildirimde kullanılan bir yapının üyelerine değer atamaya çalışırsanız hata alırsınız `With...End With` .

## <a name="syntax"></a>Sözdizimi

```vb
With objectExpression
    [ statements ]
End With
```

## <a name="parts"></a>Bölümler

|Terim|Tanım|
|---|---|
|`objectExpression`|Gereklidir. Nesne olarak değerlendirilen bir ifade. İfade rasgele karmaşık olabilir ve yalnızca bir kez değerlendirilir. İfade, basit türler de dahil olmak üzere herhangi bir veri türü olarak değerlendirilebilir.|
|`statements`|İsteğe bağlı. Ve arasındaki bir veya daha fazla deyim, `With` `End With` değerlendirmesi tarafından üretilen bir nesnenin üyelerine başvurabilir `objectExpression` .|
|`End With`|Gereklidir. Bloğunun tanımını sonlandırır `With` .|

## <a name="remarks"></a>Açıklamalar

Kullanarak `With...End With` , nesnenin adını birden çok kez belirtmeden belirtilen bir nesne üzerinde bir dizi deyim gerçekleştirebilirsiniz. Bir `With` ifade bloğunda, bir nokta ile başlayan nesnenin bir üyesini, `With` ifade nesnesi önünde olduğu gibi belirtebilirsiniz.

Örneğin, tek bir nesnedeki birden çok özelliği değiştirmek için, özellik atama deyimlerini, `With...End With` her özellik ataması için bir kez olmak yerine, nesneye yalnızca bir kez başvuruda bulunan bloğun içine yerleştirin.

Kodunuz birden çok deyimde aynı nesneye erişirse, şu avantajları kullanarak aşağıdaki avantajları elde edersiniz `With` :

- Karmaşık ifadenin üyelerine birden çok kez başvuruda bulunmak için sonucu geçici bir değişkene atamanıza veya karmaşık ifadeyi birden çok kez değerlendirmenize gerek yoktur.

- Yinelenen niteleyici ifadeleri ortadan kaldırarak kodunuzu daha okunur hale getirirsiniz.

Veri türü `objectExpression` herhangi bir sınıf veya yapı türü ya da gibi Visual Basic bir öğesel tür olabilir `Integer` .  `objectExpression`Bir nesne dışında bir işlem sonucu varsa, yalnızca üyelerinin değerlerini okuyabilir veya yöntemleri çağırabilir ve bir bildirimde kullanılan bir yapının üyelerine değer atamaya çalışırsanız hata alırsınız `With...End With` .  Bu, bir yapı döndüren ve hemen erişilen ve işlevin sonucunun bir üyesine değer atayan bir yöntemi çağırdıysanız elde ettiğiniz hatadır `GetAPoint().x = 1` .  İki durumda da sorun şudur: Yapı yalnızca çağrı yığınında mevcuttur ve değiştirilmiş bir yapı üyesinin bu durumlarda, programdaki diğer herhangi bir kodun değişikliği gözlemleyebileceği şekilde bir konuma yazabilmesinin hiçbir yolu yoktur.

, `objectExpression` Bloğa giriş yapıldığında bir kez değerlendirilir. `objectExpression`Bloğunu bloğunun içinden yeniden atayamazsınız `With` .

Bir `With` blok içinde, yalnızca belirtilen nesnenin yöntemlerine ve özelliklerine uygun olmayan şekilde erişebilirsiniz. Diğer nesnelerin yöntemlerini ve özelliklerini kullanabilirsiniz, ancak bunları nesne adlarıyla nitelemeniz gerekir.

Bir `With...End With` ifadeyi diğerinin içine yerleştirebilirsiniz. `With...End With`Başvurulan nesneler bağlamdan temizlenmemişse iç içe geçmiş deyimler kafa karıştırıcı olabilir. `With`Nesneye bir iç blok içinden başvuruluyorsa, bir dış bloktaki bir nesneye tam nitelikli bir başvuru sağlamanız gerekir `With` .

`With`Blok dışından bir ifade bloğuna dal oluşturamazsınız.

Blok bir döngü içermediği sürece deyimler yalnızca bir kez çalışır. Farklı türlerde denetim yapılarını iç içe yerleştirebilirsiniz. Daha fazla bilgi için bkz. [Iç Içe denetim yapıları](../../programming-guide/language-features/control-flow/nested-control-structures.md).

> [!NOTE]
> `With`Anahtar sözcüğünü ayrıca nesne başlatıcılarda da kullanabilirsiniz. Daha fazla bilgi ve örnek için bkz. [nesne başlatıcıları: adlandırılmış ve anonim türler](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) ve [anonim türler](../../programming-guide/language-features/objects-and-classes/anonymous-types.md).
>
> `With`Yalnızca yeni örneklediğiniz nesnenin özelliklerini veya alanlarını başlatmak için bir blok kullanıyorsanız, bunun yerine bir nesne Başlatıcısı kullanmayı düşünün.

## <a name="example"></a>Örnek

Aşağıdaki örnekte, her bir `With` blok tek bir nesne üzerinde bir dizi deyim yürütür.

[!code-vb[VbVbalrWithStatement#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrwithstatement/vb/mainwindow.xaml.vb#2)]

## <a name="example"></a>Örnek

Aşağıdaki örnek with `With…End With` deyimleri. İç içe geçmiş `With` bildiriminde sözdizimi, iç nesneye başvurur.

[!code-vb[VbVbalrWithStatement#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrwithstatement/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic.List%601>
- [İç İçe Geçmiş Denetim Yapıları](../../programming-guide/language-features/control-flow/nested-control-structures.md)
- [Nesne Başlatıcıları: Adlandırılmış ve Anonim Türler](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Anonim Türler](../../programming-guide/language-features/objects-and-classes/anonymous-types.md)

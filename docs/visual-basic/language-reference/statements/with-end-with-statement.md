---
title: With...End With Deyimi (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.With
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
caps.latest.revision: "34"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: aa1f416e1bfdf6cdb51b098c0e2bd5e9912cb309
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="withend-with-statement-visual-basic"></a>With...End With Deyimi (Visual Basic)
Deyimlerin, nesne veya yapı üyelerine erişim sağlarken basitleştirilmiş bir sözdizimi kullanabilmesi için sürekli olarak tek bir nesneye veya yapıya başvuran bir dizi deyim yürütür.  Bir yapıyı kullanırken, yalnızca üyelerinin değerlerini okuyabilir veya yöntemleri çağırma ve kullanılan bir yapı üyelerine değerleri atamak çalışırsanız bir hata alıyorsunuz bir `With...End With` deyimi.  
  
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
|`statements`|İsteğe bağlı. Bir veya daha fazla deyimleri arasında `With` ve `End With` değerlendirmesi tarafından üretilen bir nesnenin üyelerine başvurabilir `objectExpression`.|  
|`End With`|Gerekli. Tanımını sonlandırır `With` bloğu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanarak `With...End With`, birden çok kez nesnesinin adı belirtmeden belirtilen bir nesne üzerinde bir dizi deyimi gerçekleştirebilirsiniz. İçinde bir `With` deyimi blok, bir nokta ile başlayan nesne üyesi belirtebilirsiniz gibi `With` deyim nesnesi öncesinde.  
  
 Örneğin, tek bir nesne birden çok özelliklerini değiştirmek için özellik atama deyimleri içine yerleştirin `With...End With` nesneye yalnızca bir kez her özellik ataması için bir kez yerine başvuran bloğu.  
  
 Kodunuzu birden çok deyimlerinde aynı nesneye erişirse, aşağıdaki faydaları kullanarak elde `With` deyimi:  
  
-   Karmaşık ifadenin üyelerine birden çok kez başvuruda bulunmak için sonucu geçici bir değişkene atamanıza veya karmaşık ifadeyi birden çok kez değerlendirmenize gerek yoktur.  
  
-   Yinelenen niteleyici ifadeleri ortadan kaldırarak kodunuzu daha okunur hale getirirsiniz.  
  
 Veri türü `objectExpression` herhangi bir sınıf veya yapı türüne veya hatta bir Visual Basic başlangıç türü gibi olabilir `Integer`.  Varsa `objectExpression` sonuçları herhangi bir nesne dışında yalnızca kendi üyelerinin değerlerini okuyabilir veya yöntemleri çağırma ve kullanılan bir yapı üyelerine değerleri atamak çalışırsanız bir hata alıyorsunuz bir `With...End With` deyimi.  Bu alma ise bir yapı döndürdü ve hemen erişilen ve işlevin sonucu üyesi için bir değer gibi atanan bir yöntemi çağırıldığında aynı hatadır `GetAPoint().x = 1`.  İki durumda da sorun şudur: Yapı yalnızca çağrı yığınında mevcuttur ve değiştirilmiş bir yapı üyesinin bu durumlarda, programdaki diğer herhangi bir kodun değişikliği gözlemleyebileceği şekilde bir konuma yazabilmesinin hiçbir yolu yoktur.  
  
 `objectExpression` Bloğuna girişte bir kez değerlendirilir. Yeniden atama olamaz `objectExpression` içinden `With` bloğu.  
  
 İçinde bir `With` bloğu niteleme olmadan, yalnızca belirtilen nesne özelliklerini ve yöntemlerini erişebilirsiniz. Diğer nesnelerin yöntemlerini ve özelliklerini kullanabilirsiniz, ancak bunları nesne adlarıyla nitelemeniz gerekir.  
  
 Biri yerleştirileceği `With...End With` deyimi içinde başka bir. İç içe geçmiş `With...End With` deyimleri için başvurulan nesneler bağlamından Temizle yoksa kafa karıştırıcı olabilir. Bir dış bir nesne için tam bir başvuru sağlamalısınız `With` engelleme nesne içinde bir iç başvuruluyor zaman `With` bloğu.  
  
 İçine dallanamıyor bir `With` deyimi bloğundan blok dışında.  
  
 Blok bir döngü içermediği sürece deyimler yalnızca bir kez çalışır. Farklı türlerde denetim yapılarını iç içe yerleştirebilirsiniz. Daha fazla bilgi için bkz: [iç içe geçmiş denetim yapıları](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
> [!NOTE]
>  Kullanabileceğiniz `With` nesne başlatıcıları da anahtar sözcük. Daha fazla bilgi ve örnekler için bkz: [nesne başlatıcıları: adlandırılmış ve anonim türler](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) ve [anonim türler](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
>   
>  Kullanıyorsanız, bir `With` özellikler veya alanlar yalnızca örneği, bir nesnenin yalnızca başlatmak için blok nesne Başlatıcı kullanmayı düşünün.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, her `With` bloğu tek bir nesne üzerinde bir dizi deyimi yürütür.  
  
 [!code-vb[VbVbalrWithStatement#2](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/with-end-with-statement_1.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek Yuvalar `With…End With` deyimleri. İç içe içinde `With` deyimi sözdizimi iç nesnesine başvuruyor.  
  
 [!code-vb[VbVbalrWithStatement#1](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/with-end-with-statement_2.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Collections.Generic.List%601>  
 [İç içe geçmiş denetim yapıları](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [Nesne başlatıcıları: Adlandırılmış ve anonim türler](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [Anonim türler](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)

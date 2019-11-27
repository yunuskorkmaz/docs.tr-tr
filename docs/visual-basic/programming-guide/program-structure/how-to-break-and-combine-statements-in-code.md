---
title: 'Nasıl yapılır: Kodda Deyimleri Bölme ve Birleştirme'
ms.date: 07/20/2015
f1_keywords:
- vb._
helpviewer_keywords:
- colons (:)
- line continuation
- _ line-continuation character
- ': line separator character'
- Visual Basic code, line breaks in
- Visual Basic code, line breaks
- Visual Basic code, line continuation
- long lines of code
- line terminator
- line-continuation sequence
- underscores [Visual Basic], in code
- statements [Visual Basic], line continuation in
- line breaks [Visual Basic], in code
- line-continuation character [Visual Basic]
- Visual Basic code, line continuation in
- statements [Visual Basic], line breaks in
ms.assetid: dea01dad-a8ac-484a-bb3a-8c45a1b1eccc
ms.openlocfilehash: f1a24c001cd20acc7663fb4cbe60e7e35a9c8fc3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347433"
---
# <a name="how-to-break-and-combine-statements-in-code-visual-basic"></a>Nasıl yapılır: Kodda Deyimleri Bölme ve Birleştirme (Visual Basic)

Kodunuzu yazarken, kod düzenleyicisinde yatay kaydırmayı gerektiren uzun deyimler oluşturabilirsiniz. Bu, kodunuzun çalışma biçimini etkilemese de, siz veya başka birinin izleyiciden göründüğü şekilde kodu okumasını zorlaştırır. Böyle durumlarda, tek uzun bir ifadeyi birkaç satıra bozmalısınız.

## <a name="to-break-a-single-statement-into-multiple-lines"></a>Tek bir ifadeyi birden çok satıra bölmek için

Çizginin kesilmesini istediğiniz noktada alt çizgi (`_`) olan satır devamlılık karakterini kullanın. Alt çizgi hemen öncesinde bir boşluk ve hemen arkasından bir satır Sonlandırıcı (satır sonu) ya da (sürüm 16,0 ' den başlayarak) bir yorum ve ardından bir satır başı gelmelidir.

  > [!NOTE]
  > Bazı durumlarda, satır devamlılık karakterini atlarsanız Visual Basic derleyici bir sonraki kod satırında ifadeye dolaylı olarak devam eder. Satır devamlılık karakterini yok saybileceğiniz sözdizimi öğelerinin listesi için, bkz. [deyimlerde](../../../visual-basic/programming-guide/language-features/statements.md)"örtük satır devamlılığı".

  Aşağıdaki örnekte,, son satır hariç tüm satır devamlılık karakterleriyle dört satıra bölünmüştür.

  [!code-vb[VbVbcnConventions#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#20)]

  Bu dizinin kullanılması, kodunuzun hem çevrimiçi hem de yazdırıldığında okunmasını kolaylaştırır.

  Satır devamlılık karakteri bir satırdaki son karakter olmalıdır. Aynı satırdaki başka herhangi bir şeyle takip edebilirsiniz.

  Satır devamlılık karakterini nerede kullanabileceğiniz gibi bazı sınırlamalar vardır; Örneğin, bunu bir bağımsız değişken adının ortasında kullanamazsınız. Bir bağımsız değişken listesini satır devamlılık karakteriyle kesebilirsiniz, ancak bağımsız değişkenlerin bağımsız adları değişmeden kalmalıdır.

  Bir satır devamlılık karakteri kullanarak açıklamaya devam edemiyorum. Derleyici, bir yorum içindeki karakterleri özel anlam açısından inceetmez. Birden çok satırlık bir açıklama için, her satırda açıklama sembolünü (`'`) tekrarlayın.

 Her deyimin ayrı bir satıra yerleştirilmesi önerilen yöntem olduğundan, Visual Basic aynı satıra birden çok deyim yerleştirseniz de sağlar.

## <a name="to-place-multiple-statements-on-the-same-line"></a>Aynı satıra birden çok deyim yerleştirmek için

Deyimlerini aşağıdaki örnekte olduğu gibi iki nokta üst üste (`:`) ayırın:

  [!code-vb[VbVbcnConventions#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#10)]

## <a name="see-also"></a>Ayrıca bkz.

- [Program Yapısı ve Kod Kuralları](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [Deyimler](../../../visual-basic/programming-guide/language-features/statements.md)

---
title: Yordam Aşırı Yüklemesi
ms.date: 07/20/2015
helpviewer_keywords:
- signatures
- Overloads keyword [Visual Basic]
- hiding by signature
- Visual Basic code, procedures
- procedures [Visual Basic], signatures for
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- parameters [Visual Basic], lists
- signatures [Visual Basic], procedure
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- Shadows keyword [Visual Basic]
- procedure overloading
- procedures [Visual Basic], parameter lists
ms.assetid: fbc7fb18-e3b2-48b6-b554-64c00ed09d2a
ms.openlocfilehash: 41a971896fe726cbe9849fd46334910e7288afe0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352594"
---
# <a name="procedure-overloading-visual-basic"></a>Yordam Aşırı Yüklemesi (Visual Basic)

Bir yordamın *aşırı yüklenmesi* , aynı ad ancak farklı parametre listeleri kullanılarak birden çok sürümde tanımlanması anlamına gelir. Aşırı yükleme amacı, bir yordamın adına göre ayrım yapmadan daha yakından ilgili birkaç sürümünü tanımlamaktır. Bunu parametre listesini değiştirerek yapabilirsiniz.

## <a name="overloading-rules"></a>Kuralları aşırı yükleme

Bir yordamı aşırı yüklerken, aşağıdaki kurallar geçerlidir:

- **Aynı ad**. Her aşırı yüklenmiş sürüm aynı yordam adını kullanmalıdır.

- **Farklı imza**. Her aşırı yüklenmiş sürüm, aşağıdaki yönden en az birindeki diğer tüm aşırı yüklenmiş sürümlerden farklı olmalıdır:

  - Parametre sayısı

  - Parametrelerin sırası

  - Parametrelerin veri türleri

  - Tür parametrelerinin sayısı (genel yordam için)

  - Dönüş türü (yalnızca bir dönüştürme işleci için)

  Yordam adı ile birlikte, önceki öğeler her topluca yordamın *imzası* olarak adlandırılır. Aşırı yüklenmiş bir yordamı çağırdığınızda, derleyici, çağrının tanımıyla doğru şekilde eşleşip eşleşmediğini denetlemek için imzayı kullanır.

- **İmzanın bir parçası değil öğeleri**. İmzayı değiştirmeden bir yordamı aşırı yükleyemezsiniz. Özellikle, aşağıdaki öğelerden yalnızca birini veya birkaçını değiştirerek bir yordamı aşırı yükleyemezsiniz:

  - `Public`, `Shared`ve `Static` gibi yordam değiştirici anahtar sözcükleri

  - Parametre veya tür parametre adları

  - Tür parametresi kısıtlamaları (genel yordam için)

  - `ByRef` ve `Optional` gibi parametre değiştirici anahtar sözcükleri

  - Değer döndürüp döndürmeksizin

  - Dönüş değerinin veri türü (dönüştürme işleci dışında)

  Yukarıdaki listede yer olan öğeler imzaya ait değildir. Bunları aşırı yüklenmiş sürümler arasında ayrım yapmak için kullanamazsınız, ancak bunları imzalarıyla düzgün şekilde ayırt edilen aşırı yüklenmiş sürümler arasında değiştirebilirsiniz.

- **Geç bağlantılı bağımsız değişkenler**. Geç bağlantılı bir nesne değişkenini aşırı yüklenmiş bir sürüme geçirmek istiyorsanız, uygun parametreyi <xref:System.Object>olarak bildirmeniz gerekir.

## <a name="multiple-versions-of-a-procedure"></a>Yordamın birden çok sürümü

Bir müşterinin bakiyesine karşı bir işlem göndermek için bir `Sub` yordamı yazıyorsanız ve müşteriye ada veya hesap numarasına göre başvurmak istediğinizi varsayalım. Buna uyum sağlamak için, aşağıdaki örnekte olduğu gibi iki farklı `Sub` yordam tanımlayabilirsiniz:

[!code-vb[VbVbcnProcedures#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#73)]

### <a name="overloaded-versions"></a>Aşırı yüklenmiş sürümler

Bir alternatif, tek bir yordam adının aşırı yüklenmesine yönelik bir alternatiftir. Her bir parametre listesi için yordamın bir sürümünü tanımlamak üzere [overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) anahtar sözcüğünü aşağıda gösterildiği gibi kullanabilirsiniz:

[!code-vb[VbVbcnProcedures#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#72)]

#### <a name="additional-overloads"></a>Ek aşırı yüklemeler

Ayrıca `Decimal` veya `Single`bir işlem miktarı kabul etmek isterseniz, bu varyasyon için izin vermek `post` daha fazla aşırı yükleme yapabilirsiniz. Yukarıdaki örnekteki aşırı yüklemelerin her birini yaptıysanız, hepsi aynı ada sahip ancak dört farklı imzaya sahip dört `Sub` yordamımız olur.

## <a name="advantages-of-overloading"></a>Aşırı yükleme avantajları

Bir yordamı aşırı yükleme avantajı, çağrının esnekliğine sahiptir. Yukarıdaki örnekte açıklanan `post` yordamını kullanmak için, çağıran kod müşteri kimliğini bir `String` veya `Integer`olarak edinebilir ve sonra aynı yordamı her iki durumda da çağırabilir. Aşağıdaki örnek şunu göstermektedir:

[!code-vb[VbVbcnProcedures#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#56)]

[!code-vb[VbVbcnProcedures#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#57)]

## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](./index.md)
- [Nasıl yapılır: Bir Yordamın Birden Fazla Sürümünü Tanımlama](./how-to-define-multiple-versions-of-a-procedure.md)
- [Nasıl yapılır: Aşırı Yüklenmiş Bir Yordamı Çağırma](./how-to-call-an-overloaded-procedure.md)
- [Nasıl yapılır: İsteğe Bağlı Parametreler İsteyen Bir Yordamı Aşırı Yükleme](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [Nasıl yapılır: Belirsiz Sayıda Parametre İsteyen Bir Yordamı Aşırı Yükleme](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [Yordamları Aşırı Yüklemeye İlişkin Düşünceler](./considerations-in-overloading-procedures.md)
- [Aşırı Yükleme Çözümü](./overload-resolution.md)
- [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)
- [Visual Basic genel türler](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)

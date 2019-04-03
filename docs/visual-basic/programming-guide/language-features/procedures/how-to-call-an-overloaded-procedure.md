---
title: 'Nasıl yapılır: (Visual Basic) aşırı yüklenmiş bir yordamı çağırma'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], calling
- procedures [Visual Basic], multiple versions
- procedure calls [Visual Basic], overloaded
ms.assetid: 3bb331fb-f6bc-406f-9ca0-9609b497014c
ms.openlocfilehash: 9dda0fbc0cffe8904ab97c46cea40d5cf00c91e9
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843792"
---
# <a name="how-to-call-an-overloaded-procedure-visual-basic"></a>Nasıl yapılır: (Visual Basic) aşırı yüklenmiş bir yordamı çağırma
Bir yordamı aşırı yükleme çağrısının esneklik avantajlarındandır. Çağıran kod, yordama geçirin ve ardından bunu geçirerek hangi bağımsız değişkenleri ne olursa olsun bir tek yordam adı çağırmak için gereken bilgileri elde edebilirsiniz.  
  
### <a name="to-call-a-procedure-that-has-more-than-one-version-defined"></a>Tanımlanan birden fazla sürümü olan bir yordam çağırmak için  
  
1.  Çağıran kod içinde yordama geçirmeye hangi verileri belirler.  
  
2.  Yordam çağrısı bağımsız değişken listesinde veriyi sunmaktan normal bir şekilde yazın. Bağımsız değişken parametre listesinde yordamı için tanımlanan sürümlerinden birini eşleştiğinden emin olun.  
  
3.  Yordam çağırmak için hangi sürümünü gerekmez. Visual Basic, bağımsız değişken listesi ile eşleşen sürüm denetim geçer.  
  
     Aşağıdaki örnek çağrıları `post` yordam içinde bildirilen [nasıl yapılır: Bir yordamın birden fazla sürümünü tanımlama](./how-to-define-multiple-versions-of-a-procedure.md). Müşteri Kimliği alır, olup olmadığını belirleyen bir `String` veya `Integer`ve ardından her iki durumda da aynı yordamı çağırır.  
  
     [!code-vb[VbVbcnProcedures#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#56)]  
  
     [!code-vb[VbVbcnProcedures#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#57)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](./index.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Yordam Aşırı Yüklemesi](./procedure-overloading.md)
- [Yordam Sorunlarını Giderme](./troubleshooting-procedures.md)
- [Nasıl yapılır: Bir yordamın birden fazla sürümünü tanımlama](./how-to-define-multiple-versions-of-a-procedure.md)
- [Nasıl yapılır: İsteğe bağlı parametreler isteyen bir yordamı aşırı yükleme](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [Nasıl yapılır: Belirsiz sayıda parametre isteyen bir yordamı aşırı yükleme](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [Yordamları Aşırı Yüklemeye İlişkin Düşünceler](./considerations-in-overloading-procedures.md)
- [Aşırı Yükleme Çözümü](./overload-resolution.md)
- [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)

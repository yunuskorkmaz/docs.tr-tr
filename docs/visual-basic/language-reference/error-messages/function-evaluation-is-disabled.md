---
title: Önceki bir işlev değerlendirmesi zaman aşımına uğradığından işlev değerlendirmesi devre dışı bırakıldı
ms.date: 07/20/2015
f1_keywords:
- bc30957
- vbc30957
helpviewer_keywords:
- BC30957
ms.assetid: 561e593a-f50a-4b72-a708-4cab60ec7b28
ms.openlocfilehash: d004c89b742944622ce45e6a2be8d96116252745
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197572"
---
# <a name="function-evaluation-is-disabled-because-a-previous-function-evaluation-timed-out"></a>Önceki bir işlev değerlendirmesi zaman aşımına uğradığından işlev değerlendirmesi devre dışı bırakıldı
Önceki bir işlev değerlendirmesi zaman aşımına uğradığından işlev değerlendirmesi devre dışı bırakıldı. İşlev değerlendirmesini yeniden etkinleştirmek için tekrar adımla veya hata ayıklamayı yeniden başlatın.  
  
 Visual Studio hata ayıklayıcısında bir ifade bir yordam çağrısını belirtir, ancak başka bir değerlendirme zaman aşımına uğradı.  
  
 Bir yordam çağrısının zaman aşımına yönelik olası nedenleri sonsuz döngü veya sonsuz *döngü*içerir. Daha fazla bilgi için bkz.... [ Sonraki Ifade](../../../visual-basic/language-reference/statements/for-next-statement.md).  
  
 Sonsuz bir döngünün özel bir durumu *özyinelemedir*. Daha fazla bilgi için bkz. [özyinelemeli yordamlar](../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md).  
  
 **Hata kimliği:** BC30957  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Mümkünse, önceki işlev değerlendirmesinin ne olduğunu ve bunun neden zaman aşımına uğramadığını saptayın. Aksi takdirde, bu hatayla yeniden karşılaşabilirsiniz.  
  
2. Hata ayıklayıcıyı yeniden deneyin ya da Terminate ve hata ayıklamayı yeniden başlatın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio’da hata ayıklama](/visualstudio/debugger/debugger-feature-tour)
- [Hata Ayıklayıcısı ile Kodlarda gezinme](/visualstudio/debugger/navigating-through-code-with-the-debugger)

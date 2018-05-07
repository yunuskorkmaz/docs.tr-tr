---
title: Önceki bir işlev değerlendirmesi zaman aşımına uğradığından işlev değerlendirmesi devre dışı bırakıldı
ms.date: 07/20/2015
f1_keywords:
- bc30957
- vbc30957
helpviewer_keywords:
- BC30957
ms.assetid: 561e593a-f50a-4b72-a708-4cab60ec7b28
ms.openlocfilehash: 6231d48f3f90d8e436dc80bf4670886c1d030387
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="function-evaluation-is-disabled-because-a-previous-function-evaluation-timed-out"></a>Önceki bir işlev değerlendirmesi zaman aşımına uğradığından işlev değerlendirmesi devre dışı bırakıldı
Önceki bir işlev değerlendirmesi zaman aşımına uğradığından İşlev değerlendirmesi devre dışı bırakılır. İşlev değerlendirmesi yeniden etkinleştirmek için yeniden adımını veya hata ayıklamayı yeniden başlatın.  
  
 Visual Studio hata ayıklayıcısı bir yordam çağrısı bir ifade belirtir, ancak başka bir değerlendirme zaman aşımına uğradı.  
  
 Bir yordam çağrısı zaman aşımına olası nedenleri sonsuz bir döngüde olabilir veya *sonsuz bir döngüde*. Daha fazla bilgi için bkz: [için... Sonraki deyim](../../../visual-basic/language-reference/statements/for-next-statement.md).  
  
 Sonsuz bir döngüde özel bir durumdur *özyineleme*. Daha fazla bilgi için bkz: [özyinelemeli yordamlar](../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md).  
  
 **Hata Kimliği:** BC30957  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Mümkünse, önceki İşlev değerlendirmesi neydi ve zaman aşımına neyin neden olduğunu belirler. Aksi takdirde, bu hata yeniden karşılaşabilirsiniz.  
  
2.  Hata ayıklayıcı yeniden adım veya sonlandırmak ve hata ayıklamayı yeniden başlatın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio’da hata ayıklama](/visualstudio/debugger/debugging-in-visual-studio)  
 [Hata ayıklayıcısı ile kodlarda gezinme](/visualstudio/debugger/navigating-through-code-with-the-debugger)

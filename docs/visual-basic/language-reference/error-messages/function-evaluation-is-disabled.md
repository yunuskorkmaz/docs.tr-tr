---
title: Önceki bir işlev değerlendirmesi zaman aşımına uğradığından işlev değerlendirmesi devre dışı bırakıldı
ms.date: 07/20/2015
f1_keywords:
- bc30957
- vbc30957
helpviewer_keywords:
- BC30957
ms.assetid: 561e593a-f50a-4b72-a708-4cab60ec7b28
ms.openlocfilehash: bc4d05e52434cf62fa90671d29b407c83114b5d2
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59315783"
---
# <a name="function-evaluation-is-disabled-because-a-previous-function-evaluation-timed-out"></a>Önceki bir işlev değerlendirmesi zaman aşımına uğradığından işlev değerlendirmesi devre dışı bırakıldı
Bir önceki İşlev değerlendirmesi zaman aşımına uğradığından İşlev değerlendirmesi devre dışı bırakıldı. İşlev değerlendirmesi yeniden etkinleştirmek için adım yeniden veya hata ayıklamayı yeniden başlatın.  
  
 Visual Studio hata ayıklayıcı bir yordam çağrısı bir ifade belirtir, ancak başka bir değerlendirme zaman aşımına uğradı.  
  
 Bir yordam çağrısı zaman aşımına olası nedenleri sonsuz bir döngü olabilir veya *sonsuz bir döngüye*. Daha fazla bilgi için [için... Sonraki deyimi](../../../visual-basic/language-reference/statements/for-next-statement.md).  
  
 Sonsuz bir döngüye özel bir durumdur *özyineleme*. Daha fazla bilgi için [özyinelemeli yordamlar](../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md).  
  
 **Hata Kimliği:** BC30957  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Mümkünse, önceki İşlev değerlendirmesi ne olduğunu ve ne zaman aşımı nedeniyle belirler. Aksi takdirde, bu hatayla karşılaşabilirsiniz.  
  
2. Hata ayıklayıcıyı yeniden adım veya sonlandırır ve hata ayıklamayı yeniden başlatın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da Hata Ayıklama](/visualstudio/debugger/debugging-in-visual-studio)
- [Hata Ayıklayıcısı ile Kodlarda gezinme](/visualstudio/debugger/navigating-through-code-with-the-debugger)

---
title: -hıghentropyva (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- highentropyva compiler option (Visual Basic)
- /highentropyva compiler option (Visual Basic)
ms.assetid: ff25f20a-6ca2-467b-9e52-5cf439f5028e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fef3f922d3089eaca1762ffe35fa38cfe94baf22
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33656345"
---
# <a name="-highentropyva-visual-basic"></a>-hıghentropyva (Visual Basic)
Gösteren bir 64-bit yürütülebilir dosya veya tarafından işaretlenen yürütülebilir bir dosya olup olmadığını [/platform:anycpu](../../../visual-basic/reference/command-line-compiler/platform.md) derleyici seçeneği yüksek entropi adres alanı düzeni rastgele seçimini (ASLR) destekler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 İsteğe bağlı. Seçeneği varsayılan olarak kapalıdır veya belirtirseniz `-highentropyva-`. Seçenek açıksa belirtirseniz, `-highentropyva` veya `-highentropyva+`.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu seçeneği belirtirseniz, çekirdek ASLR bir parçası olarak adres alanı düzeni bir işlemin randomizes zaman uyumlu sürümlerini Windows Çekirdeği entropi yüksek derece kullanabilirsiniz. Çekirdek entropi yüksek derece kullanıyorsa, çok sayıda adresleri yığınları ve yığın gibi bellek bölgelere ayrılabilir. Sonuç olarak, belirli bellek bölge konumunu tahmin edilmesi daha zordur.  
  
 Seçenek hedef çalıştırılabilir ve herhangi bir modül, etkinleştirildiğinde, bağlı olduğu bu modüller, 64 bit işlemleri olarak çalıştırırken 4 gigabayt (GB) büyük işaretçi değerleri kaldırabilir olmalıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

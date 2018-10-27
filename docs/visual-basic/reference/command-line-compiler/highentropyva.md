---
title: -hıghentropyva (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- highentropyva compiler option (Visual Basic)
- /highentropyva compiler option (Visual Basic)
ms.assetid: ff25f20a-6ca2-467b-9e52-5cf439f5028e
ms.openlocfilehash: 5d948817d4bc71aa31c5890f6740248f4c309588
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50181507"
---
# <a name="-highentropyva-visual-basic"></a>-hıghentropyva (Visual Basic)
Belirten bir 64-bit yürütülebilir dosya ya da tarafından işaretlenen bir yürütülebilir dosya [/platform:anycpu](../../../visual-basic/reference/command-line-compiler/platform.md) derleyici seçeneği yüksek entropi adres alanı düzeni rastgele seçimini (ASLR) destekler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 İsteğe bağlı. Bu seçenek varsayılan olarak kapalıdır veya belirtirseniz `-highentropyva-`. Belirtirseniz seçeneği açıktır `-highentropyva` veya `-highentropyva+`.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu seçeneği belirtirseniz, çekirdek bir işlemin adres alanı düzeni ASLR bir parçası olarak rasgele olarak belirler, daha yüksek derece entropi Windows çekirdek uyumlu sürümlerini kullanabilirsiniz. Çekirdek entropi daha yüksek derece kullanıyorsa, çok sayıda adresleri yığınlarını ve Yığınlar gibi bölgelere bellek ayrılabilir. Sonuç olarak, belirli bir bellek bölgesinin konumunu tahmin edilmesi daha zordur.  
  
 Seçeneği, hedef çalıştırılabilir ve modüllerin açık olduğunda, bağımlı modüller 64-bit işlem çalışırken, 4 gigabayt (GB) büyük bir işaretçi değerleri işleyebilir olması gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

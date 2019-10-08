---
title: -highentropyva (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- highentropyva compiler option (Visual Basic)
- /highentropyva compiler option (Visual Basic)
ms.assetid: ff25f20a-6ca2-467b-9e52-5cf439f5028e
ms.openlocfilehash: 58026ff84f1ff501bf767adebcfc01f7de5bf4a4
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005575"
---
# <a name="-highentropyva-visual-basic"></a>-highentropyva (Visual Basic)
64 bitlik bir yürütülebilir dosyanın mı yoksa [/Platform: anycpu](../../../visual-basic/reference/command-line-compiler/platform.md) derleyicisi seçeneği tarafından işaretlenen bir yürütülebilir dosyanın yüksek Entrokten adres alanı düzeni rastgele SEÇIMINI (ASLR) destekleyip desteklemediğini gösterir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 İsteğe bağlı. Seçenek varsayılan olarak kapalıdır veya `-highentropyva-` ' yı belirtirseniz. @No__t-0 veya `-highentropyva+` ' i belirtirseniz bu seçenek açık olur.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu seçeneği belirtirseniz, Windows çekirdeğinin uyumlu sürümleri, çekirdek ASLR 'in bir parçası olarak bir işlemin adres alanı yerleşimini rasgele hale geldiğinde daha yüksek sayıda entropi kullanabilir. Çekirdek daha yüksek bir entropi kullanıyorsa, yığınlar ve yığınlar gibi bellek bölgelerine daha fazla sayıda adres tahsis edilebilir. Sonuç olarak, belirli bir bellek bölgesinin konumunu tahmin etmek daha zordur.  
  
 Seçenek açık olduğunda, hedef yürütülebilir dosya ve bağımlı olduğu tüm modüller, bu modüller 64 bit işlem olarak çalışırken 4 gigabayttan (GB) büyük olan işaretçi değerlerini işleyebilmelidir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

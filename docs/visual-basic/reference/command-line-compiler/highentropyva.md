---
title: /highentropyva (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- highentropyva compiler option (Visual Basic)
- /highentropyva compiler option (Visual Basic)
ms.assetid: ff25f20a-6ca2-467b-9e52-5cf439f5028e
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 55568808bb94f98ce7a20016fc5a2a0a2ef23a38
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="highentropyva-visual-basic"></a>/highentropyva (Visual Basic)
Gösteren bir 64-bit yürütülebilir dosya veya tarafından işaretlenen yürütülebilir bir dosya olup olmadığını [/platform:anycpu](../../../visual-basic/reference/command-line-compiler/platform.md) derleyici seçeneği yüksek entropi adres alanı düzeni rastgele seçimini (ASLR) destekler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
/highentropyva[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 İsteğe bağlı. Seçeneği varsayılan olarak kapalıdır veya belirtirseniz `/highentropyva-`. Seçenek açıksa belirtirseniz, `/highentropyva` veya `/highentropyva+`.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu seçeneği belirtirseniz, çekirdek ASLR bir parçası olarak adres alanı düzeni bir işlemin randomizes zaman uyumlu sürümlerini Windows Çekirdeği entropi yüksek derece kullanabilirsiniz. Çekirdek entropi yüksek derece kullanıyorsa, çok sayıda adresleri yığınları ve yığın gibi bellek bölgelere ayrılabilir. Sonuç olarak, belirli bellek bölge konumunu tahmin edilmesi daha zordur.  
  
 Seçenek hedef çalıştırılabilir ve herhangi bir modül, etkinleştirildiğinde, bağlı olduğu bu modüller, 64 bit işlemleri olarak çalıştırırken 4 gigabayt (GB) büyük işaretçi değerleri kaldırabilir olmalıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Örnek derleme komut satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

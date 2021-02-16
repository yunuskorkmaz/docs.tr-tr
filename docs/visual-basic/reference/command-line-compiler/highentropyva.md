---
description: Daha fazla bilgi edinin:-highentropyva (Visual Basic)
title: -highentropyva
ms.date: 03/10/2018
helpviewer_keywords:
- highentropyva compiler option (Visual Basic)
- /highentropyva compiler option (Visual Basic)
ms.assetid: ff25f20a-6ca2-467b-9e52-5cf439f5028e
ms.openlocfilehash: 90fc3713ae4f9a073a63a57c5b35114548e26cbb
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100470271"
---
# <a name="-highentropyva-visual-basic"></a>-highentropyva (Visual Basic)

64 bitlik bir yürütülebilirin veya [-Platform: anycpu](platform.md) derleyici seçeneği tarafından işaretlenen bir yürütülebilir dosyanın yüksek Entroksiz adres alanı düzeni rastgele SEÇIMINI (ASLR) destekleyip desteklemediğini gösterir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```console  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `+` &#124; `-`  
 İsteğe bağlı. Seçeneği varsayılan olarak veya öğesini belirtirseniz kapalıdır `-highentropyva-` . Veya belirtirseniz seçeneği açık olur `-highentropyva` `-highentropyva+` .  
  
## <a name="remarks"></a>Açıklamalar  

 Bu seçeneği belirtirseniz, Windows çekirdeğinin uyumlu sürümleri, çekirdek ASLR 'in bir parçası olarak bir işlemin adres alanı yerleşimini rasgele hale geldiğinde daha yüksek sayıda entropi kullanabilir. Çekirdek daha yüksek bir entropi kullanıyorsa, yığınlar ve yığınlar gibi bellek bölgelerine daha fazla sayıda adres tahsis edilebilir. Sonuç olarak, belirli bir bellek bölgesinin konumunu tahmin etmek daha zordur.  
  
 Seçenek açık olduğunda, hedef yürütülebilir dosya ve bağımlı olduğu tüm modüller, bu modüller 64 bit işlem olarak çalışırken 4 gigabayttan (GB) büyük olan işaretçi değerlerini işleyebilmelidir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic Command-Line derleyicisi](index.md)
- [Örnek Derleme Komut Satırları](sample-compilation-command-lines.md)

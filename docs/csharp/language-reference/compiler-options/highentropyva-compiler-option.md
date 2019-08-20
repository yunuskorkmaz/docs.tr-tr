---
title: -highentropyva (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /highentropyva
helpviewer_keywords:
- /highentropyva compiler option [C#]
- -highentropyva compiler option [C#]
- highentropyva compiler option [C#]
ms.assetid: eaf409b3-384e-49dd-9417-62453658f421
ms.openlocfilehash: b710bb829f6a7591159d2f2e6bacc670d21c42d1
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606851"
---
# <a name="-highentropyva-c-compiler-options"></a>-highentropyva (C# derleyici seçenekleri)
**-Highentropyva** derleyici seçeneği Windows çekirdeğine, belirli bir yürütülebilir dosyanın yüksek entropi adres alanı düzeni rastgele SEÇIMINI (ASLR) destekleyip desteklemediğini söyler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 Bu seçenek, 64 bitlik bir yürütülebilir dosyanın veya [-Platform: anycpu](./platform-compiler-option.md) derleyicisi seçeneği tarafından işaretlenen bir yürütülebilir dosyanın yüksek bir entropi sanal adres alanını desteklediğini belirtir. Seçenek varsayılan olarak devre dışıdır. Etkinleştirmek için **-highentropyva +** veya **-highentropyva** kullanın.  
  
## <a name="remarks"></a>Açıklamalar  
 **-Highentropyva** seçeneği, Windows çekirdeğinin uyumlu sürümlerinin ASLR bir parçası olarak bir işlemin adres alanı yerleşimini rastgele hale getirmek için daha yüksek bir entropi kullanmasına olanak sağlar. Daha yüksek serbestlik derecenin kullanılması, yığınlar ve yığınların gibi bellek bölgelerine daha fazla sayıda adresin ayrılabileceği anlamına gelir. Sonuç olarak, belirli bir bellek bölgesinin konumunu tahmin etmek daha zordur.  
  
 **-Highentropyva** derleyici seçeneği belirtildiğinde, hedef yürütülebilir dosya ve bağımlı olduğu tüm modüller, 64 bitlik bir işlem olarak çalışırken 4 GIGABAYTTAN (GB) büyük olan işaretçi değerlerini işleyebilmelidir.

---
description: -highentropyva (C# derleyici seçenekleri)
title: -highentropyva (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /highentropyva
helpviewer_keywords:
- /highentropyva compiler option [C#]
- -highentropyva compiler option [C#]
- highentropyva compiler option [C#]
ms.assetid: eaf409b3-384e-49dd-9417-62453658f421
ms.openlocfilehash: f3cdeb5e63d632fecbbd94501558cc53c28a918a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173210"
---
# <a name="-highentropyva-c-compiler-options"></a>-highentropyva (C# derleyici seçenekleri)

**-Highentropyva** derleyici seçeneği Windows çekirdeğine, belirli bir yürütülebilir dosyanın yüksek entropi adres alanı düzeni rastgele SEÇIMINI (ASLR) destekleyip desteklemediğini söyler.  
  
## <a name="syntax"></a>Söz dizimi  
  
```console  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `+` &#124; `-`  
 Bu seçenek, 64 bitlik bir yürütülebilir dosyanın veya [-Platform: anycpu](./platform-compiler-option.md) derleyicisi seçeneği tarafından işaretlenen bir yürütülebilir dosyanın yüksek bir entropi sanal adres alanını desteklediğini belirtir. Seçenek varsayılan olarak devre dışıdır. Etkinleştirmek için **-highentropyva +** veya **-highentropyva** kullanın.  
  
## <a name="remarks"></a>Açıklamalar  

 **-Highentropyva** seçeneği, Windows çekirdeğinin uyumlu sürümlerinin ASLR bir parçası olarak bir işlemin adres alanı yerleşimini rastgele hale getirmek için daha yüksek bir entropi kullanmasına olanak sağlar. Daha yüksek serbestlik derecenin kullanılması, yığınlar ve yığınların gibi bellek bölgelerine daha fazla sayıda adresin ayrılabileceği anlamına gelir. Sonuç olarak, belirli bir bellek bölgesinin konumunu tahmin etmek daha zordur.  
  
 **-Highentropyva** derleyici seçeneği belirtildiğinde, hedef yürütülebilir dosya ve bağımlı olduğu tüm modüller, 64 bitlik bir işlem olarak çalışırken 4 GIGABAYTTAN (GB) büyük olan işaretçi değerlerini işleyebilmelidir.

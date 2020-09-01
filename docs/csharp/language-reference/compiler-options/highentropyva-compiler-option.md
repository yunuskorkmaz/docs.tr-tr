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
ms.openlocfilehash: 2c2e2780693a89072c4bb55b318be94089bf3ced
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125663"
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

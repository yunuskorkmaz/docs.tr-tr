---
title: -highentropyva (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /highentropyva
helpviewer_keywords:
- /highentropyva compiler option [C#]
- -highentropyva compiler option [C#]
- highentropyva compiler option [C#]
ms.assetid: eaf409b3-384e-49dd-9417-62453658f421
ms.openlocfilehash: b710bb829f6a7591159d2f2e6bacc670d21c42d1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606851"
---
# <a name="-highentropyva-c-compiler-options"></a>-highentropyva (C# Derleyici Seçenekleri)
**-highentropyva** derleyici seçeneği, Windows çekirdeğine belirli bir çalıştırılabilirin yüksek entropi Adres Alanı Düzeni Randomization'ı (ASLR) destekleyip desteklemediğini söyler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
 `+`&#124;`-`  
 Bu seçenek, 64 bit çalıştırılabilir veya [-platform:anycpu](./platform-compiler-option.md) derleyici seçeneği ile işaretlenmiş bir yürütülebilir yüksek entropi sanal adres alanını desteklediğini belirtir. Seçenek varsayılan olarak devre dışı bırakılır. Bunu etkinleştirmek için **-highentropyva+** veya **-highentropyva** kullanın.  
  
## <a name="remarks"></a>Açıklamalar  
 **-highentropyva** seçeneği, ASLR'Nin bir parçası olarak bir işlemin adres alanı düzenini rasgele belirlerken Windows çekirdeğinin uyumlu sürümlerinin daha yüksek derecede entropi kullanmasını sağlar. Daha yüksek entropi derecelerinin kullanılması, yığınlar ve yığınlar gibi bellek bölgelerine daha fazla sayıda adres ayrılabileceği anlamına gelir. Sonuç olarak, belirli bir bellek bölgesinin konumunu tahmin etmek daha zordur.  
  
 **-highentropyva** derleyicisi seçeneği belirtildiğinde, hedef çalıştırılabilir ve bağlı olduğu tüm modüller, 64 bit işlem olarak çalışırken 4 gigabayttan (GB) daha büyük işaretçi değerlerini işleyebilmelidir.

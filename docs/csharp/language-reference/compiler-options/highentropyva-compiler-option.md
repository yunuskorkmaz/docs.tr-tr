---
title: -hıghentropyva (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /highentropyva
helpviewer_keywords:
- /highentropyva compiler option [C#]
- -highentropyva compiler option [C#]
- highentropyva compiler option [C#]
ms.assetid: eaf409b3-384e-49dd-9417-62453658f421
ms.openlocfilehash: 2ff63ddc48a4f5c4287fe1badb092a1db93f68dc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61662861"
---
# <a name="-highentropyva-c-compiler-options"></a>-hıghentropyva (C# derleyici seçenekleri)
**- Hıghentropyva** derleyici seçeneği, belirli bir yürütülebilir dosya yüksek entropi adres alanı düzeni rastgele seçimini (ASLR) destekleyip desteklemediğini Windows çekirdek söyler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 Bu seçenek belirten bir 64-bit yürütülebilir veya olarak işaretlenmiş bir yürütülebilir dosya [-platform: anycpu](../../../csharp/language-reference/compiler-options/platform-compiler-option.md) derleyici seçeneği yüksek entropi sanal adres alanını destekler. Seçeneği, varsayılan olarak devre dışıdır. Kullanım **- hıghentropyva +** veya **- hıghentropyva** etkinleştirin.  
  
## <a name="remarks"></a>Açıklamalar  
 **- Hıghentropyva** seçeneği entropi daha yüksek derece ASLR bir parçası olarak bir işlemin adres alanı düzeni rasgeleleştirilirken yapılırken kullanılacak Windows çekirdek uyumlu sürümlerini sağlar. Daha yüksek derece entropi kullanarak bellek bölgelere yığınlarını ve Yığınlar gibi çok sayıda adresleri ayrılabilen anlamına gelir. Sonuç olarak, belirli bir bellek bölgesinin konumunu tahmin edilmesi daha zordur.  
  
 Zaman **- hıghentropyva** derleyici seçeneği belirtilmemişse, hedef çalıştırılabilir ve bağımlı tüm modülleri 64-bit işlem olarak çalıştırılırken, 4 gigabayt (GB) büyük bir işaretçi değerleri işleyebilir olması gerekir.

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
ms.openlocfilehash: 2ff63ddc48a4f5c4287fe1badb092a1db93f68dc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33216684"
---
# <a name="-highentropyva-c-compiler-options"></a>-highentropyva (C# Derleyici Seçenekleri)
**- Hıghentropyva** derleyici seçeneği, belirli bir yürütülebilir dosya yüksek entropi adres alanı düzeni rastgele seçimini (ASLR) destekleyip desteklemediğini Windows Çekirdeği söyler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 Bu seçenek belirleyen bir 64-bit yürütülebilir dosya veya tarafından işaretlenen yürütülebilir [-platform: anycpu](../../../csharp/language-reference/compiler-options/platform-compiler-option.md) derleyici seçeneği yüksek entropi sanal adres alanı destekler. Seçeneği, varsayılan olarak devre dışıdır. Kullanım **- hıghentropyva +** veya **- hıghentropyva** etkinleştirmek için.  
  
## <a name="remarks"></a>Açıklamalar  
 **- Hıghentropyva** seçeneği ASLR bir parçası olarak adres alanı düzeni bir işlemin rasgeleleştirilirken entropi yüksek derece kullanacak şekilde Windows çekirdek uyumlu sürümlerini sağlar. Dağınık yüksek derece kullanarak çok sayıda adresleri bellek bölgelere yığınları ve yığın gibi ayrılabilen anlamına gelir. Sonuç olarak, belirli bellek bölge konumunu tahmin edilmesi daha zordur.  
  
 Zaman **- hıghentropyva** derleyici seçeneği belirtilmişse, hedef çalıştırılabilir ve bağımlı herhangi bir modül bir 64-bit işlem olarak çalıştırılırken 4 gigabayt (GB) büyük işaretçi değerleri kaldırabilir.

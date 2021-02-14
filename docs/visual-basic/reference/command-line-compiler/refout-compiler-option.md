---
description: Daha fazla bilgi edinin:-refout (Visual Basic)
title: -refout
ms.date: 03/16/2018
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [Visual Basic]
- /refout compiler option [Visual Basic]
- -refout compiler option [Visual Basic]
ms.openlocfilehash: 2760f7e60d950aaff90becad843824a2e2b4379f
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100474128"
---
# <a name="-refout-visual-basic"></a>-refout (Visual Basic)

**-Refout** seçeneği, başvuru derlemesinin çıkış olması gereken bir dosya yolunu belirtir.

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a>Söz dizimi

```console
-refout:filepath
```

## <a name="arguments"></a>Bağımsız değişkenler

`filepath`  
Başvuru derlemesinin yolu ve dosya adı. Genellikle birincil derlemenin alt klasöründe olmalıdır. Önerilen kural (MSBuild tarafından kullanılır), başvuru derlemesini birincil derlemeye göre bir "ref/" alt klasörüne yerleştirmelidir. İçindeki tüm klasörler `filepath` var olmalıdır; derleyici bunları oluşturmaz.

## <a name="remarks"></a>Açıklamalar

Visual Basic, `-refout` sürüm 15,3 ' den başlayarak anahtarı destekler.

Başvuru derlemeleri, kitaplığın ortak API yüzeyini göstermek için gereken en düşük meta veri miktarını içeren özel bir derleme türüdür. Derleme araçlarındaki bir derlemeye başvururken önemli olan tüm Üyeler için bildirimler içerirler, ancak API sözleşmeleri üzerinde herhangi bir observable etkisi olmayan özel üyelerin tüm üye uygulamalarını ve bildirimlerini hariç tutar. Daha fazla bilgi için bkz. .NET kılavuzundaki [başvuru derlemeleri](../../../standard/assembly/reference-assemblies.md) .

`-refout`Ve [`-refonly`](refonly-compiler-option.md) seçenekleri birbirini dışlıyor.

## <a name="see-also"></a>Ayrıca bkz.

- [-refonly](refonly-compiler-option.md)
- [Visual Basic Command-Line derleyicisi](index.md)
- [Örnek Derleme Komut Satırları](sample-compilation-command-lines.md)

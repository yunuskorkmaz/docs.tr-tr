---
title: -refout (Visual Basic)
ms.date: 03/16/2018
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [Visual Basic]
- /refout compiler option [Visual Basic]
- -refout compiler option [Visual Basic]
ms.openlocfilehash: 552e611f222bfcc3ce12520ecdb891fd7b8b21de
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775555"
---
# <a name="-refout-visual-basic"></a>-refout (Visual Basic)

**-Refout** seçeneği, başvuru derlemesinin çıkış olması gereken bir dosya yolunu belirtir.

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a>Sözdizimi

```console
-refout:filepath
```

## <a name="arguments"></a>Arguments

`filepath`  
Başvuru derlemesinin yolu ve dosya adı. Genellikle birincil derlemenin alt klasöründe olmalıdır. Önerilen kural (MSBuild tarafından kullanılır), başvuru derlemesini birincil derlemeye göre bir "ref/" alt klasörüne yerleştirmelidir. @No__t_0 tüm klasörler var olmalıdır; derleyici bunları oluşturmaz.

## <a name="remarks"></a>Açıklamalar

Visual Basic, sürüm 15,3 ' den başlayarak `-refout` anahtarını destekler.

Başvuru derlemeleri, kitaplığın ortak API yüzeyini göstermek için gereken en düşük meta veri miktarını içeren özel bir derleme türüdür. Derleme araçlarındaki bir derlemeye başvururken önemli olan tüm Üyeler için bildirimler içerirler, ancak API sözleşmeleri üzerinde herhangi bir observable etkisi olmayan özel üyelerin tüm üye uygulamalarını ve bildirimlerini hariç tutar. Daha fazla bilgi için bkz. .NET kılavuzundaki [başvuru derlemeleri](../../../standard/assembly/reference-assemblies.md) .

@No__t_0 ve [`-refonly`](refonly-compiler-option.md) seçenekleri birbirini dışlıyor.

## <a name="see-also"></a>Ayrıca bkz.

- [-refonly](refonly-compiler-option.md)
- [Visual Basic komut satırı derleyicisi](index.md)
- [Örnek Derleme Komut Satırları](sample-compilation-command-lines.md)

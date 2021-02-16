---
description: Daha fazla bilgi edinin:-refonly (Visual Basic)
title: -refonly
ms.date: 03/16/2018
f1_keywords:
- -refonly
helpviewer_keywords:
- /refonly compiler option [Visual Basic]
- -refonly compiler option [Visual Basic]
- refonly compiler option [Visual Basic]
ms.openlocfilehash: 283aa75fceead38c62c4cf10c1ffe08151aeac9c
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100474141"
---
# <a name="-refonly-visual-basic"></a>-Yalnızca ref(Visual Basic)

**-Refonly** seçeneği, derlemenin birincil çıktısının uygulama derlemesi yerine bir başvuru derlemesi olması gerektiğini gösterir. `-refonly`Başvuru derlemeleri yürütülene kadar parametresi, pdb 'leri çıktısını yeniden devre dışı bırakır.

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a>Syntax

```console
-refonly
```

## <a name="remarks"></a>Açıklamalar

Visual Basic, `-refonly` sürüm 15,3 ' den başlayarak anahtarı destekler.

Başvuru derlemeleri, kitaplığın ortak API yüzeyini göstermek için gereken en düşük meta veri miktarını içeren özel bir derleme türüdür. Derleme araçlarındaki bir derlemeye başvururken önemli olan tüm Üyeler için bildirimler içerirler, ancak API sözleşmeleri üzerinde herhangi bir observable etkisi olmayan özel üyelerin tüm üye uygulamalarını ve bildirimlerini hariç tutar. Daha fazla bilgi için bkz. .NET kılavuzundaki [başvuru derlemeleri](../../../standard/assembly/reference-assemblies.md) .

`-refonly`Ve [`-refout`](refout-compiler-option.md) seçenekleri birbirini dışlıyor.

## <a name="see-also"></a>Ayrıca bkz.

- [-refout](refout-compiler-option.md)
- [Visual Basic Command-Line derleyicisi](index.md)
- [Örnek Derleme Komut Satırları](sample-compilation-command-lines.md)

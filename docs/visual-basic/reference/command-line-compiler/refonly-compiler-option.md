---
title: -Yalnızca ref(Visual Basic)
ms.date: 03/16/2018
f1_keywords:
- -refonly
helpviewer_keywords:
- /refonly compiler option [Visual Basic]
- -refonly compiler option [Visual Basic]
- refonly compiler option [Visual Basic]
ms.openlocfilehash: 8e64989ac1410b51991027ffcb33e8dae0c0284b
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775560"
---
# <a name="-refonly-visual-basic"></a>-Yalnızca ref(Visual Basic)

**-Refonly** seçeneği, derlemenin birincil çıktısının uygulama derlemesi yerine bir başvuru derlemesi olması gerektiğini gösterir. Başvuru derlemeleri yürütülene kadar `-refonly` parametresi, pdb 'leri çıktısını sessizce devre dışı bırakır.

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a>Sözdizimi

```console
-refonly
```

## <a name="remarks"></a>Açıklamalar

Visual Basic, sürüm 15,3 ' den başlayarak `-refonly` anahtarını destekler.

Başvuru derlemeleri, kitaplığın ortak API yüzeyini göstermek için gereken en düşük meta veri miktarını içeren özel bir derleme türüdür. Derleme araçlarındaki bir derlemeye başvururken önemli olan tüm Üyeler için bildirimler içerirler, ancak API sözleşmeleri üzerinde herhangi bir observable etkisi olmayan özel üyelerin tüm üye uygulamalarını ve bildirimlerini hariç tutar. Daha fazla bilgi için bkz. .NET kılavuzundaki [başvuru derlemeleri](../../../standard/assembly/reference-assemblies.md) .

@No__t_0 ve [`-refout`](refout-compiler-option.md) seçenekleri birbirini dışlıyor.

## <a name="see-also"></a>Ayrıca bkz.

- [-refout](refout-compiler-option.md)
- [Visual Basic komut satırı derleyicisi](index.md)
- [Örnek Derleme Komut Satırları](sample-compilation-command-lines.md)

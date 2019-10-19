---
title: -refout (Visual Basic)
ms.date: 03/16/2018
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [Visual Basic]
- /refout compiler option [Visual Basic]
- -refout compiler option [Visual Basic]
ms.openlocfilehash: c11d83ff37da41faa3dc6b66a87e2c52c5f6c7ac
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582867"
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

Başvuru derlemeleri yalnızca meta veri içeren derlemelerdir, ancak uygulama kodu yoktur. Anonim türler hariç her şey için tür ve üye bilgilerini içerirler. Yöntem gövdeleri tek bir `throw null` ifadesiyle değiştirilmiştir. @No__t_0 yöntemi gövdelerini kullanmanın nedeni (gövdeden farklı olarak), PEVerify 'ın çalıştırılabilmesi ve geçebilmesi (Bu nedenle meta verilerin tamamlanmasının doğrulanması).

Başvuru derlemeleri derleme düzeyi [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) özniteliği içerir. Bu öznitelik kaynakta belirtilebilir (derleyicinin onu birleştirmesini gerektirmez). Bu öznitelik nedeniyle, çalışma zamanları yürütme için başvuru derlemelerini yüklemeyi reddeder (ancak yine de yalnızca bir yansıma bağlamına yüklenebilirler). Derlemeler üzerinde yansıtan araçların başvuru derlemelerini yalnızca yansıma olarak yüklediklerinden emin olunması gerekir; Aksi takdirde, çalışma zamanı bir <xref:System.BadImageFormatException> oluşturur.

@No__t_0 ve [`-refonly`](refonly-compiler-option.md) seçenekleri birbirini dışlıyor.

## <a name="see-also"></a>Ayrıca bkz.

- [-refonly](refonly-compiler-option.md)
- [Visual Basic komut satırı derleyicisi](index.md)
- [Örnek Derleme Komut Satırları](sample-compilation-command-lines.md)

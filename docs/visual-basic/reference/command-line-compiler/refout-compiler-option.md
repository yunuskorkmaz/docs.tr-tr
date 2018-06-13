---
title: -refout (Visual Basic)
ms.date: 03/16/2018
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [Visual Basic]
- /refout compiler option [Visual Basic]
- -refout compiler option [Visual Basic]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 21cea76f31bdf2ac5fcf434ee759f874f917617b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33653539"
---
# <a name="-refout-visual-basic"></a>-refout (Visual Basic)

**- Refout** seçeneği, bir dosya yolu burada referans derlemesini gerektiğini belirtir.

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a>Sözdizimi

```console
-refout:filepath
```

## <a name="arguments"></a>Arguments

 `filepath` Başvuru derlemenin dosya adı ve yolu. Genellikle bir alt birincil derlemesi klasörde olması gerekir. (MSBuild tarafından kullanılır) önerilen kuralı başvuru bütünleştirilmiş kodunda yerleştirmektir bir "ref /" Birincil derleme göreli alt klasör. Tüm klasörleri `filepath` bulunmalıdır; derleyici bunları oluşturmaz. 

## <a name="remarks"></a>Açıklamalar

Visual Basic destekler `-refout` 15.3 sürümünden başlayarak geçin.

Başvuru derlemeleri meta verileri, ancak hiçbir uygulama kodu içeren yalnızca meta veri derlemeler ' dir. Bunlar, anonim türler dışında her şeyi için tür ve üye bilgilerini içerir. Kullanıcıların yöntem gövdeleri tek bir tıklatmayla değiştirilir `throw null` deyimi. Kullanmanın nedeni `throw null` yöntem gövdeleri (aksine, gövde yok) olan PEVerify çalışmasını ve (Bu nedenle meta veri bütünlüğü doğrulama) geçirin.

Başvuru derlemeleri içeren bir derleme düzeyi [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) özniteliği. Bu öznitelik kaynağında belirtilebilir (sonra derleyici onu sentezlemek gerekmez). Bu öznitelik nedeniyle başvuru yürütme derlemelerde yüklemek çalışma zamanları Reddet (ancak bunlar hala bir salt yansıma bağlamında yüklenen olabilir). Yalnızca yansıma olarak başvuru derlemeleri yükleme emin olmak için derlemelerini yansıtacak araçları gerekir; Aksi halde, çalışma zamanı oluşturur bir <xref:System.BadImageFormatException>.

`-refout` Ve [ `-refonly` ](refonly-compiler-option.md) seçenekleri karşılıklı olarak birbirini dışlar.

## <a name="see-also"></a>Ayrıca Bkz.
[-refonly](refonly-compiler-option.md)   
[Visual Basic komut satırı derleyicisi](index.md)  
[Örnek Derleme Komut Satırları](sample-compilation-command-lines.md)  


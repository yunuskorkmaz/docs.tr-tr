---
title: -refonly (Visual Basic)
ms.date: 03/16/2018
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- -refonly
helpviewer_keywords:
- /refonly compiler option [Visual Basic]
- -refonly compiler option [Visual Basic]
- refonly compiler option [Visual Basic]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f5135ef4d33ddde27416e48c28425aa5b029237b
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2018
---
# <a name="-refonly-visual-basic"></a>-refonly (Visual Basic)

**- Refonly** seçeneği, derleme birincil çıkış uygulaması derleme yerine referans derlemesini olması gerektiğini gösterir. `-refonly` Parametre sessiz bir şekilde devre dışı bırakır pdb, kayıt çıkarma başvuru derlemeleri yürütülemez gibi.

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a>Sözdizimi

```console
-refonly
```

## <a name="remarks"></a>Açıklamalar

Visual Basic destekler `-refout` 15.3 sürümünden başlayarak geçin.

Başvuru derlemeleri meta verileri, ancak hiçbir uygulama kodu içeren yalnızca meta veri derlemeler ' dir. Bunlar, anonim türler dışında her şeyi için tür ve üye bilgilerini içerir. Kullanmanın nedeni `throw null` gövdeleri (aksine, gövde yok) olan PEVerify çalışmasını ve (Bu nedenle meta veri bütünlüğü doğrulama) geçirin.

Başvuru derlemeleri içeren bir derleme düzeyi [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) özniteliği. Bu öznitelik kaynağında belirtilebilir (sonra derleyici onu sentezlemek gerekmez). Bu öznitelik nedeniyle çalışma zamanları başvuru yürütme derlemelerde yük reddeder (ancak bunlar hala bir salt yansıma bağlamında yüklenen olabilir). Yalnızca yansıma olarak başvuru derlemeleri yükleme emin olmak için derlemelerini yansıtacak araçları gerekir; Aksi halde, çalışma zamanı oluşturur bir <xref:System.BadImageFormatException>.

`-refonly` Ve [ `-refout` ](refout-compiler-option.md) seçenekleri karşılıklı olarak birbirini dışlar.

## <a name="see-also"></a>Ayrıca bkz.
[-refout](refout-compiler-option.md)   
[Visual Basic komut satırı derleyicisi](index.md)  
[Örnek Derleme Komut Satırları](sample-compilation-command-lines.md)   

---
description: -nostdlib (C# derleyici seçenekleri)
title: -nostdlib (C# derleyici seçenekleri)
ms.date: 12/20/2019
f1_keywords:
- /nostdlib
helpviewer_keywords:
- nostdlib compiler option [C#]
- -nostdlib compiler option [C#]
- /nostdlib compiler option [C#]
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
ms.openlocfilehash: 214918b32f1f1276eb936e66daba3d372a1e9228
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125104"
---
# <a name="-nostdlib-c-compiler-options"></a>-nostdlib (C# derleyici seçenekleri)

**-nostdlib** , tüm sistem ad alanını tanımlayan mscorlib.dll içeri aktarmayı engeller.

## <a name="syntax"></a>Syntax

```console
-nostdlib[+ | -]
```

## <a name="remarks"></a>Açıklamalar

Kendi sistem ad alanınızı ve nesnelerinizi tanımlamak veya oluşturmak istiyorsanız bu seçeneği kullanın.

**-Nostdlib**belirtmezseniz, mscorlib.dll programınıza içeri aktarılır ( **-nostdlib-** belirtilerek aynı). **-Nostdlib** belirtildiğinde **-nostdlib +** belirtilerek aynıdır.

### <a name="to-set-this-compiler-option-in-visual-studio"></a>Visual Studio 'da Bu derleyici seçeneğini ayarlamak için

> [!NOTE]
> Aşağıdaki yönergeler yalnızca Visual Studio 2015 (ve önceki sürümler) için geçerlidir. **Reference mscorlib.dll** Build özelliği, Visual Studio 'nun daha yeni sürümlerinde bulunmamaktadır.

1. Projenin **Özellikler** sayfasını açın.

2. **Yapı** özellikleri sayfasına tıklayın.

3. **Gelişmiş** düğmesine tıklayın.

4. **Başvurmayın mscorlib.dll** özelliğini değiştirin.

### <a name="to-set-this-compiler-option-programmatically"></a>Bu derleyici seçeneğini program üzerinden ayarlamak için

Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A> ..

## <a name="see-also"></a>Ayrıca bkz.

- [C# derleyici seçenekleri](./index.md)

---
title: -nostdlib (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /nostdlib
helpviewer_keywords:
- nostdlib compiler option [C#]
- -nostdlib compiler option [C#]
- /nostdlib compiler option [C#]
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
ms.openlocfilehash: 486539d7abdc3e65847a0bc0e228b1b20a2b2c37
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602693"
---
# <a name="-nostdlib-c-compiler-options"></a>-nostdlib (C# derleyici seçenekleri)

**-nostdlib** , tüm sistem ad alanını tanımlayan mscorlib. dll ' nin içe aktarımını engeller.

## <a name="syntax"></a>Sözdizimi

```console
-nostdlib[+ | -]
```

## <a name="remarks"></a>Açıklamalar

Kendi sistem ad alanınızı ve nesnelerinizi tanımlamak veya oluşturmak istiyorsanız bu seçeneği kullanın.

**-Nostdlib**belirtmezseniz, mscorlib. dll programınıza içeri aktarılır ( **-nostdlib-** belirtilerek aynı). **-Nostdlib** belirtildiğinde **-nostdlib +** belirtilerek aynıdır.

### <a name="to-set-this-compiler-option-in-visual-studio"></a>Visual Studio 'da Bu derleyici seçeneğini ayarlamak için

> [!NOTE]
> Aşağıdaki yönergeler yalnızca Visual Studio 2015 (ve önceki sürümler) için geçerlidir. Visual Studio 2017 ' de **mscorlib. dll** derlemesi oluşturma özelliği yok.

1. Projenin **Özellikler** sayfasını açın.

2. **Yapı** özellikleri sayfasına tıklayın.

3. **Gelişmiş** düğmesine tıklayın.

4. **Mscorlib. dll ' nin başvurmayın** özelliğini değiştirin.

### <a name="to-set-this-compiler-option-programmatically"></a>Bu derleyici seçeneğini program üzerinden ayarlamak için

Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)

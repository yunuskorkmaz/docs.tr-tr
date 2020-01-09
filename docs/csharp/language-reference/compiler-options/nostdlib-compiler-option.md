---
title: -nostdlib (C# derleyici seçenekleri)
ms.date: 12/20/2019
f1_keywords:
- /nostdlib
helpviewer_keywords:
- nostdlib compiler option [C#]
- -nostdlib compiler option [C#]
- /nostdlib compiler option [C#]
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
ms.openlocfilehash: ad8a2b5fc87dd7beee86d96331cf3961315be533
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345084"
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
> Aşağıdaki yönergeler yalnızca Visual Studio 2015 (ve önceki sürümler) için geçerlidir. **Mscorlib. dll derleme özelliğine başvurulmayın** , Visual Studio 'nun daha yeni sürümlerinde bulunmaz.

1. Projenin **Özellikler** sayfasını açın.

2. **Yapı** özellikleri sayfasına tıklayın.

3. **Gelişmiş** düğmesine tıklayın.

4. **Mscorlib. dll ' nin başvurmayın** özelliğini değiştirin.

### <a name="to-set-this-compiler-option-programmatically"></a>Bu derleyici seçeneğini program üzerinden ayarlamak için

Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz. <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)

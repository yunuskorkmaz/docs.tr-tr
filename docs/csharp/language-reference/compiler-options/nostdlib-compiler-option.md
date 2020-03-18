---
title: -nostdlib (C# Derleyici Seçenekleri)
ms.date: 12/20/2019
f1_keywords:
- /nostdlib
helpviewer_keywords:
- nostdlib compiler option [C#]
- -nostdlib compiler option [C#]
- /nostdlib compiler option [C#]
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
ms.openlocfilehash: ad8a2b5fc87dd7beee86d96331cf3961315be533
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75345084"
---
# <a name="-nostdlib-c-compiler-options"></a>-nostdlib (C# Derleyici Seçenekleri)

**-nostdlib** tüm Sistem ad alanını tanımlayan mscorlib.dll'nin ithalatını önler.

## <a name="syntax"></a>Sözdizimi

```console
-nostdlib[+ | -]
```

## <a name="remarks"></a>Açıklamalar

Kendi Sistem ad alanınızı ve nesnelerinizi tanımlamak veya oluşturmak istiyorsanız bu seçeneği kullanın.

**-nostdlib,** mscorlib.dll belirtmezseniz programınıza alınır **(-nostdlib-** belirtilmesi yle aynıdır). **-nostdlib** belirtme **-nostdlib+** belirterek aynıdır.

### <a name="to-set-this-compiler-option-in-visual-studio"></a>Visual Studio'da bu derleyici seçeneğini ayarlamak için

> [!NOTE]
> Aşağıdaki talimatlar yalnızca Visual Studio 2015 (ve önceki sürümler) için geçerlidir. **Do not reference mscorlib.dll** build özelliği Visual Studio'nun yeni sürümlerinde yok.

1. Projenin **Özellikleri** sayfasını açın.

2. Özellikleri **Oluştur** sayfasını tıklatın.

3. **Gelişmiş** düğmesini tıklatın.

4. **Mscorlib.dll** özelliğine başvuru yapma özelliğini değiştirin.

### <a name="to-set-this-compiler-option-programmatically"></a>Bu derleyici seçeneğini program üzerinden ayarlamak için

Bu derleyici seçeneğini programlı olarak nasıl ayarlayıştırılabildiğini öğrenmek için bkz. <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>

## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)

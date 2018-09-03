---
title: -nostdlib (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /nostdlib
helpviewer_keywords:
- nostdlib compiler option [C#]
- -nostdlib compiler option [C#]
- /nostdlib compiler option [C#]
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
ms.openlocfilehash: 70007c74efe9a41bdfc15e8fa7daf3c8fc0221ed
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43484141"
---
# <a name="-nostdlib-c-compiler-options"></a>-nostdlib (C# Derleyici Seçenekleri)

**-nostdlib** tüm sistem ad alanını tanımlayan mscorlib.dll alma engeller.

## <a name="syntax"></a>Sözdizimi

```console
-nostdlib[+ | -]
```

## <a name="remarks"></a>Açıklamalar

Tanımlayın veya kendi sistem ad alanı ve nesneler oluşturmak istiyorsanız bu seçeneği kullanın.

Siz belirtmezseniz **- nostdlib**, mscorlib.dll programınız alınır (belirtmekle aynı **- nostdlib-**). Belirtme **- nostdlib** belirtmekle aynı **- nostdlib +**.

### <a name="to-set-this-compiler-option-in-visual-studio"></a>Bu derleyici seçeneğini Visual Studio'da ayarlamak için

> [!NOTE]
> Visual Studio 2015 (ve önceki sürümleri) aşağıdaki yönergeleri uygulamak yalnızca. **Mscorlib.dll dosyasına başvurma** yapı özelliği, Visual Studio 2017'de yok.

1. Açık **özellikleri** proje sayfası.

2. Tıklayın **derleme** Özellikler sayfası.

3. Tıklayın **Gelişmiş** düğmesi.

4. Değiştirme **mscorlib.dll dosyasına başvurma** özelliği.

### <a name="to-set-this-compiler-option-programmatically"></a>Bu derleyici seçeneğini program üzerinden ayarlamak için

Bu derleyici seçeneğini program üzerinden ayarlamak konusunda daha fazla bilgi için bkz: <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.

## <a name="see-also"></a>Ayrıca Bkz.

- [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)

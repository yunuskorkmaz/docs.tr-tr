---
description: -pathmap (C# derleyici seçenekleri)
title: -pathmap (C# derleyici seçenekleri)
ms.date: 05/16/2018
f1_keywords:
- /pathmap
helpviewer_keywords:
- -pathmap compiler option [C#]
- pathmap compiler option [C#]
- /pathmap compiler option [C#]
ms.openlocfilehash: 707a37c6946cfcaf429552f0aeece6b87f3ad71d
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125013"
---
# <a name="-pathmap-c-compiler-options"></a>-pathmap (C# derleyici seçenekleri)

**-Pathmap** derleyici seçeneği, fiziksel yolların derleyicinin çıkış kaynak yol adlarına nasıl eşlendiğini belirtir.

## <a name="syntax"></a>Söz dizimi

```console
-pathmap:path1=sourcePath1,path2=sourcePath2
```

## <a name="arguments"></a>Bağımsız değişkenler

 `path1` Geçerli ortamdaki kaynak dosyalarının tam yolu

 `sourcePath1` Her çıkış dosyasında yerine geçen kaynak yol `path1` .

Birden çok eşlenmiş kaynak yolunu belirtmek için, her biri virgülle ayırın.

## <a name="remarks"></a>Açıklamalar

Derleyici, kaynak yolunu aşağıdaki nedenlerden dolayı çıktısına yazar:

1. İsteğe bağlı bir parametreye uygulandığında kaynak yolu bir bağımsız değişken için değiştirilir <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> .
1. Kaynak yolu bir PDB dosyasına katıştırılır.
1. PDB dosyasının yolu bir PE (taşınabilir yürütülebilir) dosyasına katıştırılır.

Bu seçenek, derleyicinin çalıştığı makinedeki her fiziksel yolu, çıktı dosyalarında yazılması gereken karşılık gelen bir yola eşler.

## <a name="example"></a>Örnek

`t.cs` **C: \\ iş \\ testlerinde** derleyin ve bu dizini çıktıda **\publish** ile eşleyin:

```console
csc -pathmap:C:\work\tests=\publish t.cs
```

## <a name="see-also"></a>Ayrıca bkz.

- [C# derleyici seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)

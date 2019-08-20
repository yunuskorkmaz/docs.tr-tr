---
title: -pathmap (C# derleyici seçenekleri)
ms.date: 05/16/2018
f1_keywords:
- /pathmap
helpviewer_keywords:
- -pathmap compiler option [C#]
- pathmap compiler option [C#]
- /pathmap compiler option [C#]
ms.openlocfilehash: 48e96d2ec2ccbea83d573c0eb3630b1591c407a9
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606634"
---
# <a name="-pathmap-c-compiler-options"></a>-pathmap (C# derleyici seçenekleri)

**-Pathmap** derleyici seçeneği, fiziksel yolların derleyicinin çıkış kaynak yol adlarına nasıl eşlendiğini belirtir.

## <a name="syntax"></a>Sözdizimi

```console
-pathmap:path1=sourcePath1,path2=sourcePath2
```

## <a name="arguments"></a>Arguments

 `path1`Geçerli ortamdaki kaynak dosyalarının tam yolu

 `sourcePath1`Her çıkış dosyasında yerine `path1` geçen kaynak yol.

Birden çok eşlenmiş kaynak yolunu belirtmek için, her biri virgülle ayırın.

## <a name="remarks"></a>Açıklamalar

Derleyici, kaynak yolunu aşağıdaki nedenlerden dolayı çıktısına yazar:

1. İsteğe bağlı bir parametreye uygulandığında kaynak yolu bir bağımsız değişken <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> için değiştirilir.
1. Kaynak yolu bir PDB dosyasına katıştırılır.
1. PDB dosyasının yolu bir PE (taşınabilir yürütülebilir) dosyasına katıştırılır.

Bu seçenek, derleyicinin çalıştığı makinedeki her fiziksel yolu, çıktı dosyalarında yazılması gereken karşılık gelen bir yola eşler.

## <a name="example"></a>Örnek

`t.cs` **C:\\iştestlerinde\\** derleyin ve bu dizini çıktıda **\publish** ile eşleyin:

```console
csc -pathmap:C:\work\tests=\publish t.cs
```

## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)

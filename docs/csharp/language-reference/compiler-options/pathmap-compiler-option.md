---
title: -yol haritası (C# Derleyici Seçenekleri)
ms.date: 05/16/2018
f1_keywords:
- /pathmap
helpviewer_keywords:
- -pathmap compiler option [C#]
- pathmap compiler option [C#]
- /pathmap compiler option [C#]
ms.openlocfilehash: 48e96d2ec2ccbea83d573c0eb3630b1591c407a9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606634"
---
# <a name="-pathmap-c-compiler-options"></a>-yol haritası (C# Derleyici Seçenekleri)

**-pathmap** derleyici seçeneği, derleyici tarafından kaynak yol adları çıktısı için fiziksel yolların nasıl eşlenecek olduğunu belirtir.

## <a name="syntax"></a>Sözdizimi

```console
-pathmap:path1=sourcePath1,path2=sourcePath2
```

## <a name="arguments"></a>Bağımsız Değişkenler

 `path1`Geçerli ortamdaki kaynak dosyalara tam yol

 `sourcePath1`Kaynak yolu herhangi `path1` bir çıktı dosyalarında yerine geçer.

Birden çok eşlenen kaynak yolu belirtmek için, her biri virgülle ayırın.

## <a name="remarks"></a>Açıklamalar

Derleyici kaynak yolu çıktısına aşağıdaki nedenlerden dolayı yazar:

1. Kaynak yol, isteğe bağlı bir <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> parametreye uygulandığında bir bağımsız değişkenle değiştirilir.
1. Kaynak yol bir PDB dosyasına katıştırılmış.
1. PDB dosyasının yolu pe (taşınabilir çalıştırılabilir) dosyaya katıştırılır.

Bu seçenek, derleyicinin çıktı dosyalarına yazılması gereken karşılık gelen bir yola çalıştığı makinedeki her fiziksel yolu eşler.

## <a name="example"></a>Örnek

C `t.cs` dizinini derle: **\\\\çalışma testleri** ve **\çıktıda yayımlamak** için dizini eşle:

```console
csc -pathmap:C:\work\tests=\publish t.cs
```

## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)

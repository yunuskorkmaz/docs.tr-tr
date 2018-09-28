---
title: -pathmap (C# Derleyici Seçenekleri)
ms.date: 05/16/2018
f1_keywords:
- /pathmap
helpviewer_keywords:
- -pathmap compiler option [C#]
- pathmap compiler option [C#]
- /pathmap compiler option [C#]
ms.openlocfilehash: 277ab8e094f28fd5e3cbba4de12e742bb9614730
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47425790"
---
# <a name="-pathmap-c-compiler-options"></a>-pathmap (C# Derleyici Seçenekleri)

**- Pathmap** derleyici seçeneği, fiziksel yollar, derleyici tarafından kaynak yol adları çıktısına eşlemeyle ilgili bilgi belirtir.

## <a name="syntax"></a>Sözdizimi

```console
-pathmap:path1=sourcePath1,path2=sourcePath2
```

## <a name="arguments"></a>Arguments

 `path1` Geçerli ortamda kaynak dosyalarının tam yolu

 `sourcePath1` Kaynak yolu için yerine `path1` herhangi bir çıktı dosyaları içinde.

Birden çok eşleşen kaynak yolları belirlemek için her virgül ile ayırın.

## <a name="remarks"></a>Açıklamalar

Derleyici, aşağıdaki nedenlerden dolayı çıktısını kaynak yol Yazar:

1. Kaynak yolu için bağımsız değişken yerine zaman <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> için isteğe bağlı parametresi uygulanır.
1. Kaynak yolu bir PDB dosyasına eklenir.
1. PDB dosyasının yolu (taşınabilir çalıştırılabilir) PE dosyasına eklenir.

Bu seçenek derleyici çıktı dosyaları yazılmalıdır karşılık gelen bir yola çalıştırıldığı makine üzerinde her fiziksel yolu eşler.

## <a name="example"></a>Örnek

Derleme `t.cs` dizinde **C:\\çalışma\\testleri** ve bu dizine harita **\publish** çıktı:

```console
csc -pathmap:C:\work\tests=\publish t.cs
```

## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)

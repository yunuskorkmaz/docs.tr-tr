---
title: -pathmap (C# Derleyici Seçenekleri)
ms.date: 05/16/2018
f1_keywords:
- /pathmap
helpviewer_keywords:
- -pathmap compiler option [C#]
- pathmap compiler option [C#]
- /pathmap compiler option [C#]
ms.openlocfilehash: 36196ffea19cfde7ff5f830ea358d2bd83edf419
ms.sourcegitcommit: 77d9a94dac4c05827ed0663d95e0f9ad35d6682e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/24/2018
---
# <a name="-pathmap-c-compiler-options"></a>-pathmap (C# Derleyici Seçenekleri)

**- Pathmap** derleyici seçeneği nasıl derleyici tarafından kaynak yolu adları çıktısına fiziksel yollar eşleneceğini belirtir.

## <a name="syntax"></a>Sözdizimi

```console
-pathmap:path1=sourcePath1,path2=sourcePath2
```

## <a name="arguments"></a>Arguments

 `path1` Geçerli ortamda kaynak dosyalarının tam yolu

 `sourcePath1` Kaynak yolu için yerine `path1` hiçbir çıktı dosyalarında.

Birden çok eşleşen kaynak yolları belirlemek için her bir virgül ile ayırın.

## <a name="remarks"></a>Açıklamalar

Derleyici kaynak yolu yolu aşağıdaki nedenlerle çıktısını Yazar:

1. Kaynak yolu için bağımsız değişken yerine zaman <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> isteğe bağlı bir parametre uygulanır.
1. Kaynak yolu PDB dosyasında katıştırılır.
1. PDB dosyasının yolunu PE (taşınabilir yürütülebilir) dosyasına katıştırılır.

Bu seçenek her fiziksel yolu derleyici çıktı dosyaları yazılması gereken karşılık gelen bir yola çalıştığı makinede eşler.

## <a name="example"></a>Örnek

Derleme `t.cs` dizininde **C:\\iş\\testleri** ve bu dizine eşleme **\publish** çıkışı:

```console
csc -pathmap:C:\work\tests=\publish t.cs
```

## <a name="see-also"></a>Ayrıca bkz.

 [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
 [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)

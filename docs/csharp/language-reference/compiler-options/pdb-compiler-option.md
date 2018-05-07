---
title: -pdb (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /pdb
helpviewer_keywords:
- -pdb compiler option [C#]
- pdb compiler option [C#]
- /pdb compiler option [C#]
ms.assetid: e9d0f96a-5b75-45d6-9765-92538dd5f823
ms.openlocfilehash: 9f8158ec0d8de2b9249c4f69830c37480c34b390
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="-pdb-c-compiler-options"></a>-pdb (C# Derleyici Seçenekleri)
**- Pdb** derleyici seçeneği, hata ayıklama simgeleri dosyasının konumunu ve adını belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-pdb:filename  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Hata ayıklama simgeleri dosyasının konumunu ve adını.  
  
## <a name="remarks"></a>Açıklamalar  
 Belirttiğinizde [-debug (C# Derleyici Seçenekleri)](../../../csharp/language-reference/compiler-options/debug-compiler-option.md), derleyici çıkış dosyasının adı ile aynı olan bir dosya adıyla derleyici çıktı dosyası (.exe veya .dll) oluşturur, bir .pdb dosyası ile aynı dizinde oluşturulur.  
  
 **-pdb** varsayılan olmayan dosya adı ve .pdb dosyası için konum belirtmenize olanak tanır.  
  
 Visual Studio geliştirme ortamında bu derleyici seçeneği ayarlanamaz ya da programlı olarak değiştirilebilir.  
  
## <a name="example"></a>Örnek  
 Derleme `t.cs` ve tt.pdb adlı bir .pdb dosyası oluşturun:  
  
```console  
csc -debug -pdb:tt t.cs  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
 [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)

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
ms.openlocfilehash: b0a566931ac76a3adb191f423a497bc446e280c8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61662575"
---
# <a name="-pdb-c-compiler-options"></a>-pdb (C# Derleyici Seçenekleri)
**- Pdb** derleyici seçeneği, hata ayıklama sembol dosyasının konumunu ve adını belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-pdb:filename  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Hata ayıklama sembol dosyasının konumunu ve adını.  
  
## <a name="remarks"></a>Açıklamalar  
 Belirttiğinizde [-hata ayıklama (C# Derleyici Seçenekleri)](../../../csharp/language-reference/compiler-options/debug-compiler-option.md), derleyici, çıkış dosyasının adı ile aynı olan bir dosya adıyla derleyici çıktı dosyası (.exe veya .dll) oluşturur burada bir .pdb dosyası ile aynı dizinde oluşturur.  
  
 **-pdb** varsayılan olmayan dosya adı ve .pdb dosyasının konumunu belirtmenize olanak tanır.  
  
 Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlanamaz ya da programlı olarak değiştirilebilir.  
  
## <a name="example"></a>Örnek  
 Derleme `t.cs` ve tt.pdb adlı bir .pdb dosyası oluşturun:  
  
```console  
csc -debug -pdb:tt t.cs  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)

---
description: -pdb (C# derleyici seçenekleri)
title: -pdb (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /pdb
helpviewer_keywords:
- -pdb compiler option [C#]
- pdb compiler option [C#]
- /pdb compiler option [C#]
ms.assetid: e9d0f96a-5b75-45d6-9765-92538dd5f823
ms.openlocfilehash: ced1ee1f4f079830a032a628da96a389ba27da90
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91193861"
---
# <a name="-pdb-c-compiler-options"></a>-pdb (C# derleyici seçenekleri)

**-Pdb** derleyici seçeneği, hata ayıklama sembolleri dosyasının adını ve konumunu belirtir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```console  
-pdb:filename  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `filename`  
 Hata ayıklama sembolleri dosyasının adı ve konumu.  
  
## <a name="remarks"></a>Açıklamalar  

 [-Debug (C# derleyici seçenekleri)](./debug-compiler-option.md)belirttiğinizde, derleyici aynı dizinde bir. pdb dosyası oluşturur ve bu, derleyicinin çıkış dosyasını (. exe veya. dll), çıktı dosyasının adı ile aynı olan bir dosya adıyla oluşturacaktır.  
  
 **-pdb** ,. pdb dosyası için varsayılan olmayan bir dosya adı ve konum belirtmenize olanak tanır.  
  
 Bu derleyici seçeneği Visual Studio geliştirme ortamında ayarlanamaz veya program aracılığıyla değiştirilemez.  
  
## <a name="example"></a>Örnek  

 `t.cs`TT. pdb adlı bir. pdb dosyası derleyin ve oluşturun:  
  
```console  
csc -debug -pdb:tt t.cs  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# derleyici seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)

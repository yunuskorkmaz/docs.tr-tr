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
ms.openlocfilehash: 0dcafd0fd260488922c74a2330b312e80467e779
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89124922"
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

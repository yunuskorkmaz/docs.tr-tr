---
title: -pdb (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /pdb
helpviewer_keywords:
- -pdb compiler option [C#]
- pdb compiler option [C#]
- /pdb compiler option [C#]
ms.assetid: e9d0f96a-5b75-45d6-9765-92538dd5f823
ms.openlocfilehash: 3081f4716e8cd858d789db6050e635af941aa05c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602572"
---
# <a name="-pdb-c-compiler-options"></a>-pdb (C# derleyici seçenekleri)
**-Pdb** derleyici seçeneği, hata ayıklama sembolleri dosyasının adını ve konumunu belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-pdb:filename  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Hata ayıklama sembolleri dosyasının adı ve konumu.  
  
## <a name="remarks"></a>Açıklamalar  
 [-Debug (C# derleyici seçenekleri)](./debug-compiler-option.md)belirttiğinizde, derleyici aynı dizinde bir. pdb dosyası oluşturur ve bu, derleyicinin çıkış dosyasını (. exe veya. dll) çıktı dosyasının adı ile aynı olan bir dosya adı ile oluşturacaktır.  
  
 **-pdb** ,. pdb dosyası için varsayılan olmayan bir dosya adı ve konum belirtmenize olanak tanır.  
  
 Bu derleyici seçeneği Visual Studio geliştirme ortamında ayarlanamaz veya program aracılığıyla değiştirilemez.  
  
## <a name="example"></a>Örnek  
 TT `t.cs` . pdb adlı bir. pdb dosyası derleyin ve oluşturun:  
  
```console  
csc -debug -pdb:tt t.cs  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)

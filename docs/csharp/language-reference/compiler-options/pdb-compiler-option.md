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
ms.openlocfilehash: 3081f4716e8cd858d789db6050e635af941aa05c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69602572"
---
# <a name="-pdb-c-compiler-options"></a>-pdb (C# Derleyici Seçenekleri)
**-pdb** derleyici seçeneği hata ayıklama sembolleri dosyasının adını ve konumunu belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-pdb:filename  
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
 `filename`  
 Hata ayıklama sembolleri dosyasının adı ve konumu.  
  
## <a name="remarks"></a>Açıklamalar  
 [-hata ayıklama (C# Derleyici Seçenekleri)](./debug-compiler-option.md)belirttiğiniz zaman, derleyici, çıktı dosyasının adı ile aynı dosya adı ile çıktı dosyasını (.exe veya .dll) oluşturacağı aynı dizinde bir .pdb dosyası oluşturur.  
  
 **-pdb, .pdb** dosyası için varsayılan olmayan bir dosya adı ve konumu belirtmenizi sağlar.  
  
 Bu derleyici seçeneği Visual Studio geliştirme ortamında ayarlanamaz ve programlı olarak değiştirilemez.  
  
## <a name="example"></a>Örnek  
 Tt.pdb adlı bir .pdb dosyası derle `t.cs` ve oluşturun:  
  
```console  
csc -debug -pdb:tt t.cs  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)

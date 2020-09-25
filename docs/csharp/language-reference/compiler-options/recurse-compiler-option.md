---
description: -recurse (C# derleyici seçenekleri)
title: -recurse (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /recurse
helpviewer_keywords:
- /recurse compiler option [C#]
- recurse compiler option [C#]
- -recurse compiler option [C#]
ms.assetid: 4e8212e5-04e3-45b1-8a42-41bc50e683b0
ms.openlocfilehash: 9e84ff95f7f0addac1c2c2d79af0ab53572da27f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91193809"
---
# <a name="-recurse-c-compiler-options"></a>-recurse (C# derleyici seçenekleri)

-Recurse seçeneği, belirtilen dizinin (dir) veya proje dizininin tüm alt dizinlerindeki kaynak kodu dosyalarını derlemenize olanak sağlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```console  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `dir` (isteğe bağlı)  
 Aramanın başlamasını istediğiniz dizin. Bu belirtilmemişse, arama proje dizininde başlar.  
  
 `file`  
 Aranacak dosya (lar). Joker karakterlere izin verilir.  
  
## <a name="remarks"></a>Açıklamalar  

 **-Recurse** seçeneği, kaynak kodu dosyalarını belirtilen dizinin ( `dir` ) veya proje dizininin tüm alt dizinlerinde derlemenize olanak tanır.  
  
 Proje dizinindeki tüm eşleşen dosyaları **-Recurse**kullanmadan derlemek için dosya adında joker karakterler kullanabilirsiniz.  
  
 Bu derleyici seçeneği Visual Studio 'da kullanılamaz ve program aracılığıyla değiştirilemez.  
  
## <a name="example"></a>Örnek  

 Geçerli dizindeki tüm C# dosyalarını derler:  
  
```console  
csc *.cs  
```  
  
 Dir1\dir2 dizinindeki tüm C# dosyalarını ve altındaki tüm dizinleri derler ve dir2.dll üretir:  
  
```console  
csc -target:library -out:dir2.dll -recurse:dir1\dir2\*.cs  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# derleyici seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)

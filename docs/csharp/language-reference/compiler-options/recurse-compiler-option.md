---
title: -recurse (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /recurse
helpviewer_keywords:
- /recurse compiler option [C#]
- recurse compiler option [C#]
- -recurse compiler option [C#]
ms.assetid: 4e8212e5-04e3-45b1-8a42-41bc50e683b0
ms.openlocfilehash: c82e3019e1a1e3ba45a7000312b54b9d7f64a2db
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606746"
---
# <a name="-recurse-c-compiler-options"></a>-recurse (C# derleyici seçenekleri)
-Recurse seçeneği, belirtilen dizinin (dir) veya proje dizininin tüm alt dizinlerindeki kaynak kodu dosyalarını derlemenize olanak sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a>Arguments  
 `dir`seçim  
 Aramanın başlamasını istediğiniz dizin. Bu belirtilmemişse, arama proje dizininde başlar.  
  
 `file`  
 Aranacak dosya (lar). Joker karakterlere izin verilir.  
  
## <a name="remarks"></a>Açıklamalar  
 **-Recurse** seçeneği, kaynak kodu dosyalarını belirtilen dizinin (`dir`) veya proje dizininin tüm alt dizinlerinde derlemenize olanak tanır.  
  
 Proje dizinindeki tüm eşleşen dosyaları **-Recurse**kullanmadan derlemek için dosya adında joker karakterler kullanabilirsiniz.  
  
 Bu derleyici seçeneği Visual Studio 'da kullanılamaz ve program aracılığıyla değiştirilemez.  
  
## <a name="example"></a>Örnek  
 Geçerli dizindeki C# tüm dosyaları derler:  
  
```console  
csc *.cs  
```  
  
 Dir1\dir2 dizinindeki tüm C# dosyaları ve bunun altındaki dizinleri derler ve dir2. dll oluşturur:  
  
```console  
csc -target:library -out:dir2.dll -recurse:dir1\dir2\*.cs  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)

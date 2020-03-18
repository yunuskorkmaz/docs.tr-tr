---
title: -recurse (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /recurse
helpviewer_keywords:
- /recurse compiler option [C#]
- recurse compiler option [C#]
- -recurse compiler option [C#]
ms.assetid: 4e8212e5-04e3-45b1-8a42-41bc50e683b0
ms.openlocfilehash: c82e3019e1a1e3ba45a7000312b54b9d7f64a2db
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606746"
---
# <a name="-recurse-c-compiler-options"></a>-recurse (C# Derleyici Seçenekleri)
-recurse seçeneği, belirtilen dizinin (dir) veya proje dizininin tüm alt dizilişlerinde kaynak kodu dosyalarını derlemenize olanak tanır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
 `dir` (isteğe bağlı)  
 Aramanın başlamasını istediğiniz dizini. Bu belirtilmemişse, arama proje dizininde başlar.  
  
 `file`  
 Dosya(lar) aramak için. Joker karaktere izin verilir.  
  
## <a name="remarks"></a>Açıklamalar  
 **-recurse** seçeneği, belirtilen dizinin tüm alt dizilişlerinde (`dir`) veya proje dizininin kaynak kodu dosyalarını derlemenize olanak tanır.  
  
 Proje dizinindeki eşleşen tüm dosyaları **-recurse**kullanmadan derlemek için dosya adındaki joker karakterleri kullanabilirsiniz.  
  
 Bu derleyici seçeneği Visual Studio'da kullanılamaz ve programlı olarak değiştirilemez.  
  
## <a name="example"></a>Örnek  
 Geçerli dizindeki tüm C# dosyalarını derler:  
  
```console  
csc *.cs  
```  
  
 Dir1\dir2 dizinindeki tüm C# dosyalarını ve altındaki dizinleri derler ve dir2.dll oluşturur:  
  
```console  
csc -target:library -out:dir2.dll -recurse:dir1\dir2\*.cs  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)

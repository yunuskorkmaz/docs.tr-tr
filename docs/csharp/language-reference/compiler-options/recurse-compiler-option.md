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
ms.openlocfilehash: 7d18fb2b1710e074653e054d003be762d947d1be
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="-recurse-c-compiler-options"></a>-recurse (C# Derleyici Seçenekleri)
Recurse seçeneği, belirtilen dizin (dir) veya proje dizininin tüm alt dizinlerdeki kaynak kodu dosyaları derlemek sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a>Arguments  
 `dir` (isteğe bağlı)  
 Aramayı başlatmak istediğiniz dizin. Bu belirtilmezse arama proje dizininde başlar.  
  
 `file`  
 Aranacak dosya. Joker karakterlere izin verilir.  
  
## <a name="remarks"></a>Açıklamalar  
 **-Recurse** seçeneği belirtilen dizinin tüm alt dizinlerdeki kaynak kodu dosyaları derleme olanak tanır (`dir`) veya proje dizininin.  
  
 Proje dizininde eşleşen tüm dosyaları kullanmadan derlemek için dosya adında joker karakterleri kullanabilirsiniz **-recurse**.  
  
 Bu derleyici seçeneği Visual Studio'da kullanılamıyor ve programlı olarak değiştirilemez.  
  
## <a name="example"></a>Örnek  
 Geçerli dizindeki tüm C# dosyalarını derler:  
  
```console  
csc *.cs  
```  
  
 C# dosyalarını dir1\dir2 dizininde tümüne ve altındaki herhangi bir dizin derler ve dir2.dll oluşturur:  
  
```console  
csc -target:library -out:dir2.dll -recurse:dir1\dir2\*.cs  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
 [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)

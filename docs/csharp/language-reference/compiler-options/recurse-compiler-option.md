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
ms.openlocfilehash: 1fc5591cb73164e15384eb4407a6e61e903eedbb
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43529903"
---
# <a name="-recurse-c-compiler-options"></a>-recurse (C# Derleyici Seçenekleri)
Recurse seçenek, tüm alt dizinleri belirtilen dizin (dizini) veya proje dizininin kaynak kodu dosyalarını derlemek etkinleştirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a>Arguments  
 `dir` (isteğe bağlı)  
 Aramayı başlatmak istediğiniz dizin. Bu seçenek belirtilmezse arama proje dizininde başlar.  
  
 `file`  
 Aranacak dosya. Joker karakterlere izin verilir.  
  
## <a name="remarks"></a>Açıklamalar  
 **-Recurse** belirtilen dizinin tüm alt dizinlerdeki kaynak kodu dosyaları derleme seçeneği sağlar (`dir`) veya proje dizini.  
  
 Proje dizininde eşleşen tüm dosyaları kullanmadan derlemek için bir dosya adında joker karakterler kullanabilirsiniz **-recurse**.  
  
 Bu derleyici seçeneğini Visual Studio'da kullanılamıyor ve program aracılığıyla değiştirilemez.  
  
## <a name="example"></a>Örnek  
 Geçerli dizindeki tüm C# dosyaları derler:  
  
```console  
csc *.cs  
```  
  
 Tüm dir1\dir2 dizinde C# dosyaları ve dizinleri aşağıdaki derler ve dir2.dll oluşturur:  
  
```console  
csc -target:library -out:dir2.dll -recurse:dir1\dir2\*.cs  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  

- [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)

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
ms.openlocfilehash: a4a55090cf465d0eac05303392ba7500dd96ee90
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61662523"
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)

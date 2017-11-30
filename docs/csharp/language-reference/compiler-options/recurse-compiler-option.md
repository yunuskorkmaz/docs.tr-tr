---
title: "-recurse (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /recurse
helpviewer_keywords:
- /recurse compiler option [C#]
- recurse compiler option [C#]
- -recurse compiler option [C#]
ms.assetid: 4e8212e5-04e3-45b1-8a42-41bc50e683b0
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a053e5676b10de3bd2eecf6de8be7a30329962af
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="recurse-c-compiler-options"></a>/recurse (C# Derleyici Seçenekleri)
/ Recurse seçenek, tüm alt dizinlerde belirtilen dizin (dir) veya proje dizininin kaynak kodu dosyaları derlemek sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
/recurse:[dir\]file  
```  
  
## <a name="arguments"></a>Arguments  
 `dir`(isteğe bağlı)  
 Aramayı başlatmak istediğiniz dizin. Bu belirtilmezse arama proje dizininde başlar.  
  
 `file`  
 Aranacak dosya. Joker karakterlere izin verilir.  
  
## <a name="remarks"></a>Açıklamalar  
 **/Recurse** seçeneği belirtilen dizinin tüm alt dizinlerdeki kaynak kodu dosyaları derleme olanak tanır (`dir`) veya proje dizininin.  
  
 Proje dizininde eşleşen tüm dosyaları kullanmadan derlemek için dosya adında joker karakterleri kullanabilirsiniz **/recurse**.  
  
 Bu derleyici seçeneği Visual Studio'da kullanılamıyor ve programlı olarak değiştirilemez.  
  
## <a name="example"></a>Örnek  
 Geçerli dizindeki tüm C# dosyalarını derler:  
  
```console  
csc *.cs  
```  
  
 C# dosyalarını dir1\dir2 dizininde tümüne ve altındaki herhangi bir dizin derler ve dir2.dll oluşturur:  
  
```console  
csc /target:library /out:dir2.dll /recurse:dir1\dir2\*.cs  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
 [Proje ve çözüm özelliklerini yönetme](/visualstudio/ide/managing-project-and-solution-properties)

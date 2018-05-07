---
title: '@ (C# Derleyici Seçenekleri)'
ms.date: 07/20/2015
f1_keywords:
- '@'
helpviewer_keywords:
- response files, specifying for compilation [C#]
- '@ compiler option'
ms.assetid: dda4fa9f-a02c-400f-8b6a-d58834e13d7f
ms.openlocfilehash: facf2d45aff424d54dde45973cfec8cc8f93cb6a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="-c-compiler-options"></a>@ (C# Derleyici Seçenekleri)
@ Derleyici seçenekleri içeren bir dosya ve derlemek için kaynak kodu dosyaları belirttiğiniz seçeneği sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
@response_file  
```  
  
## <a name="arguments"></a>Arguments  
 `response_file`  
 Derleyici seçeneklerini veya kaynak kodu dosyaları derlemek için listeleyen bir dosya.  
  
## <a name="remarks"></a>Açıklamalar  
 Komut satırında bunlar yalnızca belirtilmiş sanki derleyici seçenekleri ve kaynak kodu dosyaları derleyici tarafından işlenir.  
  
 Bir derlemede birden fazla yanıt dosyası belirtmek için birden çok yanıt dosyası seçeneklerini belirtin. Örneğin:  
  
```  
@file1.rsp @file2.rsp  
```  
  
 Bir yanıt dosyası, birden çok derleyici seçenekleri ve kaynak kodu dosyaları tek bir satırda görünebilir. Bir tek derleyici seçeneği belirtimi (birden çok satıra yayılamaz) tek bir satırda görünmesi gerekir. Yanıt dosyaları # sembolü ile başlayan açıklamaları olabilir.  
  
 Derleyici seçeneklerini içinde bir yanıt dosyası belirtme komutlarda komut satırında verilmesine benzer olur. Bkz: [komut satırından derleme](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) daha fazla bilgi için.  
  
 Karşılaşılan derleyici komut seçeneklerini işler. Bu nedenle, komut satırı bağımsız değişkenleri yanıt dosyalarında önceden listelenen seçenekleri geçersiz kılabilirsiniz. Buna karşılık, bir yanıt dosyası seçeneklerinde komut satırında veya diğer yanıt dosyaları daha önce listelenen seçenekleri geçersiz kılar.  
  
 C# csc.exe dosya ile aynı dizinde bulunan csc.rsp dosyası sağlar. Bkz: [- noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) csc.rsp hakkında daha fazla bilgi için.  
  
 Visual Studio geliştirme ortamında bu derleyici seçeneği ayarlanamaz ya da programlı olarak değiştirilebilir.  
  
## <a name="example"></a>Örnek  
 Örnek bir yanıt dosyası birkaç satırlarından şunlardır:  
  
```console  
# build the first output file  
-target:exe -out:MyExe.exe source1.cs source2.cs  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)

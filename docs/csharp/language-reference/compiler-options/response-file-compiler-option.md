---
title: '@ (C# Derleyici Seçenekleri)'
ms.date: 07/20/2015
f1_keywords:
- '@'
helpviewer_keywords:
- response files, specifying for compilation [C#]
- '@ compiler option'
ms.assetid: dda4fa9f-a02c-400f-8b6a-d58834e13d7f
ms.openlocfilehash: 32a06c596c44cdf28e5c1bb3422b9cf8262f2c08
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54738098"
---
# <a name="-c-compiler-options"></a>@ (C# Derleyici Seçenekleri)
@ Derleyici seçenekleri içeren bir dosyayı ve kaynak kodu dosyalarını derlemek için belirttiğiniz seçenek sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
@response_file  
```  
  
## <a name="arguments"></a>Arguments  
 `response_file`  
 Derleyici Seçenekleri veya kaynak kodu dosyalarını derlemek için listeleyen bir dosya.  
  
## <a name="remarks"></a>Açıklamalar  
 Kaynak kodu dosyaları ve derleyici seçenekleri derleyici tarafından yalnızca komut satırında, belirtilmiş gibi işlenir.  
  
 Bir derlemede birden fazla yanıt dosyası belirtmek için birden çok yanıt dosyası seçeneği belirtin. Örneğin:  
  
```  
@file1.rsp @file2.rsp  
```  
  
 Bir yanıt dosyası, birden çok derleme seçenekleri ve kaynak kodu dosyaları tek bir satırda görünebilir. Bir tek derleyici seçeneği belirtimi (çok satırlı yayılamaz) tek bir satırda yer almalıdır. Yanıt dosyaları # sembolü ile başlayan açıklamaları olabilir.  
  
 Bir yanıt dosyası derleyici seçeneklerini belirterek bu komutlar komut satırında verilmesine benzer olur. Bkz: [komut satırından derleme](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) daha fazla bilgi için.  
  
 Karşılaşılan derleyici komut seçenekleri işler. Bu nedenle, komut satırı bağımsız değişkenleri, yanıt dosyaları daha önce listelenen seçeneklerini geçersiz kılabilirsiniz. Buna karşılık, bir yanıt dosyasında seçenekleri komut satırında veya diğer yanıt dosyaları daha önce listelenen seçenekleri geçersiz kılar.  
  
 C# csc.exe dosyasıyla aynı dizinde bulunan csc.rsp dosyasını sağlar. Bkz: [- noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) csc.rsp hakkında daha fazla bilgi için.  
  
 Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlanamaz ya da programlı olarak değiştirilebilir.  
  
## <a name="example"></a>Örnek  
 Birkaç örnek yanıt dosyasından şunlardır:  
  
```console  
# build the first output file  
-target:exe -out:MyExe.exe source1.cs source2.cs  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)

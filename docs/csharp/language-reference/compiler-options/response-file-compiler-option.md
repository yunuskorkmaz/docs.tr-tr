---
title: '@ (C# Derleyici Seçenekleri)'
ms.date: 07/20/2015
f1_keywords:
- '@'
helpviewer_keywords:
- response files, specifying for compilation [C#]
- '@ compiler option'
ms.assetid: dda4fa9f-a02c-400f-8b6a-d58834e13d7f
ms.openlocfilehash: f342f26ee8abe29e6c5a1477469c8b7292cd702e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43672020"
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
  
## <a name="see-also"></a>Ayrıca Bkz.  

- [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)

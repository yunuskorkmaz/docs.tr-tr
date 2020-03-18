---
title: '@ (C# Derleyici Seçenekleri)'
ms.date: 07/20/2015
f1_keywords:
- '@'
helpviewer_keywords:
- response files, specifying for compilation [C#]
- '@ compiler option'
ms.assetid: dda4fa9f-a02c-400f-8b6a-d58834e13d7f
ms.openlocfilehash: d8e5c0ec148754c3e4cebfa32ad9f44a0bb0119e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70202915"
---
# <a name="-c-compiler-options"></a>@ (C# Derleyici Seçenekleri)
@ seçeneği derleyici seçenekleri ve derlemek için kaynak kodu dosyaları içeren bir dosya belirtmenizi sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
@response_file  
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
 `response_file`  
 Derleyici seçeneklerini veya derlemide kaynak kod dosyalarını listeleyen bir dosya.  
  
## <a name="remarks"></a>Açıklamalar  
 Derleyici seçenekleri ve kaynak kod dosyaları, komut satırında belirtilmiş gibi derleyici tarafından işlenir.  
  
 Derlemede birden fazla yanıt dosyası belirtmek için birden çok yanıt dosyası seçeneği belirtin. Örnek:  
  
```console  
@file1.rsp @file2.rsp  
```  
  
 Yanıt dosyasında, birden çok derleyici seçeneği ve kaynak kodu dosyası tek bir satırda görünebilir. Tek bir derleyici seçeneği belirtimi tek bir satırda görünmelidir (birden çok satıra yayılamaz). Yanıt dosyaları # sembolü ile başlayan yorumlar olabilir.  
  
 Yanıt dosyasının içinden derleyici seçeneklerini belirtmek, komut satırında bu komutları vermek gibidir. Daha fazla bilgi için [Komut Satırı'ndan Bina'ya](./how-to-set-environment-variables-for-the-visual-studio-command-line.md) bakın.  
  
 Derleyici, komut seçeneklerini karşılaşılan şekilde işler. Bu nedenle, komut satırı bağımsız değişkenleri yanıt dosyalarında daha önce listelenen seçenekleri geçersiz kılabilir. Tersine, yanıt dosyasındaki seçenekler komut satırında veya diğer yanıt dosyalarında daha önce listelenen seçenekleri geçersiz kılar.  
  
 C# csc.exe dosyası ile aynı dizinde bulunan csc.rsp dosyasını sağlar. CSc.rsp hakkında daha fazla bilgi için [-noconfig](./noconfig-compiler-option.md) bakın.  
  
 Bu derleyici seçeneği Visual Studio geliştirme ortamında ayarlanamaz ve programlı olarak değiştirilemez.  
  
## <a name="example"></a>Örnek  
 Örnek yanıt dosyasından birkaç satır şunlardır:  
  
```console  
# build the first output file  
-target:exe -out:MyExe.exe source1.cs source2.cs  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)

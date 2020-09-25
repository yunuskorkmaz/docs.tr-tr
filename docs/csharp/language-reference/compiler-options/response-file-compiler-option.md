---
description: '@ (C# Derleyici Seçenekleri)'
title: '@ (C# Derleyici Seçenekleri)'
ms.date: 07/20/2015
f1_keywords:
- '@'
helpviewer_keywords:
- response files, specifying for compilation [C#]
- '@ compiler option'
ms.assetid: dda4fa9f-a02c-400f-8b6a-d58834e13d7f
ms.openlocfilehash: 8f7e222e194fc4ba96159ecd792765f64b4d1c57
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91193769"
---
# <a name="-c-compiler-options"></a>@ (C# Derleyici Seçenekleri)

@ Seçeneği, derlemek için derleyici seçeneklerini ve kaynak kodu dosyalarını içeren bir dosya belirtmenizi sağlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```console  
@response_file  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `response_file`  
 Derlemek için derleyici seçeneklerini veya kaynak kodu dosyalarını listeleyen bir dosya.  
  
## <a name="remarks"></a>Açıklamalar  

 Derleyici seçenekleri ve kaynak kodu dosyaları, derleyici tarafından, tıpkı komut satırında belirtildikleri gibi işlenecek şekilde işlenir.  
  
 Bir derlemede birden fazla yanıt dosyası belirtmek için, birden çok yanıt dosyası seçeneği belirtin. Örneğin:  
  
```console  
@file1.rsp @file2.rsp  
```  
  
 Bir yanıt dosyasında, bir satırda birden çok derleyici seçeneği ve kaynak kodu dosyası görünebilir. Tek bir derleyici seçenek belirtiminin tek bir satırda görünmesi gerekir (birden çok satıra yayılamaz). Yanıt dosyaları # simgesiyle başlayan açıklamalara sahip olabilir.  
  
 Bir yanıt dosyası içinden derleyici seçeneklerinin belirtilmesi, komut satırında bu komutları verme gibidir. Daha fazla bilgi için bkz. [komut satırından oluşturma](./how-to-set-environment-variables-for-the-visual-studio-command-line.md) .  
  
 Derleyici komut seçeneklerini karşılaştığı şekilde işler. Bu nedenle, komut satırı bağımsız değişkenleri yanıt dosyalarındaki daha önce listelenen seçenekleri geçersiz kılabilir. Buna karşılık, bir yanıt dosyasındaki seçenekler, önceden komut satırında veya diğer yanıt dosyalarında listelenen seçenekleri geçersiz kılar.  
  
 C#, csc.exe dosyası ile aynı dizinde bulunan CSC. rsp dosyasını sağlar. Csc. rsp hakkında daha fazla bilgi için bkz. [-noconfig](./noconfig-compiler-option.md) .  
  
 Bu derleyici seçeneği Visual Studio geliştirme ortamında ayarlanamaz veya program aracılığıyla değiştirilemez.  
  
## <a name="example"></a>Örnek  

 Örnek yanıt dosyasından birkaç satır aşağıda verilmiştir:  
  
```console  
# build the first output file  
-target:exe -out:MyExe.exe source1.cs source2.cs  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# derleyici seçenekleri](./index.md)

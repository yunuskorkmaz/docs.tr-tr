---
title: '@ (Yanıt Dosyası Belirtme) (Visual Basic)'
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- '@ (Specify Response File) compiler option [Visual Basic]'
ms.assetid: a6847eaa-e5f9-4303-9421-45b55484b9ca
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: af66000208dee0896792892a52dc6acdf5cb1e37
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2018
---
# <a name="-specify-response-file-visual-basic"></a>@ (Yanıt Dosyası Belirtme) (Visual Basic)
Derleyici seçenekleri içeren bir dosya ve derlemek için kaynak kodu dosyaları belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
@response_file  
```  
  
## <a name="arguments"></a>Arguments  
 `response_file`  
 Gerekli. Derleyici seçeneklerini veya kaynak kodu dosyaları derlemek için listeleyen bir dosya. Dosya adını tırnak işaretleri içine alın ("") boşluk içeriyorsa.  
  
## <a name="remarks"></a>Açıklamalar  
 Derleyici derleyici seçenekleri ve komut satırında belirtilmiş gibi bir yanıt dosyası içinde belirtilen kaynak kodu dosyaları işler.  
  
 Bir derlemede birden fazla yanıt dosyası belirtmek için aşağıdaki gibi birden çok yanıt dosyası seçeneklerini belirtin.  
  
```  
@file1.rsp @file2.rsp  
```  
  
 Bir yanıt dosyası, birden çok derleyici seçenekleri ve kaynak kodu dosyaları tek bir satırda görünebilir. Tek bir derleyici seçeneği belirtimi (birden çok satıra yayılamaz) tek bir satırda görünmesi gerekir. Yanıt dosyaları ile başlayan açıklamaları olabilir `#` simgesi.  
  
 Bir veya daha fazla yanıt dosyalarında belirtilen seçeneklerle komut satırında belirtilen Seçenekleri birleştirebilirsiniz. Bunları bulduğu gibi derleyici komut seçeneklerini işler. Bu nedenle, komut satırı bağımsız değişkenleri yanıt dosyalarında önceden listelenen seçenekleri geçersiz kılabilirsiniz. Buna karşılık, bir yanıt dosyası seçeneklerinde, komut satırında veya diğer yanıt dosyaları daha önce listelenen seçenekleri geçersiz kılar.  
  
 Visual Basic Vbc.exe dosya ile aynı dizinde bulunan Vbc.rsp dosyasını sağlar. Vbc.rsp dosya varsayılan olarak sürece dahil `-noconfig` seçenek kullanılır. Daha fazla bilgi için bkz: [- noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md).  
  
> [!NOTE]
>  `@` Seçeneği Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derlerken kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki satırları örnek yanıt dosyasından ' dir.  
  
```console
# build the first output file  
-target:exe   
-out:MyExe.exe  
source1.vb   
source2.vb  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte nasıl kullanılacağı ortaya `@` adlı yanıt dosyası seçeneğiyle `File1.rsp`.  
  
```console
vbc @file1.rsp  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

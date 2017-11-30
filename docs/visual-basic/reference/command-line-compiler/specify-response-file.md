---
title: "@ (Yanıt Dosyası Belirtme) (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: '@ (Specify Response File) compiler option [Visual Basic]'
ms.assetid: a6847eaa-e5f9-4303-9421-45b55484b9ca
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ced258713983ded06fa70cb65d56071b41cdc75b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
  
 Visual Basic Vbc.exe dosya ile aynı dizinde bulunan Vbc.rsp dosyasını sağlar. Vbc.rsp dosya varsayılan olarak, sürece dahil `/noconfig` seçenek kullanılır. Daha fazla bilgi için bkz: [/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md).  
  
> [!NOTE]
>  `@` Seçeneği Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derlerken kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki satırları örnek yanıt dosyasından ' dir.  
  
```  
# build the first output file  
/target:exe   
/out:MyExe.exe  
source1.vb   
source2.vb  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte nasıl kullanılacağı ortaya `@` adlı yanıt dosyası seçeneğiyle `File1.rsp`.  
  
```  
vbc @file1.rsp  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/ noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [Örnek derleme komut satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

---
title: '@ (Yanıt Dosyası Belirtme) (Visual Basic)'
ms.date: 03/13/2018
helpviewer_keywords:
- '@ (Specify Response File) compiler option [Visual Basic]'
ms.assetid: a6847eaa-e5f9-4303-9421-45b55484b9ca
ms.openlocfilehash: d790e66e04cc62011550e894eec4000a43783765
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54494789"
---
# <a name="-specify-response-file-visual-basic"></a>@ (Yanıt Dosyası Belirtme) (Visual Basic)
Derleyici seçenekleri içeren bir dosyayı ve derlemek için kaynak kodu dosyaları belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
@response_file  
```  
  
## <a name="arguments"></a>Arguments  
 `response_file`  
 Gerekli. Derleyici Seçenekleri veya kaynak kodu dosyalarına derlemek listeleyen bir dosya. Dosya adı tırnak içine alın ("") bir boşluk içeriyorsa.  
  
## <a name="remarks"></a>Açıklamalar  
 Derleyici derleyici seçenekleri ve komut satırı üzerinde belirtilmiş gibi bir yanıt dosyası içinde belirtilen kaynak kodu dosyaları işler.  
  
 Bir derlemede birden fazla yanıt dosyası belirtmek için aşağıdaki gibi birden çok yanıt dosyası seçeneği belirtin.  
  
```  
@file1.rsp @file2.rsp  
```  
  
 Bir yanıt dosyası, birden çok derleme seçenekleri ve kaynak kodu dosyaları tek bir satırda görünebilir. Tek bir derleyici seçeneği belirtimi (çok satırlı yayılamaz) tek bir satırda yer almalıdır. Yanıt dosyaları ile başlayan açıklamaları olabilir `#` simgesi.  
  
 Bir veya daha fazla yanıt dosyalarında belirtilen seçeneklerle komut satırında belirtilen seçenekler birleştirebilirsiniz. Derleyici bunları komut seçenekleri işler. Bu nedenle, komut satırı bağımsız değişkenleri, yanıt dosyaları daha önce listelenen seçeneklerini geçersiz kılabilirsiniz. Buna karşılık, bir yanıt dosyasında seçenekleri komut satırında veya diğer yanıt dosyaları daha önce listelenen seçenekleri geçersiz kılar.  
  
 Visual Basic Vbc.exe dosyasıyla aynı dizinde bulunan nezahrnovat dosyasını sağlar. Nezahrnovat dosya, sürece varsayılan olarak dahil edilir `-noconfig` seçeneği kullanılır. Daha fazla bilgi için [- noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md).  
  
> [!NOTE]
>  `@` Seçeneği, Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derleme yapılırken kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki satırları bir örnek yanıt dosyasında bulunur.  
  
```console
# build the first output file  
-target:exe   
-out:MyExe.exe  
source1.vb   
source2.vb  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek nasıl kullanılacağını gösterir `@` adlı yanıt dosyası seçeneği `File1.rsp`.  
  
```console
vbc @file1.rsp  
```  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

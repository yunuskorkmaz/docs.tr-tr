---
title: '@ (Yanıt Dosyası Belirtme) (Visual Basic)'
ms.date: 03/13/2018
helpviewer_keywords:
- '@ (Specify Response File) compiler option [Visual Basic]'
ms.assetid: a6847eaa-e5f9-4303-9421-45b55484b9ca
ms.openlocfilehash: b84d50334e56305c27c5c0bc54578ba871a28365
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937293"
---
# <a name="-specify-response-file-visual-basic"></a>@ (Yanıt Dosyası Belirtme) (Visual Basic)
Derlemek için derleyici seçeneklerini ve kaynak kodu dosyalarını içeren bir dosyayı belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
@response_file  
```  
  
## <a name="arguments"></a>Arguments  
 `response_file`  
 Gerekli. Derlemek için derleyici seçeneklerini veya kaynak kodu dosyalarını listeleyen bir dosya. Bir boşluk içeriyorsa dosya adını tırnak işaretleri ("") içine alın.  
  
## <a name="remarks"></a>Açıklamalar  
 Derleyici, bir yanıt dosyasında belirtilen derleyici seçeneklerini ve kaynak kodu dosyalarını komut satırında belirtildikleri gibi işler.  
  
 Bir derlemede birden fazla yanıt dosyası belirtmek için, aşağıdaki gibi birden çok yanıt dosyası seçeneği belirtin.  
  
```  
@file1.rsp @file2.rsp  
```  
  
 Bir yanıt dosyasında, tek satırda birden çok derleyici seçeneği ve kaynak kodu dosyası görünebilir. Tek bir derleyici-seçenek belirtiminin tek bir satırda görünmesi gerekir (birden çok satıra yayılamaz). Yanıt dosyaları `#` sembolle başlayan açıklamalara sahip olabilir.  
  
 Komut satırında belirtilen seçenekleri, bir veya daha fazla yanıt dosyasında belirtilen seçeneklerle birleştirebilirsiniz. Derleyici, komut seçeneklerini kendileriyle karşılaştığı şekilde işler. Bu nedenle, komut satırı bağımsız değişkenleri yanıt dosyalarında daha önce listelenen seçenekleri geçersiz kılabilir. Buna karşılık, bir yanıt dosyasındaki seçenekler, önceden komut satırında veya diğer yanıt dosyalarında listelenen seçenekleri geçersiz kılar.  
  
 Visual Basic, vbc. exe dosyası ile aynı dizinde bulunan Vbc. rsp dosyasını sağlar. `-noconfig` Seçenek kullanılmamışsa, vbc. rsp dosyası varsayılan olarak dahil edilir. Daha fazla bilgi için bkz. [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md).  
  
> [!NOTE]
> Bu `@` seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki satırlar örnek bir yanıt dosyasından alınır.  
  
```console
# build the first output file  
-target:exe   
-out:MyExe.exe  
source1.vb   
source2.vb  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `@` seçeneğinin adlı `File1.rsp`yanıt dosyası ile nasıl kullanılacağını gösterir.  
  
```console
vbc @file1.rsp  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

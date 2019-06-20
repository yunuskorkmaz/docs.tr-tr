---
title: -sdkpath
ms.date: 07/20/2015
f1_keywords:
- sdkpath
- -sdkpath
helpviewer_keywords:
- -sdkpath compiler option [Visual Basic]
- /sdkpath compiler option [Visual Basic]
- sdkpath compiler option [Visual Basic]
ms.assetid: fec8a3f1-b791-4a37-8af7-344859f8212d
ms.openlocfilehash: 91f64756b2fbf14dc96550420cd936973e6bec87
ms.sourcegitcommit: 4c41ec195caf03d98b7900007c3c8e24eba20d34
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/20/2019
ms.locfileid: "67268300"
---
# <a name="-sdkpath"></a>-sdkpath
Mscorlib.dll'nin ve Microsoft.VisualBasic.dll'nin konumunu belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-sdkpath:path  
```  
  
## <a name="arguments"></a>Arguments  
 `path`  
 Mscorlib.dll'nin ve Microsoft.VisualBasic.dll'nin derleme için kullanılacak sürümlerini içeren dizin. Bu yolu, yüklü olduğu kadar doğrulanmadı. Dizin adı tırnak içine alın ("") bir boşluk içeriyorsa.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu seçenek, mscorlib.dll'nin ve Microsoft.VisualBasic.dll içinde dosyaları varsayılan olmayan bir konumdan yüklemek için Visual Basic Derleyicisi söyler. `-sdkpath` Seçeneği ile kullanılmak üzere tasarlanmış [- netcf](../../../visual-basic/reference/command-line-compiler/netcf.md). .NET Compact Framework kullanan farklı sürümlerini bu destek kitaplıklar türleri ve cihazlarda bulunamadı dil özellikleri kullanmaktan kaçının.  
  
> [!NOTE]
>  `-sdkpath` Seçeneği, Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derleme yapılırken kullanılabilir. `-sdkpath` Seçeneği, Visual Basic cihaz projesi yüklendiğinde ayarlanır.  
  
 Kullanarak derleyicinin Visual Basic çalışma zamanı kitaplığı başvurusu olmadan derlemelisiniz belirtebilirsiniz `-vbruntime` derleyici seçeneği. Daha fazla bilgi için [- vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod derlenir `Myfile.vb` .NET Compact Framework ile mscorlib.dll'nin ve Microsoft.VisualBasic.dll'nin sürümlerini kullanan C sürücüsünde .NET Compact Framework'ün varsayılan yükleme dizini bulunamadı. Genellikle, .NET Compact Framework en son sürümünü kullanmanız gerekir.  
  
```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)
- [-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)

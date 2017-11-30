---
title: /sdkpath
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- sdkpath
- /sdkpath
helpviewer_keywords:
- -sdkpath compiler option [Visual Basic]
- /sdkpath compiler option [Visual Basic]
- sdkpath compiler option [Visual Basic]
ms.assetid: fec8a3f1-b791-4a37-8af7-344859f8212d
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 876922385124db3e8db12c93c75194da83d2526c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="sdkpath"></a>/sdkpath
Mscorlib.dll ve Microsoft.VisualBasic.dll içinde konumunu belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
/sdkpath:path  
```  
  
## <a name="arguments"></a>Arguments  
 `path`  
 Derleme için kullanılacak Mscorlib.dll ve Microsoft.VisualBasic.dll içinde sürümlerini içeren dizini. Bunu yüklenene kadar bu yolu doğrulanmaz. Dizin adı tırnak işaretleri içine alın ("") boşluk içeriyorsa.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu seçenek söyler [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] derleyici varsayılan olmayan konumdan Mscorlib.dll ve Microsoft.VisualBasic.dll içinde dosyaları yüklemek için. `/sdkpath` Seçeneği ile kullanılmak üzere tasarlanmış [/netcf](../../../visual-basic/reference/command-line-compiler/netcf.md). [!INCLUDE[Compact](~/includes/compact-md.md)] Bunlardan farklı sürümlerini kullanan destek kitaplıkları türleri ve farklı dil özelliklerini cihazlarda bulunamadı kullanmaktan kaçının.  
  
> [!NOTE]
>  `/sdkpath` Seçeneği Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derlerken kullanılabilir. `/sdkpath` Seçeneği ayarlanmış olduğunda bir [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] aygıt proje yüklenir.  
  
 Derleyici Visual Basic çalışma zamanı kitaplığı başvurusu olmadan kullanarak derleme belirtebilirsiniz `/vbruntime` derleyici seçeneği. Daha fazla bilgi için bkz: [/vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod derlerken `Myfile.vb` ile [!INCLUDE[Compact](~/includes/compact-md.md)], Mscorlib.dll ve Microsoft.VisualBasic.dll içinde sürümleri kullanılarak varsayılan yükleme dizininde bulunan [!INCLUDE[Compact](~/includes/compact-md.md)] C sürücüsünde. Genellikle, en son sürümünü kullanmak [!INCLUDE[Compact](~/includes/compact-md.md)].  
  
```  
vbc /netcf /sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Örnek derleme komut satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [/ netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)  
 [/ vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)

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
ms.openlocfilehash: 25368d23c398fb3674d5c2d75d4997f917a1c3d6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937350"
---
# <a name="-sdkpath"></a>-sdkpath
Mscorlib. dll ve Microsoft. VisualBasic. dll dosyasının konumunu belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-sdkpath:path  
```  
  
## <a name="arguments"></a>Arguments  
 `path`  
 Derleme için kullanılacak mscorlib. dll ve Microsoft. VisualBasic. dll sürümlerini içeren dizin. Bu yol, yükleninceye kadar doğrulanmaz. Dizin adını bir boşluk içeriyorsa tırnak işaretleri ("") içine alın.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu seçenek, Visual Basic derleyicisine mscorlib. dll ve Microsoft. VisualBasic. dll dosyalarını varsayılan olmayan bir konumdan yüklemesini söyler. Seçeneği-netcf ile kullanılmak üzere tasarlanmıştır. [](../../../visual-basic/reference/command-line-compiler/netcf.md) `-sdkpath` .NET Compact Framework, cihazlarda bulunmayan türlerin ve dil özelliklerinin kullanımını önlemek için bu destek kitaplıklarının farklı sürümlerini kullanır.  
  
> [!NOTE]
> Bu `-sdkpath` seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir. Visual Basic bir cihaz projesi yüklendiğinde bu seçenekayarlanır.`-sdkpath`  
  
 Derleyicinin `-vbruntime` derleyici seçeneğini kullanarak Visual Basic çalışma zamanı kitaplığı başvurusu olmadan derlenmesi gerektiğini belirtebilirsiniz. Daha fazla bilgi için bkz. [-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, C `Myfile.vb` sürücüsündeki .NET Compact Framework varsayılan yükleme dizininde bulunan mscorlib. dll ve Microsoft. VisualBasic. dll sürümlerini kullanarak .NET Compact Framework ile derlenir. Genellikle .NET Compact Framework en son sürümünü kullanırsınız.  
  
```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)
- [-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)

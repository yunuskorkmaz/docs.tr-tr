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
ms.openlocfilehash: 46cec7ac3cb78c4fc97e299535f9085eff6daeff
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004687"
---
# <a name="-sdkpath"></a>-sdkpath
Mscorlib. dll ve Microsoft. VisualBasic. dll dosyasının konumunu belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-sdkpath:path  
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
 `path`  
 Derleme için kullanılacak mscorlib. dll ve Microsoft. VisualBasic. dll sürümlerini içeren dizin. Bu yol, yükleninceye kadar doğrulanmaz. Dizin adını bir boşluk içeriyorsa tırnak işaretleri ("") içine alın.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu seçenek, Visual Basic derleyicisine mscorlib. dll ve Microsoft. VisualBasic. dll dosyalarını varsayılan olmayan bir konumdan yüklemesini söyler. `-sdkpath` Seçeneği [-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)ile kullanılmak üzere tasarlanmıştır. .NET Compact Framework, cihazlarda bulunmayan türlerin ve dil özelliklerinin kullanımını önlemek için bu destek kitaplıklarının farklı sürümlerini kullanır.  
  
> [!NOTE]
> Bu `-sdkpath` seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir. Visual Basic `-sdkpath` bir cihaz projesi yüklendiğinde bu seçenek ayarlanır.  
  
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

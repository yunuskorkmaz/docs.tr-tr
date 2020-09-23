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
ms.openlocfilehash: 18bf22861c1cbc3a37ef917b421491c2d01efba8
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085119"
---
# <a name="-sdkpath"></a>-sdkpath

mscorlib.dll ve Microsoft.VisualBasic.dll konumunu belirtir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```console  
-sdkpath:path  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `path`  
 Derleme için kullanılacak mscorlib.dll ve Microsoft.VisualBasic.dll sürümlerini içeren dizin. Bu yol, yükleninceye kadar doğrulanmaz. Dizin adını bir boşluk içeriyorsa tırnak işaretleri ("") içine alın.  
  
## <a name="remarks"></a>Açıklamalar  

 Bu seçenek, Visual Basic derleyicisine mscorlib.dll ve Microsoft.VisualBasic.dll dosyalarını varsayılan olmayan bir konumdan yüklemesini söyler. `-sdkpath`Seçeneği [-netcf](netcf.md)ile kullanılmak üzere tasarlanmıştır. .NET Compact Framework, cihazlarda bulunmayan türlerin ve dil özelliklerinin kullanımını önlemek için bu destek kitaplıklarının farklı sürümlerini kullanır.  
  
> [!NOTE]
> `-sdkpath`Bu seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir. `-sdkpath`Visual Basic bir cihaz projesi yüklendiğinde bu seçenek ayarlanır.  
  
 Derleyicinin derleyici seçeneğini kullanarak Visual Basic çalışma zamanı kitaplığı başvurusu olmadan derlenmesi gerektiğini belirtebilirsiniz `-vbruntime` . Daha fazla bilgi için bkz. [-vbruntime](vbruntime.md).  
  
## <a name="example"></a>Örnek  

 Aşağıdaki kod, `Myfile.vb` C sürücüsündeki .NET Compact Framework varsayılan yükleme dizininde bulunan Mscorlib.dll ve Microsoft.VisualBasic.dll sürümlerini kullanarak .NET Compact Framework ile derlenir. Genellikle .NET Compact Framework en son sürümünü kullanırsınız.  
  
```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](index.md)
- [Örnek Derleme Komut Satırları](sample-compilation-command-lines.md)
- [-netcf](netcf.md)
- [-vbruntime](vbruntime.md)

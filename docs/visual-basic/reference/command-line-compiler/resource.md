---
title: -resource
ms.date: 03/13/2018
helpviewer_keywords:
- /resource compiler option [Visual Basic]
- -resource compiler option [Visual Basic]
- /res compiler option [Visual Basic]
- res compiler option [Visual Basic]
- -res compiler option [Visual Basic]
- resource compiler option [Visual Basic]
ms.assetid: eee2f227-91f2-4f2b-a9d6-1c51c5320858
ms.openlocfilehash: a781d543dd32ffb3d0ac0b11c544dbfd8cd5d806
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348564"
---
# <a name="-resource-visual-basic"></a>-Kaynak (Visual Basic)
Bir derlemede yönetilen bir kaynak gömer.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-resource:filename[,identifier[,public|private]]  
```

veya  

```console
-res:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
  
|Terim|Tanım|  
|---|---|  
|`filename`|Gerekli. Çıkış dosyasına eklemek için kaynak dosyasının adı. Varsayılan olarak, `filename` derlemede ortaktır. Bir boşluk içeriyorsa dosya adını tırnak işaretleri ("") içine alın.|  
|`identifier`|İsteğe bağlı. Kaynağın mantıksal adı; yüklemek için kullanılan ad. Varsayılan değer, dosyanın adıdır. İsteğe bağlı olarak, aşağıdaki gibi, derleme bildiriminde kaynağın genel mi yoksa özel mi olduğunu belirtebilirsiniz: `-res:filename.res, myname.res, public`|  
  
## <a name="remarks"></a>Açıklamalar  
 Kaynak dosyasını çıkış dosyasına yerleştirmeksizin bir kaynağı derlemeye bağlamak için `-linkresource` kullanın.  
  
 `filename`, örneğin [Resgen. exe (kaynak dosya Oluşturucu)](../../../framework/tools/resgen-exe-resource-file-generator.md) veya geliştirme ortamında oluşturulmuş bir .NET Framework kaynak dosyası ise, <xref:System.Resources> ad alanındaki üyelerle erişilebilir (daha fazla bilgi için bkz. <xref:System.Resources.ResourceManager>). Çalışma zamanında diğer tüm kaynaklara erişmek için aşağıdaki yöntemlerden birini kullanın: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>veya <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.  
  
 `-resource` kısa biçimi `-res`.  
  
 Visual Studio IDE 'de `-resource` ayarlama hakkında daha fazla bilgi için bkz. [uygulama kaynaklarını yönetme (.net)](/visualstudio/ide/managing-application-resources-dotnet).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod `In.vb` derler ve kaynak dosyası `Rf.resource`ekler.  
  
```console
vbc -res:rf.resource in.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)
- [-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md)
- [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

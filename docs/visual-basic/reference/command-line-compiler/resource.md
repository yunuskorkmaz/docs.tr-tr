---
title: -Kaynak (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- /resource compiler option [Visual Basic]
- -resource compiler option [Visual Basic]
- /res compiler option [Visual Basic]
- res compiler option [Visual Basic]
- -res compiler option [Visual Basic]
- resource compiler option [Visual Basic]
ms.assetid: eee2f227-91f2-4f2b-a9d6-1c51c5320858
ms.openlocfilehash: 5bedc346381f6de293933dce14a8c5c3044b246f
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005196"
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
  
## <a name="arguments"></a>Arguments  
  
|Terim|Tanım|  
|---|---|  
|`filename`|Gerekli. Çıkış dosyasına eklemek için kaynak dosyasının adı. Varsayılan olarak, `filename`, derlemede ortaktır. Bir boşluk içeriyorsa dosya adını tırnak işaretleri ("") içine alın.|  
|`identifier`|İsteğe bağlı. Kaynağın mantıksal adı; yüklemek için kullanılan ad. Varsayılan değer, dosyanın adıdır. İsteğe bağlı olarak, aşağıdaki gibi, derleme bildiriminde kaynağın genel mi yoksa özel mi olduğunu belirtebilirsiniz: `-res:filename.res, myname.res, public`|  
  
## <a name="remarks"></a>Açıklamalar  
 Kaynak dosyasını çıkış dosyasına yerleştirmeksizin bir kaynağı derlemeye bağlamak için `-linkresource` kullanın.  
  
 @No__t-0 oluşturulmuş bir .NET Framework kaynak dosyası ise (örneğin, [Resgen. exe (kaynak dosya Oluşturucu)](../../../framework/tools/resgen-exe-resource-file-generator.md) veya geliştirme ortamında, <xref:System.Resources> ad alanındaki üyelerle erişilebilir (daha fazla bilgi için bkz. <xref:System.Resources.ResourceManager>). Çalışma zamanında diğer tüm kaynaklara erişmek için aşağıdaki yöntemlerden birini kullanın: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A> veya <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.  
  
 @No__t-0 ' ın kısa biçimi `-res` ' dir.  
  
 Visual Studio IDE 'de `-resource` ' ı ayarlama hakkında daha fazla bilgi için bkz. [uygulama kaynaklarını yönetme (.net)](/visualstudio/ide/managing-application-resources-dotnet).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod `In.vb` derler ve kaynak dosyası `Rf.resource` ' i iliştirir.  
  
```console
vbc -res:rf.resource in.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)
- [-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md)
- [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

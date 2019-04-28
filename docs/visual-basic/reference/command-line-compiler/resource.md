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
ms.openlocfilehash: 46122eaa7ca54679c9a52b939f9100c9a0747e7b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61639090"
---
# <a name="-resource-visual-basic"></a>-Kaynak (Visual Basic)
Yönetilen kaynak bir derlemeye gömer.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-resource:filename[,identifier[,public|private]]  
' -or-  
-res:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terim|Tanım|  
|---|---|  
|`filename`|Gerekli. Çıkış dosyasına eklemek için kaynak dosyanın adı. Varsayılan olarak, `filename` derleme içinde geneldir. Dosya adı tırnak içine alın ("") bir boşluk içeriyorsa.|  
|`identifier`|İsteğe bağlı. Kaynağın mantıksal adı; yüklemek için kullanılan ad. Varsayılan dosya adıdır. İsteğe bağlı olarak, kaynak olarak aşağıdaki genel veya özel derleme bildiriminde olup olmadığını belirtebilirsiniz: `-res:filename.res, myname.res, public`|  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanım `-linkresource` kaynak dosyası çıkış dosyasına koymadan bir kaynak bir derlemeye bağlanır.  
  
 Varsa `filename` olduğu bir [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] , örneğin, göre oluşturulmuş kaynak dosyası [Resgen.exe (kaynak dosya oluşturucu)](../../../framework/tools/resgen-exe-resource-file-generator.md) veya geliştirme ortamında üyelerle erişilebileceğini <xref:System.Resources> (bkz: adalanı<xref:System.Resources.ResourceManager> daha fazla bilgi için). Çalışma zamanında diğer kaynaklara erişmek için aşağıdaki yöntemlerden birini kullanın: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>, veya <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.  
  
 Kısa formunu da `-resource` olduğu `-res`.  
  
 Nasıl ayarlanacağı hakkında daha fazla bilgi için `-resource` Visual Studio IDE'de bkz [uygulama kaynaklarını yönetme (.NET)](/visualstudio/ide/managing-application-resources-dotnet).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod derlenir `In.vb` ve kaynak dosyası ekler `Rf.resource`.  
  
```console
vbc -res:rf.resource in.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)
- [-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md)
- [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

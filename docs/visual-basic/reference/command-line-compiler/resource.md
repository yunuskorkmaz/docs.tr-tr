---
title: /resource (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /resource compiler option [Visual Basic]
- -resource compiler option [Visual Basic]
- /res compiler option [Visual Basic]
- res compiler option [Visual Basic]
- -res compiler option [Visual Basic]
- resource compiler option [Visual Basic]
ms.assetid: eee2f227-91f2-4f2b-a9d6-1c51c5320858
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 858a216873ad9999722388e45d5de28398b27fbe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="resource-visual-basic"></a>/resource (Visual Basic)
Yönetilen bir kaynağın bir derlemede katıştırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
/resource:filename[,identifier[,public|private]]  
' -or-  
/res:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terim|Tanım|  
|---|---|  
|`filename`|Gerekli. Çıktı dosyasına katıştırmak için kaynak dosyanın adı. Varsayılan olarak, `filename` bütünleştirilmiş kodunda geneldir. Dosya adını tırnak işaretleri içine alın ("") boşluk içeriyorsa.|  
|`identifier`|İsteğe bağlı. Kaynak için mantıksal ad; yüklemek için kullanılan ad. Varsayılan dosya adıdır. İsteğe bağlı olarak, kaynağın aşağıdaki gibi ortak veya özel derleme bildiriminde olup olmadığını belirtebilirsiniz: `/res:``filename.res`,`myname.res`,`public`|  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanım `/linkresource` kaynak dosyasını çıktı dosyasına yerleştirerek olmadan bir kaynağı bir derlemeye bağlamak için.  
  
 Varsa `filename` olan bir [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] , örneğin, tarafından oluşturulan kaynak dosyasını [Resgen.exe (kaynak dosya oluşturucu)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) veya geliştirme ortamında üyelerle erişilebileceğini <xref:System.Resources> ad alanı (bkz: <xref:System.Resources.ResourceManager> daha fazla bilgi için). Çalışma zamanında tüm diğer kaynaklarına erişmek için aşağıdaki yöntemlerden birini kullanın: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>, veya <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.  
  
 Kısa formunu `/resource` olan `/res`.  
  
 Nasıl ayarlanacağı hakkında bilgi için `/resource` Visual Studio IDE'de bkz [yönetme uygulama kaynakları (.NET)](/visualstudio/ide/managing-application-resources-dotnet).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod derlerken `In.vb` ve ekler kaynak dosyası `Rf.resource`.  
  
```  
vbc /res:rf.resource in.vb  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/ win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)  
 [/ linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md)  
 [/ target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [Örnek derleme komut satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

---
title: /moduleassemblyname
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0d9a5307970ac745b4f102d0008e64b985c00e52
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="moduleassemblyname"></a>/moduleassemblyname
Bu modül bir parçası olacak bütünleştirilmiş kodun adını belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
/moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terim|Tanım|  
|---|---|  
|`assembly_name`|Bu modül bir parçası olacak derleme adı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Derleyici işlemleri `/moduleassemblyname` seçeneği yalnızca IF `/target:module` seçeneği belirtilmedi. Bu modül oluşturmak derleyici neden olur. Derleyici tarafından oluşturulan modülü ile belirtilen derleme için geçerli `/moduleassemblyname` seçeneği. Farklı bir derlemede modülü yerleştirirseniz, çalışma zamanı hataları oluşur.  
  
 `/moduleassemblyname` Seçeneği yalnızca aşağıdaki doğru olduğunda gereklidir:  
  
-   Modül bir veri türü erişmesi gereken bir `Friend` başvurulan bir derleme türü.  
  
-   Başvurulan derlemeyi içine modülü oluşturulacak derlemeye arkadaş derleme erişimi verildi.  
  
 Bir modül oluşturma hakkında daha fazla bilgi için bkz: [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md). Arkadaş derlemeleri hakkında daha fazla bilgi için bkz: [arkadaş derlemeleri](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055).  
  
> [!NOTE]
>  `/moduleassemblyname` Seçeneği Visual Studio geliştirme ortamında kullanılabilir değil; bir komut isteminden derleme zaman yalnızca kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: birden fazla dosya derleme](../../../framework/app-domains/how-to-build-a-multifile-assembly.md)  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/ target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [/ main](../../../visual-basic/reference/command-line-compiler/main.md)  
 [/ Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)  
 [/ addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)  
 [Derlemeler ve Genel Derleme Önbelleği](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Örnek derleme komut satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Arkadaş derlemeleri](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055)

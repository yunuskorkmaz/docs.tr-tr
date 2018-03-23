---
title: -moduleassemblyname
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
author: rpetrusha
ms.author: ronpett
ms.openlocfilehash: 0a097ea8a7e30f25a0abb877dc496fb81d1c139f
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2018
---
# <a name="-moduleassemblyname"></a>-moduleassemblyname
Bu modül bir parçası olacak bütünleştirilmiş kodun adını belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terim|Tanım|  
|---|---|  
|`assembly_name`|Bu modül bir parçası olacak derleme adı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Derleyici işlemleri `-moduleassemblyname` seçeneği yalnızca IF `-target:module` seçeneği belirtilmedi. Bu modül oluşturmak derleyici neden olur. Derleyici tarafından oluşturulan modülü ile belirtilen derleme için geçerli `-moduleassemblyname` seçeneği. Farklı bir derlemede modülü yerleştirirseniz, çalışma zamanı hataları oluşur.  
  
 `-moduleassemblyname` Seçeneği yalnızca aşağıdaki doğru olduğunda gereklidir:  
  
-   Modül bir veri türü erişmesi gereken bir `Friend` başvurulan bir derleme türü.  
  
-   Başvurulan derlemeyi içine modülü oluşturulacak derlemeye arkadaş derleme erişimi verildi.  
  
 Bir modül oluşturma hakkında daha fazla bilgi için bkz: [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md). Arkadaş derlemeleri hakkında daha fazla bilgi için bkz: [arkadaş derlemeleri](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055).  
  
> [!NOTE]
>  `-moduleassemblyname` Seçeneği Visual Studio geliştirme ortamında kullanılabilir değil; bir komut isteminden derleme zaman yalnızca kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Çok Dosyalı Bütünleştirilmiş Kod Derleme](../../../framework/app-domains/how-to-build-a-multifile-assembly.md)  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [-main](../../../visual-basic/reference/command-line-compiler/main.md)  
 [-başvuru (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)  
 [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)  
 [Derlemeler ve Genel Derleme Önbelleği](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Arkadaş Bütünleştirilmiş Kodları](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055)

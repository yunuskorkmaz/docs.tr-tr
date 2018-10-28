---
title: -moduleassemblyname
ms.date: 03/13/2018
helpviewer_keywords:
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
ms.openlocfilehash: 92fd068ef0ff892c8b76396edbf1d532a36e338c
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50189517"
---
# <a name="-moduleassemblyname"></a>-moduleassemblyname
Bu modül bir parçası olacağı derlemenin adını belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terim|Tanım|  
|---|---|  
|`assembly_name`|Bu modül bir parçası olacağı derlemenin adı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Derleyici işlemleri `-moduleassemblyname` seçeneği yalnızca şu durumlarda `-target:module` seçeneği belirtilmedi. Bu modülü oluşturmak derleyicinin neden olur. Yalnızca belirtilen derleme için geçerli olduğundan derleyici tarafından oluşturulan Modülü `-moduleassemblyname` seçeneği. Farklı bir derlemede modülü yerleştirirseniz, çalışma zamanı hataları oluşur.  
  
 `-moduleassemblyname` Seçeneği, yalnızca aşağıdaki true olduğunda gereklidir:  
  
-   Modül bir veri türü erişmesi gereken bir `Friend` başvurulan bir derleme türü.  
  
-   Başvurulan derleme modülü derlenecek olan derlemeye arkadaş derleme erişim verildi.  
  
 Bir modül oluşturma hakkında daha fazla bilgi için bkz. [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md). Arkadaş bütünleştirilmiş kodları hakkında daha fazla bilgi için bkz: [arkadaş derlemeleri](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md).  
  
> [!NOTE]
>  `-moduleassemblyname` Seçeneği, Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca bir komut istemi'nden derleme yaptığınızda kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Çok Dosyalı Bütünleştirilmiş Kod Derleme](../../../framework/app-domains/how-to-build-a-multifile-assembly.md)  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [-main](../../../visual-basic/reference/command-line-compiler/main.md)  
 [-başvuru (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)  
 [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)  
 [Derlemeler ve Genel Derleme Önbelleği](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Arkadaş Bütünleştirilmiş Kodları](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md)

---
title: -moduleassemblyname
ms.date: 03/13/2018
helpviewer_keywords:
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
ms.openlocfilehash: 5b26e36346858d95526f5d5ce7d4645bea1dbe05
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005471"
---
# <a name="-moduleassemblyname"></a>-moduleassemblyname
Bu modülün bir parçası olacağı derlemenin adını belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terim|Tanım|  
|---|---|  
|`assembly_name`|Bu modülün bir parçası olacağı derlemenin adı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Derleyici `-moduleassemblyname` seçeneğini yalnızca `-target:module` seçeneği belirtilmişse işler. Bu, derleyicinin bir modül oluşturmasına neden olur. Derleyici tarafından oluşturulan modül yalnızca `-moduleassemblyname` seçeneğiyle belirtilen derleme için geçerlidir. Modülü farklı bir derlemeye yerleştirirseniz, çalışma zamanı hataları oluşur.  
  
 @No__t-0 seçeneği yalnızca aşağıdakilerin doğru olması durumunda gereklidir:  
  
- Modüldeki bir veri türünün başvurulan bir derlemede `Friend` türüne erişmesi gerekir.  
  
- Başvurulan derleme, modülün derleyecek olduğu derlemeye arkadaş bütünleştirilmiş kodu erişimi verdi.  
  
 Modül oluşturma hakkında daha fazla bilgi için bkz. [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md). Arkadaş derlemeleri hakkında daha fazla bilgi için bkz. [arkadaş derlemeler](../../../standard/assembly/friend.md).  
  
> [!NOTE]
> @No__t-0 seçeneği, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca bir komut isteminden derleme yaptığınızda kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Çok Dosyalı Bütünleştirilmiş Kod Derleme](../../../framework/app-domains/build-multifile-assembly.md)
- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [-main](../../../visual-basic/reference/command-line-compiler/main.md)
- [-başvuru (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
- [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)
- [.NET’te bütünleştirilmiş kodlar](../../../standard/assembly/index.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Arkadaş Bütünleştirilmiş Kodları](../../../standard/assembly/friend.md)

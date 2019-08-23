---
title: -moduleassemblyname
ms.date: 03/13/2018
helpviewer_keywords:
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
ms.openlocfilehash: 052d6937846df39bd94d532e1b63ebe522dbf6c7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964683"
---
# <a name="-moduleassemblyname"></a>-moduleassemblyname
Bu modülün bir parçası olacağı derlemenin adını belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terim|Tanım|  
|---|---|  
|`assembly_name`|Bu modülün bir parçası olacağı derlemenin adı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Derleyici, `-moduleassemblyname` seçeneği yalnızca `-target:module` seçenek belirtilmişse işler. Bu, derleyicinin bir modül oluşturmasına neden olur. Derleyici tarafından oluşturulan modül yalnızca `-moduleassemblyname` seçeneğiyle belirtilen derleme için geçerlidir. Modülü farklı bir derlemeye yerleştirirseniz, çalışma zamanı hataları oluşur.  
  
 `-moduleassemblyname` Seçeneği yalnızca aşağıdakilerin doğru olması durumunda gereklidir:  
  
- Modüldeki bir veri türünün başvurulan derlemedeki bir `Friend` türe erişmesi gerekir.  
  
- Başvurulan derleme, modülün derleyecek olduğu derlemeye arkadaş bütünleştirilmiş kodu erişimi verdi.  
  
 Modül oluşturma hakkında daha fazla bilgi için bkz. [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md). Arkadaş derlemeleri hakkında daha fazla bilgi için bkz. [arkadaş derlemeler](../../../standard/assembly/friend-assemblies.md).  
  
> [!NOTE]
> Bu `-moduleassemblyname` seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca bir komut isteminden derlerken kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Çoklu dosya derlemesi oluşturma](../../../framework/app-domains/how-to-build-a-multifile-assembly.md)
- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [-main](../../../visual-basic/reference/command-line-compiler/main.md)
- [-başvuru (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
- [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)
- [.NET’te bütünleştirilmiş kodlar](../../../standard/assembly/index.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Arkadaş Bütünleştirilmiş Kodları](../../../standard/assembly/friend-assemblies.md)

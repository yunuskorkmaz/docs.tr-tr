---
title: -baseaddress
ms.date: 08/09/2018
f1_keywords:
- /baseaddress
- baseaddress
helpviewer_keywords:
- -baseaddress compiler option [Visual Basic]
- /baseaddress compiler option [Visual Basic]
- baseaddress compiler option [Visual Basic]
ms.assetid: c982bcf2-46e5-47a2-bc8f-a5cc32b7dc47
ms.openlocfilehash: 6331a55bb1d20b5804605db103dcfd2997e348d9
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42930448"
---
# <a name="-baseaddress"></a>-baseaddress
DLL oluştururken varsayılan temel adresini belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-baseaddress:address  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terim|Tanım|  
|---|---|  
|`address`|Gerekli. DLL için temel adres. Bu adres, onaltılık bir sayı olarak belirtilmelidir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir DLL için varsayılan taban adresi belirlediği [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].  
  
 Bu adres alt sıra Word'de yuvarlanır dikkat edin. Örneğin, 0x11110001 belirtirseniz 0x11110000 için yuvarlanır.  
  
 Bir DLL için imzalama işlemini tamamlamak için kullanın `–R` seçeneği tanımlayıcı adlandırma aracı (Sn.exe).  
  
 Hedef DLL değilse, bu seçenek göz ardı edilir.  
  
|-Baseaddress Visual Studio IDE'de ayarlamak için|  
|---|  
|1.  Seçili bir projeyi **Çözüm Gezgini**. Üzerinde **proje** menüsünü tıklatın **özellikleri**. <br />2.  Tıklayın **derleme** sekmesi.<br />3.  **Gelişmiş**'e tıklayın.<br />4.  Değer değiştirme **DLL temel adresi:** kutusu. **Not:** **DLL temel adresi:** kutusu, salt okunur bir DLL hedef olmadığı sürece.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Sn.exe (tanımlayıcı ad aracı)] [Sn.exe (tanımlayıcı ad aracı)](../../../framework/tools/sn-exe-strong-name-tool.md))

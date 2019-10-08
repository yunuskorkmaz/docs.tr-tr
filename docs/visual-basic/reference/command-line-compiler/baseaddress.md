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
ms.openlocfilehash: 6ee842dbe65cbd9d147e77ec523a2b031d303738
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002393"
---
# <a name="-baseaddress"></a>-baseaddress
DLL oluşturulurken varsayılan bir temel adresi belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-baseaddress:address  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terim|Tanım|  
|---|---|  
|`address`|Gerekli. DLL 'nin temel adresi. Bu adres, onaltılık bir sayı olarak belirtilmelidir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir DLL için varsayılan temel adres .NET Framework tarafından ayarlanır.  
  
 Bu adresteki alt sıra sözcüğünün yuvarlanacağını unutmayın. Örneğin, 0x11110001 belirtirseniz, 0x11110000 ' a yuvarlanır.  
  
 DLL imzalama işlemini gerçekleştirmek için, tanımlayıcı adlandırma aracının (sn. exe) `–R` seçeneğini kullanın.  
  
 Hedef bir DLL değilse, bu seçenek yoksayılır.  
  
|Visual Studio IDE 'de-BaseAddress ayarlamak için|  
|---|  
|1. **Çözüm Gezgini**bir proje seçili olmalıdır. **Proje** menüsünde **Özellikler**' e tıklayın. <br />2. **Derle** sekmesine tıklayın.<br />3. **Gelişmiş**'e tıklayın.<br />4. **dll taban adresi:** kutusunda değeri değiştirin. **Note:**      **Dll taban adresi:** kutusu, hedef dll olmadığı takdirde salt okunurdur.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Sn. exe (tanımlayıcı ad aracı)](../../../framework/tools/sn-exe-strong-name-tool.md))

---
title: /optimize
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization [Visual Basic], enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e157fb0e1fcdb3899440eed02a42b16f75541989
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="optimize"></a>/optimize
Etkinleştirir veya derleyici iyileştirmelerini devre dışı bırakır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
/optimize[ + | - ]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terim|Tanım|  
|---|---|  
|`+` &#124; `-`|İsteğe bağlı. `/optimize-` Seçeneği, derleyici iyileştirmelerini devre dışı bırakır. `/optimize+` Seçeneği iyileştirmeler sağlar. Varsayılan olarak, en iyi duruma getirme devre dışıdır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Derleyici en iyi duruma getirme, daha küçük, daha hızlı ve daha verimli çıkış dosyanızın olun. Ancak, en iyi duruma getirme kodu yeniden düzenleme yapılmasını çıktı dosyasında neden `/optimize+` hata ayıklama zorlaştırabilir.  
  
 İle oluşturulan tüm modüllerin `/target:module` bütünleştirilmiş aynı kullanmalıdır `/optimize` derleme gibi ayarlar. Daha fazla bilgi için bkz: [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).  
  
 Birleştirebilirsiniz `/optimize` ve `/debug` seçenekleri.  
  
|Ayarlamak için Visual Studio tümleşik geliştirme ortamında en iyi duruma getirme|  
|---|  
|1.  Seçili bir projeyi **Çözüm Gezgini**. Üzerinde **proje** menüsünde tıklatın **özellikleri**.<br />     <br />2.  Tıklatın **derleme** sekmesi.<br />3.  Tıklatın **Gelişmiş** düğmesi.<br />4.  Değiştirme **etkinleştirmek en iyi duruma getirme** onay kutusu.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod derlerken `T2.vb` ve derleyici iyileştirmelerini sağlar.  
  
```  
vbc t2.vb /optimize  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/ Debug (Visual Basic)](../../../visual-basic/reference/command-line-compiler/debug.md)  
 [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [/ target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)

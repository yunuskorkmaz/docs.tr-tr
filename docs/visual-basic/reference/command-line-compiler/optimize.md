---
title: -en iyi duruma getirme
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization [Visual Basic], enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7df1c873c166def9fde1bedc139470263e3e4437
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2018
---
# <a name="-optimize"></a>-en iyi duruma getirme
Etkinleştirir veya derleyici iyileştirmelerini devre dışı bırakır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-optimize[ + | - ]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terim|Tanım|  
|---|---|  
|`+` &#124; `-`|İsteğe bağlı. `-optimize-` Seçeneği, derleyici iyileştirmelerini devre dışı bırakır. `-optimize+` Seçeneği iyileştirmeler sağlar. Varsayılan olarak, en iyi duruma getirme devre dışıdır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Derleyici en iyi duruma getirme, daha küçük, daha hızlı ve daha verimli çıkış dosyanızın olun. Ancak, en iyi duruma getirme kodu yeniden düzenleme yapılmasını çıktı dosyasında neden `-optimize+` hata ayıklama zorlaştırabilir.  
  
 İle oluşturulan tüm modüllerin `-target:module` bütünleştirilmiş aynı kullanmalıdır `-optimize` derleme gibi ayarlar. Daha fazla bilgi için bkz: [-hedef (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).  
  
 Birleştirebilirsiniz `-optimize` ve `-debug` seçenekleri.  
  
|Ayarlanacak - Visual Studio tümleşik geliştirme ortamında en iyi duruma getirme|  
|---|  
|1.  Seçili bir projeyi **Çözüm Gezgini**. Üzerinde **proje** menüsünde tıklatın **özellikleri**.<br />     <br />2.  Tıklatın **derleme** sekmesi.<br />3.  Tıklatın **Gelişmiş** düğmesi.<br />4.  Değiştirme **etkinleştirmek en iyi duruma getirme** onay kutusu.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod derlerken `T2.vb` ve derleyici iyileştirmelerini sağlar.  
  
```console
vbc t2.vb -optimize  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-debug (Visual Basic)](../../../visual-basic/reference/command-line-compiler/debug.md)  
 [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)

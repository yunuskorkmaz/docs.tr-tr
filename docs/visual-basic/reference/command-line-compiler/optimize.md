---
title: -optimize
ms.date: 07/20/2015
helpviewer_keywords:
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization [Visual Basic], enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
ms.openlocfilehash: eb84e0a7038e7ff8cb399ac7222b6ac1661b5bc1
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842167"
---
# <a name="-optimize"></a>-optimize
Etkinleştirir veya derleyici iyileştirmeleri devre dışı bırakır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-optimize[ + | - ]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terim|Tanım|  
|---|---|  
|`+` &#124; `-`|İsteğe bağlı. `-optimize-` Seçeneği, derleyici iyileştirmeleri devre dışı bırakır. `-optimize+` Seçeneği iyileştirmeler sağlar. Varsayılan olarak, en iyi duruma getirme devre dışıdır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Derleyici iyileştirmeleri çıkış dosyanızı daha küçük, daha hızlı ve daha verimli olun. Ancak, çıkış dosyasında, kod yeniden iyileştirmeleri neden `-optimize+` hata ayıklamayı zorlaştırabilir.  
  
 İle oluşturulan tüm modülleri `-target:module` bir derleme, aynı kullanmalıdır `-optimize` derleme gibi ayarlar. Daha fazla bilgi için [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).  
  
 Birleştirebilirsiniz `-optimize` ve `-debug` seçenekleri.  
  
|Visual Studio tümleşik geliştirme ortamında ayarlamak için - iyileştirin|  
|---|  
|1.  Seçili bir projeyi **Çözüm Gezgini**. Üzerinde **proje** menüsünü tıklatın **özellikleri**.<br />     <br />2.  Tıklayın **derleme** sekmesi.<br />3.  Tıklayın **Gelişmiş** düğmesi.<br />4.  Değiştirme **iyileştirmeleri etkinleştir** onay kutusu.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod derlenir `T2.vb` ve derleyici iyileştirmelerini sağlar.  
  
```console
vbc t2.vb -optimize  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [-debug (Visual Basic)](../../../visual-basic/reference/command-line-compiler/debug.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)

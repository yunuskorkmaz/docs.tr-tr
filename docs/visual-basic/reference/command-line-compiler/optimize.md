---
title: -optimize
ms.date: 07/20/2015
helpviewer_keywords:
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization [Visual Basic], enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
ms.openlocfilehash: e8daf4a49123623b6470bc3c6281869f1b9b3d0f
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005377"
---
# <a name="-optimize"></a>-optimize
Derleyici iyileştirmelerini etkinleştirilir veya devre dışı bırakır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-optimize[ + | - ]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terim|Tanım|  
|---|---|  
|`+` &#124; `-`|İsteğe bağlı. @No__t-0 seçeneği derleyici iyileştirmelerini devre dışı bırakır. @No__t-0 seçeneği iyileştirmeleri sunar. Varsayılan olarak, iyileştirmeler devre dışıdır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Derleyici iyileştirmeleri çıkış dosyanızı daha küçük, daha hızlı ve daha verimli hale getirir. Ancak, iyileştirmeler çıkış dosyasında kod yeniden düzenleme ile sonuçlandığından `-optimize+`, hata ayıklamayı zorlaştırır.  
  
 Derleme için `-target:module` ile oluşturulan tüm modüllerin derleme ile aynı `-optimize` ayarları kullanması gerekir. Daha fazla bilgi için bkz. [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).  
  
 @No__t-0 ve `-debug` seçeneklerini birleştirebilirsiniz.  
  
|Visual Studio tümleşik geliştirme ortamında ayarlanacak şekilde iyileştirmek için|  
|---|  
|1. **Çözüm Gezgini**bir proje seçili olmalıdır. **Proje** menüsünde **Özellikler**' e tıklayın.<br />     <br />2. **Derle** sekmesine tıklayın.<br />3. **Gelişmiş** düğmesine tıklayın.<br />4. **Iyileştirmeleri etkinleştir** onay kutusunu değiştirin.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod `T2.vb` derler ve derleyici iyileştirmelerini sunar.  
  
```console
vbc t2.vb -optimize  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [-Debug (Visual Basic)](../../../visual-basic/reference/command-line-compiler/debug.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)

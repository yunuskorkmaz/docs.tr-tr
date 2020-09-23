---
title: -optimize
ms.date: 07/20/2015
helpviewer_keywords:
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization [Visual Basic], enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
ms.openlocfilehash: d4b50d56373676bf78a7591102095209401c907d
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91097598"
---
# <a name="-optimize"></a>-optimize

Derleyici iyileştirmelerini etkinleştirilir veya devre dışı bırakır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```console  
-optimize[ + | - ]  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  
  
|Terim|Tanım|  
|---|---|  
|`+` &#124; `-`|İsteğe bağlı. `-optimize-`Seçeneği derleyici iyileştirmelerini devre dışı bırakır. `-optimize+`Seçeneği iyileştirmeleri izin vermez. Varsayılan olarak, iyileştirmeler devre dışıdır.|  
  
## <a name="remarks"></a>Açıklamalar  

 Derleyici iyileştirmeleri çıkış dosyanızı daha küçük, daha hızlı ve daha verimli hale getirir. Ancak, iyileştirmeler çıkış dosyasında kod yeniden düzenleme ile sonuçlandığından `-optimize+` hata ayıklamayı zorlaştırır.  
  
 Bir derleme için ile oluşturulan tüm modüllerin `-target:module` derleme ile aynı ayarları kullanması gerekir `-optimize` . Daha fazla bilgi için bkz. [-target (Visual Basic)](target.md).  
  
 `-optimize`Ve `-debug` seçeneklerini birleştirebilirsiniz.  
  
|Visual Studio tümleşik geliştirme ortamında ayarlanacak şekilde iyileştirmek için|  
|---|  
|1. **Çözüm Gezgini**bir proje seçili olmalıdır. **Proje** menüsünde **Özellikler**' e tıklayın.<br />     <br />2. **Derle** sekmesine tıklayın.<br />3. **Gelişmiş** düğmesine tıklayın.<br />4. **Iyileştirmeleri etkinleştir** onay kutusunu değiştirin.|  
  
## <a name="example"></a>Örnek  

 Aşağıdaki kod, `T2.vb` derleyici iyileştirmelerini derler ve sunar.  
  
```console
vbc t2.vb -optimize  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](index.md)
- [-Debug (Visual Basic)](debug.md)
- [Örnek Derleme Komut Satırları](sample-compilation-command-lines.md)
- [-target (Visual Basic)](target.md)

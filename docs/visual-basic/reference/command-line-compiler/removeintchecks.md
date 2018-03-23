---
title: -removeintchecks
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- removeintchecks
- -removeintchecks
helpviewer_keywords:
- removeintchecks compiler option [Visual Basic]
- /removeintchecks compiler option [Visual Basic]
- -removeintchecks compiler option [Visual Basic]
ms.assetid: c1835bd5-1e38-4fba-bd2f-6984774765d4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 25a14ffaca6e61c6e3306f8ff58de441e2ba2ade
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2018
---
# <a name="-removeintchecks"></a>-removeintchecks
Taşma hatası tamsayı işlemleri açmak veya kapatmak için denetimini etkinleştirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terim|Tanım|  
|---|---|  
|`+` &#124; `-`|İsteğe bağlı. `-removeintchecks-` Seçeneği tamsayı hesaplamalarının taşma hataları için denetlenecek derleyicinin neden olur. Varsayılan, `-removeintchecks-` değeridir.<br /><br /> Belirtme `-removeintchecks` veya `-removeintchecks+` hata denetimi engeller ve tamsayı hesaplamaları daha hızlı hale getirebilir. Ancak, hata denetimi, olmadan ve veri türü kapasiteleri taştı, hatalı sonuçlar hata yükseltmeden depolanabilir.|  
  
|Visual Studio tümleşik geliştirme ortamında - removeintchecks ayarlamak için|  
|---|  
|1.  Seçili bir projeyi **Çözüm Gezgini**. Üzerinde **proje** menüsünde tıklatın **özellikleri**. <br />2.  Tıklatın **derleme** sekmesi.<br />3.  Tıklatın **Gelişmiş** düğmesi.<br />4.  Değeri değiştirme **kaldırmak tamsayı taşma denetimleri** kutusu.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod derlerken `Test.vb` ve tamsayı taşma hatası denetimini devre dışı bırakır.  
  
```console
vbc -removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

---
title: /removeintchecks
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- removeintchecks
- /removeintchecks
helpviewer_keywords:
- removeintchecks compiler option [Visual Basic]
- /removeintchecks compiler option [Visual Basic]
- -removeintchecks compiler option [Visual Basic]
ms.assetid: c1835bd5-1e38-4fba-bd2f-6984774765d4
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 917977d8e5e12c231370ab3c956aca9d96e8a8a8
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="removeintchecks"></a>/removeintchecks
Taşma hatası tamsayı işlemleri açmak veya kapatmak için denetimini etkinleştirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
/removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terim|Tanım|  
|---|---|  
|`+` &#124; `-`|İsteğe bağlı. `/removeintchecks-` Seçeneği tamsayı hesaplamalarının taşma hataları için denetlenecek derleyicinin neden olur. Varsayılan, `/removeintchecks-` değeridir.<br /><br /> Belirtme `/removeintchecks` veya `/removeintchecks+` hata denetimi engeller ve tamsayı hesaplamaları daha hızlı hale getirebilir. Ancak, hata denetimi, olmadan ve veri türü kapasiteleri taştı, hatalı sonuçlar hata yükseltmeden depolanabilir.|  
  
|Tümleşik geliştirme ortamı/removeintchecks Visual Studio'da ayarlamak için|  
|---|  
|1.  Seçili bir projeyi **Çözüm Gezgini**. Üzerinde **proje** menüsünde tıklatın **özellikleri**. <br />2.  Tıklatın **derleme** sekmesi.<br />3.  Tıklatın **Gelişmiş** düğmesi.<br />4.  Değeri değiştirme **kaldırmak tamsayı taşma denetimleri** kutusu.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod derlerken `Test.vb` ve tamsayı taşma hatası denetimini devre dışı bırakır.  
  
```  
vbc /removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

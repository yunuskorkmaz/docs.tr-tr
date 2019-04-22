---
title: -removeintchecks
ms.date: 03/13/2018
f1_keywords:
- removeintchecks
- -removeintchecks
helpviewer_keywords:
- removeintchecks compiler option [Visual Basic]
- /removeintchecks compiler option [Visual Basic]
- -removeintchecks compiler option [Visual Basic]
ms.assetid: c1835bd5-1e38-4fba-bd2f-6984774765d4
ms.openlocfilehash: c086a031d5cef4563a6769e7683dcb1110b8fe49
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58822732"
---
# <a name="-removeintchecks"></a>-removeintchecks
Taşma hatasıyla açıp tamsayı işlemleri denetleme kapatır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terim|Tanım|  
|---|---|  
|`+` &#124; `-`|İsteğe bağlı. `-removeintchecks-` Seçeneği tüm tamsayı hesaplamalar taşma hataları için denetlenecek derleyicinin neden olur. Varsayılan, `-removeintchecks-` değeridir.<br /><br /> Belirtme `-removeintchecks` veya `-removeintchecks+` hata denetimi engeller ve tamsayı hesaplamalar daha hızlı hale getirebilirsiniz. Ancak, hata denetimi olmadan ve veri türü kapasiteler taştı, hatalı sonuçlar hata yükseltmeden depolanabilir.|  
  
|-Removeintchecks Visual Studio tümleşik geliştirme ortamında ayarlamak için|  
|---|  
|1.  Seçili bir projeyi **Çözüm Gezgini**. Üzerinde **proje** menüsünü tıklatın **özellikleri**. <br />2.  Tıklayın **derleme** sekmesi.<br />3.  Tıklayın **Gelişmiş** düğmesi.<br />4.  Değerini değiştirmek **tamsayı taşması denetimlerini Kaldır** kutusu.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod derlenir `Test.vb` ve tamsayı taşma hatası denetimini devre dışı bırakır.  
  
```console
vbc -removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

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
ms.openlocfilehash: ec4722cb7088819dae95ca1b7cbc1469d957a7aa
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400480"
---
# <a name="-removeintchecks"></a>-removeintchecks
Taşma, tamsayı işlemleri için hata denetimini açar veya kapatır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```console  
-removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  
  
|Terim|Tanım|  
|---|---|  
|`+`&#124;`-`|İsteğe bağlı. `-removeintchecks-`Seçeneği, derleyicinin taşma hataları için tüm tamsayı hesaplamalarını denetlemesini sağlar. Varsayılan değer: `-removeintchecks-`.<br /><br /> `-removeintchecks` `-removeintchecks+` Hata denetimini belirtme veya engeller ve tamsayı hesaplamaları daha hızlı hale getirebilirsiniz. Ancak, hata denetimi olmadan ve veri türü kapasiteleri taşırsa, yanlış sonuçlar bir hata oluşturulmadan depolanabilir.|  
  
|Visual Studio tümleşik geliştirme ortamında-removeintdenetimleri ayarlamak için|  
|---|  
|1. **Çözüm Gezgini**bir proje seçili olmalıdır. **Proje** menüsünde **Özellikler**' e tıklayın. <br />2. **Derle** sekmesine tıklayın.<br />3. **Gelişmiş** düğmesine tıklayın.<br />4. **tamsayı taşma denetimlerini kaldır** kutusunun değerini değiştirin.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, `Test.vb` tamsayı taşmasını derler ve devre dışı bırakır-hata denetimi.  
  
```console
vbc -removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](index.md)
- [Örnek Derleme Komut Satırları](sample-compilation-command-lines.md)

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
ms.openlocfilehash: bea6ca24ea6da9000267e754d52fe0ca152f7d7f
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005233"
---
# <a name="-removeintchecks"></a>-removeintchecks
Taşma, tamsayı işlemleri için hata denetimini açar veya kapatır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
  
|Sözleşme Dönemi|Tanım|  
|---|---|  
|`+`&#124;`-`|İsteğe bağlı. Seçeneği `-removeintchecks-` , derleyicinin taşma hataları için tüm tamsayı hesaplamalarını denetlemesini sağlar. Varsayılan değer: `-removeintchecks-`.<br /><br /> Hata `-removeintchecks` denetimini `-removeintchecks+` belirtme veya engeller ve tamsayı hesaplamaları daha hızlı hale getirebilirsiniz. Ancak, hata denetimi olmadan ve veri türü kapasiteleri taşırsa, yanlış sonuçlar bir hata oluşturulmadan depolanabilir.|  
  
|Visual Studio tümleşik geliştirme ortamında-removeintdenetimleri ayarlamak için|  
|---|  
|1. **Çözüm Gezgini**bir proje seçili olmalıdır. **Proje** menüsünde **Özellikler**' e tıklayın. <br />2. **Derle** sekmesine tıklayın.<br />3. **Gelişmiş** düğmesine tıklayın.<br />4. **tamsayı taşma denetimlerini kaldır** kutusunun değerini değiştirin.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, tamsayı `Test.vb` taşmasını derler ve devre dışı bırakır-hata denetimi.  
  
```console
vbc -removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

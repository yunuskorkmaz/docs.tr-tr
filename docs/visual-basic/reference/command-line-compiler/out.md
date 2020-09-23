---
title: -out
ms.date: 07/20/2015
helpviewer_keywords:
- /out compiler option [Visual Basic]
- -out compiler option [Visual Basic]
- out compiler option [Visual Basic]
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
ms.openlocfilehash: 7c013270c8a6b7c2b28f02766df7437b43075dd2
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91098910"
---
# <a name="-out-visual-basic"></a>-Out (Visual Basic)

Çıktı dosyasının adını belirtir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```console  
-out:filename  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  
  
|Terim|Tanım|  
|---|---|  
|`filename`|Gereklidir. Derleyicinin oluşturduğu çıkış dosyasının adı. Dosya adı bir boşluk içeriyorsa, adı tırnak işaretleri ("") içine alın.|  
  
## <a name="remarks"></a>Açıklamalar  

 Oluşturulacak dosyanın tam adını ve uzantısını belirtin. Bunu yapmazsanız,. exe dosyası, yordamı içeren kaynak kodu dosyasından adını alır `Sub Main` ve. dll dosyası adı ilk kaynak kodu dosyasından alır.  
  
 Bir. exe veya. dll uzantısı olmadan bir dosya adı belirtirseniz, derleyici, derleyici seçeneği için belirtilen değere bağlı olarak uzantıyı sizin için otomatik olarak ekler `-target` .  
  
|Visual Studio tümleşik geliştirme ortamında ayarlamak için|  
|---|  
|1. **Çözüm Gezgini**bir proje seçili olmalıdır. **Proje** menüsünde **Özellikler**' e tıklayın. <br />2. **uygulama** sekmesine tıklayın.<br />3. **derleme adı** kutusundaki değeri değiştirin.|  
  
## <a name="example"></a>Örnek  

 Aşağıdaki kod derleme `T2.vb` ve çıkış dosyası oluşturur `T2.exe` .  
  
```console
vbc t2.vb -out:t3.exe  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](index.md)
- [-target (Visual Basic)](target.md)
- [Örnek Derleme Komut Satırları](sample-compilation-command-lines.md)

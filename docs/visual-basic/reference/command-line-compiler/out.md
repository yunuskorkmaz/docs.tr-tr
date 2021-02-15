---
description: Daha fazla bilgi edinin:-Out (Visual Basic)
title: -out
ms.date: 07/20/2015
helpviewer_keywords:
- /out compiler option [Visual Basic]
- -out compiler option [Visual Basic]
- out compiler option [Visual Basic]
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
ms.openlocfilehash: 82fb43ecf2239c38245f3afe7cacef8bad573175
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475896"
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
|1. **Çözüm Gezgini** bir proje seçili olmalıdır. **Proje** menüsünde **Özellikler**' e tıklayın. <br />2. **uygulama** sekmesine tıklayın.<br />3. **derleme adı** kutusundaki değeri değiştirin.|  
  
## <a name="example"></a>Örnek  

 Aşağıdaki kod derleme `T2.vb` ve çıkış dosyası oluşturur `T2.exe` .  
  
```console
vbc t2.vb -out:t3.exe  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic Command-Line derleyicisi](index.md)
- [-target (Visual Basic)](target.md)
- [Örnek Derleme Komut Satırları](sample-compilation-command-lines.md)

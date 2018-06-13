---
title: -out (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- /out compiler option [Visual Basic]
- -out compiler option [Visual Basic]
- out compiler option [Visual Basic]
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 234071d043b2649e2438ed20fe044fb89cdb9bf8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33655895"
---
# <a name="-out-visual-basic"></a>-out (Visual Basic)
Çıktı dosyası adını belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-out:filename  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terim|Tanım|  
|---|---|  
|`filename`|Gerekli. Derleyici çıktı dosyası adını oluşturur. Dosya adı boşluk içeriyorsa adı tırnak işaretleri içine alın ("").|  
  
## <a name="remarks"></a>Açıklamalar  
 Tam adı ve uzantısı oluşturmak için dosya belirtin. Bunu yapmazsanız, .exe dosya gelen kaynak kodu içeren dosyanın adını alır `Sub Main` yordamı ve .dll dosyasının ilk kaynak kod dosyasının adını alır.  
  
 Bir .exe veya .dll uzantısı olmadan dosya adı belirtirseniz, derleyici uzantısını otomatik sizin için belirtilen değer bağlı olarak ekler `-target` derleyici seçeneği.  
  
|-Out Visual Studio tümleşik geliştirme ortamında ayarlamak için|  
|---|  
|1.  Seçili bir projeyi **Çözüm Gezgini**. Üzerinde **proje** menüsünde tıklatın **özellikleri**. <br />2.  Tıklatın **uygulama** sekmesi.<br />3.  Değer değiştirme **derleme adı** kutusu.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod derlerken `T2.vb` ve çıktı dosyası oluşturur `T2.exe`.  
  
```console
vbc t2.vb -out:t3.exe  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

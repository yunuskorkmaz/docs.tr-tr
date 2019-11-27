---
title: -out
ms.date: 07/20/2015
helpviewer_keywords:
- /out compiler option [Visual Basic]
- -out compiler option [Visual Basic]
- out compiler option [Visual Basic]
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
ms.openlocfilehash: 67366e13e4dceea4772d0730222413cb25b4e8b7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352382"
---
# <a name="-out-visual-basic"></a>-Out (Visual Basic)
Çıktı dosyasının adını belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-out:filename  
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
  
|Terim|Tanım|  
|---|---|  
|`filename`|Gerekli. Derleyicinin oluşturduğu çıkış dosyasının adı. Dosya adı bir boşluk içeriyorsa, adı tırnak işaretleri ("") içine alın.|  
  
## <a name="remarks"></a>Açıklamalar  
 Oluşturulacak dosyanın tam adını ve uzantısını belirtin. Bunu yapmazsanız,. exe dosyası adını `Sub Main` yordamını içeren kaynak kodu dosyasından alır ve. dll dosyası adı ilk kaynak kodu dosyasından alır.  
  
 Bir. exe veya. dll uzantısı olmadan bir dosya adı belirtirseniz, derleyici, `-target` derleyici seçeneği için belirtilen değere bağlı olarak uzantıyı sizin için otomatik olarak ekler.  
  
|Visual Studio tümleşik geliştirme ortamında ayarlamak için|  
|---|  
|1. **Çözüm Gezgini**bir proje seçili olmalıdır. **Proje** menüsünde **Özellikler**' e tıklayın. <br />2. **uygulama** sekmesine tıklayın.<br />3. **derleme adı** kutusundaki değeri değiştirin.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod `T2.vb` derler ve `T2.exe`çıktı dosyası oluşturur.  
  
```console
vbc t2.vb -out:t3.exe  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

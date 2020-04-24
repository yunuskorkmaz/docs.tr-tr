---
title: -imports
ms.date: 03/10/2018
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
ms.openlocfilehash: 2a1dd19189ff65413255b9bc137e1a7f0227bbe1
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716642"
---
# <a name="-imports-visual-basic"></a>-içeri aktarmalar (Visual Basic)
Belirtilen bir derlemeden ad alanlarını içeri aktarır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-imports:namespaceList  
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
  
|Sözleşme Dönemi|Tanım|  
|---|---|  
|`namespaceList`|Gereklidir. İçeri aktarılacak ad alanlarının virgülle ayrılmış listesi.|  
  
## <a name="remarks"></a>Açıklamalar  
 `-imports` Seçeneği, geçerli kaynak dosyaları kümesi içinde veya başvurulan herhangi bir derlemeden tanımlanmış herhangi bir ad alanını içeri aktarır.  
  
 İle `-imports` belirtilen bir ad alanındaki Üyeler, derlemedeki tüm kaynak kodu dosyaları için kullanılabilir. Tek kaynak kodu dosyasında bir ad alanı kullanmak için [Imports ifadesini (.net ad alanı ve türü)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) kullanın.  
  
|Visual Studio tümleşik geliştirme ortamında ayarlama-içeri aktarmalar|  
|---|  
|1. **Çözüm Gezgini**bir proje seçili olmalıdır. **Proje** menüsünde **Özellikler**' e tıklayın. <br />2. **Başvurular** sekmesine tıklayın.<br />3. ad alanı adını **Kullanıcı Içeri aktarma Ekle** düğmesinin yanındaki kutuya girin.<br />4. **Kullanıcı Içeri aktarma Ekle** düğmesine tıklayın.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, belirtildiğinde derlenir `-imports:system.globalization` . Bu olmadan, başarılı derleme kaynak kodu dosyasının başına `Imports System.Globalization` bir deyimin dahil edilmesini veya özelliğin tam olarak `System.Globalization.CultureInfo.CurrentCulture.Name`nitelenmesini gerektirir.

```vb
Module Example
   Public Sub Main()
      Console.WriteLine($"The current culture is {CultureInfo.CurrentCulture.Name}")
   End Sub
End Module
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [References ve Imports Deyimi](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

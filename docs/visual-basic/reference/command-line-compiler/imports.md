---
title: -imports
ms.date: 03/10/2018
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
ms.openlocfilehash: cc9fc222843bdfe8e49d2d291dc36ff3e0c63fc2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408601"
---
# <a name="-imports-visual-basic"></a>-içeri aktarmalar (Visual Basic)
Belirtilen bir derlemeden ad alanlarını içeri aktarır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```console  
-imports:namespaceList  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  
  
|Terim|Tanım|  
|---|---|  
|`namespaceList`|Gereklidir. İçeri aktarılacak ad alanlarının virgülle ayrılmış listesi.|  
  
## <a name="remarks"></a>Açıklamalar  
 `-imports`Seçeneği, geçerli kaynak dosyaları kümesi içinde veya başvurulan herhangi bir derlemeden tanımlanmış herhangi bir ad alanını içeri aktarır.  
  
 İle belirtilen bir ad alanındaki Üyeler, `-imports` derlemedeki tüm kaynak kodu dosyaları için kullanılabilir. Tek kaynak kodu dosyasında bir ad alanı kullanmak için [Imports ifadesini (.net ad alanı ve türü)](../../language-reference/statements/imports-statement-net-namespace-and-type.md) kullanın.  
  
|Visual Studio tümleşik geliştirme ortamında ayarlama-içeri aktarmalar|  
|---|  
|1. **Çözüm Gezgini**bir proje seçili olmalıdır. **Proje** menüsünde **Özellikler**' e tıklayın. <br />2. **Başvurular** sekmesine tıklayın.<br />3. ad alanı adını **Kullanıcı Içeri aktarma Ekle** düğmesinin yanındaki kutuya girin.<br />4. **Kullanıcı Içeri aktarma Ekle** düğmesine tıklayın.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, belirtildiğinde derlenir `-imports:system.globalization` . Bu olmadan, başarılı derleme `Imports System.Globalization` kaynak kodu dosyasının başına bir deyimin dahil edilmesini veya özelliğin tam olarak nitelenmesini gerektirir `System.Globalization.CultureInfo.CurrentCulture.Name` .

```vb
Module Example
   Public Sub Main()
      Console.WriteLine($"The current culture is {CultureInfo.CurrentCulture.Name}")
   End Sub
End Module
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](index.md)
- [References ve Imports Deyimi](../../programming-guide/program-structure/references-and-the-imports-statement.md)
- [Örnek Derleme Komut Satırları](sample-compilation-command-lines.md)

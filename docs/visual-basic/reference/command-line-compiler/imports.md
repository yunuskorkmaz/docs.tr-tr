---
title: -alır (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
ms.openlocfilehash: 075eeccc7d80943d2757a97b9a355bbea3ef9d4e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58833619"
---
# <a name="-imports-visual-basic"></a>-alır (Visual Basic)
Ad alanları, belirtilen bir derlemesinden içeri aktarır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-imports:namespaceList  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terim|Tanım|  
|---|---|  
|`namespaceList`|Gerekli. İçeri aktarılacak ad alanlarının virgülle ayrılmış listesi.|  
  
## <a name="remarks"></a>Açıklamalar  
 `-imports` Seçeneği geçerli kaynak dosyalarının veya tüm başvurulan bütünleştirilmiş koddan küme içinde tanımlanan herhangi bir ad alanı içeri aktarır.  
  
 Belirtilen bir ad alanı üyelerini `-imports` derlemedeki tüm kaynak kodu dosyaları için kullanılabilir. Kullanma [Imports deyimi (.NET Namespace ve türü)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) tek kaynak kodu dosyasında bir ad alanını kullanacak şekilde.  
  
|Ayarlamak için/Visual Studio tümleşik geliştirme ortamında içeri aktarır|  
|---|  
|1.  Seçili bir projeyi **Çözüm Gezgini**. Üzerinde **proje** menüsünü tıklatın **özellikleri**. <br />2.  Tıklayın **başvuruları** sekmesi.<br />3.  Ad alanı adının kutuya girin **kullanıcı içeri aktarma eklemek** düğmesi.<br />4.  Tıklayın **kullanıcı içeri aktarma eklemek** düğmesi.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod zaman derler `/imports:system.globalization` belirtilir. Bu olmadan başarılı derleme ya da gerektiren bir `Imports System.Globalization` deyimi kaynak kodu dosyasının başında eklenir veya özellik tam olarak nitelenmiş `System.Globalization.CultureInfo.CurrentCulture.Name`.

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

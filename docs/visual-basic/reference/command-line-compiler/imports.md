---
title: -alır (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
ms.openlocfilehash: 9e5adcce85c4ca4863d28784a7d7f61c441a06c8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54588450"
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
  
 [!code-vb[imports example](codesnippet/VisualBasic/imports_2.vb)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [References ve Imports Deyimi](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

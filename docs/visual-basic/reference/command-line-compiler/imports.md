---
title: -içeri aktarmalar (Visual Basic)
ms.date: 03/10/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d81e9d2bd55e6e38e337805b950a0b85680d129b
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2018
---
# <a name="-imports-visual-basic"></a>-içeri aktarmalar (Visual Basic)
Ad alanları belirtilen derlemesinden alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-imports:namespaceList  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terim|Tanım|  
|---|---|  
|`namespaceList`|Gerekli. İçeri aktarılacak ad alanları virgülle ayrılmış listesi.|  
  
## <a name="remarks"></a>Açıklamalar  
 `-imports` Seçeneği geçerli kaynak dosyaları veya başvurulan derlemeler küme içinde tanımlanan tüm ad alanı içe aktarır.  
  
 İle belirtilen bir ad alanı üyeleri `-imports` derlemedeki tüm kaynak kodu dosyaları için kullanılabilir. Kullanmak [Imports deyimi (.NET Namespace ve türü)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) bir tek kaynak kodu dosyasına bir ad alanını kullanmak için.  
  
|Ayarlanacak/Visual Studio tümleşik geliştirme ortamında alır|  
|---|  
|1.  Seçili bir projeyi **Çözüm Gezgini**. Üzerinde **proje** menüsünde tıklatın **özellikleri**. <br />2.  Tıklatın **başvuruları** sekmesi.<br />3.  Ad alanı adı kutuya girin **ekleme kullanıcı alma** düğmesi.<br />4.  Tıklatın **ekleme kullanıcı alma** düğmesi.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod ne zaman derler `/imports:system.globalization` belirtilir. Bu olmadan başarılı derleme ya da gerektiren bir `Imports System.Globalization` deyimi dahil kaynak kodu dosyasının başında veya özelliği tam olarak `System.Globalization.CultureInfo.CurrentCulture.Name`. 
  
 [!code-vb[imports example](codesnippet/VisualBasic/imports_2.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [References ve Imports Deyimi](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

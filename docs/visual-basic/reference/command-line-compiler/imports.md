---
title: /imports (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e8e9cd761263b3b61a4e6d3e33c5f7f875be7a1d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imports-visual-basic"></a>/imports (Visual Basic)
Ad alanları belirtilen derlemesinden alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
/imports:namespaceList  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terim|Tanım|  
|---|---|  
|`namespaceList`|Gerekli. İçeri aktarılacak ad alanları virgülle ayrılmış listesi.|  
  
## <a name="remarks"></a>Açıklamalar  
 `/imports` Seçeneği geçerli kaynak dosyaları veya başvurulan derlemeler küme içinde tanımlanan tüm ad alanı içe aktarır.  
  
 İle belirtilen bir ad alanı üyeleri `/imports` derlemedeki tüm kaynak kodu dosyaları için kullanılabilir. Kullanmak [Imports deyimi (.NET Namespace ve türü)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) bir tek kaynak kodu dosyasına bir ad alanını kullanmak için.  
  
|Ayarlanacak/Visual Studio tümleşik geliştirme ortamında alır|  
|---|  
|1.  Seçili bir projeyi **Çözüm Gezgini**. Üzerinde **proje** menüsünde tıklatın **özellikleri**. Daha fazla bilgi için bkz: [Proje Tasarımcısı giriş](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).<br />2.  Tıklatın **başvuruları** sekmesi.<br />3.  Ad alanı adı kutuya girin **ekleme kullanıcı alma** düğmesi.<br />4.  Tıklatın **ekleme kullanıcı alma** düğmesi.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod ne zaman derler `/imports:system` belirtilir.  
  
 [!code-vb[VbVbalrCompiler#21](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/imports_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [References ve Imports deyimi](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 [Örnek derleme komut satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

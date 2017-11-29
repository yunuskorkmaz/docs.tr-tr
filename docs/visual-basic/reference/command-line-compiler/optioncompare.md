---
title: /optioncompare
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: /optioncompare
helpviewer_keywords:
- optioncompare compiler option [Visual Basic]
- -optioncompare compiler option [Visual Basic]
- /optioncompare compiler option [Visual Basic]
ms.assetid: 7237b766-b44d-4cc5-9a3c-885348a7d9e4
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a6f602e0b0b23345bf1f5aae843bd44bd2642bc9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="optioncompare"></a>/optioncompare
Dize karşılaştırmaları nasıl yapılacağını belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
/optioncompare:{binary | text}  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Belirleyebileceğiniz `/optioncompare` iki forms birinde: `/optioncompare:binary` ikili dize karşılaştırmaları kullanmak için ve `/optioncompare:text` metin dize karşılaştırmaları kullanmak için. Varsayılan olarak, derleyici kullanır `/optioncompare:binary`.  
  
 Microsoft Windows'daki kullanılan kod sayfası ikili sıralama düzenini belirler. Tipik bir ikili sıralama aşağıdaki gibidir:  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 Metin tabanlı dize karşılaştırmaları sisteminizin bölgeye göre belirlenir büyük küçük harf duyarsız metin sıralama düzenini temel alır. Bir normal metin sıralama aşağıdaki gibidir:  
  
 `(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
### <a name="to-set-optioncompare-in-the-visual-studio-ide"></a>/ Optioncompare Visual Studio IDE'de ayarlamak için  
  
1.  Seçili bir projeyi **Çözüm Gezgini**. Üzerinde **proje** menüsünde tıklatın **özellikleri**. Daha fazla bilgi için bkz: [Proje Tasarımcısı giriş](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).  
  
2.  Tıklatın **derleme** sekmesi.  
  
3.  Değer değiştirme **seçeneği karşılaştırmak** kutusu.  
  
### <a name="to-set-optioncompare-programmatically"></a>/ Optioncompare programlı olarak ayarlamak için  
  
-   Bkz: [Option Compare deyimi](../../../visual-basic/language-reference/statements/option-compare-statement.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod derlerken `ProjFile.vb` ve ikili dize karşılaştırmalarını kullanır.  
  
```  
vbc /optioncompare:binary projFile.vb  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/ optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [/ optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [/ optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [Örnek derleme komut satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Option Compare deyimi](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [Visual Basic Varsayılanları, projeler, Seçenekler iletişim kutusu](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)

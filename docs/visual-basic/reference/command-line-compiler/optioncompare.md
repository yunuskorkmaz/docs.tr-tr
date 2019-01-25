---
title: -optioncompare
ms.date: 07/20/2015
f1_keywords:
- /optioncompare
- -optioncompare
helpviewer_keywords:
- optioncompare compiler option [Visual Basic]
- -optioncompare compiler option [Visual Basic]
- /optioncompare compiler option [Visual Basic]
ms.assetid: 7237b766-b44d-4cc5-9a3c-885348a7d9e4
ms.openlocfilehash: 86564b7ce419ef6c6e56a6b677b71009830b5fc4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54662315"
---
# <a name="-optioncompare"></a>-optioncompare
Dize karşılaştırmaları nasıl yapılacağını belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-optioncompare:{binary | text}  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Belirtebileceğiniz `-optioncompare` içindeki iki farklı: `-optioncompare:binary` ikili dize karşılaştırmaları, kullanılacak ve `-optioncompare:text` metin dize karşılaştırmaları kullanılacak. Varsayılan olarak, derleyicinin kullandığı `-optioncompare:binary`.  
  
 Microsoft Windows içinde mevcut kod sayfasında ikili sıralama düzenini belirler. Tipik ikili sıralama düzeninde aşağıdaki gibidir:  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 Metin tabanlı dize karşılaştırmaları büyük/küçük harfe metin sıralama düzeni, sisteminizin yerel ayarı tarafından belirlenen temel alır. Normal metin sıralama düzeni aşağıdaki gibidir:  
  
 `(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
### <a name="to-set--optioncompare-in-the-visual-studio-ide"></a>-Optioncompare Visual Studio IDE'de ayarlamak için  
  
1.  Seçili bir projeyi **Çözüm Gezgini**. Üzerinde **proje** menüsünü tıklatın **özellikleri**.   
  
2.  Tıklayın **derleme** sekmesi.  
  
3.  Değer değiştirme **Option Compare** kutusu.  
  
### <a name="to-set--optioncompare-programmatically"></a>-Optioncompare program üzerinden ayarlamak için  
  
-   Bkz: [Option Compare deyimi](../../../visual-basic/language-reference/statements/option-compare-statement.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod derlenir `ProjFile.vb` ve ikili dize karşılaştırmaları kullanır.  
  
```console
vbc -optioncompare:binary projFile.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Option Compare Deyimi](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [Visual Basic Varsayılanları, Projeler, Seçenekler İletişim Kutusu](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)

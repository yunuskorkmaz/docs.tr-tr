---
title: -optionexplicit
ms.date: 07/20/2015
f1_keywords:
- /optionexplicit
- -optionexplicit
helpviewer_keywords:
- /optionexplicit compiler option [Visual Basic]
- optionexplicit compiler option [Visual Basic]
- -optionexplicit compiler option [Visual Basic]
ms.assetid: 5d296ab3-bafe-4c4d-9887-78f162ed86c7
ms.openlocfilehash: 220d6e06ef692655bd6db000fa98b4eb2fc69ba9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54683852"
---
# <a name="-optionexplicit"></a>-optionexplicit
Bunlar kullanılmadan önce değişkenleri bildirilmedikçe derleyici hatalarını raporlamak için neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 İsteğe bağlı. Belirtin `-optionexplicit+` değişkenleri açık bildirimini gerektiren. `-optionexplicit+` Seçenek varsayılandır ve aynı `-optionexplicit`. `-optionexplicit-` Örtük bir değişken bildirimi seçeneği sağlar.  
  
## <a name="remarks"></a>Açıklamalar  
 Kaynak kodu dosyası içeriyorsa bir [Option Explicit deyimi](../../../visual-basic/language-reference/statements/option-explicit-statement.md), deyim geçersiz kılmalar `-optionexplicit` komut satırı derleyicisini ayarı.  
  
### <a name="to-set--optionexplicit-in-the-visual-studio-ide"></a>-Optionexplicit Visual Studio IDE'de ayarlamak için  
  
1.  Seçili bir projeyi **Çözüm Gezgini**. Üzerinde **proje** menüsünü tıklatın **özellikleri**.   
  
2.  Tıklayın **derleme** sekmesi.  
  
3.  Değer değiştirme **Option Explicit** kutusu.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod zaman derler `-optionexplicit-` kullanılır.  
  
 [!code-vb[VbVbalrCompiler#5](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/optionexplicit_1.vb)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Option Explicit Deyimi](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [Visual Basic Varsayılanları, Projeler, Seçenekler İletişim Kutusu](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)

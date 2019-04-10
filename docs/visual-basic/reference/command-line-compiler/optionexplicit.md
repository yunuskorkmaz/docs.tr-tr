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
ms.openlocfilehash: 54d438541e8840e4394b24b20b4f394ff8cdb820
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59332397"
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
  
1. Seçili bir projeyi **Çözüm Gezgini**. Üzerinde **proje** menüsünü tıklatın **özellikleri**.   
  
2. Tıklayın **derleme** sekmesi.  
  
3. Değer değiştirme **Option Explicit** kutusu.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod zaman derler `-optionexplicit-` kullanılır.  
  
 [!code-vb[VbVbalrCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionExplicitOff.vb#5)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic Komut Satırı Derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Option Explicit Deyimi](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [Visual Basic Varsayılanları, Projeler, Seçenekler İletişim Kutusu](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)

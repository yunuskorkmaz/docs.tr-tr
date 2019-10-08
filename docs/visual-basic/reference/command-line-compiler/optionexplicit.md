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
ms.openlocfilehash: 5c0946b94bfe02d797d1a484088869375703eb6a
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005308"
---
# <a name="-optionexplicit"></a>-optionexplicit
Değişkenler kullanılmadan önce bildirilmemiş olursa derleyicinin hata raporlamasına neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 İsteğe bağlı. Değişkenlerin açık bildirimini gerektirmek için `-optionexplicit+` belirtin. @No__t-0 seçeneği varsayılandır ve `-optionexplicit` ile aynıdır. @No__t-0 seçeneği, değişkenlerin örtülü bildirimini sunar.  
  
## <a name="remarks"></a>Açıklamalar  
 Kaynak kodu dosyası [açık bir seçenek ifade](../../../visual-basic/language-reference/statements/option-explicit-statement.md)içeriyorsa, ifade `-optionexplicit` komut satırı derleyici ayarını geçersiz kılar.  
  
### <a name="to-set--optionexplicit-in-the-visual-studio-ide"></a>Visual Studio IDE 'de ayarlamak için-OptionExplicit  
  
1. **Çözüm Gezgini**' de bir proje seçili olmalıdır. **Proje** menüsünde **Özellikler**' e tıklayın.   
  
2. **Derle** sekmesine tıklayın.  
  
3. **Açık** kutudaki değeri değiştirin.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod `-optionexplicit-` kullanıldığında derlenir.  
  
 [!code-vb[VbVbalrCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionExplicitOff.vb#5)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Option Explicit Deyimi](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [Visual Basic Varsayılanları, Projeler, Seçenekler İletişim Kutusu](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)

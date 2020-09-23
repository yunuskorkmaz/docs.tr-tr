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
ms.openlocfilehash: 65cc3fb1b2fa9daa04013caa2b93a3949d0a15b9
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91098946"
---
# <a name="-optionexplicit"></a>-optionexplicit

Değişkenler kullanılmadan önce bildirilmemiş olursa derleyicinin hata raporlamasına neden olur.  
  
## <a name="syntax"></a>Söz dizimi  
  
```console  
-optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `+` &#124; `-`  
 İsteğe bağlı. `-optionexplicit+`Değişkenlerin açık bildirimini gerektirmek için belirtin. `-optionexplicit+`Varsayılan seçenektir ve ile aynıdır `-optionexplicit` . `-optionexplicit-`Seçeneği, değişkenlerin örtülü bildirimini sunar.  
  
## <a name="remarks"></a>Açıklamalar  

 Kaynak kodu dosyası [açık bir seçenek ifade](../../language-reference/statements/option-explicit-statement.md)içeriyorsa, ifade `-optionexplicit` komut satırı derleyici ayarını geçersiz kılar.  
  
### <a name="to-set--optionexplicit-in-the-visual-studio-ide"></a>Visual Studio IDE 'de ayarlamak için-OptionExplicit  
  
1. **Çözüm Gezgini**' de bir proje seçili olmalıdır. **Proje** menüsünde **Özellikler**' e tıklayın.
  
2. **Derle** sekmesine tıklayın.  
  
3. **Açık** kutudaki değeri değiştirin.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki kod, kullanıldığında derlenir `-optionexplicit-` .  
  
 [!code-vb[VbVbalrCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionExplicitOff.vb#5)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](index.md)
- [-optioncompare](optioncompare.md)
- [-optionstrict](optionstrict.md)
- [-optioninfer](optioninfer.md)
- [Örnek Derleme Komut Satırları](sample-compilation-command-lines.md)
- [Option Explicit Deyimi](../../language-reference/statements/option-explicit-statement.md)
- [Visual Basic Varsayılanları, Projeler, Seçenekler İletişim Kutusu](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)

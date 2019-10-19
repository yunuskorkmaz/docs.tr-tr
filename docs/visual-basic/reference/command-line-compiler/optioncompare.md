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
ms.openlocfilehash: ac385880f8c13c23dffff67fc2a1ecc5609fd189
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581412"
---
# <a name="-optioncompare"></a>-optioncompare

Dize karşılaştırmalarının nasıl yapılacağını belirtir.

## <a name="syntax"></a>Sözdizimi

```console
-optioncompare:{binary | text}
```

## <a name="remarks"></a>Açıklamalar

@No__t_0 iki formdan birini belirtebilirsiniz: ikili dize karşılaştırmaları kullanmak için `-optioncompare:binary` ve metin dizesi karşılaştırmaları kullanmak için `-optioncompare:text`. Varsayılan olarak, derleyici `-optioncompare:binary` ' ı kullanır.

Microsoft Windows 'da, geçerli kod sayfası ikili sıralama düzenini belirler. Tipik bir ikili sıralama düzeni aşağıdaki gibidir:

`A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`

Metin tabanlı dize karşılaştırmaları, sisteminizin yerel ayarı tarafından belirlenen, büyük/küçük harfe duyarsız metin sıralama düzenini temel alır. Tipik bir metin sıralama düzeni aşağıdaki gibidir:

`(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`

### <a name="to-set--optioncompare-in-the-visual-studio-ide"></a>Visual Studio IDE 'de set-OptionCompare

1. **Çözüm Gezgini**' de bir proje seçili olmalıdır. **Proje** menüsünde **Özellikler**' e tıklayın.

2. **Derle** sekmesine tıklayın.

3. **Seçenek karşılaştırma** kutusundaki değeri değiştirin.

### <a name="to-set--optioncompare-programmatically"></a>Programlı olarak ayarlama-OptionCompare

Bkz. [Option Compare deyimin](../../../visual-basic/language-reference/statements/option-compare-statement.md).

## <a name="example"></a>Örnek

Aşağıdaki kod `ProjFile.vb` derler ve ikili dize karşılaştırmaları kullanır.

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

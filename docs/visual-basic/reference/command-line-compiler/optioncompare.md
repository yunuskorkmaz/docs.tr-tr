---
description: :-OptionCompare hakkında daha fazla bilgi edinin
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
ms.openlocfilehash: 9be4867c75cc16a8f699cf492dc41e9d08b96495
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475935"
---
# <a name="-optioncompare"></a>-optioncompare

Dize karşılaştırmalarının nasıl yapılacağını belirtir.

## <a name="syntax"></a>Syntax

```console
-optioncompare:{binary | text}
```

## <a name="remarks"></a>Açıklamalar

`-optioncompare`İki formdan birini belirtebilirsiniz: `-optioncompare:binary` ikili dize karşılaştırmaları kullanmak ve `-optioncompare:text` metin dizesi karşılaştırmaları kullanmak için. Varsayılan olarak, derleyici kullanır `-optioncompare:binary` .

Microsoft Windows 'da, geçerli kod sayfası ikili sıralama düzenini belirler. Tipik bir ikili sıralama düzeni aşağıdaki gibidir:

`A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`

Metin tabanlı dize karşılaştırmaları, sisteminizin yerel ayarı tarafından belirlenen, büyük/küçük harfe duyarsız metin sıralama düzenini temel alır. Tipik bir metin sıralama düzeni aşağıdaki gibidir:

`(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`

### <a name="to-set--optioncompare-in-the-visual-studio-ide"></a>Visual Studio IDE 'de set-OptionCompare

1. **Çözüm Gezgini**' de bir proje seçili olmalıdır. **Proje** menüsünde **Özellikler**' e tıklayın.

2. **Derle** sekmesine tıklayın.

3. **Seçenek karşılaştırma** kutusundaki değeri değiştirin.

### <a name="to-set--optioncompare-programmatically"></a>Programlı olarak ayarlama-OptionCompare

Bkz. [Option Compare deyimin](../../language-reference/statements/option-compare-statement.md).

## <a name="example"></a>Örnek

Aşağıdaki kod derlenir `ProjFile.vb` ve ikili dize karşılaştırmaları kullanır.

```console
vbc -optioncompare:binary projFile.vb
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic Command-Line derleyicisi](index.md)
- [-optionexplicit](optionexplicit.md)
- [-optionstrict](optionstrict.md)
- [-optioninfer](optioninfer.md)
- [Örnek Derleme Komut Satırları](sample-compilation-command-lines.md)
- [Option Compare Deyimi](../../language-reference/statements/option-compare-statement.md)
- [Visual Basic Varsayılanları, Projeler, Seçenekler İletişim Kutusu](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)

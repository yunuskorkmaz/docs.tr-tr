---
title: -optionstrict
ms.date: 07/20/2015
f1_keywords:
- -optionstrict
helpviewer_keywords:
- -optionstrict compiler option [Visual Basic]
- optionstrict compiler option [Visual Basic]
- /optionstrict compiler option [Visual Basic]
ms.assetid: c7b10086-0fa4-49db-b3c8-4ae0db5957da
ms.openlocfilehash: 3dd12971a082869c32b6292ed45e2014b8b0e2c0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400545"
---
# <a name="-optionstrict"></a>-optionstrict

Örtük tür dönüşümlerini kısıtlamak için katı tür semantiğini zorlar.

## <a name="syntax"></a>Söz dizimi

```console
-optionstrict[+ | -]
-optionstrict[:custom]
```

## <a name="arguments"></a>Bağımsız değişkenler

`+`&#124;`-`  
İsteğe bağlı. `-optionstrict+`Seçeneği örtük tür dönüştürmeyi kısıtlar. Bu seçenek için varsayılan değer `-optionstrict-` . `-optionstrict+`Seçeneği ile aynıdır `-optionstrict` . Hem izin veren tür semantiğinin hem de kullanabilirsiniz.

`custom`  
Gereklidir. Katı dil semantiklerine uyulmadığında uyar.

## <a name="remarks"></a>Açıklamalar

`-optionstrict+`Etkin olduğunda, yalnızca genişleyen tür dönüştürmeleri örtülü olarak yapılabilir. Bir tamsayı türü nesnesine bir tür nesnesi atama gibi örtülü daraltma tür dönüştürmeleri `Decimal` hata olarak bildirilir.

Örtülü daraltma tür dönüştürmeleri için uyarı oluşturmak için kullanın `-optionstrict:custom` . `-nowarn:numberlist`Belirli uyarıları yoksaymak ve `-warnaserror:numberlist` belirli uyarıları hata olarak değerlendirmek için kullanın.

### <a name="to-set--optionstrict-in-the-visual-studio-ide"></a>Visual Studio IDE 'de-OptionStrict öğesini ayarlamak için

1. **Çözüm Gezgini**' de bir proje seçili olmalıdır. **Proje** menüsünde Özellikler ' e tıklayın **.**

2. **Derle** sekmesine tıklayın.

3. **Seçenek katı** kutusunda değeri değiştirin.

### <a name="to-set--optionstrict-programmatically"></a>Program aracılığıyla ayarlama-OptionStrict

Bkz. [Option Strict deyimdir](../../language-reference/statements/option-strict-statement.md).

## <a name="example"></a>Örnek

Aşağıdaki kod, `Test.vb` katı tür semantiğini kullanarak derlenir.

```console
vbc -optionstrict+ test.vb
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](index.md)
- [-optioncompare](optioncompare.md)
- [-optionexplicit](optionexplicit.md)
- [-optioninfer](optioninfer.md)
- [-nowarn](nowarn.md)
- [-warnaserror (Visual Basic)](warnaserror.md)
- [Örnek Derleme Komut Satırları](sample-compilation-command-lines.md)
- [Option Strict Deyimi](../../language-reference/statements/option-strict-statement.md)
- [Visual Basic Varsayılanları, Projeler, Seçenekler İletişim Kutusu](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)

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
ms.openlocfilehash: 22423877325806e6e6abe535ad98530eb924780e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625902"
---
# <a name="-optionstrict"></a>-optionstrict
Örtük tür dönüştürmelerini kısıtlamak için katı türü anlamları zorlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-optionstrict[+ | -]  
-optionstrict[:custom]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 İsteğe bağlı. `-optionstrict+` Seçeneği örtük tür dönüştürme kısıtlar. Bu seçenek için varsayılan değer `-optionstrict-`. `-optionstrict+` Seçeneği aynıdır `-optionstrict`. Esnek türü anlamları için her ikisini de kullanabilirsiniz.  
  
 `custom`  
 Gerekli. Katı dil semantiği değil uymaya uyar.  
  
## <a name="remarks"></a>Açıklamalar  
 Zaman `-optionstrict+` kıyaslandığında geçerli tür dönüştürmelerine yalnızca bir örtülü olarak yapılabilir. Örtük tür dönüştürmelerini atama gibi daraltma bir `Decimal` türü nesnesi bir tamsayı türü nesne, hata olarak raporlanır.  
  
 Daraltma örtük tür dönüştürmelerini için Uyarılar oluşturmak için `-optionstrict:custom`. Kullanım `-nowarn:numberlist` belirli uyarılarını gözardı etme ve `-warnaserror:numberlist` belirli uyarıları hata olarak değerlendirilecek.  
  
### <a name="to-set--optionstrict-in-the-visual-studio-ide"></a>-Optionstrict Visual Studio IDE'de ayarlamak için  
  
1. Seçili bir projeyi **Çözüm Gezgini**. Üzerinde **proje** menüsünü tıklatın **özellikleri.**   
  
2. Tıklayın **derleme** sekmesi.  
  
3. Değer değiştirme **Option Strict** kutusu.  
  
### <a name="to-set--optionstrict-programmatically"></a>-Optionstrict program üzerinden ayarlamak için  
  
- Bkz: [Option Strict deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod derlenir `Test.vb` katı tür semantiği kullanarak.  
  
```console
vbc -optionstrict+ test.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)
- [-warnaserror (Visual Basic)](../../../visual-basic/reference/command-line-compiler/warnaserror.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Option Strict Deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Visual Basic Varsayılanları, Projeler, Seçenekler İletişim Kutusu](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)

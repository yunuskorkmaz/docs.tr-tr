---
title: -optioninfer
ms.date: 07/20/2015
f1_keywords:
- -optioninfer
helpviewer_keywords:
- -optioninfer compiler option [Visual Basic]
- /optioninfer compiler option [Visual Basic]
- optioninfer compiler option [Visual Basic]
ms.assetid: f6c09db1-0553-464a-abe3-d4510c61d6ed
ms.openlocfilehash: 89fcd981dbb5442f6150f539db4c7d404fe8d691
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58839853"
---
# <a name="-optioninfer"></a>-optioninfer
Değişken bildiriminde yerel tür çıkarımı kullanımını etkinleştirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-optioninfer[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terim|Tanım|  
|---|---|  
|`+` &#124; `-`|İsteğe bağlı. Belirtin `-optioninfer+` yerel tür çıkarımı etkinleştirmek için veya `-optioninfer-` bunu engellemek için. `-optioninfer` Seçeneği, belirtilen değer ile aynı olup `-optioninfer+`. Varsayılan değer `-optioninfer` anahtar mevcut değil aynı zamanda `-optioninfer+`. Varsayılan değer nezahrnovat yanıt dosyasında ayarlanır.|  
  
> [!NOTE]
>  Kullanabileceğiniz `-noconfig` seçeneği derleyicinin nezahrnovat içinde belirtilenlerden yerine iç Varsayılanları koruyun. Bu seçenek derleyici varsayılan `-optioninfer-`.  
  
## <a name="remarks"></a>Açıklamalar  
 Kaynak kodu dosyası içeriyorsa bir [Option Infer deyimi](../../../visual-basic/language-reference/statements/option-infer-statement.md), deyim geçersiz kılmalar `-optioninfer` komut satırı derleyicisini ayarı.  
  
### <a name="to-set--optioninfer-in-the-visual-studio-ide"></a>-Optioninfer Visual Studio IDE'de ayarlamak için  
  
1.  Bir proje seçin **Çözüm Gezgini**. Üzerinde **proje** menüsünü tıklatın **özellikleri**.  
  
2.  Üzerinde **derleme** sekmesinde, bu değeri değiştirmek **Option Infer** kutusu.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod derlenir `test.vb` etkin yerel tür çıkarımı ile.  
  
```console
vbc -optioninfer+ test.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Option Infer Deyimi](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [Yerel Çıkarım](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Visual Basic Varsayılanları, Projeler, Seçenekler İletişim Kutusu](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
- [Derleme Sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [Komut Satırından Derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)

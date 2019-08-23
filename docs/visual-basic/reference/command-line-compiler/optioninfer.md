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
ms.openlocfilehash: 4848dec148bc528e7a30940643e3364f1bb5f805
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939198"
---
# <a name="-optioninfer"></a>-optioninfer
Değişken bildirimlerinde yerel tür çıkarımı kullanımını mümkün.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-optioninfer[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terim|Tanım|  
|---|---|  
|`+` &#124; `-`|İsteğe bağlı. Yerel `-optioninfer+` tür çıkarımını etkinleştirmek veya `-optioninfer-` engellemek için belirtin. Belirtilen değer olmadan `-optioninfer+`seçeneği, ile aynıdır. `-optioninfer` `-optioninfer` Anahtar mevcut olmadığında varsayılan değer de `-optioninfer+`vardır. Varsayılan değer Vbc. rsp yanıt dosyasında ayarlanır.|  
  
> [!NOTE]
> Söz konusu seçeneği, `-noconfig` Vbc. rsp ' de belirtilenler yerine derleyicinin iç varsayılan değerlerini koruma için kullanabilirsiniz. Bu seçenek için varsayılan derleyicidir `-optioninfer-`.  
  
## <a name="remarks"></a>Açıklamalar  
 Kaynak kodu dosyası bir [seçenek çıkarımı bildirisi](../../../visual-basic/language-reference/statements/option-infer-statement.md)içeriyorsa, ifade `-optioninfer` komut satırı derleyici ayarını geçersiz kılar.  
  
### <a name="to-set--optioninfer-in-the-visual-studio-ide"></a>Visual Studio IDE 'de set-OptionInfer  
  
1. **Çözüm Gezgini**bir proje seçin. **Proje** menüsünde **Özellikler**' e tıklayın.  
  
2. **Derle** sekmesinde, **seçenek çıkarımı** kutusunda değeri değiştirin.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, yerel `test.vb` tür çıkarımı etkin ile derlenir.  
  
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

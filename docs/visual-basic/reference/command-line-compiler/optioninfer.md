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
ms.openlocfilehash: e7dbc4d5f06096978c4d93ea20677dcb60bc3fcb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33655931"
---
# <a name="-optioninfer"></a>-optioninfer
Yerel türü çıkarımı değişken bildirimlerden kullanımını etkinleştirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-optioninfer[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terim|Tanım|  
|---|---|  
|`+` &#124; `-`|İsteğe bağlı. Belirtin `-optioninfer+` yerel türü çıkarımı etkinleştirmek için veya `-optioninfer-` bunu engellemek için. `-optioninfer` Seçeneği, belirtilen herhangi bir değer ile aynı olup `-optioninfer+`. Varsayılan değer `-optioninfer` anahtar mevcut değil de `-optioninfer+`. Varsayılan değer Vbc.rsp yanıt dosyasında ayarlanır.|  
  
> [!NOTE]
>  Kullanabileceğiniz `-noconfig` seçeneği vbc.rsp içinde belirtilen yerine derleyicinin iç Varsayılanları koruyun. Bu seçenek için derleyici varsayılan değer `-optioninfer-`.  
  
## <a name="remarks"></a>Açıklamalar  
 Kaynak kodu dosyasının içeriyorsa bir [Option Infer deyimi](../../../visual-basic/language-reference/statements/option-infer-statement.md), deyim için geçersiz kılar `-optioninfer` komut satırı derleyicisi ayarı.  
  
### <a name="to-set--optioninfer-in-the-visual-studio-ide"></a>Visual Studio IDE'de - optioninfer ayarlamak için  
  
1.  Bir projedeki seçin **Çözüm Gezgini**. Üzerinde **proje** menüsünde tıklatın **özellikleri**.  
  
2.  Üzerinde **derleme** sekmesinde, değeri Değiştir **Option Infer** kutusu.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod derlerken `test.vb` etkin yerel türü çıkarımı ile.  
  
```console
vbc -optioninfer+ test.vb  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Option Infer Deyimi](../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [Yerel Çıkarım](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Visual Basic Varsayılanları, projeler, Seçenekler iletişim kutusu](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)  
 [Derleme Sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)  
 [/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [Komut Satırından Derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)

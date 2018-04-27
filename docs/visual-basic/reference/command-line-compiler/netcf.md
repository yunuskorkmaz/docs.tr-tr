---
title: -netcf
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /netcf
- -netcf
helpviewer_keywords:
- -netcf compiler option [Visual Basic]
- netcf compiler option [Visual Basic]
- /netcf compiler option [Visual Basic]
ms.assetid: db7cfa59-c315-401c-a59b-0daf355343d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f07fc7988c4329397e464f05d334648e98cb129d
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="-netcf"></a>-netcf
Hedefe derleyici ayarlar [!INCLUDE[Compact](~/includes/compact-md.md)].  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-netcf  
```  
  
## <a name="remarks"></a>Açıklamalar  
 `-netcf` Seçeneği neden hedef için Visual Basic derleyici [!INCLUDE[Compact](~/includes/compact-md.md)] tam yerine [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Yalnızca tam olarak mevcut dil işlevleri [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] devre dışı bırakılır.  
  
 `-netcf` Seçeneği ile kullanılmak üzere tasarlanmıştır [- sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md). Devre dışı dil özellikleri `-netcf` aynı dil özellikleri ile hedeflenen dosyalarında yok `-sdkpath`.  
  
> [!NOTE]
>  `-netcf` Seçeneği Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derlerken kullanılabilir. `-netcf` Seçeneği, bir Visual Basic cihaz projesi yüklendiğinde ayarlanır.  
  
 `-netcf` Seçenek aşağıdaki dil özellikleri değiştirir:  
  
-   [Son \<anahtar sözcüğü > deyimi](../../../visual-basic/language-reference/statements/end-keyword-statement.md) bir programın yürütülmesini sonlandırır, anahtar sözcüğü devre dışıdır. Aşağıdaki programı derlenir ve olmadan çalışır `-netcf` ancak derleme zamanında başarısız `-netcf`.  
  
     [!code-vb[VbVbalrCompiler#34](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_1.vb)]  
  
-   Geç bağlama, tüm formlarında devre dışı bırakılır. Tanınan geç bağlama senaryoları karşılaşılırsa, derleme zamanı hataları üretilir. Aşağıdaki programı derlenir ve olmadan çalışır `-netcf` ancak derleme zamanında başarısız `-netcf`.  
  
     [!code-vb[VbVbalrCompiler#35](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_2.vb)]  
  
-   [Otomatik](../../../visual-basic/language-reference/modifiers/auto.md), [ANSI](../../../visual-basic/language-reference/modifiers/ansi.md), ve [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) değiştiricileri devre dışı bırakılır. Söz dizimi [Declare deyimi](../../../visual-basic/language-reference/statements/declare-statement.md) deyimi için değişiklik de `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`. Aşağıdaki kod etkisini gösterir `-netcf` bir derleme üzerinde.  
  
     [!code-vb[VbVbalrCompiler#36](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_3.vb)]  
  
-   Visual Basic'ten kaldırıldı Visual Basic 6.0 anahtar sözcükleri kullanarak farklı bir hata oluşturur, `-netcf` kullanılır. Bu, aşağıdaki anahtar sözcükler için hata iletileri etkiler:  
  
    -   `Open`  
  
    -   `Close`  
  
    -   `Put`  
  
    -   `Print`  
  
    -   `Write`  
  
    -   `Input`  
  
    -   `Lock`  
  
    -   `Unlock`  
  
    -   `Seek`  
  
    -   `Width`  
  
    -   `Name`  
  
    -   `FreeFile`  
  
    -   `EOF`  
  
    -   `Loc`  
  
    -   `LOF`  
  
    -   `Line`  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod derlerken `Myfile.vb` ile [!INCLUDE[Compact](~/includes/compact-md.md)], mscorlib.dll ve Microsoft.VisualBasic.dll içinde sürümleri kullanılarak varsayılan yükleme dizininde bulunan [!INCLUDE[Compact](~/includes/compact-md.md)] C sürücüsünde. Genellikle, en son sürümünü kullanmak [!INCLUDE[Compact](~/includes/compact-md.md)].  
  
```console  
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)

---
title: /netcf
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- /netcf
- netcf
helpviewer_keywords:
- -netcf compiler option [Visual Basic]
- netcf compiler option [Visual Basic]
- /netcf compiler option [Visual Basic]
ms.assetid: db7cfa59-c315-401c-a59b-0daf355343d6
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4a75573b0881af71e907a488c2b3c15db3816fc0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="netcf"></a>/netcf
Hedefe derleyici ayarlar [!INCLUDE[Compact](~/includes/compact-md.md)].  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
/netcf  
```  
  
## <a name="remarks"></a>Açıklamalar  
 `/netcf` Seçeneği neden [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] derleyici hedef [!INCLUDE[Compact](~/includes/compact-md.md)] tam yerine [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Yalnızca tam olarak mevcut dil işlevleri [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] devre dışı bırakılır.  
  
 `/netcf` Seçeneği ile kullanılmak üzere tasarlanmıştır [/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md). Devre dışı dil özellikleri `/netcf` aynı dil özellikleri ile hedeflenen dosyalarında yok `/sdkpath`.  
  
> [!NOTE]
>  `/netcf` Seçeneği Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derlerken kullanılabilir. `/netcf` Seçeneği ayarlanmış olduğunda bir [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] aygıt proje yüklenir.  
  
 `/netcf` Seçenek aşağıdaki dil özellikleri değiştirir:  
  
-   [Son \<anahtar sözcüğü > deyimi](../../../visual-basic/language-reference/statements/end-keyword-statement.md) bir programın yürütülmesini sonlandırır, anahtar sözcüğü devre dışıdır. Aşağıdaki programı derlenir ve olmadan çalışır `/netcf` ancak derleme zamanında başarısız `/netcf`.  
  
     [!code-vb[VbVbalrCompiler#34](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_1.vb)]  
  
-   Geç bağlama, tüm formlarında devre dışı bırakılır. Tanınan geç bağlama senaryoları karşılaşılırsa, derleme zamanı hataları üretilir. Aşağıdaki programı derlenir ve olmadan çalışır `/netcf` ancak derleme zamanında başarısız `/netcf`.  
  
     [!code-vb[VbVbalrCompiler#35](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_2.vb)]  
  
-   [Otomatik](../../../visual-basic/language-reference/modifiers/auto.md), [ANSI](../../../visual-basic/language-reference/modifiers/ansi.md), ve [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) değiştiricileri devre dışı bırakılır. Söz dizimi [Declare deyimi](../../../visual-basic/language-reference/statements/declare-statement.md) deyimi için değişiklik de `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`. Aşağıdaki kod etkisini gösterir `/netcf` bir derleme üzerinde.  
  
     [!code-vb[VbVbalrCompiler#36](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_3.vb)]  
  
-   Sıradan kaldırıldığını Visual Basic 6.0 anahtar sözcükler kullanmayı [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] farklı bir hata oluşturur, `/netcf` kullanılır. Bu, aşağıdaki anahtar sözcükler için hata iletileri etkiler:  
  
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
  
```  
vbc /netcf /sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Örnek derleme komut satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [/ sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)

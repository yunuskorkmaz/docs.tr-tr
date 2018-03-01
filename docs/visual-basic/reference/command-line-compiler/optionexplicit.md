---
title: /optionexplicit
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /optionexplicit
helpviewer_keywords:
- /optionexplicit compiler option [Visual Basic]
- optionexplicit compiler option [Visual Basic]
- -optionexplicit compiler option [Visual Basic]
ms.assetid: 5d296ab3-bafe-4c4d-9887-78f162ed86c7
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1e701addb31b361e55f2761f441c23deaef7c10d
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="optionexplicit"></a>/optionexplicit
Kullanıldıkları önce değişkenleri bildirilmeyen, derleyici hatalarını raporlamak neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
/optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 İsteğe bağlı. Belirtin `/optionexplicit+` değişkenlerin açıkça bildirilmesini istemek için. `/optionexplicit+` Seçenek varsayılandır ve aynı `/optionexplicit`. `/optionexplicit-` Seçeneği değişkenlerin örtük bildirimi sağlar.  
  
## <a name="remarks"></a>Açıklamalar  
 Kaynak kodu dosyasının içeriyorsa bir [Option Explicit deyimi](../../../visual-basic/language-reference/statements/option-explicit-statement.md), deyim için geçersiz kılar `/optionexplicit` komut satırı derleyicisi ayarı.  
  
### <a name="to-set-optionexplicit-in-the-visual-studio-ide"></a>/ Optionexplicit Visual Studio IDE'de ayarlamak için  
  
1.  Seçili bir projeyi **Çözüm Gezgini**. Üzerinde **proje** menüsünde tıklatın **özellikleri**.   
  
2.  Tıklatın **derleme** sekmesi.  
  
3.  Değer değiştirme **Option Explicit** kutusu.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod ne zaman derler `/optionexplicit-` kullanılır.  
  
 [!code-vb[VbVbalrCompiler#5](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/optionexplicit_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Option Explicit Deyimi](../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [Visual Basic Varsayılanları, projeler, Seçenekler iletişim kutusu](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)

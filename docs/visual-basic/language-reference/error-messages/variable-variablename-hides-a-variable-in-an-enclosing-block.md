---
title: "'<variablename>' değişkeni, kapsayan bir bloktaki değişkeni gizliyor"
ms.date: 07/20/2015
f1_keywords:
- vbc30616
- bc30616
helpviewer_keywords:
- BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
ms.openlocfilehash: 15c35cbb829bec782771b584ea25b111b81b5e1f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61766897"
---
# <a name="variable-variablename-hides-a-variable-in-an-enclosing-block"></a>Değişken '\<variablename >' kapsayan bir blok içinde bir değişken gizliyor
İçine bir blokta bir değişkeni başka bir yerel değişken aynı ada sahip.  
  
 **Hata Kimliği:** BC30616  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Böylece, aynı diğer herhangi bir yerel değişkenler değil kapalı bloktaki değişkeni yeniden adlandırın. Örneğin:  
  
    ```  
    Dim a, b, x As Integer  
    If a = b Then  
       Dim y As Integer = 20 ' Uniquely named block variable.  
    End If  
    ```  
  
- Bu hatanın yaygın bir nedeni kullanımıdır `Catch e As Exception` içinde bir olay işleyicisi. Bu durumda, ad `Catch` bloğu değişkeni `ex` yerine `e`.  
  
- Bu hatanın başka bir ortak kaynak içinde bildirilen yerel değişken erişme denemesi, bir `Try` ayrı bir engelleme `Catch` blok. Bunu düzeltmek için değişken dışında bildirmek `Try...Catch...Finally` yapısı.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Try...Catch...Finally Deyimi](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [Değişken Bildirimi](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)

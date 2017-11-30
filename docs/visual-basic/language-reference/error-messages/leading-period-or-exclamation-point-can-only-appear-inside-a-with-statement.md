---
title: "Önde gelen &#39;. &#39; ya &#39;! &#39; içinde yalnızca görünebilir bir &#39; İle &#39; deyimi"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30157
- bc30157
helpviewer_keywords: BC30157
ms.assetid: 70daaee1-14f9-45b7-9f30-53794310b95e
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 961f2d737123ab68b200d5fc7658cb81291a5de6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="leading-3939-or-3939-can-only-appear-inside-a-39with39-statement"></a>Önde gelen &#39;. &#39; ya &#39;! &#39; içinde yalnızca görünebilir bir &#39; İle &#39; deyimi
Bir nokta (.) veya ünlem işareti (!) olmayan iç bir `With` soldaki bir ifade olmadan blok oluşur. Üye erişimi (`.`) ve sözlük üye erişimi (`!`) üyeyi içeren öğe belirten bir ifade gerektirir. Bu hemen solundaki erişimci veya hedefi olarak görünmelidir bir `With` üye erişimi içeren bloğu.  
  
 **Hata Kimliği:** BC30157  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Emin `With` blok doğru biçimlendirilmiş.  
  
2.  Varsa hiçbir `With` engellemek, bir ifade değerlendirir erişimci üyeyi içeren tanımlanmış bir öğe sola ekleyin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kod'da özel karakterler](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)  
 [İle... End With deyimi](../../../visual-basic/language-reference/statements/with-end-with-statement.md)

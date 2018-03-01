---
title: "Başlatıcı bekleniyor"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30996
- bc30996
helpviewer_keywords:
- BC30996
ms.assetid: 6e183fe0-8888-43ed-a062-01571079455f
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 46ff91ec240212571f7ec9f26e82d9d128263545
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="initializer-expected"></a>Başlatıcı bekleniyor
Başlatma listesi aşağıdaki örnekte gösterildiği gibi boş olduğu nesne Başlatıcı kullanarak bir sınıfın örneğini bildirme denediniz.  
  
 `' Not valid.`  
  
 `' Dim aStudent As New Student With {}`  
  
 En az bir alan veya özellik Başlatıcı listesinde, aşağıdaki örnekte gösterildiği gibi başlatılması gerekir.  
  
 `Dim aStudent As New Student With {.year = "Senior"}`  
  
 **Hata Kimliği:** BC30996  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  En az bir alan veya Başlatıcı özelliğinde başlatmak veya nesne Başlatıcı kullanmayın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nesne başlatıcıları: Adlandırılmış ve anonim türler](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [Nasıl yapılır: nesne Başlatıcı kullanarak nesne bildirme](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)

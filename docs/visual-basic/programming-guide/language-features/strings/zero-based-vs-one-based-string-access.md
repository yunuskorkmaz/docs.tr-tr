---
title: "Sıfır tabanlı vs. Visual Basic'de dize tabanlı erişim"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 911f063d6ca9a3f5d88a1f50d9df7f908a488f66
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a>Sıfır tabanlı vs. Visual Basic'de dize tabanlı erişim
Bu konuda karşılaştırır nasıl [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] ve [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] bir dizedeki karakter erişim sağlar. [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Ancak her zaman bir dizedeki karakter sıfır tabanlı erişim sağlayan [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] işlevi bağlı olarak sıfır tabanlı ve tabanlı erişim sağlar.  
  
## <a name="one-based"></a>Tabanlı  
 Bir tabanlı ilişkin bir örnek [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] işlev, göz önünde bulundurun `Mid` işlevi. Alt dizeyi, 1 konumundan başlayarak başlayacağı karakterin gösteren bağımsız değişken alır. [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Substring%2A?displayProperty=nameWithType> Yöntemi alır karakter dizinini alt dizeyi olduğu başlatmak için dizesinde başlama konumu 0 ile. "ABCDE" dize varsa, bu nedenle, tek tek karakterleri 1,2,3,4,5 ile kullanmak için numaralandırılmış `Mid` işlevi ancak ile kullanılmak üzere 0,1,2,3,4 <xref:System.String.Substring%2A?displayProperty=nameWithType> yöntemi.  
  
## <a name="zero-based"></a>Sıfır tabanlı  
 Sıfır tabanlı bir örneği için [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] işlev, göz önünde bulundurun `Split` işlevi. Bir dize böler ve alt dize içeren bir dizi döndürür. [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Split%2A?displayProperty=nameWithType> Yöntemi de bir dize böler ve alt dize içeren bir dizi döndürür. Çünkü `Split` işlevi ve <xref:System.String.Split%2A> yöntemi dönüş [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] dizileri, bunlar olmalıdır sıfır tabanlı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.Strings.Mid%2A>  
 <xref:Microsoft.VisualBasic.Strings.Split%2A>  
 <xref:System.String.Substring%2A>  
 <xref:System.String.Split%2A>  
 [Visual Basic'de dizelere giriş](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)

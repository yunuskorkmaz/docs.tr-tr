---
title: Sıfır tabanlı vs. Visual Basic'de dize tabanlı erişim
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bbc418147a83b93f94449beb607d7f6bc3eff7a2
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a>Sıfır tabanlı vs. Visual Basic'de dize tabanlı erişim
Bu konuda nasıl Visual Basic karşılaştırır ve [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] bir dizedeki karakter erişim sağlar. [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Visual Basic işlevi bağlı olarak sıfır tabanlı ve tabanlı erişim sağlar ancak her zaman bir dizedeki karakter sıfır tabanlı erişim sağlar.  
  
## <a name="one-based"></a>Tabanlı  
 Örneği tabanlı Visual Basic işlevi için göz önünde bulundurun `Mid` işlevi. Alt dizeyi, 1 konumundan başlayarak başlayacağı karakterin gösteren bağımsız değişken alır. [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Substring%2A?displayProperty=nameWithType> Yöntemi alır karakter dizinini alt dizeyi olduğu başlatmak için dizesinde başlama konumu 0 ile. "ABCDE" dize varsa, bu nedenle, tek tek karakterleri 1,2,3,4,5 ile kullanmak için numaralandırılmış `Mid` işlevi ancak ile kullanılmak üzere 0,1,2,3,4 <xref:System.String.Substring%2A?displayProperty=nameWithType> yöntemi.  
  
## <a name="zero-based"></a>Sıfır tabanlı  
 Örneği sıfır tabanlı bir Visual Basic işlevi için göz önünde bulundurun `Split` işlevi. Bir dize böler ve alt dize içeren bir dizi döndürür. [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Split%2A?displayProperty=nameWithType> Yöntemi de bir dize böler ve alt dize içeren bir dizi döndürür. Çünkü `Split` işlevi ve <xref:System.String.Split%2A> yöntemi dönüş [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] dizileri, bunlar olmalıdır sıfır tabanlı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.Strings.Mid%2A>  
 <xref:Microsoft.VisualBasic.Strings.Split%2A>  
 <xref:System.String.Substring%2A>  
 <xref:System.String.Split%2A>  
 [Visual Basic'de dizelere giriş](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)

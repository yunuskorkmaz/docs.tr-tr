---
title: "&#39; Dir &#39; işlev önce çağrılmalıdır ile bir &#39; Yol &#39; bağımsız değişken"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 843918fe9cb0b9dece076b5dc1373c3571588caa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="39dir39-function-must-first-be-called-with-a-39pathname39-argument"></a>&#39; Dir &#39; işlev önce çağrılmalıdır ile bir &#39; Yol &#39; bağımsız değişken
İlk çağrısına `Dir` işlevi içermez `PathName` bağımsız değişkeni. İlk çağrıda `Dir` içermelidir bir `PathName`, ancak sonraki çağrılar `Dir` sonraki öğe almak için parametreleri gerekmez.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Tedarik bir `PathName` işlev çağrısı bağımsız değişkeni.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>

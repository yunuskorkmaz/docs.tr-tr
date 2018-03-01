---
title: '&lt;type1&gt;&#39;&lt; TypeName&gt;&#39; zorunlu uygulama &#39;&lt; MethodName&gt;&#39; arabirimi &#39;&lt; InterfaceName&gt;&#39;'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e803ec7d0054f2fa1b9ed2a731fd30c9c3060468
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="lttype1gt39lttypenamegt39-must-implement-39ltmethodnamegt39-for-interface-39ltinterfacenamegt39"></a>&lt;type1&gt;&#39;&lt; TypeName&gt;&#39; zorunlu uygulama &#39;&lt; MethodName&gt;&#39; arabirimi &#39;&lt; InterfaceName&gt;&#39;
Bir sınıf veya yapı bir arabirim talep ancak arabirim tarafından tanımlanan bir yordam uygulamıyor. Her üye arabirimin uygulanması gerekir.  
  
 **Hata Kimliği:** BC30149  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Aynı ada ve arabiriminde tanımlanan imzaya sahip bir yordam bildirin. Eklediğinizden emin olun; en az `End Function` veya `End Sub` deyimi.  
  
2.  Ekleme bir `Implements` yan tümcesi sonuna `Function` veya `Sub` deyimi. Örneğin:  
  
    ```  
    Public Sub DoSomething() Implements IBaseInterface.DoSomething  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Implements deyimi](../../../visual-basic/language-reference/statements/implements-statement.md)  
 [Arabirimleri](../../../visual-basic/programming-guide/language-features/interfaces/index.md)

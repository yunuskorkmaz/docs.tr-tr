---
title: '&lt;type1&gt;&#39;&lt; TypeName&gt;&#39; zorunlu uygulama &#39;&lt; membername&gt;&#39; arabirimi &#39;&lt; InterfaceName&gt;&#39;'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30154
- bc30154
helpviewer_keywords: BC30154
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 05e0229d0259c519d4db265c017a5040b425c79a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="lttype1gt39lttypenamegt39-must-implement-39ltmembernamegt39-for-interface-39ltinterfacenamegt39"></a>&lt;type1&gt;&#39;&lt; TypeName&gt;&#39; zorunlu uygulama &#39;&lt; membername&gt;&#39; arabirimi &#39;&lt; InterfaceName&gt;&#39;
'\<typename >' uygulamalıdır '\<membername >' arabirimi için '\<InterfaceName >'. Özellik uygulama olmalıdır eşleşen 'ReadOnly' / 'WriteOnly' tanımlayıcıları.  
  
 Bir sınıf veya yapı bir arabirim talep ancak yordamı, özelliği veya arabirim tarafından tanımlanan olay uygulamıyor. Her üye arabirimin uygulanması gerekir.  
  
 **Hata Kimliği:** BC30154  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Aynı ada ve arabiriminde tanımlanan imzaya sahip bir üye bildirin. Eklediğinizden emin olun; en az `End Function`, `End Sub`, veya `End Property` deyimi.  
  
2.  Ekleme bir `Implements` yan tümcesi sonuna `Function`, `Sub`, `Property`, veya `Event` deyimi. Örneğin:  
  
    ```  
    Public Event ItHappened() Implements IBaseInterface.ItHappened  
    ```  
  
3.  Bir özellik uygularken emin olun `ReadOnly` veya `WriteOnly` arabirim tanımı olduğu gibi aynı şekilde kullanılır.  
  
4.  Bir özellik uygularken bildirme `Get` ve `Set` uygun yordamlar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Implements deyimi](../../../visual-basic/language-reference/statements/implements-statement.md)  
 [Arabirimleri](../../../visual-basic/programming-guide/language-features/interfaces/index.md)

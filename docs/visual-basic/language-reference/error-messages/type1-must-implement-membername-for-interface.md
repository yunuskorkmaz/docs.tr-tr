---
title: '&lt;type1&gt;&#39;&lt;typename&gt; &#39; uygulamalıdır &#39; &lt;membername&gt; &#39; arabirimi için &#39; &lt;InterfaceName&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- vbc30154
- bc30154
helpviewer_keywords:
- BC30154
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
ms.openlocfilehash: 0f93bd137bdc21268cbca139ae739843561350ac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33596752"
---
# <a name="lttype1gt39lttypenamegt39-must-implement-39ltmembernamegt39-for-interface-39ltinterfacenamegt39"></a>&lt;type1&gt;&#39;&lt;typename&gt; &#39; uygulamalıdır &#39; &lt;membername&gt; &#39; arabirimi için &#39; &lt;InterfaceName&gt;&#39;
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
 [Implements Deyimi](../../../visual-basic/language-reference/statements/implements-statement.md)  
 [Arabirimler](../../../visual-basic/programming-guide/language-features/interfaces/index.md)

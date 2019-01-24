---
title: '&lt;type1&gt;&#39;&lt;typename&gt; &#39; uygulamalıdır &#39; &lt;membername&gt; &#39; Arabirimin &#39; &lt;InterfaceName&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- vbc30154
- bc30154
helpviewer_keywords:
- BC30154
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
ms.openlocfilehash: 14e7bd199215764676a4b563eafc68bd6dabadc7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574748"
---
# <a name="lttype1gt39lttypenamegt39-must-implement-39ltmembernamegt39-for-interface-39ltinterfacenamegt39"></a>&lt;type1&gt;&#39;&lt;typename&gt; &#39; uygulamalıdır &#39; &lt;membername&gt; &#39; Arabirimin &#39; &lt;InterfaceName&gt;&#39;
'\<typename >' uygulamalıdır '\<membername >' arabirimi için '\<InterfaceName >'. Uygulama özelliği olmalıdır eşleşen 'ReadOnly' / 'WriteOnly' tanımlayıcıları.  
  
 Bir sınıf veya yapı bir arabirim uygulamak talep ancak bir yordam, özellik veya olay arabirim tarafından tanımlanan uygulamaz. Her arabirimin üyesi uygulanmalıdır.  
  
 **Hata Kimliği:** BC30154  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Aynı ada ve arabirim içinde tanımlanmış olarak imzaya sahip bir üye bildirir. Eklediğinizden emin olun en az `End Function`, `End Sub`, veya `End Property` deyimi.  
  
2.  Ekleme bir `Implements` sonuna yan tümcesi `Function`, `Sub`, `Property`, veya `Event` deyimi. Örneğin:  
  
    ```  
    Public Event ItHappened() Implements IBaseInterface.ItHappened  
    ```  
  
3.  Bir özellik uygularken emin `ReadOnly` veya `WriteOnly` arabirim tanımı aynı şekilde kullanılır.  
  
4.  Bir özellik uygularken bildirmek `Get` ve `Set` yordamlar, uygun şekilde.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Implements Deyimi](../../../visual-basic/language-reference/statements/implements-statement.md)
- [Arabirimler](../../../visual-basic/programming-guide/language-features/interfaces/index.md)

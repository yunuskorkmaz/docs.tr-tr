---
title: '&lt;type1&gt;&#39;&lt;typename&gt; &#39; uygulamalıdır &#39; &lt;methodname&gt; &#39; arabirimi için &#39; &lt;InterfaceName&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
ms.openlocfilehash: daeeab853f6a7f582542fa15ffc09ce749731d6f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="lttype1gt39lttypenamegt39-must-implement-39ltmethodnamegt39-for-interface-39ltinterfacenamegt39"></a>&lt;type1&gt;&#39;&lt;typename&gt; &#39; uygulamalıdır &#39; &lt;methodname&gt; &#39; arabirimi için &#39; &lt;InterfaceName&gt;&#39;
Bir sınıf veya yapı bir arabirim talep ancak arabirim tarafından tanımlanan bir yordam uygulamıyor. Her üye arabirimin uygulanması gerekir.  
  
 **Hata Kimliği:** BC30149  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Aynı ada ve arabiriminde tanımlanan imzaya sahip bir yordam bildirin. Eklediğinizden emin olun; en az `End Function` veya `End Sub` deyimi.  
  
2.  Ekleme bir `Implements` yan tümcesi sonuna `Function` veya `Sub` deyimi. Örneğin:  
  
    ```  
    Public Sub DoSomething() Implements IBaseInterface.DoSomething  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Implements Deyimi](../../../visual-basic/language-reference/statements/implements-statement.md)  
 [Arabirimler](../../../visual-basic/programming-guide/language-features/interfaces/index.md)

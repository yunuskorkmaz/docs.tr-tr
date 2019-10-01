---
title: <type1>'<typename>', '<interfacename>' arabirimi için '<membername>' uygulamalıdır
ms.date: 07/20/2015
f1_keywords:
- vbc30154
- bc30154
helpviewer_keywords:
- BC30154
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
ms.openlocfilehash: a824b66eaad964049ced5cae5eb2cc370d00ba7f
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71696892"
---
# <a name="type1typename-must-implement-membername-for-interface-interfacename"></a>\<type1 > ' \<typename > ', ' \<ınterfacename > ' arabirimi için ' \<membername > ' uygulamalıdır
' \<typename > ', ' \<ınterfacename > ' arabirimi için ' \<membername > ' uygulamalıdır. Uygulama özelliğinin eşleşen ' ReadOnly '/' WriteOnly ' belirticileri olmalıdır.  
  
 Bir sınıf veya yapı, arabirim uygulamak için talepler, ancak arabirim tarafından tanımlanan bir yordam, özellik veya olay uygulamaz. Arabirimin her üyesinin uygulanması gerekir.  
  
 **Hata kimliği:** BC30154  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Arabirimde tanımlanan aynı ada ve imzaya sahip bir üye bildirin. En az `End Function`, `End Sub` veya `End Property` ifadesini eklediğinizden emin olun.  
  
2. @No__t-1, `Sub`, `Property` veya `Event` deyimlerinin sonuna bir `Implements` yan tümcesi ekleyin. Örneğin:  
  
    ```vb  
    Public Event ItHappened() Implements IBaseInterface.ItHappened  
    ```  
  
3. Bir özellik uygularken, `ReadOnly` veya `WriteOnly` ' in arabirim tanımındaki ile aynı şekilde kullanıldığından emin olun.  
  
4. Bir özellik uygularken, uygun şekilde `Get` ve `Set` yordamları bildirin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Implements Deyimi](../../../visual-basic/language-reference/statements/implements-statement.md)
- [Arabirimler](../../../visual-basic/programming-guide/language-features/interfaces/index.md)

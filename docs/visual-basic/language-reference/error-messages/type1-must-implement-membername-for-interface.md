---
title: <type1>'<typename>'uygulamalıdır'<membername>'interfaceiçin'<interfacename>'
ms.date: 07/20/2015
f1_keywords:
- vbc30154
- bc30154
helpviewer_keywords:
- BC30154
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
ms.openlocfilehash: 485680a2984a29037b2836fcba13cf1aa1e2e699
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58822758"
---
# <a name="type1typename-must-implement-membername-for-interface-interfacename"></a>\<type1 >'\<typename >' uygulamalıdır '\<membername >' arabirimi için '\<InterfaceName >'
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

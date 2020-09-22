---
title: <type1>'<typename>', '<interfacename>' arabirimi için '<membername>' uygulamalıdır
ms.date: 07/20/2015
f1_keywords:
- vbc30154
- bc30154
helpviewer_keywords:
- BC30154
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
ms.openlocfilehash: 7b74ee3a05000f5d6cd94176b48dea116b647a2a
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90872167"
---
# <a name="type1typename-must-implement-membername-for-interface-interfacename"></a>\<type1>'\<typename>', '\<interfacename>' arabirimi için '\<membername>' uygulamalıdır

' ', ' ' \<typename> \<membername> arabirimi için ' ' uygulamalıdır \<interfacename> . Uygulama özelliğinin eşleşen ' ReadOnly '/' WriteOnly ' belirticileri olmalıdır.  
  
 Bir sınıf veya yapı, arabirim uygulamak için talepler, ancak arabirim tarafından tanımlanan bir yordam, özellik veya olay uygulamaz. Arabirimin her üyesinin uygulanması gerekir.  
  
 **Hata kimliği:** BC30154  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Arabirimde tanımlanan aynı ada ve imzaya sahip bir üye bildirin. En azından `End Function` , `End Sub` , veya ifadesini eklediğinizden emin olun `End Property` .  
  
2. ,, `Implements` `Function` `Sub` `Property` Veya ifadesinin sonuna bir yan tümce ekleyin `Event` . Örnek:  
  
    ```vb  
    Public Event ItHappened() Implements IBaseInterface.ItHappened  
    ```  
  
3. Bir özellik uygularken, ya da ' `ReadOnly` `WriteOnly` nin arabirim tanımındaki ile aynı şekilde kullanıldığından emin olun.  
  
4. Bir özellik uygularken, `Get` ve `Set` yordamları uygun şekilde bildirir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Implements Deyimi](../statements/implements-statement.md)
- [Arabirimler](../../programming-guide/language-features/interfaces/index.md)

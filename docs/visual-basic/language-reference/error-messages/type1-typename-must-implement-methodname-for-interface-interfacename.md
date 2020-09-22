---
title: <type1>'<typename>', '<interfacename>' arabirimi için '<methodname>' uygulamalıdır
ms.date: 07/20/2015
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
ms.openlocfilehash: 8bf8872277ec901e066a8b950aaf3e61babfcc48
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90872101"
---
# <a name="type1typename-must-implement-methodname-for-interface-interfacename"></a>\<type1>'\<typename>', '\<interfacename>' arabirimi için '\<methodname>' uygulamalıdır

Bir sınıf veya yapı, arabirim uygulamak için talepler, ancak arabirim tarafından tanımlanan bir yordam uygulamaz. Arabirimin her üyesinin uygulanması gerekir.  
  
 **Hata kimliği:** BC30149  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Arabirimde tanımlanan aynı ada ve imzaya sahip bir yordam bildirin. En azından veya ifadesini eklediğinizden emin olun `End Function` `End Sub` .  
  
2. `Implements`Or ifadesinin sonuna bir yan tümce ekleyin `Function` `Sub` . Örnek:  
  
    ```vb  
    Public Sub DoSomething() Implements IBaseInterface.DoSomething  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Implements Deyimi](../statements/implements-statement.md)
- [Arabirimler](../../programming-guide/language-features/interfaces/index.md)

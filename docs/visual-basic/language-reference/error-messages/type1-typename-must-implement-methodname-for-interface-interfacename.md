---
description: "Hakkında daha fazla bilgi edinin: BC30149: <type1> ' <typename> ' <methodname> arabirim için ' ' uygulamalıdır<interfacename>"
title: <type1>'<typename>', '<interfacename>' arabirimi için '<methodname>' uygulamalıdır
ms.date: 07/20/2015
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
ms.openlocfilehash: 34635cbe5b8736d273d5972a1bb83aa3d975490b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99675019"
---
# <a name="bc30149-type1typename-must-implement-methodname-for-interface-interfacename"></a>BC30149: ' ', ' ' \<type1> \<typename> \<methodname> arabirimi için ' ' \<interfacename> uygulamalıdır

Bir sınıf veya yapı, arabirim uygulamak için talepler, ancak arabirim tarafından tanımlanan bir yordam uygulamaz. Arabirimin her üyesinin uygulanması gerekir.

 **Hata kimliği:** BC30149

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

1. Arabirimde tanımlanan aynı ada ve imzaya sahip bir yordam bildirin. En azından veya ifadesini eklediğinizden emin olun `End Function` `End Sub` .

2. `Implements`Or ifadesinin sonuna bir yan tümce ekleyin `Function` `Sub` . Örneğin:

    ```vb
    Public Sub DoSomething() Implements IBaseInterface.DoSomething
    ```

## <a name="see-also"></a>Ayrıca bkz.

- [Implements Deyimi](../statements/implements-statement.md)
- [Arabirimler](../../programming-guide/language-features/interfaces/index.md)

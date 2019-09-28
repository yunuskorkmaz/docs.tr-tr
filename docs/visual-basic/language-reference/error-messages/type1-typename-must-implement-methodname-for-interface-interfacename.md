---
title: <type1>'<typename>', '<interfacename>' arabirimi için '<methodname>' uygulamalıdır
ms.date: 07/20/2015
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
ms.openlocfilehash: c387b0225375f4675042bef593b23a084305b4fd
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71591594"
---
# <a name="type1typename-must-implement-methodname-for-interface-interfacename"></a>\<type1 > ' \<typename > ', ' \<arabirimadı > ' arabirimi için ' \<methodname > ' uygulamalıdır
Bir sınıf veya yapı, arabirim uygulamak için talepler, ancak arabirim tarafından tanımlanan bir yordam uygulamaz. Arabirimin her üyesinin uygulanması gerekir.  
  
 **Hata KIMLIĞI:** BC30149  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Arabirimde tanımlanan aynı ada ve imzaya sahip bir yordam bildirin. En azından `End Function` veya `End Sub` ifadesini eklediğinizden emin olun.  
  
2. @No__t-1 veya `Sub` ifadesinin sonuna `Implements` yan tümcesi ekleyin. Örneğin:  
  
    ```vb  
    Public Sub DoSomething() Implements IBaseInterface.DoSomething  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Implements Deyimi](../../../visual-basic/language-reference/statements/implements-statement.md)
- [Arabirimler](../../../visual-basic/programming-guide/language-features/interfaces/index.md)

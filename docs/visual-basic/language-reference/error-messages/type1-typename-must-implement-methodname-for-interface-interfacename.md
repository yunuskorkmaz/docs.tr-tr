---
title: <type1>'<typename>', '<methodname>' arabirimi için '<interfacename>' uygulamalıdır
ms.date: 07/20/2015
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
ms.openlocfilehash: c5dd7c6889a3fb5344142ee9914f98e8922d748b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55264446"
---
# <a name="type1typename-must-implement-methodname-for-interface-interfacename"></a>\<type1 >'\<typename >' uygulamalıdır '\<yöntemAdı >' arabirimi için '\<InterfaceName >'
Bir sınıf veya yapı bir arabirim uygulamak talep ancak arabirim tarafından tanımlanan bir yordam uygulamaz. Her arabirimin üyesi uygulanmalıdır.  
  
 **Hata Kimliği:** BC30149  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Bir yordam aynı adı ve imzası arabirim içinde tanımlanmış olarak bildirin. Eklediğinizden emin olun en az `End Function` veya `End Sub` deyimi.  
  
2.  Ekleme bir `Implements` sonuna yan tümcesi `Function` veya `Sub` deyimi. Örneğin:  
  
    ```  
    Public Sub DoSomething() Implements IBaseInterface.DoSomething  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Implements Deyimi](../../../visual-basic/language-reference/statements/implements-statement.md)
- [Arabirimler](../../../visual-basic/programming-guide/language-features/interfaces/index.md)

---
description: 'Daha fazla bilgi edinin: ParamArray (Visual Basic)'
title: ParamArray
ms.date: 07/20/2015
f1_keywords:
- vb.ParamArray
- ParamArray
helpviewer_keywords:
- ParamArray keyword [Visual Basic]
- ParamArray keyword [Visual Basic], syntax
ms.assetid: a5f18789-92bd-488f-9c7e-cf3719963635
ms.openlocfilehash: 064bad8a558308ee3361c11d07020e0e3bf40c13
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99730401"
---
# <a name="paramarray-visual-basic"></a>ParamArray (Visual Basic)

Bir yordam parametresinin, belirtilen türde öğe için isteğe bağlı bir dizi aldığını belirtir. `ParamArray` , yalnızca bir parametre listesinin son parametresinde kullanılabilir.  
  
## <a name="remarks"></a>Açıklamalar  

 `ParamArray` yordama rastgele sayıda bağımsız değişken geçirmenize olanak sağlar. Bir `ParamArray` parametre, her zaman [ByVal](byval.md)kullanılarak bildirilmiştir.  
  
 `ParamArray`Uygun veri türünde bir diziyi, virgülle ayrılmış bir değer listesini veya hiç bir şeyi geçirerek bir parametreye bir veya daha fazla bağımsız değişken sağlayabilirsiniz. Ayrıntılar için, [parametre dizilerindeki](../../programming-guide/language-features/procedures/parameter-arrays.md)"ParamArray çağırma" konusuna bakın.  
  
> [!IMPORTANT]
> Süresiz olarak büyük olabilecek bir dizi ile uğraşmanız durumunda, uygulamanızın bazı iç kapasitesini çok fazla çalıştırmaya yönelik bir risk vardır. Çağıran koddan bir parametre dizisini kabul ediyorsanız, uzunluğunu sınamanız ve uygulamanız için çok büyükse uygun adımları uygulamanız gerekir.  
  
 `ParamArray`Değiştirici şu bağlamlarda kullanılabilir:  
  
 [Declare Deyimi](../statements/declare-statement.md)  
  
 [Function Deyimi](../statements/function-statement.md)  
  
 [Property Deyimi](../statements/property-statement.md)  
  
 [Sub Deyimi](../statements/sub-statement.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Anahtar sözcükler](../keywords/index.md)
- [Parametre Dizileri](../../programming-guide/language-features/procedures/parameter-arrays.md)

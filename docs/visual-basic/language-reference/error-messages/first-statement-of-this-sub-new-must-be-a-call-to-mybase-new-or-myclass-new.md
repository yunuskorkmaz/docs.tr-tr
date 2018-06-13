---
title: Bu ilk deyimi &#39;Sub New&#39; yapılan bir çağrı olmalıdır &#39;MyBase.New&#39; veya &#39;MyClass.New&#39; (No Parametreler olmadan erişilebilir yapıcı)
ms.date: 07/20/2015
f1_keywords:
- bc30148
- vbc30148
helpviewer_keywords:
- BC30148
ms.assetid: 4426e8fc-cb39-4eb8-ba95-503cd32fcc89
ms.openlocfilehash: 3b24385932700a4843ae295bc82ef9529cc86b9b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33589466"
---
# <a name="first-statement-of-this-39sub-new39-must-be-a-call-to-39mybasenew39-or-39myclassnew39-no-accessible-constructor-without-parameters"></a>Bu ilk deyimi &#39;Sub New&#39; yapılan bir çağrı olmalıdır &#39;MyBase.New&#39; veya &#39;MyClass.New&#39; (No Parametreler olmadan erişilebilir yapıcı)
Bu 'Sub New' ilk deyimi 'MyBase.New' veya 'MyClass.New' için bir çağrı olmalıdır, çünkü temel sınıfı\<basename >', '\<derivedname >' bir erişilebilir 'Sub bağımsız değişkenler olmadan çağrılabilen New' yok.  
  
 Türetilen bir sınıfta her Oluşturucusu bir temel sınıf oluşturucu çağırmanız gerekir (`MyBase.New`). Taban sınıfı türetilen sınıflar için erişilebilir olan bir parametresiz oluşturucu varsa `MyBase.New` otomatik olarak çağrılabilir. Yoksa, bir taban sınıf oluşturucu parametrelerle çağrılması gerekir ve bu otomatik olarak yapılamaz. Bu durumda, her türetilmiş sınıf oluşturucu ilk deyimi gerekir parametreli Oluşturucusu çağrı üzerinde temel sınıfı veya başka bir oluşturucu çağrısı bir temel sınıf oluşturucu yapar türetilen sınıfta çağırın.  
  
 **Hata Kimliği:** BC30148  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Her iki çağrı `MyBase.New` gerekli parametreleri belirtin veya böyle bir çağrı yapar eş Oluşturucusu çağırın.  
  
     Örneğin, temel sınıf olarak bildirilen bir oluşturucu varsa `Public Sub New(ByVal index as Integer)`, ilk ifade türetilen sınıf oluşturucu olabilir `MyBase.New(100)`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Devralma Temelleri](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)

---
title: "İlk ifade bu &#39; Yeni alt &#39; Çağrı &#39;olmalıdır; MyBase.New &#39; ya &#39; MyClass.New &#39; (Parametreler olmadan erişilebilir oluşturucu yok)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30148
- vbc30148
helpviewer_keywords: BC30148
ms.assetid: 4426e8fc-cb39-4eb8-ba95-503cd32fcc89
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1065643e1f6c868092fbad839af0dbbd33afaf01
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="first-statement-of-this-39sub-new39-must-be-a-call-to-39mybasenew39-or-39myclassnew39-no-accessible-constructor-without-parameters"></a>İlk ifade bu &#39; Yeni alt &#39; Çağrı &#39;olmalıdır; MyBase.New &#39; ya &#39; MyClass.New &#39; (Parametreler olmadan erişilebilir oluşturucu yok)
Bu 'Sub New' ilk deyimi 'MyBase.New' veya 'MyClass.New' için bir çağrı olmalıdır, çünkü temel sınıfı\<basename >', '\<derivedname >' bir erişilebilir 'Sub bağımsız değişkenler olmadan çağrılabilen New' yok.  
  
 Türetilen bir sınıfta her Oluşturucusu bir temel sınıf oluşturucu çağırmanız gerekir (`MyBase.New`). Taban sınıfı türetilen sınıflar için erişilebilir olan bir parametresiz oluşturucu varsa `MyBase.New` otomatik olarak çağrılabilir. Yoksa, bir taban sınıf oluşturucu parametrelerle çağrılması gerekir ve bu otomatik olarak yapılamaz. Bu durumda, her türetilmiş sınıf oluşturucu ilk deyimi gerekir parametreli Oluşturucusu çağrı üzerinde temel sınıfı veya başka bir oluşturucu çağrısı bir temel sınıf oluşturucu yapar türetilen sınıfta çağırın.  
  
 **Hata Kimliği:** BC30148  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Her iki çağrı `MyBase.New` gerekli parametreleri belirtin veya böyle bir çağrı yapar eş Oluşturucusu çağırın.  
  
     Örneğin, temel sınıf olarak bildirilen bir oluşturucu varsa `Public Sub New(ByVal index as Integer)`, ilk ifade türetilen sınıf oluşturucu olabilir `MyBase.New(100)`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Devralma temelleri](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)

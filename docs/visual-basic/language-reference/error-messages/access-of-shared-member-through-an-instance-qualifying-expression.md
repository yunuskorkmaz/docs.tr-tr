---
title: Paylaşılan üyeye bir örnek üzerinden erişim; niteleyen ifade değerlendirilmeyecek
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42025
- BC42025
helpviewer_keywords:
- BC42025
ms.assetid: db3337e5-c349-42bf-86df-d9c1e00952a5
caps.latest.revision: 23
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bcf3c37852e73464eec612e9e1d458ca707342e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="access-of-shared-member-through-an-instance-qualifying-expression-will-not-be-evaluated"></a>Paylaşılan üyeye bir örnek üzerinden erişim; niteleyen ifade değerlendirilmeyecek
Bir örnek değişkeni bir sınıf veya yapı kullanılan erişmek için bir `Shared` değişkeni, özelliği, yordam ya da bu sınıf veya yapı tanımlanan olay. Bu uyarı bir sınıf veya bir sabit veya numaralandırma, veya iç içe geçmiş sınıf veya yapı gibi yapı örtük olarak paylaşılan bir üyesi erişmek için kullanılan bir örnek değişkeni de oluşabilir.  
  
 Üye paylaşımı amacı, bu üye yalnızca tek bir kopyasını oluşturun ve bu tek bir kopya sınıf veya yapı içinde bildirilmiş her örneği için kullanılabilir hale olmaktır. Erişmek için bu amacı ile tutarlı bir `Shared` üye, sınıf veya yapı adını aracılığıyla yerine bu sınıf veya yapı tek bir örneğini tutan bir değişken.  
  
 Erişen bir `Shared` üyesi bir örnek değişkeni üzerinden yapabilir kodunuzu üye olgu anlaşılması güç anlaşılması daha zor `Shared`. Bu tür erişim ifadenin bir parçası ise, ayrıca, diğer eylemler gibi gerçekleştiren bir `Function` paylaştırılmış üye örneğini döndürür yordamı [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] ifade ve, aksi takdirde gerçekleştirmek diğer eylemler atlar.  
  
 Daha fazla bilgi ve bir örnek için bkz: [paylaşılan](../../../visual-basic/language-reference/modifiers/shared.md).  
  
 Varsayılan olarak, bu iletiyi bir uyarıdır. Uyarıları gizleme veya uyarıları hata olarak davranma hakkında daha fazla bilgi için bkz: [yapılandırma uyarılarını Visual Basic'te](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Hata Kimliği:** BC42025  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Sınıf veya tanımlayan yapı adını kullanmak `Shared` , aşağıdaki örnekte gösterildiği gibi erişmek için üye.  
  
```vb  
Public Class testClass  
    Public Shared Sub sayHello()  
        MsgBox("Hello")  
    End Sub  
End Class  
  
Module testModule  
    Public Sub Main()  
        ' Access a shared method through an instance variable.  
        ' This generates a warning.  
        Dim tc As New testClass  
        tc.sayHello()  
  
        ' Access a shared method by using the class name.  
        ' This does not generate a warning.  
        testClass.sayHello()  
    End Sub  
End Module  
```  
  
> [!NOTE]
>  Kapsam etkilerini için uyarı iki programlama öğeleri ile aynı ada sahip olabilir. Önceki örnekte kullanarak bir örnek bildirirseniz `Dim testClass as testClass = Nothing`, çağrı derleyici değerlendirir `testClass.sayHello()` sınıf adı ve hiçbir uyarı aracılığıyla yönteminin bir erişim gerçekleştiği sırada.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Paylaşılan](../../../visual-basic/language-reference/modifiers/shared.md)  
 [Visual Basic'de kapsam](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)

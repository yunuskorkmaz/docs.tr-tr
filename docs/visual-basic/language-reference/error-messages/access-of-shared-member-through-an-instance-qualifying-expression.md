---
title: Paylaşılan üyeye bir örnek üzerinden erişim; niteleyen ifade değerlendirilmeyecek
ms.date: 07/20/2015
f1_keywords:
- vbc42025
- BC42025
helpviewer_keywords:
- BC42025
ms.assetid: db3337e5-c349-42bf-86df-d9c1e00952a5
ms.openlocfilehash: 3174d463744303e8c90ed0b2e1a4d86ed08fbcfb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947706"
---
# <a name="access-of-shared-member-through-an-instance-qualifying-expression-will-not-be-evaluated"></a>Paylaşılan üyeye bir örnek üzerinden erişim; niteleyen ifade değerlendirilmeyecek
Bir sınıf veya yapının örnek değişkeni, bu sınıf veya yapıda tanımlanan bir `Shared` değişkene, özelliğe, yordama veya olaya erişmek için kullanılır. Bu uyarı, bir sınıf veya yapının bir sabit veya numaralandırma ya da iç içe geçmiş sınıf veya yapı gibi örtülü olarak paylaşılan üyesine erişmek için kullanılıyorsa da oluşabilir.  
  
 Bir üyeyi paylaşma amacı söz konusu üyenin yalnızca tek bir kopyasını oluşturmak ve bu tek kopyayı, bildirildiği sınıf veya yapının her örneği için kullanılabilir hale getirir. Bu amaçla, bu sınıf veya yapının tek bir `Shared` örneğini tutan bir değişken yerine, sınıfının veya yapısının adı aracılığıyla bir üyeye erişmek için tutarlıdır.  
  
 Bir örnek `Shared` değişken aracılığıyla bir üyeye erişmek, kodun, üyenin olduğunu `Shared`obscuring açısından anlaşılması daha zor hale getirir. Ayrıca, bu tür erişim, paylaşılan üyenin bir örneğini döndüren bir `Function` yordam gibi diğer eylemleri gerçekleştiren bir ifadenin parçasıysa, Visual Basic ifadeyi ve aksi takdirde gerçekleştireceği diğer eylemleri atlar.  
  
 Daha fazla bilgi ve bir örnek için bkz. [Shared](../../../visual-basic/language-reference/modifiers/shared.md).  
  
 Bu ileti, varsayılan olarak bir uyarıdır. Uyarıları gizleme veya uyarıları hata olarak değerlendirme hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Hata KIMLIĞI:** BC42025  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Aşağıdaki örnekte gösterildiği gibi, ona erişmek için `Shared` üyeyi tanımlayan sınıf veya yapının adını kullanın.  
  
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
> İki programlama öğesi aynı ada sahip olduğunda kapsamın etkileri için uyarı olun. Önceki örnekte, kullanarak `Dim testClass as testClass = Nothing`bir örneği bildirirseniz derleyici, sınıf adı aracılığıyla yöntemine bir erişim `testClass.sayHello()` olarak bir çağrı uygular ve uyarı oluşmaz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
- [Visual Basic kapsam](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)

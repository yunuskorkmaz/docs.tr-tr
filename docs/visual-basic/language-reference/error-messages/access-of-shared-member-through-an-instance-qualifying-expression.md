---
title: Paylaşılan üyeye bir örnek üzerinden erişim; niteleyen ifade değerlendirilmeyecek
ms.date: 07/20/2015
f1_keywords:
- vbc42025
- BC42025
helpviewer_keywords:
- BC42025
ms.assetid: db3337e5-c349-42bf-86df-d9c1e00952a5
ms.openlocfilehash: 773a97c301e7cb5bec0234ae466d487ec9716437
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250341"
---
# <a name="access-of-shared-member-through-an-instance-qualifying-expression-will-not-be-evaluated"></a>Paylaşılan üyeye bir örnek üzerinden erişim; niteleyen ifade değerlendirilmeyecek

Bir sınıf veya yapının örnek değişkeni, bu sınıf veya yapıda tanımlanmış bir `Shared` değişkenine, özelliğe, yordama veya olaya erişmek için kullanılır. Bu uyarı, bir sınıf veya yapının bir sabit veya numaralandırma ya da iç içe geçmiş sınıf veya yapı gibi örtülü olarak paylaşılan üyesine erişmek için kullanılıyorsa da oluşabilir.

Bir üyeyi paylaşma amacı söz konusu üyenin yalnızca tek bir kopyasını oluşturmak ve bu tek kopyayı, bildirildiği sınıf veya yapının her örneği için kullanılabilir hale getirir. Bu amaçla, bu sınıf veya yapının tek bir örneğini tutan bir değişken yerine, sınıfının veya yapısının adı aracılığıyla `Shared` üyesine erişmek için tutarlıdır.

Örnek değişken aracılığıyla `Shared` üyesine erişmek, üyenin `Shared` olduğunu bularak kodunuzun anlaşılması daha zor hale getirir. Ayrıca, bu tür erişim, paylaşılan üyenin bir örneğini döndüren `Function` yordamı gibi diğer eylemleri gerçekleştiren bir ifadenin parçasıysa, Visual Basic ifadeyi ve aksi takdirde gerçekleştireceği diğer eylemleri atlar.  
  
Daha fazla bilgi ve bir örnek için bkz. [Shared](../modifiers/shared.md).  
  
Bu ileti, varsayılan olarak bir uyarıdır. Uyarıları gizleme veya uyarıları hata olarak değerlendirme hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
**Hata kimliği:** BC42025  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
Aşağıdaki örnekte gösterildiği gibi, ona erişmek için `Shared` üyesini tanımlayan sınıf veya yapının adını kullanın:
  
```vb
Public Class TestClass
    Public Shared Sub SayHello()
        MsgBox("Hello")
    End Sub
End Class
  
Module Program
    Public Sub Main()  
        ' Access a shared method through an instance variable.  
        ' This generates a warning.  
        Dim tc As New TestClass()
        tc.SayHello()
  
        ' Access a shared method by using the class name.  
        ' This does not generate a warning.  
        TestClass.SayHello()
    End Sub  
End Module  
```  
  
> [!NOTE]
> İki programlama öğesi aynı ada sahip olduğunda kapsamın etkileri için uyarı olun. Önceki örnekte, `Dim testClass as testClass = Nothing` kullanarak bir örnek bildirirseniz, derleyici, sınıf adı aracılığıyla yöntemin erişimi olarak `testClass.sayHello()` ' e bir çağrı uygular ve uyarı oluşmaz.
  
## <a name="see-also"></a>Ayrıca bkz.

- [Shared](../modifiers/shared.md)
- [Visual Basic kapsam](../../programming-guide/language-features/declared-elements/scope.md)

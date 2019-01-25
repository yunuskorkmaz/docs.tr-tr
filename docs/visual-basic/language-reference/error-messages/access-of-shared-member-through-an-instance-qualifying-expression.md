---
title: Paylaşılan üyeye bir örnek üzerinden erişim; niteleyen ifade değerlendirilmeyecek
ms.date: 07/20/2015
f1_keywords:
- vbc42025
- BC42025
helpviewer_keywords:
- BC42025
ms.assetid: db3337e5-c349-42bf-86df-d9c1e00952a5
ms.openlocfilehash: 78981e5af0d4bf1694a3ad7c9ead2e4e7fd9330e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54703555"
---
# <a name="access-of-shared-member-through-an-instance-qualifying-expression-will-not-be-evaluated"></a>Paylaşılan üyeye bir örnek üzerinden erişim; niteleyen ifade değerlendirilmeyecek
Bir sınıfın veya yapının bir örnek değişkeni kullanılan erişmek için bir `Shared` değişken, özellik, yordam veya o sınıfta veya yapıda da tanımlı olay. Bu uyarı bir sınıf veya yapı, sabit veya sabit listesi, bir iç içe geçmiş sınıf veya yapı gibi örtük olarak paylaşılan bir üyesine erişmek için kullanılan bir örnek değişkeni de oluşabilir.  
  
 Üye paylaşımı amacı, bu üyede tek bir kopyasını oluşturun ve bu tek kopyası, sınıf veya yapı içinde bildirildiği'nin her örneğinin kullanımına sağlamaktır. Bu amaca uygun erişmek için tutarlı bir `Shared` üyesi, bir sınıfın veya yapının adını, yerine bu sınıfı ya da yapı tek bir örneğini tutan değişken üzerinden.  
  
 Erişim bir `Shared` üyeye bir örnek değişkeni üzerinden yapabilir, kodunuzun daha zor bir üyesi olan bir olgu, anlaşılması güç tarafından anlamak `Shared`. Bu tür erişim ifadesinin bir parçası ise Ayrıca, diğer eylemler gibi gerçekleştiren bir `Function` paylaşılan üyenin bir örneğinin döndüren yordam, Visual Basic atlar ifade ve aksi takdirde gerçekleştirmek diğer tüm eylemler.  
  
 Daha fazla bilgi ve örnek için bkz. [paylaşılan](../../../visual-basic/language-reference/modifiers/shared.md).  
  
 Varsayılan olarak, bu iletiyi bir uyarıdır. Uyarıları gizleme veya uyarıları hata olarak değerlendirmesini hakkında daha fazla bilgi için bkz. [Visual Basic'teki uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Hata Kimliği:** BC42025  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Sınıf veya tanımlayan yapısını adını kullanın `Shared` , aşağıdaki örnekte gösterildiği gibi erişmek için üye.  
  
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
>  Kapsam etkileri için uyarı iki programlama öğeleri aynı ada sahip olun. Önceki örnekte kullanarak örneği bildirirseniz `Dim testClass as testClass = Nothing`, derleyici bir çağrı işler `testClass.sayHello()` yöntemin sınıf adı ve hiçbir uyarı aracılığıyla erişim gerçekleştiği sırada.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
- [Visual Basic'de kapsam](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)

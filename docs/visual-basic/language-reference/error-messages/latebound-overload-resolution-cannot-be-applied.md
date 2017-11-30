---
title: "Bağlanan aşırı yükleme çözünürlüğü uygulanamaz &#39; &lt;procedurename&gt;&#39; çünkü erişen örnek bir arabirim türü"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30933
- bc30933
helpviewer_keywords:
- overload resolution [Visual Basic], with late-bound argument
- BC30933
ms.assetid: 8182eea0-dd34-4d6e-9ca0-41d8713e9dc4
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fb7f8a9f6eadfc9fd856ea57d362b43d25ff81a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="latebound-overload-resolution-cannot-be-applied-to-39ltprocedurenamegt39-because-the-accessing-instance-is-an-interface-type"></a>Bağlanan aşırı yükleme çözünürlüğü uygulanamaz &#39; &lt;procedurename&gt;&#39; çünkü erişen örnek bir arabirim türü
Derleyici aşırı yüklenmiş özelliği ya da yordamı başvuru çözümlemeye çalışıyor, ancak başvuru türünde bir bağımsız değişken olduğu için başarısız `Object` ve başvuran nesne bir arabirim veri türüne sahip. `Object` Bağımsız değişkeni referans geç bağlama olarak çözmek için derleme zorlar.  
  
 Bu durumlarda, derleyici yerine uygulayan sınıfa temel arabirimi aracılığıyla aracılığıyla aşırı çözümler. Sınıfı aşırı yüklenmiş sürümlerinden birini adlandırdığında derleyici adından farklı olduğundan bir aşırı olması için bu sürümü dikkate almaz. Bu sırayla başvuruyu çözümlemek için doğru seçim olabilir, yeniden adlandırılmış sürüm yoksay derleyici neden olur.  
  
 **Hata Kimliği:** BC30933  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Kullanım `CType` bağımsız değişkende yayınlanamıyor `Object` istediğiniz çağırmak için aşırı yük imzayı tarafından belirtilen tür için.  
  
     Bu temel arabirimi başvuran nesnesi yayınlanamıyor korumaz unutmayın. Bu hatayı önlemek için bağımsız değişken dönüştürmeniz gerekir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte bir aşırı yüklenmiş bir çağrı gösterilmektedir `Sub` derleme zamanında bu hataya neden yordamı.  
  
```  
Module m1  
    Interface i1  
        Sub s1(ByVal p1 As Integer)  
        Sub s1(ByVal p1 As Double)  
    End Interface  
    Class c1  
        Implements i1  
        Public Overloads Sub s1(ByVal p1 As Integer) Implements i1.s1  
        End Sub  
        Public Overloads Sub s2(ByVal p1 As Double) Implements i1.s1  
        End Sub  
    End Class  
    Sub Main()  
        Dim refer As i1 = New c1  
        Dim o1 As Object = 3.1415  
        ' The following reference is INVALID and causes a compiler error.  
        refer.s1(o1)   
    End Sub  
End Module  
```  
  
 Önceki örnekte derleyici çağrısına izin veriyorsa `s1` yazıldığı şekilde çözümleme sınıfı aracılığıyla gerçekleşmesi `c1` arabirimi yerine `i1`. Derleyici değil düşünün anlamına gelir `s2` adından farklı olduğundan `c1`, doğru seçim tarafından tanımlanan olmasına rağmen `i1`.  
  
 Aşağıdaki kod satırlarını birini çağrısı değiştirerek hatayı çözebilirsiniz:  
  
```  
refer.s1(CType(o1, Integer))  
refer.s1(CType(o1, Double))  
```  
  
 Her bir önceki kod satırları açıkça bıraktığı `Object` değişkeni `o1` aşırı yüklemeleri için tanımlanan parametre türleri birine.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yordam aşırı yüklemesi](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)  
 [Aşırı yükleme çözümü](../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md)  
 [CType işlevi](../../../visual-basic/language-reference/functions/ctype-function.md)

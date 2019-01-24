---
title: Geç bağlanan aşırı yükleme çözünürlüğü uygulanamaz &#39; &lt;procedurename&gt; &#39; örnek bir arabirim türü olduğundan
ms.date: 07/20/2015
f1_keywords:
- vbc30933
- bc30933
helpviewer_keywords:
- overload resolution [Visual Basic], with late-bound argument
- BC30933
ms.assetid: 8182eea0-dd34-4d6e-9ca0-41d8713e9dc4
ms.openlocfilehash: db0ce88f63be8d58cc1c1abf91eda6a0e56456c6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54651528"
---
# <a name="latebound-overload-resolution-cannot-be-applied-to-39ltprocedurenamegt39-because-the-accessing-instance-is-an-interface-type"></a>Geç bağlanan aşırı yükleme çözünürlüğü uygulanamaz &#39; &lt;procedurename&gt; &#39; örnek bir arabirim türü olduğundan
Derleyici bir aşırı yüklenmiş özellik veya yordamı başvuru çözmeye çalışıyor, ancak başvuru türünde bir bağımsız değişken olduğu için başarısız `Object` ve başvurulan nesne bir arabirim için veri türüne sahip. `Object` Bağımsız değişken başvuru geç bağlama olarak çözümlemek için derleyici zorlar.  
  
 Bu durumlarda, derleyici aşırı yükleme yerine temel alınan arabirimini uygulayan sınıfa aracılığıyla çözümler. Sınıfı aşırı yüklü sürümlerini adlandırdığında derleyici bu sürümü adını farklı olduğundan, bir yükleme olarak dikkate almaz. Bu sırayla başvuru gidermek için doğru seçim olabilir, yeniden adlandırılmış sürüm yoksayma konusunda derleyici neden olur.  
  
 **Hata Kimliği:** BC30933  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Kullanım `CType` bağımsız değişkende bir şekilde `Object` istediğiniz çağırmak için aşırı yükleme imzası tarafından belirtilen tür için.  
  
     Bu temel arabirimi başvuran nesnenin korumaz unutmayın. Bu hatayı önlemek için bağımsız değişken dönüştürmeniz gerekir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, aşırı yüklenmiş bir çağrı gösterir `Sub` yordam derleme zamanında bu hataya neden olur.  
  
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
  
 Önceki örnekte derleyici çağrısına izin veriliyorsa `s1` yazıldığı gibi çözümleme sınıfı üzerinden gerçekleşmesi `c1` arabirimi yerine `i1`. Bu derleyici değil dikkate alır anlamına gelir `s2` adını farklı olduğundan `c1`, doğru seçeneği tarafından tanımlanan olmasına rağmen `i1`.  
  
 Hatayı düzeltmek için ya da aşağıdaki kod satırlarını çağrısı değiştirerek:  
  
```  
refer.s1(CType(o1, Integer))  
refer.s1(CType(o1, Double))  
```  
  
 Her biri önceki kod satırlarını açıkça bıraktığı `Object` değişkeni `o1` biri aşırı yüklemeleri için tanımlanmış bir parametre türleri olarak.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Yordam Aşırı Yüklemesi](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)
- [Aşırı Yükleme Çözümü](../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md)
- [CType İşlevi](../../../visual-basic/language-reference/functions/ctype-function.md)

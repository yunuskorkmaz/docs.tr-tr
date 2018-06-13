---
title: Değişken için tür &#39; &lt;variablename&gt; &#39; kapsayan bir kapsama alanına bağlı olduğundan, çıkarılabilir olacaktır değil
ms.date: 07/20/2015
f1_keywords:
- vbc42110
- bc42110
helpviewer_keywords:
- BC42110
ms.assetid: ef4442eb-08d1-434f-a03b-4aa2ed4e4414
ms.openlocfilehash: cb423e8dcced6956eb86d484607915030c91412b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33594289"
---
# <a name="the-type-for-variable-39ltvariablenamegt39-will-not-be-inferred-because-it-is-bound-to-a-field-in-an-enclosing-scope"></a>Değişken için tür &#39; &lt;variablename&gt; &#39; kapsayan bir kapsama alanına bağlı olduğundan, çıkarılabilir olacaktır değil
Değişken türü '\<variablename >' kapsayan bir kapsama alanına bağlı olduğundan, çıkarılabilir olacaktır değil. Adını değiştirmek '\<variablename >', veya tam adı (örneğin, 'Me.variablename' veya 'MyBase.variablename') kullanın.  
  
 For döngüsü denetim değişkeni kodunuzda sınıfı ya da diğer çevreleyen kapsamdaki bir alan olarak aynı ada sahip. Denetim değişkeni olmadan kullanıldığından bir `As` yan tümcesi, çevreleyen kapsamdaki alanına bağlı ve derleyici yeni bir değişken için oluşturamadı veya türünü Infer.  
  
 Aşağıdaki örnekte, `Index`, Denetim değişkeninde `For` deyimi, bağlı `Index` alanındaki `Customer` sınıfı. Derleyici denetimi değişken için yeni bir değişken oluşturmaz `Index` veya türünü Infer.  
  
```  
Class Customer  
  
    ' The class has a field named Index.  
    Private Index As Integer  
  
    Sub Main()  
  
    ' The following line will raise this warning.  
        For Index = 1 To 10  
            ' ...  
        Next  
  
    End Sub  
End Class  
```  
  
 Varsayılan olarak, bu iletiyi bir uyarıdır. Uyarıları gizleme veya uyarıları hata ele hakkında daha fazla bilgi için bkz: [yapılandırma uyarılarını Visual Basic'te](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Hata Kimliği:** BC42110  
  
### <a name="to-address-this-warning"></a>Bu uyarıyı gidermek için  
  
-   For döngüsü denetim değişkeni sınıfının bir alanın adı olmayan bir tanımlayıcı adını değiştirerek yerel olun.  
  
    ```  
    For I = 1 To 10  
    ```  
  
-   For döngüsü denetim değişkeni ekleyerek sınıfı alanına bağlar açıklamak `Me.` değişken adı.  
  
    ```  
    For Me.Index = 1 To 10  
    ```  
  
-   Yerel türü çıkarımı güvenmek yerine, kullanın bir `As` tümcesi for döngüsü denetim değişkeni için bir tür belirtin.  
  
    ```  
    For Index As Integer = 1 To 10  
    ```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, daha önceki örnekteki ilk düzeltme yerinde gösterir.  
  
```  
Class Customer  
  
    ' The class has a field named Index.  
    Private Index As Integer  
  
    Sub Main()  
  
        For I = 1 To 10  
            ' ...  
        Next  
  
    End Sub  
End Class  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Option Infer Deyimi](../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [For Each...Next Deyimi](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [For...Next Deyimi](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [Nasıl yapılır: Bir Nesnenin Geçerli Örneğine Başvurma](../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)  
 [Yerel Çıkarım](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Me, My, MyBase ve MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)

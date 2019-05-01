---
title: "'<variablename>' değişkeninin türü sarmalayan bir kapsamda bir alana bağlı olduğundan çıkarılmayacak"
ms.date: 07/20/2015
f1_keywords:
- vbc42110
- bc42110
helpviewer_keywords:
- BC42110
ms.assetid: ef4442eb-08d1-434f-a03b-4aa2ed4e4414
ms.openlocfilehash: bcd142785d8ee736c6a1b41950fae80e4d26fa18
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013653"
---
# <a name="the-type-for-variable-variablename-will-not-be-inferred-because-it-is-bound-to-a-field-in-an-enclosing-scope"></a>Değişkeninin türü '\<variablename >' sarmalayan bir kapsamda bir alana bağlı olduğundan çıkarılmayacak
Değişkeninin türü '\<variablename >' sarmalayan bir kapsamda bir alana bağlı olduğundan çıkarılmayacak. Adını değiştirmek ya da '\<variablename >', veya tam adı (örneğin, 'Me.variablename' veya 'MyBase.variablename') kullanın.  
  
 Bir for döngüsü denetim değişkeni kodunuzda, sınıf ya da diğer kapsayan kapsam alan olarak aynı ada sahip. Denetim değişkeni olmadan kullanıldığından bir `As` yan tümcesi, kapsayan kapsamda alana bağlı ve derleyici için yeni bir değişken oluşturamadı veya kendi türü çıkarımı.  
  
 Aşağıdaki örnekte, `Index`, Denetim değişkeninde `For` deyimi, bağlı `Index` alanındaki `Customer` sınıfı. Derleyici, denetim değişkeni için yeni bir değişken oluşturmaz `Index` veya türü çıkarılamıyor.  
  
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
  
 Varsayılan olarak, bu iletiyi bir uyarıdır. Uyarıları Gizle veya uyarıları hata olarak değerlendir hakkında daha fazla bilgi için bkz: [Visual Basic'teki uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Hata Kimliği:** BC42110  
  
### <a name="to-address-this-warning"></a>Bu uyarıyı gidermek için  
  
- Ayrıca sınıfın bir alanın adı olmayan bir tanımlayıcı adını değiştirerek döngü denetim değişkeni yerel olun.  
  
    ```  
    For I = 1 To 10  
    ```  
  
- Döngü denetim değişkeni ekleyerek sınıfı alanına bağlar açıklamak `Me.` değişken adı.  
  
    ```  
    For Me.Index = 1 To 10  
    ```  
  
- Yerel tür çıkarımı üzerinde bağlı olan yerine bir `As` yan tümcesi for döngüsü denetim değişkeni için bir tür belirtmek için.  
  
    ```  
    For Index As Integer = 1 To 10  
    ```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, önceki örnekte ilk düzeltme yerinde gösterir.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [Option Infer Deyimi](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [For Each...Next Deyimi](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [For...Next Deyimi](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Nasıl yapılır: Bir nesnenin geçerli örneğine başvurma](../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)
- [Yerel Çıkarım](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Me, My, MyBase ve MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)

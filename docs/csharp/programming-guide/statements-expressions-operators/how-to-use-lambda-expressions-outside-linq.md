---
title: 'Nasıl yapılır: LINQ Dışında Lambda İfadeleri Kullanma (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], outside LINQ
ms.assetid: 2b519274-6ee4-4455-ab2e-aed67dbfd07c
ms.openlocfilehash: 7a4595859839ea964d85ed89e6732198bd8a30f1
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44176789"
---
# <a name="how-to-use-lambda-expressions-outside-linq-c-programming-guide"></a>Nasıl yapılır: LINQ Dışında Lambda İfadeleri Kullanma (C# Programlama Kılavuzu)
Lambda ifadeleri, bunlarla sınırlı değildir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgular. Anonim bir yöntem kullanılabilir her yerde bunları bir temsilci değeri, diğer bir deyişle, beklenen her yerde kullanabilirsiniz. Aşağıdaki örnek, bir Windows Forms olay işleyicisinde bir lambda ifadesi kullanmayı gösterir. Dikkat girişleri türleri (<xref:System.Object> ve <xref:System.Windows.Forms.MouseEventArgs>) derleyici tarafından algılanır ve lambda giriş parametreleri açıkça verilmesi gerekmez.  
  
## <a name="example"></a>Örnek  
  
```  
public partial class Form1 : Form  
{  
    public Form1()  
    {  
        InitializeComponent();  
        // Use a lambda expression to define an event handler.  
       this.Click += (s, e) => { MessageBox.Show(((MouseEventArgs)e).Location.ToString());};  
    }  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [Lambda İfadeleri](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
- [Anonim Metotlar](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
- [Dil ile tümleşik sorgu (LINQ))](../../../csharp/programming-guide/concepts/linq/index.md)

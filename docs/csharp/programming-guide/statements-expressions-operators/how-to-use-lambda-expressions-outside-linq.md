---
title: 'Nasıl yapılır: LINQ C# programlama kılavuzunun dışında lambda ifadeleri kullanma'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], outside LINQ
ms.assetid: 2b519274-6ee4-4455-ab2e-aed67dbfd07c
ms.openlocfilehash: 947f80fdaa90b6b5f8176aac01dd8e3cf40e38cc
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2019
ms.locfileid: "68363778"
---
# <a name="how-to-use-lambda-expressions-outside-linq-c-programming-guide"></a>Nasıl yapılır: LINQ dışında lambda Ifadeleri kullanma (C# Programlama Kılavuzu)
Lambda ifadeleri [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgularla sınırlı değildir. Bunları bir temsilci değeri beklendiğinde, yani anonim bir yöntemin kullanılabileceği her yerde kullanabilirsiniz. Aşağıdaki örnek, Windows Forms olay işleyicisinde bir lambda ifadesinin nasıl kullanılacağını gösterir. Giriş türlerinin (<xref:System.Object> ve <xref:System.Windows.Forms.MouseEventArgs>) derleyici tarafından çıkarsandığına ve lambda giriş parametrelerinde açıkça verilmemelidir.  
  
## <a name="example"></a>Örnek  
  
```csharp  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [Lambda İfadeleri](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
- [Dil ile tümleşik sorgu (LINQ))](../../../csharp/programming-guide/concepts/linq/index.md)

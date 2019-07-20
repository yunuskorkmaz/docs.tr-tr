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
# <a name="how-to-use-lambda-expressions-outside-linq-c-programming-guide"></a><span data-ttu-id="5006d-102">Nasıl yapılır: LINQ dışında lambda Ifadeleri kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="5006d-102">How to: Use Lambda Expressions Outside LINQ (C# Programming Guide)</span></span>
<span data-ttu-id="5006d-103">Lambda ifadeleri [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgularla sınırlı değildir.</span><span class="sxs-lookup"><span data-stu-id="5006d-103">Lambda expressions are not limited to [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries.</span></span> <span data-ttu-id="5006d-104">Bunları bir temsilci değeri beklendiğinde, yani anonim bir yöntemin kullanılabileceği her yerde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5006d-104">You can use them anywhere a delegate value is expected, that is, wherever an anonymous method can be used.</span></span> <span data-ttu-id="5006d-105">Aşağıdaki örnek, Windows Forms olay işleyicisinde bir lambda ifadesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5006d-105">The following example shows how to use a lambda expression in a Windows Forms event handler.</span></span> <span data-ttu-id="5006d-106">Giriş türlerinin (<xref:System.Object> ve <xref:System.Windows.Forms.MouseEventArgs>) derleyici tarafından çıkarsandığına ve lambda giriş parametrelerinde açıkça verilmemelidir.</span><span class="sxs-lookup"><span data-stu-id="5006d-106">Notice that the types of the inputs (<xref:System.Object> and <xref:System.Windows.Forms.MouseEventArgs>) are inferred by the compiler and do not have to be explicitly given in the lambda input parameters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5006d-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="5006d-107">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5006d-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5006d-108">See also</span></span>

- [<span data-ttu-id="5006d-109">Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="5006d-109">Lambda Expressions</span></span>](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
- [<span data-ttu-id="5006d-110">Dil ile tümleşik sorgu (LINQ))</span><span class="sxs-lookup"><span data-stu-id="5006d-110">Language Integrated Query (LINQ))</span></span>](../../../csharp/programming-guide/concepts/linq/index.md)

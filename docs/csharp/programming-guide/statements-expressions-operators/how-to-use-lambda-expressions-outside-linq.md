---
title: 'Nasıl yapılır: LINQ Dışında Lambda İfadeleri Kullanma (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], outside LINQ
ms.assetid: 2b519274-6ee4-4455-ab2e-aed67dbfd07c
ms.openlocfilehash: eb9fea64b8aeb96a880b7e177673c1316b7aa4c1
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2018
ms.locfileid: "44368776"
---
# <a name="how-to-use-lambda-expressions-outside-linq-c-programming-guide"></a><span data-ttu-id="00ca8-102">Nasıl yapılır: LINQ Dışında Lambda İfadeleri Kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="00ca8-102">How to: Use Lambda Expressions Outside LINQ (C# Programming Guide)</span></span>
<span data-ttu-id="00ca8-103">Lambda ifadeleri, bunlarla sınırlı değildir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgular.</span><span class="sxs-lookup"><span data-stu-id="00ca8-103">Lambda expressions are not limited to [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries.</span></span> <span data-ttu-id="00ca8-104">Anonim bir yöntem kullanılabilir her yerde bunları bir temsilci değeri, diğer bir deyişle, beklenen her yerde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="00ca8-104">You can use them anywhere a delegate value is expected, that is, wherever an anonymous method can be used.</span></span> <span data-ttu-id="00ca8-105">Aşağıdaki örnek, bir Windows Forms olay işleyicisinde bir lambda ifadesi kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="00ca8-105">The following example shows how to use a lambda expression in a Windows Forms event handler.</span></span> <span data-ttu-id="00ca8-106">Dikkat girişleri türleri (<xref:System.Object> ve <xref:System.Windows.Forms.MouseEventArgs>) derleyici tarafından algılanır ve lambda giriş parametreleri açıkça verilmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="00ca8-106">Notice that the types of the inputs (<xref:System.Object> and <xref:System.Windows.Forms.MouseEventArgs>) are inferred by the compiler and do not have to be explicitly given in the lambda input parameters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="00ca8-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="00ca8-107">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="00ca8-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="00ca8-108">See Also</span></span>

- [<span data-ttu-id="00ca8-109">Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="00ca8-109">Lambda Expressions</span></span>](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
- [<span data-ttu-id="00ca8-110">Anonim Metotlar</span><span class="sxs-lookup"><span data-stu-id="00ca8-110">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
- [<span data-ttu-id="00ca8-111">Dil ile tümleşik sorgu (LINQ))</span><span class="sxs-lookup"><span data-stu-id="00ca8-111">Language Integrated Query (LINQ))</span></span>](../../../csharp/programming-guide/concepts/linq/index.md)

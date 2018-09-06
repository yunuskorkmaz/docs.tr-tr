---
title: 'Nasıl yapılır: LINQ Dışında Lambda İfadeleri Kullanma (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], outside LINQ
ms.assetid: 2b519274-6ee4-4455-ab2e-aed67dbfd07c
ms.openlocfilehash: 7a4595859839ea964d85ed89e6732198bd8a30f1
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43866748"
---
# <a name="how-to-use-lambda-expressions-outside-linq-c-programming-guide"></a><span data-ttu-id="0d4f8-102">Nasıl yapılır: LINQ Dışında Lambda İfadeleri Kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="0d4f8-102">How to: Use Lambda Expressions Outside LINQ (C# Programming Guide)</span></span>
<span data-ttu-id="0d4f8-103">Lambda ifadeleri, bunlarla sınırlı değildir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgular.</span><span class="sxs-lookup"><span data-stu-id="0d4f8-103">Lambda expressions are not limited to [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries.</span></span> <span data-ttu-id="0d4f8-104">Anonim bir yöntem kullanılabilir her yerde bunları bir temsilci değeri, diğer bir deyişle, beklenen her yerde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d4f8-104">You can use them anywhere a delegate value is expected, that is, wherever an anonymous method can be used.</span></span> <span data-ttu-id="0d4f8-105">Aşağıdaki örnek, bir Windows Forms olay işleyicisinde bir lambda ifadesi kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="0d4f8-105">The following example shows how to use a lambda expression in a Windows Forms event handler.</span></span> <span data-ttu-id="0d4f8-106">Dikkat girişleri türleri (<xref:System.Object> ve <xref:System.Windows.Forms.MouseEventArgs>) derleyici tarafından algılanır ve lambda giriş parametreleri açıkça verilmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="0d4f8-106">Notice that the types of the inputs (<xref:System.Object> and <xref:System.Windows.Forms.MouseEventArgs>) are inferred by the compiler and do not have to be explicitly given in the lambda input parameters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d4f8-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="0d4f8-107">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0d4f8-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0d4f8-108">See Also</span></span>

- [<span data-ttu-id="0d4f8-109">Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="0d4f8-109">Lambda Expressions</span></span>](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
- [<span data-ttu-id="0d4f8-110">Anonim Metotlar</span><span class="sxs-lookup"><span data-stu-id="0d4f8-110">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
- [<span data-ttu-id="0d4f8-111">Dil ile tümleşik sorgu (LINQ))</span><span class="sxs-lookup"><span data-stu-id="0d4f8-111">Language Integrated Query (LINQ))</span></span>](../../../csharp/programming-guide/concepts/linq/index.md)

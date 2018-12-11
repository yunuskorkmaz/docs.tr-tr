---
title: 'Nasıl Yapılır: -LINQ dışında lambda ifadeleri kullanma C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], outside LINQ
ms.assetid: 2b519274-6ee4-4455-ab2e-aed67dbfd07c
ms.openlocfilehash: d4dc0375552ef1fe00f629c22b5296399b4cc99d
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243939"
---
# <a name="how-to-use-lambda-expressions-outside-linq-c-programming-guide"></a><span data-ttu-id="f8c23-102">Nasıl Yapılır: LINQ dışında lambda ifadeleri kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="f8c23-102">How to: Use Lambda Expressions Outside LINQ (C# Programming Guide)</span></span>
<span data-ttu-id="f8c23-103">Lambda ifadeleri, bunlarla sınırlı değildir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgular.</span><span class="sxs-lookup"><span data-stu-id="f8c23-103">Lambda expressions are not limited to [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries.</span></span> <span data-ttu-id="f8c23-104">Anonim bir yöntem kullanılabilir her yerde bunları bir temsilci değeri, diğer bir deyişle, beklenen her yerde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8c23-104">You can use them anywhere a delegate value is expected, that is, wherever an anonymous method can be used.</span></span> <span data-ttu-id="f8c23-105">Aşağıdaki örnek, bir Windows Forms olay işleyicisinde bir lambda ifadesi kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="f8c23-105">The following example shows how to use a lambda expression in a Windows Forms event handler.</span></span> <span data-ttu-id="f8c23-106">Dikkat girişleri türleri (<xref:System.Object> ve <xref:System.Windows.Forms.MouseEventArgs>) derleyici tarafından algılanır ve lambda giriş parametreleri açıkça verilmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="f8c23-106">Notice that the types of the inputs (<xref:System.Object> and <xref:System.Windows.Forms.MouseEventArgs>) are inferred by the compiler and do not have to be explicitly given in the lambda input parameters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8c23-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="f8c23-107">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f8c23-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f8c23-108">See Also</span></span>

- [<span data-ttu-id="f8c23-109">Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="f8c23-109">Lambda Expressions</span></span>](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
- [<span data-ttu-id="f8c23-110">Anonim Metotlar</span><span class="sxs-lookup"><span data-stu-id="f8c23-110">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
- [<span data-ttu-id="f8c23-111">Dil ile tümleşik sorgu (LINQ))</span><span class="sxs-lookup"><span data-stu-id="f8c23-111">Language Integrated Query (LINQ))</span></span>](../../../csharp/programming-guide/concepts/linq/index.md)

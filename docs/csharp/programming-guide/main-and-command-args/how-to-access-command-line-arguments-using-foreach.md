---
title: "Nasıl yapılır: foreach Kullanarak Komut Satırı Bağımsız Değişkenlerine Erişme (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: command-line arguments [C#]
ms.assetid: 89c3e335-3f5b-4e24-8c5a-b8036561fe8a
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 557e72342901fab8bbe66e9cc3405cb4b2d9c1e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-command-line-arguments-using-foreach-c-programming-guide"></a><span data-ttu-id="bb829-102">Nasıl yapılır: foreach Kullanarak Komut Satırı Bağımsız Değişkenlerine Erişme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="bb829-102">How to: Access Command-Line Arguments Using foreach (C# Programming Guide)</span></span>
<span data-ttu-id="bb829-103">Dizi yineleme için başka bir yaklaşım kullanmaktır [foreach](../../../csharp/language-reference/keywords/foreach-in.md) Bu örnekte gösterildiği gibi deyimi.</span><span class="sxs-lookup"><span data-stu-id="bb829-103">Another approach to iterating over the array is to use the [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement as shown in this example.</span></span> <span data-ttu-id="bb829-104">`foreach` deyimi, <xref:System.Collections.IEnumerable> ara birimini uygulayan bir dizi, .NET Framework koleksiyon sınıfı veya herhangi bir sınıf ya da yapının yinelenmesi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bb829-104">The `foreach` statement can be used to iterate over an array, a .NET Framework collection class, or any class or struct that implements the <xref:System.Collections.IEnumerable> interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bb829-105">Bir uygulamayı Visual Studio'da çalıştırırken, komut satırı bağımsız değişkenleri belirtebilirsiniz [hata ayıklama sayfası, Proje Tasarımcısı](/visualstudio/ide/reference/debug-page-project-designer).</span><span class="sxs-lookup"><span data-stu-id="bb829-105">When running an application in Visual Studio, you can specify command-line arguments in the [Debug Page, Project Designer](/visualstudio/ide/reference/debug-page-project-designer).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb829-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="bb829-106">Example</span></span>  
 <span data-ttu-id="bb829-107">Bu örnekte, `foreach`kullanarak komut satırı değişkenlerinin nasıl yazdırılacağı gösterilir.</span><span class="sxs-lookup"><span data-stu-id="bb829-107">This example demonstrates how to print out the command line arguments using `foreach`.</span></span>  
  
 [!code-csharp[csProgGuideMain#10](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-access-command-line-arguments-using-foreach_1.cs)]  
  
 [!code-csharp[csProgGuideMain#11](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-access-command-line-arguments-using-foreach_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="bb829-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bb829-108">See Also</span></span>  
 <xref:System.Array>  
 <xref:System.Collections>  
 [<span data-ttu-id="bb829-109">Komut satırı csc.exe derleme</span><span class="sxs-lookup"><span data-stu-id="bb829-109">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
 [<span data-ttu-id="bb829-110">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="bb829-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="bb829-111">foreach,</span><span class="sxs-lookup"><span data-stu-id="bb829-111">foreach, in</span></span>](../../../csharp/language-reference/keywords/foreach-in.md)  
 [<span data-ttu-id="bb829-112">Ana() ve komut satırı bağımsız değişkenleri</span><span class="sxs-lookup"><span data-stu-id="bb829-112">Main() and Command-Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/index.md)  
 [<span data-ttu-id="bb829-113">Nasıl yapılır: komut satırı bağımsız değişkenlerini görüntüleme</span><span class="sxs-lookup"><span data-stu-id="bb829-113">How to: Display Command Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)  
 [<span data-ttu-id="bb829-114">Ana() dönüş değerleri</span><span class="sxs-lookup"><span data-stu-id="bb829-114">Main() Return Values</span></span>](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)

---
title: 'Nasıl Yapılır: Foreach kullanarak komut satırı bağımsız değişkenlerine erişim - C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#]
ms.assetid: 89c3e335-3f5b-4e24-8c5a-b8036561fe8a
ms.openlocfilehash: 79c798bb6ec16fc639d37defc40da5af770e5bba
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53242444"
---
# <a name="how-to-access-command-line-arguments-using-foreach-c-programming-guide"></a><span data-ttu-id="c56c2-102">Nasıl Yapılır: Erişim foreach kullanarak komut satırı bağımsız değişkenleri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="c56c2-102">How to: Access Command-Line Arguments Using foreach (C# Programming Guide)</span></span>
<span data-ttu-id="c56c2-103">Başka bir dizi yineleme yaklaşımı kullanmaktır [foreach](../../../csharp/language-reference/keywords/foreach-in.md) Bu örnekte gösterildiği gibi bir ifade.</span><span class="sxs-lookup"><span data-stu-id="c56c2-103">Another approach to iterating over the array is to use the [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement as shown in this example.</span></span> <span data-ttu-id="c56c2-104">`foreach` deyimi, <xref:System.Collections.IEnumerable> ara birimini uygulayan bir dizi, .NET Framework koleksiyon sınıfı veya herhangi bir sınıf ya da yapının yinelenmesi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c56c2-104">The `foreach` statement can be used to iterate over an array, a .NET Framework collection class, or any class or struct that implements the <xref:System.Collections.IEnumerable> interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c56c2-105">Visual Studio'da bir uygulama çalıştırırken, komut satırı bağımsız değişkenlerinde belirtebilirsiniz [hata ayıklama sayfası, Proje Tasarımcısı](/visualstudio/ide/reference/debug-page-project-designer).</span><span class="sxs-lookup"><span data-stu-id="c56c2-105">When running an application in Visual Studio, you can specify command-line arguments in the [Debug Page, Project Designer](/visualstudio/ide/reference/debug-page-project-designer).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c56c2-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="c56c2-106">Example</span></span>  
 <span data-ttu-id="c56c2-107">Bu örnekte, `foreach`kullanarak komut satırı değişkenlerinin nasıl yazdırılacağı gösterilir.</span><span class="sxs-lookup"><span data-stu-id="c56c2-107">This example demonstrates how to print out the command line arguments using `foreach`.</span></span>  
  
 [!code-csharp[csProgGuideMain#10](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-access-command-line-arguments-using-foreach_1.cs)]  
  
 [!code-csharp[csProgGuideMain#11](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-access-command-line-arguments-using-foreach_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="c56c2-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c56c2-108">See Also</span></span>

- <xref:System.Array>  
- <xref:System.Collections>  
- [<span data-ttu-id="c56c2-109">csc.exe Kullanarak Komut Satırı Derleme</span><span class="sxs-lookup"><span data-stu-id="c56c2-109">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
- [<span data-ttu-id="c56c2-110">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c56c2-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="c56c2-111">foreach, in</span><span class="sxs-lookup"><span data-stu-id="c56c2-111">foreach, in</span></span>](../../../csharp/language-reference/keywords/foreach-in.md)  
- [<span data-ttu-id="c56c2-112">Ana() ve Komut Satırı Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="c56c2-112">Main() and Command-Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/index.md)  
- [<span data-ttu-id="c56c2-113">Nasıl yapılır: Komut satırı bağımsız değişkenlerini görüntüleme</span><span class="sxs-lookup"><span data-stu-id="c56c2-113">How to: Display Command Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)  
- [<span data-ttu-id="c56c2-114">Ana() Dönüş Değerleri</span><span class="sxs-lookup"><span data-stu-id="c56c2-114">Main() Return Values</span></span>](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)

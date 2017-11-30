---
title: "Nasıl yapılır: Komut Satırı Bağımsız Değişkenlerini Görüntüleme (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f6ae495eef227c6e4d9fb9ca0d4d0c031163fd52
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a><span data-ttu-id="c3e4d-102">Nasıl yapılır: Komut Satırı Bağımsız Değişkenlerini Görüntüleme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="c3e4d-102">How to: Display Command Line Arguments (C# Programming Guide)</span></span>
<span data-ttu-id="c3e4d-103">Komut satırında bir yürütülebilir dosya için sağlanan bağımsız değişkenler isteğe bağlı bir parametre üzerinden erişilebilir `Main`.</span><span class="sxs-lookup"><span data-stu-id="c3e4d-103">Arguments provided to an executable on the command-line are accessible through an optional parameter to `Main`.</span></span> <span data-ttu-id="c3e4d-104">Bağımsız değişken bir dize dizisi biçiminde sağlanır.</span><span class="sxs-lookup"><span data-stu-id="c3e4d-104">The arguments are provided in the form of an array of strings.</span></span> <span data-ttu-id="c3e4d-105">Dizideki her öğe bir bağımsız değişken içeriyor.</span><span class="sxs-lookup"><span data-stu-id="c3e4d-105">Each element of the array contains one argument.</span></span> <span data-ttu-id="c3e4d-106">Boşluk bağımsız değişkenler arasındaki kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="c3e4d-106">White-space between arguments is removed.</span></span> <span data-ttu-id="c3e4d-107">Örneğin, bu komut satırı çağrılarını kurgusal bir yürütülebilir dosyanın göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="c3e4d-107">For example, consider these command-line invocations of a fictitious executable:</span></span>  
  
|<span data-ttu-id="c3e4d-108">Komut satırında giriş</span><span class="sxs-lookup"><span data-stu-id="c3e4d-108">Input on Command-line</span></span>|<span data-ttu-id="c3e4d-109">Ana geçirilen bir dize dizisi</span><span class="sxs-lookup"><span data-stu-id="c3e4d-109">Array of strings passed to Main</span></span>|  
|----------------------------|-------------------------------------|  
|<span data-ttu-id="c3e4d-110">**executable.exe b c**</span><span class="sxs-lookup"><span data-stu-id="c3e4d-110">**executable.exe a b c**</span></span>|<span data-ttu-id="c3e4d-111">"a"</span><span class="sxs-lookup"><span data-stu-id="c3e4d-111">"a"</span></span><br /><br /> <span data-ttu-id="c3e4d-112">"b"</span><span class="sxs-lookup"><span data-stu-id="c3e4d-112">"b"</span></span><br /><br /> <span data-ttu-id="c3e4d-113">"c"</span><span class="sxs-lookup"><span data-stu-id="c3e4d-113">"c"</span></span>|  
|<span data-ttu-id="c3e4d-114">**executable.exe bir iki**</span><span class="sxs-lookup"><span data-stu-id="c3e4d-114">**executable.exe one two**</span></span>|<span data-ttu-id="c3e4d-115">"tek"</span><span class="sxs-lookup"><span data-stu-id="c3e4d-115">"one"</span></span><br /><br /> <span data-ttu-id="c3e4d-116">"iki"</span><span class="sxs-lookup"><span data-stu-id="c3e4d-116">"two"</span></span>|  
|<span data-ttu-id="c3e4d-117">**executable.exe "bir iki" üç**</span><span class="sxs-lookup"><span data-stu-id="c3e4d-117">**executable.exe "one two" three**</span></span>|<span data-ttu-id="c3e4d-118">"one two"</span><span class="sxs-lookup"><span data-stu-id="c3e4d-118">"one two"</span></span><br /><br /> <span data-ttu-id="c3e4d-119">"üç"</span><span class="sxs-lookup"><span data-stu-id="c3e4d-119">"three"</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="c3e4d-120">Visual Studio'da Uygulama çalışırken, komut satırı bağımsız değişkenleri belirtebilirsiniz [hata ayıklama sayfası, Proje Tasarımcısı](/visualstudio/ide/reference/debug-page-project-designer).</span><span class="sxs-lookup"><span data-stu-id="c3e4d-120">When you are running an application in Visual Studio, you can specify command-line arguments in the [Debug Page, Project Designer](/visualstudio/ide/reference/debug-page-project-designer).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3e4d-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="c3e4d-121">Example</span></span>  
 <span data-ttu-id="c3e4d-122">Bu örnek, bir komut satırı uygulamaya geçirilen komut satırı bağımsız değişkenleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="c3e4d-122">This example displays the command line arguments passed to a command-line application.</span></span> <span data-ttu-id="c3e4d-123">İlk giriş yukarıdaki tabloda gösterilen çıkış içindir.</span><span class="sxs-lookup"><span data-stu-id="c3e4d-123">The output shown is for the first entry in the table above.</span></span>  
  
 [!code-csharp[csProgGuideMain#9](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-display-command-line-arguments_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="c3e4d-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c3e4d-124">See Also</span></span>  
 [<span data-ttu-id="c3e4d-125">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c3e4d-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c3e4d-126">Komut satırı csc.exe derleme</span><span class="sxs-lookup"><span data-stu-id="c3e4d-126">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
 [<span data-ttu-id="c3e4d-127">Ana() ve komut satırı bağımsız değişkenleri</span><span class="sxs-lookup"><span data-stu-id="c3e4d-127">Main() and Command-Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/index.md)  
 [<span data-ttu-id="c3e4d-128">Nasıl yapılır: foreach kullanarak komut satırı bağımsız değişkenlerine erişme</span><span class="sxs-lookup"><span data-stu-id="c3e4d-128">How to: Access Command-Line Arguments Using foreach</span></span>](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)  
 [<span data-ttu-id="c3e4d-129">Ana() dönüş değerleri</span><span class="sxs-lookup"><span data-stu-id="c3e4d-129">Main() Return Values</span></span>](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)

---
title: 'Nasıl yapılır: Komut satırı bağımsız değişkenlerini - görüntüleme C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
ms.openlocfilehash: 948ff6e752b3f5cce870b483340cbbf9f4e78b01
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54607721"
---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a><span data-ttu-id="e6c57-102">Nasıl yapılır: Komut satırı bağımsız değişkenlerini görüntüleme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="e6c57-102">How to: Display Command Line Arguments (C# Programming Guide)</span></span>
<span data-ttu-id="e6c57-103">Komut satırında yürütülebilir bir dosya için sağlanan bağımsız değişkenler için isteğe bağlı bir parametre üzerinden erişilebilir `Main`.</span><span class="sxs-lookup"><span data-stu-id="e6c57-103">Arguments provided to an executable on the command-line are accessible through an optional parameter to `Main`.</span></span> <span data-ttu-id="e6c57-104">Bağımsız değişken bir dize dizisi biçiminde sağlanır.</span><span class="sxs-lookup"><span data-stu-id="e6c57-104">The arguments are provided in the form of an array of strings.</span></span> <span data-ttu-id="e6c57-105">Dizinin her öğesinin tek bağımsız değişken içeriyor.</span><span class="sxs-lookup"><span data-stu-id="e6c57-105">Each element of the array contains one argument.</span></span> <span data-ttu-id="e6c57-106">Bağımsız değişkenler arasındaki boşluk kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="e6c57-106">White-space between arguments is removed.</span></span> <span data-ttu-id="e6c57-107">Örneğin, kurgusal bir yürütülebilir komut satırı bu çağrıları göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="e6c57-107">For example, consider these command-line invocations of a fictitious executable:</span></span>  
  
|<span data-ttu-id="e6c57-108">Komut satırında giriş</span><span class="sxs-lookup"><span data-stu-id="e6c57-108">Input on Command-line</span></span>|<span data-ttu-id="e6c57-109">Ana geçirilen bir dize dizisi</span><span class="sxs-lookup"><span data-stu-id="e6c57-109">Array of strings passed to Main</span></span>|  
|----------------------------|-------------------------------------|  
|<span data-ttu-id="e6c57-110">**executable.exe a b c.**</span><span class="sxs-lookup"><span data-stu-id="e6c57-110">**executable.exe a b c**</span></span>|<span data-ttu-id="e6c57-111">"a"</span><span class="sxs-lookup"><span data-stu-id="e6c57-111">"a"</span></span><br /><br /> <span data-ttu-id="e6c57-112">"b"</span><span class="sxs-lookup"><span data-stu-id="e6c57-112">"b"</span></span><br /><br /> <span data-ttu-id="e6c57-113">"c"</span><span class="sxs-lookup"><span data-stu-id="e6c57-113">"c"</span></span>|  
|<span data-ttu-id="e6c57-114">**bir executable.exe iki**</span><span class="sxs-lookup"><span data-stu-id="e6c57-114">**executable.exe one two**</span></span>|<span data-ttu-id="e6c57-115">"bir"</span><span class="sxs-lookup"><span data-stu-id="e6c57-115">"one"</span></span><br /><br /> <span data-ttu-id="e6c57-116">"iki"</span><span class="sxs-lookup"><span data-stu-id="e6c57-116">"two"</span></span>|  
|<span data-ttu-id="e6c57-117">**executable.exe "bir iki" üç**</span><span class="sxs-lookup"><span data-stu-id="e6c57-117">**executable.exe "one two" three**</span></span>|<span data-ttu-id="e6c57-118">"one two"</span><span class="sxs-lookup"><span data-stu-id="e6c57-118">"one two"</span></span><br /><br /> <span data-ttu-id="e6c57-119">"üç"</span><span class="sxs-lookup"><span data-stu-id="e6c57-119">"three"</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="e6c57-120">Visual Studio'da bir uygulamayı çalıştırırken, komut satırı bağımsız değişkenlerini belirtebilirsiniz [hata ayıklama sayfası, Proje Tasarımcısı](/visualstudio/ide/reference/debug-page-project-designer).</span><span class="sxs-lookup"><span data-stu-id="e6c57-120">When you are running an application in Visual Studio, you can specify command-line arguments in the [Debug Page, Project Designer](/visualstudio/ide/reference/debug-page-project-designer).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6c57-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="e6c57-121">Example</span></span>  
 <span data-ttu-id="e6c57-122">Bu örnek, bir komut satırı uygulamaya geçirilen komut satırı bağımsız değişkenlerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="e6c57-122">This example displays the command line arguments passed to a command-line application.</span></span> <span data-ttu-id="e6c57-123">İlk giriş yukarıdaki tabloda gösterilen çıktıya içindir.</span><span class="sxs-lookup"><span data-stu-id="e6c57-123">The output shown is for the first entry in the table above.</span></span>  
  
 [!code-csharp[csProgGuideMain#9](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-display-command-line-arguments_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="e6c57-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e6c57-124">See also</span></span>

- [<span data-ttu-id="e6c57-125">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e6c57-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="e6c57-126">csc.exe Kullanarak Komut Satırı Derleme</span><span class="sxs-lookup"><span data-stu-id="e6c57-126">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [<span data-ttu-id="e6c57-127">Ana() ve Komut Satırı Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="e6c57-127">Main() and Command-Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/index.md)
- [<span data-ttu-id="e6c57-128">Nasıl yapılır: Erişim foreach kullanarak komut satırı bağımsız değişkenleri</span><span class="sxs-lookup"><span data-stu-id="e6c57-128">How to: Access Command-Line Arguments Using foreach</span></span>](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)
- [<span data-ttu-id="e6c57-129">Ana() Dönüş Değerleri</span><span class="sxs-lookup"><span data-stu-id="e6c57-129">Main() Return Values</span></span>](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)

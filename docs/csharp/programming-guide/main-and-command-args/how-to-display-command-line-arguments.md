---
title: 'Nasıl yapılır: Komut Satırı Bağımsız Değişkenlerini Görüntüleme (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
ms.openlocfilehash: 7b9e488e84c78c8fdbf64431f42ea5797fdca916
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33334142"
---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a><span data-ttu-id="0fef8-102">Nasıl yapılır: Komut Satırı Bağımsız Değişkenlerini Görüntüleme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="0fef8-102">How to: Display Command Line Arguments (C# Programming Guide)</span></span>
<span data-ttu-id="0fef8-103">Komut satırında bir yürütülebilir dosya için sağlanan bağımsız değişkenler isteğe bağlı bir parametre üzerinden erişilebilir `Main`.</span><span class="sxs-lookup"><span data-stu-id="0fef8-103">Arguments provided to an executable on the command-line are accessible through an optional parameter to `Main`.</span></span> <span data-ttu-id="0fef8-104">Bağımsız değişken bir dize dizisi biçiminde sağlanır.</span><span class="sxs-lookup"><span data-stu-id="0fef8-104">The arguments are provided in the form of an array of strings.</span></span> <span data-ttu-id="0fef8-105">Dizideki her öğe bir bağımsız değişken içeriyor.</span><span class="sxs-lookup"><span data-stu-id="0fef8-105">Each element of the array contains one argument.</span></span> <span data-ttu-id="0fef8-106">Boşluk bağımsız değişkenler arasındaki kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="0fef8-106">White-space between arguments is removed.</span></span> <span data-ttu-id="0fef8-107">Örneğin, bu komut satırı çağrılarını kurgusal bir yürütülebilir dosyanın göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="0fef8-107">For example, consider these command-line invocations of a fictitious executable:</span></span>  
  
|<span data-ttu-id="0fef8-108">Komut satırında giriş</span><span class="sxs-lookup"><span data-stu-id="0fef8-108">Input on Command-line</span></span>|<span data-ttu-id="0fef8-109">Ana geçirilen bir dize dizisi</span><span class="sxs-lookup"><span data-stu-id="0fef8-109">Array of strings passed to Main</span></span>|  
|----------------------------|-------------------------------------|  
|<span data-ttu-id="0fef8-110">**executable.exe b c**</span><span class="sxs-lookup"><span data-stu-id="0fef8-110">**executable.exe a b c**</span></span>|<span data-ttu-id="0fef8-111">"a"</span><span class="sxs-lookup"><span data-stu-id="0fef8-111">"a"</span></span><br /><br /> <span data-ttu-id="0fef8-112">"b"</span><span class="sxs-lookup"><span data-stu-id="0fef8-112">"b"</span></span><br /><br /> <span data-ttu-id="0fef8-113">"c"</span><span class="sxs-lookup"><span data-stu-id="0fef8-113">"c"</span></span>|  
|<span data-ttu-id="0fef8-114">**executable.exe bir iki**</span><span class="sxs-lookup"><span data-stu-id="0fef8-114">**executable.exe one two**</span></span>|<span data-ttu-id="0fef8-115">"tek"</span><span class="sxs-lookup"><span data-stu-id="0fef8-115">"one"</span></span><br /><br /> <span data-ttu-id="0fef8-116">"iki"</span><span class="sxs-lookup"><span data-stu-id="0fef8-116">"two"</span></span>|  
|<span data-ttu-id="0fef8-117">**executable.exe "bir iki" üç**</span><span class="sxs-lookup"><span data-stu-id="0fef8-117">**executable.exe "one two" three**</span></span>|<span data-ttu-id="0fef8-118">"one two"</span><span class="sxs-lookup"><span data-stu-id="0fef8-118">"one two"</span></span><br /><br /> <span data-ttu-id="0fef8-119">"üç"</span><span class="sxs-lookup"><span data-stu-id="0fef8-119">"three"</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="0fef8-120">Visual Studio'da Uygulama çalışırken, komut satırı bağımsız değişkenleri belirtebilirsiniz [hata ayıklama sayfası, Proje Tasarımcısı](/visualstudio/ide/reference/debug-page-project-designer).</span><span class="sxs-lookup"><span data-stu-id="0fef8-120">When you are running an application in Visual Studio, you can specify command-line arguments in the [Debug Page, Project Designer](/visualstudio/ide/reference/debug-page-project-designer).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0fef8-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="0fef8-121">Example</span></span>  
 <span data-ttu-id="0fef8-122">Bu örnek, bir komut satırı uygulamaya geçirilen komut satırı bağımsız değişkenleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="0fef8-122">This example displays the command line arguments passed to a command-line application.</span></span> <span data-ttu-id="0fef8-123">İlk giriş yukarıdaki tabloda gösterilen çıkış içindir.</span><span class="sxs-lookup"><span data-stu-id="0fef8-123">The output shown is for the first entry in the table above.</span></span>  
  
 [!code-csharp[csProgGuideMain#9](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-display-command-line-arguments_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="0fef8-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0fef8-124">See Also</span></span>  
 [<span data-ttu-id="0fef8-125">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0fef8-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="0fef8-126">csc.exe Kullanarak Komut Satırı Derleme</span><span class="sxs-lookup"><span data-stu-id="0fef8-126">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
 [<span data-ttu-id="0fef8-127">Ana() ve Komut Satırı Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="0fef8-127">Main() and Command-Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/index.md)  
 [<span data-ttu-id="0fef8-128">Nasıl yapılır: foreach Kullanarak Komut Satırı Bağımsız Değişkenlerine Erişme</span><span class="sxs-lookup"><span data-stu-id="0fef8-128">How to: Access Command-Line Arguments Using foreach</span></span>](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)  
 [<span data-ttu-id="0fef8-129">Ana() Dönüş Değerleri</span><span class="sxs-lookup"><span data-stu-id="0fef8-129">Main() Return Values</span></span>](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)

---
title: 'Nasıl Yapılır: Komut satırı bağımsız değişkenlerini - görüntüleme C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
ms.openlocfilehash: 9b09f5a1991ab5545ab31b1879f30c383a0e9a9f
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53236537"
---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a><span data-ttu-id="ee86a-102">Nasıl Yapılır: Komut satırı bağımsız değişkenlerini görüntüleme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="ee86a-102">How to: Display Command Line Arguments (C# Programming Guide)</span></span>
<span data-ttu-id="ee86a-103">Komut satırında yürütülebilir bir dosya için sağlanan bağımsız değişkenler için isteğe bağlı bir parametre üzerinden erişilebilir `Main`.</span><span class="sxs-lookup"><span data-stu-id="ee86a-103">Arguments provided to an executable on the command-line are accessible through an optional parameter to `Main`.</span></span> <span data-ttu-id="ee86a-104">Bağımsız değişken bir dize dizisi biçiminde sağlanır.</span><span class="sxs-lookup"><span data-stu-id="ee86a-104">The arguments are provided in the form of an array of strings.</span></span> <span data-ttu-id="ee86a-105">Dizinin her öğesinin tek bağımsız değişken içeriyor.</span><span class="sxs-lookup"><span data-stu-id="ee86a-105">Each element of the array contains one argument.</span></span> <span data-ttu-id="ee86a-106">Bağımsız değişkenler arasındaki boşluk kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="ee86a-106">White-space between arguments is removed.</span></span> <span data-ttu-id="ee86a-107">Örneğin, kurgusal bir yürütülebilir komut satırı bu çağrıları göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="ee86a-107">For example, consider these command-line invocations of a fictitious executable:</span></span>  
  
|<span data-ttu-id="ee86a-108">Komut satırında giriş</span><span class="sxs-lookup"><span data-stu-id="ee86a-108">Input on Command-line</span></span>|<span data-ttu-id="ee86a-109">Ana geçirilen bir dize dizisi</span><span class="sxs-lookup"><span data-stu-id="ee86a-109">Array of strings passed to Main</span></span>|  
|----------------------------|-------------------------------------|  
|<span data-ttu-id="ee86a-110">**executable.exe a b c.**</span><span class="sxs-lookup"><span data-stu-id="ee86a-110">**executable.exe a b c**</span></span>|<span data-ttu-id="ee86a-111">"a"</span><span class="sxs-lookup"><span data-stu-id="ee86a-111">"a"</span></span><br /><br /> <span data-ttu-id="ee86a-112">"b"</span><span class="sxs-lookup"><span data-stu-id="ee86a-112">"b"</span></span><br /><br /> <span data-ttu-id="ee86a-113">"c"</span><span class="sxs-lookup"><span data-stu-id="ee86a-113">"c"</span></span>|  
|<span data-ttu-id="ee86a-114">**bir executable.exe iki**</span><span class="sxs-lookup"><span data-stu-id="ee86a-114">**executable.exe one two**</span></span>|<span data-ttu-id="ee86a-115">"bir"</span><span class="sxs-lookup"><span data-stu-id="ee86a-115">"one"</span></span><br /><br /> <span data-ttu-id="ee86a-116">"iki"</span><span class="sxs-lookup"><span data-stu-id="ee86a-116">"two"</span></span>|  
|<span data-ttu-id="ee86a-117">**executable.exe "bir iki" üç**</span><span class="sxs-lookup"><span data-stu-id="ee86a-117">**executable.exe "one two" three**</span></span>|<span data-ttu-id="ee86a-118">"one two"</span><span class="sxs-lookup"><span data-stu-id="ee86a-118">"one two"</span></span><br /><br /> <span data-ttu-id="ee86a-119">"üç"</span><span class="sxs-lookup"><span data-stu-id="ee86a-119">"three"</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="ee86a-120">Visual Studio'da bir uygulamayı çalıştırırken, komut satırı bağımsız değişkenlerini belirtebilirsiniz [hata ayıklama sayfası, Proje Tasarımcısı](/visualstudio/ide/reference/debug-page-project-designer).</span><span class="sxs-lookup"><span data-stu-id="ee86a-120">When you are running an application in Visual Studio, you can specify command-line arguments in the [Debug Page, Project Designer](/visualstudio/ide/reference/debug-page-project-designer).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee86a-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="ee86a-121">Example</span></span>  
 <span data-ttu-id="ee86a-122">Bu örnek, bir komut satırı uygulamaya geçirilen komut satırı bağımsız değişkenlerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="ee86a-122">This example displays the command line arguments passed to a command-line application.</span></span> <span data-ttu-id="ee86a-123">İlk giriş yukarıdaki tabloda gösterilen çıktıya içindir.</span><span class="sxs-lookup"><span data-stu-id="ee86a-123">The output shown is for the first entry in the table above.</span></span>  
  
 [!code-csharp[csProgGuideMain#9](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-display-command-line-arguments_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="ee86a-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ee86a-124">See Also</span></span>

- [<span data-ttu-id="ee86a-125">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ee86a-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="ee86a-126">csc.exe Kullanarak Komut Satırı Derleme</span><span class="sxs-lookup"><span data-stu-id="ee86a-126">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
- [<span data-ttu-id="ee86a-127">Ana() ve Komut Satırı Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="ee86a-127">Main() and Command-Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/index.md)  
- [<span data-ttu-id="ee86a-128">Nasıl yapılır: Erişim foreach kullanarak komut satırı bağımsız değişkenleri</span><span class="sxs-lookup"><span data-stu-id="ee86a-128">How to: Access Command-Line Arguments Using foreach</span></span>](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)  
- [<span data-ttu-id="ee86a-129">Ana() Dönüş Değerleri</span><span class="sxs-lookup"><span data-stu-id="ee86a-129">Main() Return Values</span></span>](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)

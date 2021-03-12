---
title: Komut satırı bağımsız değişkenlerini görüntüleme-C# Programlama Kılavuzu
description: Komut satırı bağımsız değişkenlerini görüntülemeyi öğrenin. Bir kod örneğine bakın ve kullanılabilir ek kaynakları görüntüleyin.
ms.date: 03/08/2021
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
ms.openlocfilehash: 38122f55e9886c677f6f7189ea6fe45c13c8c13b
ms.sourcegitcommit: e3cf8227573e13b8e1f4e3dc007404881cdafe47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/11/2021
ms.locfileid: "103190261"
---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a><span data-ttu-id="bb0a5-104">Komut satırı bağımsız değişkenlerini görüntüleme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="bb0a5-104">How to display command-line arguments (C# Programming Guide)</span></span>

<span data-ttu-id="bb0a5-105">Komut satırındaki bir yürütülebilir dosyaya belirtilen bağımsız değişkenler, [en üst düzey deyimlerde](top-level-statements.md) veya için isteğe bağlı bir parametre aracılığıyla erişilebilir `Main` .</span><span class="sxs-lookup"><span data-stu-id="bb0a5-105">Arguments provided to an executable on the command line are accessible in [top-level statements](top-level-statements.md) or through an optional parameter to `Main`.</span></span> <span data-ttu-id="bb0a5-106">Bağımsız değişkenler, dizeler dizisi biçiminde sağlanır.</span><span class="sxs-lookup"><span data-stu-id="bb0a5-106">The arguments are provided in the form of an array of strings.</span></span> <span data-ttu-id="bb0a5-107">Dizinin her öğesi bir bağımsız değişken içerir.</span><span class="sxs-lookup"><span data-stu-id="bb0a5-107">Each element of the array contains one argument.</span></span> <span data-ttu-id="bb0a5-108">Bağımsız değişkenler arasındaki beyaz boşluk kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="bb0a5-108">White-space between arguments is removed.</span></span> <span data-ttu-id="bb0a5-109">Örneğin, kurgusal bir yürütülebilirin şu komut satırı çağırmaları göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="bb0a5-109">For example, consider these command-line invocations of a fictitious executable:</span></span>  
  
|<span data-ttu-id="bb0a5-110">Komut satırında giriş</span><span class="sxs-lookup"><span data-stu-id="bb0a5-110">Input on command line</span></span>|<span data-ttu-id="bb0a5-111">Main 'e geçirilen dizelerin dizisi</span><span class="sxs-lookup"><span data-stu-id="bb0a5-111">Array of strings passed to Main</span></span>|  
|----------------------------|-------------------------------------|  
|<span data-ttu-id="bb0a5-112">**B cexecutable.exe**</span><span class="sxs-lookup"><span data-stu-id="bb0a5-112">**executable.exe a b c**</span></span>|<span data-ttu-id="bb0a5-113">a</span><span class="sxs-lookup"><span data-stu-id="bb0a5-113">"a"</span></span><br /><br /> <span data-ttu-id="bb0a5-114">kenarı</span><span class="sxs-lookup"><span data-stu-id="bb0a5-114">"b"</span></span><br /><br /> <span data-ttu-id="bb0a5-115">,</span><span class="sxs-lookup"><span data-stu-id="bb0a5-115">"c"</span></span>|  
|<span data-ttu-id="bb0a5-116">**executable.exe 1 2**</span><span class="sxs-lookup"><span data-stu-id="bb0a5-116">**executable.exe one two**</span></span>|<span data-ttu-id="bb0a5-117">biriyle</span><span class="sxs-lookup"><span data-stu-id="bb0a5-117">"one"</span></span><br /><br /> <span data-ttu-id="bb0a5-118">ikiye</span><span class="sxs-lookup"><span data-stu-id="bb0a5-118">"two"</span></span>|  
|<span data-ttu-id="bb0a5-119">**executable.exe "1 2" üç**</span><span class="sxs-lookup"><span data-stu-id="bb0a5-119">**executable.exe "one two" three**</span></span>|<span data-ttu-id="bb0a5-120">"one two"</span><span class="sxs-lookup"><span data-stu-id="bb0a5-120">"one two"</span></span><br /><br /> <span data-ttu-id="bb0a5-121">ünden</span><span class="sxs-lookup"><span data-stu-id="bb0a5-121">"three"</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="bb0a5-122">Visual Studio 'da bir uygulama çalıştırırken, [hata ayıklama sayfasında, proje Tasarımcısı](/visualstudio/ide/reference/debug-page-project-designer)' nda komut satırı bağımsız değişkenlerini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bb0a5-122">When you are running an application in Visual Studio, you can specify command-line arguments in the [Debug Page, Project Designer](/visualstudio/ide/reference/debug-page-project-designer).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb0a5-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="bb0a5-123">Example</span></span>  

 <span data-ttu-id="bb0a5-124">Bu örnek, komut satırı uygulamasına geçirilen komut satırı bağımsız değişkenlerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="bb0a5-124">This example displays the command-line arguments passed to a command-line application.</span></span> <span data-ttu-id="bb0a5-125">Gösterilen çıktı, yukarıdaki tablodaki ilk giriş içindir.</span><span class="sxs-lookup"><span data-stu-id="bb0a5-125">The output shown is for the first entry in the table above.</span></span>  
  
 [!code-csharp[csProgGuideMain#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#9)]  
  
## <a name="see-also"></a><span data-ttu-id="bb0a5-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bb0a5-126">See also</span></span>

- [<span data-ttu-id="bb0a5-127">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="bb0a5-127">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="bb0a5-128">csc.exe Kullanarak Komut Satırı Derleme</span><span class="sxs-lookup"><span data-stu-id="bb0a5-128">Command-line Building With csc.exe</span></span>](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [<span data-ttu-id="bb0a5-129">Main () ve Command-Line bağımsız değişkenleri</span><span class="sxs-lookup"><span data-stu-id="bb0a5-129">Main() and Command-Line Arguments</span></span>](./index.md)
- [<span data-ttu-id="bb0a5-130">Ana() Dönüş Değerleri</span><span class="sxs-lookup"><span data-stu-id="bb0a5-130">Main() Return Values</span></span>](./main-return-values.md)

---
title: Komut satırı bağımsız değişkenlerini görüntüleme-C# Programlama Kılavuzu
description: Komut satırı bağımsız değişkenlerini görüntülemeyi öğrenin. Bir kod örneğine bakın ve kullanılabilir ek kaynakları görüntüleyin.
ms.date: 03/08/2021
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
ms.openlocfilehash: 7c3e8d7f6ad2a599308057e996808509e70b7508
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2021
ms.locfileid: "103480266"
---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a><span data-ttu-id="81c4b-104">Komut satırı bağımsız değişkenlerini görüntüleme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="81c4b-104">How to display command-line arguments (C# Programming Guide)</span></span>

<span data-ttu-id="81c4b-105">Komut satırındaki bir yürütülebilir dosyaya belirtilen bağımsız değişkenler, [en üst düzey deyimlerde](top-level-statements.md) veya için isteğe bağlı bir parametre aracılığıyla erişilebilir `Main` .</span><span class="sxs-lookup"><span data-stu-id="81c4b-105">Arguments provided to an executable on the command line are accessible in [top-level statements](top-level-statements.md) or through an optional parameter to `Main`.</span></span> <span data-ttu-id="81c4b-106">Bağımsız değişkenler, dizeler dizisi biçiminde sağlanır.</span><span class="sxs-lookup"><span data-stu-id="81c4b-106">The arguments are provided in the form of an array of strings.</span></span> <span data-ttu-id="81c4b-107">Dizinin her öğesi bir bağımsız değişken içerir.</span><span class="sxs-lookup"><span data-stu-id="81c4b-107">Each element of the array contains one argument.</span></span> <span data-ttu-id="81c4b-108">Bağımsız değişkenler arasındaki beyaz boşluk kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="81c4b-108">White-space between arguments is removed.</span></span> <span data-ttu-id="81c4b-109">Örneğin, kurgusal bir yürütülebilirin şu komut satırı çağırmaları göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="81c4b-109">For example, consider these command-line invocations of a fictitious executable:</span></span>  
  
|<span data-ttu-id="81c4b-110">Komut satırında giriş</span><span class="sxs-lookup"><span data-stu-id="81c4b-110">Input on command line</span></span>|<span data-ttu-id="81c4b-111">Main 'e geçirilen dizelerin dizisi</span><span class="sxs-lookup"><span data-stu-id="81c4b-111">Array of strings passed to Main</span></span>|  
|----------------------------|-------------------------------------|  
|<span data-ttu-id="81c4b-112">**B cexecutable.exe**</span><span class="sxs-lookup"><span data-stu-id="81c4b-112">**executable.exe a b c**</span></span>|<span data-ttu-id="81c4b-113">a</span><span class="sxs-lookup"><span data-stu-id="81c4b-113">"a"</span></span><br /><br /> <span data-ttu-id="81c4b-114">kenarı</span><span class="sxs-lookup"><span data-stu-id="81c4b-114">"b"</span></span><br /><br /> <span data-ttu-id="81c4b-115">,</span><span class="sxs-lookup"><span data-stu-id="81c4b-115">"c"</span></span>|  
|<span data-ttu-id="81c4b-116">**executable.exe 1 2**</span><span class="sxs-lookup"><span data-stu-id="81c4b-116">**executable.exe one two**</span></span>|<span data-ttu-id="81c4b-117">biriyle</span><span class="sxs-lookup"><span data-stu-id="81c4b-117">"one"</span></span><br /><br /> <span data-ttu-id="81c4b-118">ikiye</span><span class="sxs-lookup"><span data-stu-id="81c4b-118">"two"</span></span>|  
|<span data-ttu-id="81c4b-119">**executable.exe "1 2" üç**</span><span class="sxs-lookup"><span data-stu-id="81c4b-119">**executable.exe "one two" three**</span></span>|<span data-ttu-id="81c4b-120">"one two"</span><span class="sxs-lookup"><span data-stu-id="81c4b-120">"one two"</span></span><br /><br /> <span data-ttu-id="81c4b-121">ünden</span><span class="sxs-lookup"><span data-stu-id="81c4b-121">"three"</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="81c4b-122">Visual Studio 'da bir uygulama çalıştırırken, [hata ayıklama sayfasında, proje Tasarımcısı](/visualstudio/ide/reference/debug-page-project-designer)' nda komut satırı bağımsız değişkenlerini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="81c4b-122">When you are running an application in Visual Studio, you can specify command-line arguments in the [Debug Page, Project Designer](/visualstudio/ide/reference/debug-page-project-designer).</span></span>  
  
## <a name="example"></a><span data-ttu-id="81c4b-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="81c4b-123">Example</span></span>  

 <span data-ttu-id="81c4b-124">Bu örnek, komut satırı uygulamasına geçirilen komut satırı bağımsız değişkenlerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="81c4b-124">This example displays the command-line arguments passed to a command-line application.</span></span> <span data-ttu-id="81c4b-125">Gösterilen çıktı, yukarıdaki tablodaki ilk giriş içindir.</span><span class="sxs-lookup"><span data-stu-id="81c4b-125">The output shown is for the first entry in the table above.</span></span>  
  
 [!code-csharp[csProgGuideMain#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#9)]  
  
## <a name="see-also"></a><span data-ttu-id="81c4b-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="81c4b-126">See also</span></span>

- [<span data-ttu-id="81c4b-127">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="81c4b-127">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="81c4b-128">Main () ve Command-Line bağımsız değişkenleri</span><span class="sxs-lookup"><span data-stu-id="81c4b-128">Main() and Command-Line Arguments</span></span>](./index.md)
- [<span data-ttu-id="81c4b-129">Ana() Dönüş Değerleri</span><span class="sxs-lookup"><span data-stu-id="81c4b-129">Main() Return Values</span></span>](./main-return-values.md)

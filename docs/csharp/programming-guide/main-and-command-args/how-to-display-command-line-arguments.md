---
title: Komut satırı bağımsız değişkenlerini görüntüleme- C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
ms.openlocfilehash: 210dad71220572535a0325fac925b0453b0d4e03
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712032"
---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a><span data-ttu-id="e943f-102">Komut satırı bağımsız değişkenlerini görüntüleme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="e943f-102">How to display command line arguments (C# Programming Guide)</span></span>
<span data-ttu-id="e943f-103">Komut satırındaki bir yürütülebilir dosyaya sunulan bağımsız değişkenlere `Main`için isteğe bağlı bir parametre üzerinden erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="e943f-103">Arguments provided to an executable on the command-line are accessible through an optional parameter to `Main`.</span></span> <span data-ttu-id="e943f-104">Bağımsız değişkenler, dizeler dizisi biçiminde sağlanır.</span><span class="sxs-lookup"><span data-stu-id="e943f-104">The arguments are provided in the form of an array of strings.</span></span> <span data-ttu-id="e943f-105">Dizinin her öğesi bir bağımsız değişken içerir.</span><span class="sxs-lookup"><span data-stu-id="e943f-105">Each element of the array contains one argument.</span></span> <span data-ttu-id="e943f-106">Bağımsız değişkenler arasındaki beyaz boşluk kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="e943f-106">White-space between arguments is removed.</span></span> <span data-ttu-id="e943f-107">Örneğin, kurgusal bir yürütülebilirin şu komut satırı çağırmaları göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="e943f-107">For example, consider these command-line invocations of a fictitious executable:</span></span>  
  
|<span data-ttu-id="e943f-108">Komut satırında giriş</span><span class="sxs-lookup"><span data-stu-id="e943f-108">Input on Command-line</span></span>|<span data-ttu-id="e943f-109">Main 'e geçirilen dizelerin dizisi</span><span class="sxs-lookup"><span data-stu-id="e943f-109">Array of strings passed to Main</span></span>|  
|----------------------------|-------------------------------------|  
|<span data-ttu-id="e943f-110">**çalıştırılabilir. exe a b c**</span><span class="sxs-lookup"><span data-stu-id="e943f-110">**executable.exe a b c**</span></span>|<span data-ttu-id="e943f-111">a</span><span class="sxs-lookup"><span data-stu-id="e943f-111">"a"</span></span><br /><br /> <span data-ttu-id="e943f-112">kenarı</span><span class="sxs-lookup"><span data-stu-id="e943f-112">"b"</span></span><br /><br /> <span data-ttu-id="e943f-113">,</span><span class="sxs-lookup"><span data-stu-id="e943f-113">"c"</span></span>|  
|<span data-ttu-id="e943f-114">**yürütülebilir. exe 1 2**</span><span class="sxs-lookup"><span data-stu-id="e943f-114">**executable.exe one two**</span></span>|<span data-ttu-id="e943f-115">biriyle</span><span class="sxs-lookup"><span data-stu-id="e943f-115">"one"</span></span><br /><br /> <span data-ttu-id="e943f-116">ikiye</span><span class="sxs-lookup"><span data-stu-id="e943f-116">"two"</span></span>|  
|<span data-ttu-id="e943f-117">**yürütülebilir. exe "1 2" üç**</span><span class="sxs-lookup"><span data-stu-id="e943f-117">**executable.exe "one two" three**</span></span>|<span data-ttu-id="e943f-118">"one two"</span><span class="sxs-lookup"><span data-stu-id="e943f-118">"one two"</span></span><br /><br /> <span data-ttu-id="e943f-119">ünden</span><span class="sxs-lookup"><span data-stu-id="e943f-119">"three"</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="e943f-120">Visual Studio 'da bir uygulama çalıştırırken, [hata ayıklama sayfasında, proje Tasarımcısı](/visualstudio/ide/reference/debug-page-project-designer)' nda komut satırı bağımsız değişkenlerini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e943f-120">When you are running an application in Visual Studio, you can specify command-line arguments in the [Debug Page, Project Designer](/visualstudio/ide/reference/debug-page-project-designer).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e943f-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="e943f-121">Example</span></span>  
 <span data-ttu-id="e943f-122">Bu örnek, komut satırı uygulamasına geçirilen komut satırı bağımsız değişkenlerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="e943f-122">This example displays the command line arguments passed to a command-line application.</span></span> <span data-ttu-id="e943f-123">Gösterilen çıktı, yukarıdaki tablodaki ilk giriş içindir.</span><span class="sxs-lookup"><span data-stu-id="e943f-123">The output shown is for the first entry in the table above.</span></span>  
  
 [!code-csharp[csProgGuideMain#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#9)]  
  
## <a name="see-also"></a><span data-ttu-id="e943f-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e943f-124">See also</span></span>

- [<span data-ttu-id="e943f-125">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e943f-125">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e943f-126">csc.exe Kullanarak Komut Satırı Derleme</span><span class="sxs-lookup"><span data-stu-id="e943f-126">Command-line Building With csc.exe</span></span>](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [<span data-ttu-id="e943f-127">Ana() ve Komut Satırı Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="e943f-127">Main() and Command-Line Arguments</span></span>](./index.md)
- [<span data-ttu-id="e943f-128">Ana() Dönüş Değerleri</span><span class="sxs-lookup"><span data-stu-id="e943f-128">Main() Return Values</span></span>](./main-return-values.md)

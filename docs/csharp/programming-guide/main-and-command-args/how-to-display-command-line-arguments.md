---
title: 'Nasıl yapılır: Komut satırı bağımsız değişkenlerini görüntüle C# -Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
ms.openlocfilehash: 030fd2bd3286bd4f25513e26b3de9e87eaee9029
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588890"
---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a><span data-ttu-id="be05c-102">Nasıl yapılır: Komut satırı bağımsız değişkenlerini görüntüleC# (Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="be05c-102">How to: Display Command Line Arguments (C# Programming Guide)</span></span>
<span data-ttu-id="be05c-103">Komut satırındaki bir çalıştırılabilir dosyaya girilen bağımsız değişkenlere, için `Main`isteğe bağlı bir parametre üzerinden erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="be05c-103">Arguments provided to an executable on the command-line are accessible through an optional parameter to `Main`.</span></span> <span data-ttu-id="be05c-104">Bağımsız değişkenler, dizeler dizisi biçiminde sağlanır.</span><span class="sxs-lookup"><span data-stu-id="be05c-104">The arguments are provided in the form of an array of strings.</span></span> <span data-ttu-id="be05c-105">Dizinin her öğesi bir bağımsız değişken içerir.</span><span class="sxs-lookup"><span data-stu-id="be05c-105">Each element of the array contains one argument.</span></span> <span data-ttu-id="be05c-106">Bağımsız değişkenler arasındaki beyaz boşluk kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="be05c-106">White-space between arguments is removed.</span></span> <span data-ttu-id="be05c-107">Örneğin, kurgusal bir yürütülebilirin şu komut satırı çağırmaları göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="be05c-107">For example, consider these command-line invocations of a fictitious executable:</span></span>  
  
|<span data-ttu-id="be05c-108">Komut satırında giriş</span><span class="sxs-lookup"><span data-stu-id="be05c-108">Input on Command-line</span></span>|<span data-ttu-id="be05c-109">Main 'e geçirilen dizelerin dizisi</span><span class="sxs-lookup"><span data-stu-id="be05c-109">Array of strings passed to Main</span></span>|  
|----------------------------|-------------------------------------|  
|<span data-ttu-id="be05c-110">**çalıştırılabilir. exe a b c**</span><span class="sxs-lookup"><span data-stu-id="be05c-110">**executable.exe a b c**</span></span>|<span data-ttu-id="be05c-111">a</span><span class="sxs-lookup"><span data-stu-id="be05c-111">"a"</span></span><br /><br /> <span data-ttu-id="be05c-112">kenarı</span><span class="sxs-lookup"><span data-stu-id="be05c-112">"b"</span></span><br /><br /> <span data-ttu-id="be05c-113">,</span><span class="sxs-lookup"><span data-stu-id="be05c-113">"c"</span></span>|  
|<span data-ttu-id="be05c-114">**yürütülebilir. exe 1 2**</span><span class="sxs-lookup"><span data-stu-id="be05c-114">**executable.exe one two**</span></span>|<span data-ttu-id="be05c-115">biriyle</span><span class="sxs-lookup"><span data-stu-id="be05c-115">"one"</span></span><br /><br /> <span data-ttu-id="be05c-116">ikiye</span><span class="sxs-lookup"><span data-stu-id="be05c-116">"two"</span></span>|  
|<span data-ttu-id="be05c-117">**yürütülebilir. exe "1 2" üç**</span><span class="sxs-lookup"><span data-stu-id="be05c-117">**executable.exe "one two" three**</span></span>|<span data-ttu-id="be05c-118">"one two"</span><span class="sxs-lookup"><span data-stu-id="be05c-118">"one two"</span></span><br /><br /> <span data-ttu-id="be05c-119">ünden</span><span class="sxs-lookup"><span data-stu-id="be05c-119">"three"</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="be05c-120">Visual Studio 'da bir uygulama çalıştırırken, [hata ayıklama sayfasında, proje Tasarımcısı](/visualstudio/ide/reference/debug-page-project-designer)' nda komut satırı bağımsız değişkenlerini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="be05c-120">When you are running an application in Visual Studio, you can specify command-line arguments in the [Debug Page, Project Designer](/visualstudio/ide/reference/debug-page-project-designer).</span></span>  
  
## <a name="example"></a><span data-ttu-id="be05c-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="be05c-121">Example</span></span>  
 <span data-ttu-id="be05c-122">Bu örnek, komut satırı uygulamasına geçirilen komut satırı bağımsız değişkenlerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="be05c-122">This example displays the command line arguments passed to a command-line application.</span></span> <span data-ttu-id="be05c-123">Gösterilen çıktı, yukarıdaki tablodaki ilk giriş içindir.</span><span class="sxs-lookup"><span data-stu-id="be05c-123">The output shown is for the first entry in the table above.</span></span>  
  
 [!code-csharp[csProgGuideMain#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#9)]  
  
## <a name="see-also"></a><span data-ttu-id="be05c-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="be05c-124">See also</span></span>

- [<span data-ttu-id="be05c-125">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="be05c-125">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="be05c-126">csc.exe Kullanarak Komut Satırı Derleme</span><span class="sxs-lookup"><span data-stu-id="be05c-126">Command-line Building With csc.exe</span></span>](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [<span data-ttu-id="be05c-127">Ana() ve Komut Satırı Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="be05c-127">Main() and Command-Line Arguments</span></span>](./index.md)
- [<span data-ttu-id="be05c-128">Ana() Dönüş Değerleri</span><span class="sxs-lookup"><span data-stu-id="be05c-128">Main() Return Values</span></span>](./main-return-values.md)

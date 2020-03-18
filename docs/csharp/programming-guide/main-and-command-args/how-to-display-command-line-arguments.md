---
title: Komut satırı bağımsız değişkenleri nasıl görüntülenir - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
ms.openlocfilehash: 210dad71220572535a0325fac925b0453b0d4e03
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712032"
---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a><span data-ttu-id="a539f-102">Komut satırı bağımsız değişkenleri nasıl görüntülenir (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="a539f-102">How to display command line arguments (C# Programming Guide)</span></span>
<span data-ttu-id="a539f-103">Komut satırında yürütülebilir bir bağımsız değişkene `Main`isteğe bağlı bir parametre ile erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="a539f-103">Arguments provided to an executable on the command-line are accessible through an optional parameter to `Main`.</span></span> <span data-ttu-id="a539f-104">Bağımsız değişkenler bir dizi dize biçiminde sağlanır.</span><span class="sxs-lookup"><span data-stu-id="a539f-104">The arguments are provided in the form of an array of strings.</span></span> <span data-ttu-id="a539f-105">Dizinin her öğesi bir bağımsız değişken içerir.</span><span class="sxs-lookup"><span data-stu-id="a539f-105">Each element of the array contains one argument.</span></span> <span data-ttu-id="a539f-106">Bağımsız değişkenler arasındaki beyaz boşluk kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="a539f-106">White-space between arguments is removed.</span></span> <span data-ttu-id="a539f-107">Örneğin, hayali bir yürütülebilir bu komut satırı çağrıları düşünün:</span><span class="sxs-lookup"><span data-stu-id="a539f-107">For example, consider these command-line invocations of a fictitious executable:</span></span>  
  
|<span data-ttu-id="a539f-108">Komut satırına Giriş</span><span class="sxs-lookup"><span data-stu-id="a539f-108">Input on Command-line</span></span>|<span data-ttu-id="a539f-109">Main'e geçirilen dizeleri dizisi</span><span class="sxs-lookup"><span data-stu-id="a539f-109">Array of strings passed to Main</span></span>|  
|----------------------------|-------------------------------------|  
|<span data-ttu-id="a539f-110">**icra edilebilir.exe a b c**</span><span class="sxs-lookup"><span data-stu-id="a539f-110">**executable.exe a b c**</span></span>|<span data-ttu-id="a539f-111">"a"</span><span class="sxs-lookup"><span data-stu-id="a539f-111">"a"</span></span><br /><br /> <span data-ttu-id="a539f-112">"b"</span><span class="sxs-lookup"><span data-stu-id="a539f-112">"b"</span></span><br /><br /> <span data-ttu-id="a539f-113">"c"</span><span class="sxs-lookup"><span data-stu-id="a539f-113">"c"</span></span>|  
|<span data-ttu-id="a539f-114">**executable.exe bir iki**</span><span class="sxs-lookup"><span data-stu-id="a539f-114">**executable.exe one two**</span></span>|<span data-ttu-id="a539f-115">"bir"</span><span class="sxs-lookup"><span data-stu-id="a539f-115">"one"</span></span><br /><br /> <span data-ttu-id="a539f-116">"iki"</span><span class="sxs-lookup"><span data-stu-id="a539f-116">"two"</span></span>|  
|<span data-ttu-id="a539f-117">**executable.exe "bir iki" üç**</span><span class="sxs-lookup"><span data-stu-id="a539f-117">**executable.exe "one two" three**</span></span>|<span data-ttu-id="a539f-118">"one two"</span><span class="sxs-lookup"><span data-stu-id="a539f-118">"one two"</span></span><br /><br /> <span data-ttu-id="a539f-119">"üç"</span><span class="sxs-lookup"><span data-stu-id="a539f-119">"three"</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="a539f-120">Visual Studio'da bir uygulama çalıştırırken Hata [Ayıklama Sayfasında, Proje Tasarımcısı'nda](/visualstudio/ide/reference/debug-page-project-designer)komut satırı bağımsız değişkenlerini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a539f-120">When you are running an application in Visual Studio, you can specify command-line arguments in the [Debug Page, Project Designer](/visualstudio/ide/reference/debug-page-project-designer).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a539f-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="a539f-121">Example</span></span>  
 <span data-ttu-id="a539f-122">Bu örnek, komut satırı uygulamasına geçirilen komut satırı bağımsız değişkenlerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="a539f-122">This example displays the command line arguments passed to a command-line application.</span></span> <span data-ttu-id="a539f-123">Gösterilen çıktı yukarıdaki tablodaki ilk giriş içindir.</span><span class="sxs-lookup"><span data-stu-id="a539f-123">The output shown is for the first entry in the table above.</span></span>  
  
 [!code-csharp[csProgGuideMain#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#9)]  
  
## <a name="see-also"></a><span data-ttu-id="a539f-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a539f-124">See also</span></span>

- [<span data-ttu-id="a539f-125">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a539f-125">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="a539f-126">csc.exe Kullanarak Komut Satırı Derleme</span><span class="sxs-lookup"><span data-stu-id="a539f-126">Command-line Building With csc.exe</span></span>](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [<span data-ttu-id="a539f-127">Ana() ve Komut Satırı Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="a539f-127">Main() and Command-Line Arguments</span></span>](./index.md)
- [<span data-ttu-id="a539f-128">Ana() Dönüş Değerleri</span><span class="sxs-lookup"><span data-stu-id="a539f-128">Main() Return Values</span></span>](./main-return-values.md)

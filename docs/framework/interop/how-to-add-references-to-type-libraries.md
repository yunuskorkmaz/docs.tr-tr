---
title: 'Nasıl yapılır: Tür Kitaplıklarına Başvurular Ekleme'
description: Visual Studio 'da veya komut satırı derlemesinde tür kitaplıklarına nasıl başvurular ekleneceğini anlayın.
ms.date: 03/30/2017
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- type libraries
- COM interop, importing type library
ms.assetid: f5cfa6ba-cc25-4017-82cd-ba7391859113
ms.openlocfilehash: a3c24385c9cc7debe95aa10369b050897415bc46
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617437"
---
# <a name="how-to-add-references-to-type-libraries"></a><span data-ttu-id="bf029-103">Nasıl yapılır: Tür Kitaplıklarına Başvurular Ekleme</span><span class="sxs-lookup"><span data-stu-id="bf029-103">How to: Add References to Type Libraries</span></span>
<span data-ttu-id="bf029-104">Visual Studio, bir tür kitaplığına bir başvuru eklediğinizde meta verileri içeren bir birlikte çalışma derlemesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bf029-104">Visual Studio generates an interop assembly containing metadata when you add a reference to a type library.</span></span> <span data-ttu-id="bf029-105">Birincil birlikte çalışma derlemesi varsa, Visual Studio yeni bir birlikte çalışma derlemesi oluşturmadan önce mevcut derlemeyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="bf029-105">If a primary interop assembly is available, Visual Studio uses the existing assembly before generating a new interop assembly.</span></span>  
  
### <a name="to-add-a-reference-to-a-type-library-in-visual-studio"></a><span data-ttu-id="bf029-106">Visual Studio 'da bir tür kitaplığına başvuru eklemek için</span><span class="sxs-lookup"><span data-stu-id="bf029-106">To add a reference to a type library in Visual Studio</span></span>  
  
1. <span data-ttu-id="bf029-107">Bir Windows Setup.exe dosyası yüklemeyi sizin için gerçekleştirmediği takdirde, COM DLL veya EXE dosyasını bilgisayarınıza yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bf029-107">Install the COM DLL or EXE file on your computer, unless a Windows Setup.exe file performs the installation for you.</span></span>  
  
2. <span data-ttu-id="bf029-108">**Proje**, **Başvuru Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="bf029-108">Choose **Project**, **Add Reference**.</span></span>  
  
3. <span data-ttu-id="bf029-109">Başvuru Yöneticisi 'nde **com**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="bf029-109">In the Reference Manager, choose **COM**.</span></span>  
  
4. <span data-ttu-id="bf029-110">Listeden tür kitaplığını seçin veya. tlb dosyasına gözatamazsınız.</span><span class="sxs-lookup"><span data-stu-id="bf029-110">Select the type library from the list, or browse for the .tlb file.</span></span>  
  
5. <span data-ttu-id="bf029-111">**Tamam ' ı**seçin.</span><span class="sxs-lookup"><span data-stu-id="bf029-111">Choose **OK**.</span></span>  
  
6. <span data-ttu-id="bf029-112">Çözüm Gezgini ' de, yeni eklediğiniz başvurunun kısayol menüsünü açın ve ardından **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="bf029-112">In Solution Explorer, open the shortcut menu for the reference you just added, and then choose **Properties**.</span></span>  
  
7. <span data-ttu-id="bf029-113">**Özellikler** penceresinde, **birlikte çalışma türlerini katıştır** özelliğinin **true**olarak ayarlandığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="bf029-113">In the **Properties** window, make sure that the **Embed Interop Types** property is set to **True**.</span></span> <span data-ttu-id="bf029-114">Bu, Visual Studio 'Nun çalıştırılabilirlerinizdeki COM türlerine ait tür bilgilerini katıştırmasına ve birincil birlikte çalışma derlemelerini uygulamanızla birlikte dağıtma gereksinimini ortadan kaldırmaya neden olur.</span><span class="sxs-lookup"><span data-stu-id="bf029-114">This causes Visual Studio to embed type information for COM types in your executables, eliminating the need to deploy primary interop assemblies with your app.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bf029-115">Menü ve iletişim kutusu seçenekleri, kullanmakta olduğunuz Visual Studio sürümüne bağlı olarak farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="bf029-115">The menu and dialog box options may vary depending on the version of Visual Studio you're using.</span></span>  
  
### <a name="to-add-a-reference-to-a-type-library-for-command-line-compilation"></a><span data-ttu-id="bf029-116">Komut satırı derlemesi için bir tür kitaplığına başvuru eklemek için</span><span class="sxs-lookup"><span data-stu-id="bf029-116">To add a reference to a type library for command-line compilation</span></span>  
  
1. <span data-ttu-id="bf029-117">[Nasıl yapılır: tür kitaplıklarından birlikte çalışma derlemeleri oluşturma](how-to-generate-interop-assemblies-from-type-libraries.md)bölümünde açıklandığı gibi bir birlikte çalışma derlemesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="bf029-117">Generate an interop assembly as described in [How to: Generate Interop Assemblies from Type Libraries](how-to-generate-interop-assemblies-from-type-libraries.md).</span></span>  
  
2. <span data-ttu-id="bf029-118">Çalıştırılabilirlerinizde COM türlerine ilişkin tür bilgilerini eklemek için [-Link (C# derleyici seçenekleri)](../../csharp/language-reference/compiler-options/link-compiler-option.md) veya [-Link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) derleyici seçeneğini birlikte çalışma derleme adıyla birlikte kullanın.</span><span class="sxs-lookup"><span data-stu-id="bf029-118">Use the [-link (C# Compiler Options)](../../csharp/language-reference/compiler-options/link-compiler-option.md) or [-link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) compiler option with the interop assembly name to embed type information for COM types in your executables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf029-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bf029-119">See also</span></span>

- [<span data-ttu-id="bf029-120">Tür Kitaplığını Derleme Olarak İçeri Aktarma</span><span class="sxs-lookup"><span data-stu-id="bf029-120">Importing a Type Library as an Assembly</span></span>](importing-a-type-library-as-an-assembly.md)
- [<span data-ttu-id="bf029-121">COM Bileşenlerini .NET Framework'te Gösterme</span><span class="sxs-lookup"><span data-stu-id="bf029-121">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)
- [<span data-ttu-id="bf029-122">İzlenecek yol: Visual Studio’da Yönetilen Bütünleştirilmiş Kodlardan Türleri Katıştırma</span><span class="sxs-lookup"><span data-stu-id="bf029-122">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio</span></span>](../../standard/assembly/embed-types-visual-studio.md)
- [<span data-ttu-id="bf029-123">-Link (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="bf029-123">-link (C# Compiler Options)</span></span>](../../csharp/language-reference/compiler-options/link-compiler-option.md)
- [<span data-ttu-id="bf029-124">-bağlantı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bf029-124">-link (Visual Basic)</span></span>](../../visual-basic/reference/command-line-compiler/link.md)

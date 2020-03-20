---
title: 'Nasıl yapılır: Tür Kitaplıklarına Başvurular Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- type libraries
- COM interop, importing type library
ms.assetid: f5cfa6ba-cc25-4017-82cd-ba7391859113
ms.openlocfilehash: 1e82a499b77cc6d1d49eaf13e243201bbdc4c5fe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181440"
---
# <a name="how-to-add-references-to-type-libraries"></a><span data-ttu-id="2509a-102">Nasıl yapılır: Tür Kitaplıklarına Başvurular Ekleme</span><span class="sxs-lookup"><span data-stu-id="2509a-102">How to: Add References to Type Libraries</span></span>
<span data-ttu-id="2509a-103">Visual Studio, tür kitaplığına bir başvuru eklediğinizde meta verileri içeren bir interop derlemesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2509a-103">Visual Studio generates an interop assembly containing metadata when you add a reference to a type library.</span></span> <span data-ttu-id="2509a-104">Birincil interop derlemesi varsa, Visual Studio yeni bir interop derlemesi oluşturmadan önce varolan derlemeyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="2509a-104">If a primary interop assembly is available, Visual Studio uses the existing assembly before generating a new interop assembly.</span></span>  
  
### <a name="to-add-a-reference-to-a-type-library-in-visual-studio"></a><span data-ttu-id="2509a-105">Visual Studio'daki tür kitaplığına başvuru eklemek için</span><span class="sxs-lookup"><span data-stu-id="2509a-105">To add a reference to a type library in Visual Studio</span></span>  
  
1. <span data-ttu-id="2509a-106">Bir Windows Setup.exe dosyası yüklemeyi sizin için gerçekleştirmedikçe, COM DLL veya EXE dosyasını bilgisayarınıza yükleyin.</span><span class="sxs-lookup"><span data-stu-id="2509a-106">Install the COM DLL or EXE file on your computer, unless a Windows Setup.exe file performs the installation for you.</span></span>  
  
2. <span data-ttu-id="2509a-107">**Proje**seçin , **Referans Ekle**.</span><span class="sxs-lookup"><span data-stu-id="2509a-107">Choose **Project**, **Add Reference**.</span></span>  
  
3. <span data-ttu-id="2509a-108">Başvuru Yöneticisi'nde **COM'u**seçin.</span><span class="sxs-lookup"><span data-stu-id="2509a-108">In the Reference Manager, choose **COM**.</span></span>  
  
4. <span data-ttu-id="2509a-109">Listeden tür kitaplığını seçin veya .tlb dosyasına göz atın.</span><span class="sxs-lookup"><span data-stu-id="2509a-109">Select the type library from the list, or browse for the .tlb file.</span></span>  
  
5. <span data-ttu-id="2509a-110">**Tamam'ı**seçin.</span><span class="sxs-lookup"><span data-stu-id="2509a-110">Choose **OK**.</span></span>  
  
6. <span data-ttu-id="2509a-111">Çözüm Gezgini'nde, az önce eklediğiniz başvuru için kısayol menüsünü açın ve ardından **Özellikler'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="2509a-111">In Solution Explorer, open the shortcut menu for the reference you just added, and then choose **Properties**.</span></span>  
  
7. <span data-ttu-id="2509a-112">**Özellikler** penceresinde, **Embed Interop Türleri** özelliğinin **True**olarak ayarlandıkından emin olun.</span><span class="sxs-lookup"><span data-stu-id="2509a-112">In the **Properties** window, make sure that the **Embed Interop Types** property is set to **True**.</span></span> <span data-ttu-id="2509a-113">Bu, Visual Studio'nun çalıştırılabilir lerinize COM türleri için tür bilgilerini gömmesine neden olarak uygulamanızla birincil interop derlemeleri dağıtma gereksinimini ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="2509a-113">This causes Visual Studio to embed type information for COM types in your executables, eliminating the need to deploy primary interop assemblies with your app.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2509a-114">Menü ve iletişim kutusu seçenekleri, kullandığınız Visual Studio sürümüne bağlı olarak değişebilir.</span><span class="sxs-lookup"><span data-stu-id="2509a-114">The menu and dialog box options may vary depending on the version of Visual Studio you're using.</span></span>  
  
### <a name="to-add-a-reference-to-a-type-library-for-command-line-compilation"></a><span data-ttu-id="2509a-115">Komut satırı derlemesi için tür kitaplığına başvuru eklemek için</span><span class="sxs-lookup"><span data-stu-id="2509a-115">To add a reference to a type library for command-line compilation</span></span>  
  
1. <span data-ttu-id="2509a-116">Nasıl açıklandığı gibi bir interop derlemesi [oluşturun: Tür Kitaplıklarından Interop Derlemeleri Oluşturun.](how-to-generate-interop-assemblies-from-type-libraries.md)</span><span class="sxs-lookup"><span data-stu-id="2509a-116">Generate an interop assembly as described in [How to: Generate Interop Assemblies from Type Libraries](how-to-generate-interop-assemblies-from-type-libraries.md).</span></span>  
  
2. <span data-ttu-id="2509a-117">Yürütülebilirlerinize COM türleri için tür bilgilerini gömmek için interop montaj adı ile [-link (C# Derleyici Seçenekleri)](../../csharp/language-reference/compiler-options/link-compiler-option.md) veya [-link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) derleyicisi seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="2509a-117">Use the [-link (C# Compiler Options)](../../csharp/language-reference/compiler-options/link-compiler-option.md) or [-link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) compiler option with the interop assembly name to embed type information for COM types in your executables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2509a-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2509a-118">See also</span></span>

- [<span data-ttu-id="2509a-119">Tür Kitaplığını Derleme Olarak İçeri Aktarma</span><span class="sxs-lookup"><span data-stu-id="2509a-119">Importing a Type Library as an Assembly</span></span>](importing-a-type-library-as-an-assembly.md)
- [<span data-ttu-id="2509a-120">COM Bileşenlerini .NET Framework'te Gösterme</span><span class="sxs-lookup"><span data-stu-id="2509a-120">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)
- [<span data-ttu-id="2509a-121">İzlenecek yol: Visual Studio’da Yönetilen Bütünleştirilmiş Kodlardan Türleri Katıştırma</span><span class="sxs-lookup"><span data-stu-id="2509a-121">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio</span></span>](../../standard/assembly/embed-types-visual-studio.md)
- [<span data-ttu-id="2509a-122">-link (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="2509a-122">-link (C# Compiler Options)</span></span>](../../csharp/language-reference/compiler-options/link-compiler-option.md)
- [<span data-ttu-id="2509a-123">-bağlantı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2509a-123">-link (Visual Basic)</span></span>](../../visual-basic/reference/command-line-compiler/link.md)

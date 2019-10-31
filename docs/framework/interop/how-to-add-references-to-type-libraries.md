---
title: 'Nasıl yapılır: Tür Kitaplıklarına Başvurular Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- type libraries
- COM interop, importing type library
ms.assetid: f5cfa6ba-cc25-4017-82cd-ba7391859113
ms.openlocfilehash: b4b78d377cf3ff2b43f7776567583c71c479054c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123950"
---
# <a name="how-to-add-references-to-type-libraries"></a><span data-ttu-id="2c335-102">Nasıl yapılır: Tür Kitaplıklarına Başvurular Ekleme</span><span class="sxs-lookup"><span data-stu-id="2c335-102">How to: Add References to Type Libraries</span></span>
<span data-ttu-id="2c335-103">Visual Studio, bir tür kitaplığına bir başvuru eklediğinizde meta verileri içeren bir birlikte çalışma derlemesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2c335-103">Visual Studio generates an interop assembly containing metadata when you add a reference to a type library.</span></span> <span data-ttu-id="2c335-104">Birincil birlikte çalışma derlemesi varsa, Visual Studio yeni bir birlikte çalışma derlemesi oluşturmadan önce mevcut derlemeyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="2c335-104">If a primary interop assembly is available, Visual Studio uses the existing assembly before generating a new interop assembly.</span></span>  
  
### <a name="to-add-a-reference-to-a-type-library-in-visual-studio"></a><span data-ttu-id="2c335-105">Visual Studio 'da bir tür kitaplığına başvuru eklemek için</span><span class="sxs-lookup"><span data-stu-id="2c335-105">To add a reference to a type library in Visual Studio</span></span>  
  
1. <span data-ttu-id="2c335-106">Bir Windows Kurulumu. exe dosyası yüklemeyi sizin için gerçekleştirmediği müddetçe COM DLL veya EXE dosyasını bilgisayarınıza yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2c335-106">Install the COM DLL or EXE file on your computer, unless a Windows Setup.exe file performs the installation for you.</span></span>  
  
2. <span data-ttu-id="2c335-107">**Proje**, **Başvuru Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="2c335-107">Choose **Project**, **Add Reference**.</span></span>  
  
3. <span data-ttu-id="2c335-108">Başvuru Yöneticisi 'nde **com**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="2c335-108">In the Reference Manager, choose **COM**.</span></span>  
  
4. <span data-ttu-id="2c335-109">Listeden tür kitaplığını seçin veya. tlb dosyasına gözatamazsınız.</span><span class="sxs-lookup"><span data-stu-id="2c335-109">Select the type library from the list, or browse for the .tlb file.</span></span>  
  
5. <span data-ttu-id="2c335-110">**Tamam ' ı**seçin.</span><span class="sxs-lookup"><span data-stu-id="2c335-110">Choose **OK**.</span></span>  
  
6. <span data-ttu-id="2c335-111">Çözüm Gezgini ' de, yeni eklediğiniz başvurunun kısayol menüsünü açın ve ardından **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="2c335-111">In Solution Explorer, open the shortcut menu for the reference you just added, and then choose **Properties**.</span></span>  
  
7. <span data-ttu-id="2c335-112">**Özellikler** penceresinde, **birlikte çalışma türlerini katıştır** özelliğinin **true**olarak ayarlandığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="2c335-112">In the **Properties** window, make sure that the **Embed Interop Types** property is set to **True**.</span></span> <span data-ttu-id="2c335-113">Bu, Visual Studio 'Nun çalıştırılabilirlerinizdeki COM türlerine ait tür bilgilerini katıştırmasına ve birincil birlikte çalışma derlemelerini uygulamanızla birlikte dağıtma gereksinimini ortadan kaldırmaya neden olur.</span><span class="sxs-lookup"><span data-stu-id="2c335-113">This causes Visual Studio to embed type information for COM types in your executables, eliminating the need to deploy primary interop assemblies with your app.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2c335-114">Menü ve iletişim kutusu seçenekleri, kullanmakta olduğunuz Visual Studio sürümüne bağlı olarak farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="2c335-114">The menu and dialog box options may vary depending on the version of Visual Studio you're using.</span></span>  
  
### <a name="to-add-a-reference-to-a-type-library-for-command-line-compilation"></a><span data-ttu-id="2c335-115">Komut satırı derlemesi için bir tür kitaplığına başvuru eklemek için</span><span class="sxs-lookup"><span data-stu-id="2c335-115">To add a reference to a type library for command-line compilation</span></span>  
  
1. <span data-ttu-id="2c335-116">[Nasıl yapılır: tür kitaplıklarından birlikte çalışma derlemeleri oluşturma](how-to-generate-interop-assemblies-from-type-libraries.md)bölümünde açıklandığı gibi bir birlikte çalışma derlemesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2c335-116">Generate an interop assembly as described in [How to: Generate Interop Assemblies from Type Libraries](how-to-generate-interop-assemblies-from-type-libraries.md).</span></span>  
  
2. <span data-ttu-id="2c335-117">Çalıştırılabilirlerinizde COM türlerine ilişkin tür bilgilerini eklemek için, birlikte çalışma derlemesi adı ile [-Link (C# derleyici seçenekleri)](../../csharp/language-reference/compiler-options/link-compiler-option.md) veya [-Link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) derleyici seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="2c335-117">Use the [-link (C# Compiler Options)](../../csharp/language-reference/compiler-options/link-compiler-option.md) or [-link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) compiler option with the interop assembly name to embed type information for COM types in your executables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c335-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2c335-118">See also</span></span>

- [<span data-ttu-id="2c335-119">Tür Kitaplığını Bütünleştirilmiş Kod Olarak İçeri Aktarma</span><span class="sxs-lookup"><span data-stu-id="2c335-119">Importing a Type Library as an Assembly</span></span>](importing-a-type-library-as-an-assembly.md)
- [<span data-ttu-id="2c335-120">COM Bileşenlerini .NET Framework'te Gösterme</span><span class="sxs-lookup"><span data-stu-id="2c335-120">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)
- [<span data-ttu-id="2c335-121">İzlenecek yol: Visual Studio’da Yönetilen Bütünleştirilmiş Kodlardan Türleri Katıştırma</span><span class="sxs-lookup"><span data-stu-id="2c335-121">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio</span></span>](../../standard/assembly/embed-types-visual-studio.md) 
- [<span data-ttu-id="2c335-122">-Link (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="2c335-122">-link (C# Compiler Options)</span></span>](../../csharp/language-reference/compiler-options/link-compiler-option.md)
- [<span data-ttu-id="2c335-123">-bağlantı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2c335-123">-link (Visual Basic)</span></span>](../../visual-basic/reference/command-line-compiler/link.md)

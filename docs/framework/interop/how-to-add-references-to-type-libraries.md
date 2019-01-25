---
title: 'Nasıl yapılır: Tür kitaplıklarına başvurular ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- type libraries
- COM interop, importing type library
ms.assetid: f5cfa6ba-cc25-4017-82cd-ba7391859113
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ebd7599205206e026c7de7b4e7bc2e5352771bd5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54522225"
---
# <a name="how-to-add-references-to-type-libraries"></a><span data-ttu-id="2d2a1-102">Nasıl yapılır: Tür kitaplıklarına başvurular ekleme</span><span class="sxs-lookup"><span data-stu-id="2d2a1-102">How to: Add References to Type Libraries</span></span>
<span data-ttu-id="2d2a1-103">Visual Studio, bir tür kitaplığına bir başvuru eklediğinizde, meta verileri içeren bir birlikte çalışma derlemesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2d2a1-103">Visual Studio generates an interop assembly containing metadata when you add a reference to a type library.</span></span> <span data-ttu-id="2d2a1-104">Visual Studio, bir birincil birlikte çalışma derlemesi varsa, yeni bir birlikte çalışma bütünleştirilmiş kodu oluşturuluyor önce mevcut bütünleştirilmiş kodu kullanır.</span><span class="sxs-lookup"><span data-stu-id="2d2a1-104">If a primary interop assembly is available, Visual Studio uses the existing assembly before generating a new interop assembly.</span></span>  
  
### <a name="to-add-a-reference-to-a-type-library-in-visual-studio"></a><span data-ttu-id="2d2a1-105">Visual Studio'da bir tür kitaplığına bir başvuru eklemek için</span><span class="sxs-lookup"><span data-stu-id="2d2a1-105">To add a reference to a type library in Visual Studio</span></span>  
  
1.  <span data-ttu-id="2d2a1-106">Bir Windows Setup.exe dosyasını yükleme sizin için gerçekleştirir, bilgisayarınızda COM DLL veya EXE dosyasının yükleyin.</span><span class="sxs-lookup"><span data-stu-id="2d2a1-106">Install the COM DLL or EXE file on your computer, unless a Windows Setup.exe file performs the installation for you.</span></span>  
  
2.  <span data-ttu-id="2d2a1-107">Seçin **proje**, **Başvurusu Ekle**.</span><span class="sxs-lookup"><span data-stu-id="2d2a1-107">Choose **Project**, **Add Reference**.</span></span>  
  
3.  <span data-ttu-id="2d2a1-108">Başvuru Yöneticisi'nde seçin **COM**.</span><span class="sxs-lookup"><span data-stu-id="2d2a1-108">In the Reference Manager, choose **COM**.</span></span>  
  
4.  <span data-ttu-id="2d2a1-109">Tür kitaplığını listeden seçin veya .tlb dosyasına göz at.</span><span class="sxs-lookup"><span data-stu-id="2d2a1-109">Select the type library from the list, or browse for the .tlb file.</span></span>  
  
5.  <span data-ttu-id="2d2a1-110">**Tamam**’ı seçin.</span><span class="sxs-lookup"><span data-stu-id="2d2a1-110">Choose **OK**.</span></span>  
  
6.  <span data-ttu-id="2d2a1-111">Çözüm Gezgini içinde eklenen yeni başvuru için kısayol menüsünü açın ve ardından **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="2d2a1-111">In Solution Explorer, open the shortcut menu for the reference you just added, and then choose **Properties**.</span></span>  
  
7.  <span data-ttu-id="2d2a1-112">İçinde **özellikleri** penceresinde emin **birlikte çalışma türlerini katıştır** özelliği **True**.</span><span class="sxs-lookup"><span data-stu-id="2d2a1-112">In the **Properties** window, make sure that the **Embed Interop Types** property is set to **True**.</span></span> <span data-ttu-id="2d2a1-113">Bu, uygulamanız ile birincil birlikte çalışma derlemelerini dağıtma gereksinimini ortadan kaldıran, yürütülebilir dosyaları, COM türleri için tür bilgisi katıştırma Visual Studio neden olur.</span><span class="sxs-lookup"><span data-stu-id="2d2a1-113">This causes Visual Studio to embed type information for COM types in your executables, eliminating the need to deploy primary interop assemblies with your app.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2d2a1-114">Menü ve iletişim kutusu seçenekleri, kullanmakta olduğunuz Visual Studio sürümüne bağlı olarak değişiklik gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="2d2a1-114">The menu and dialog box options may vary depending on the version of Visual Studio you're using.</span></span>  
  
### <a name="to-add-a-reference-to-a-type-library-for-command-line-compilation"></a><span data-ttu-id="2d2a1-115">Komut satırı derlemesi için bir tür kitaplığına bir başvuru eklemek için</span><span class="sxs-lookup"><span data-stu-id="2d2a1-115">To add a reference to a type library for command-line compilation</span></span>  
  
1.  <span data-ttu-id="2d2a1-116">Birlikte çalışma derlemesi açıklandığı gibi oluşturmak [nasıl yapılır: Tür kitaplıklarından birlikte çalışma derlemeleri oluşturma](how-to-generate-interop-assemblies-from-type-libraries.md).</span><span class="sxs-lookup"><span data-stu-id="2d2a1-116">Generate an interop assembly as described in [How to: Generate Interop Assemblies from Type Libraries](how-to-generate-interop-assemblies-from-type-libraries.md).</span></span>  
  
2.  <span data-ttu-id="2d2a1-117">Kullanım [/link (C# derleyici seçenekleri)](../../csharp/language-reference/compiler-options/link-compiler-option.md) veya [/Link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) COM için tür bilgilerini katıştırma derleyici seçeneğiyle birlikte çalışma bütünleştirilmiş kod adı, yürütülebilir dosyaların türleri.</span><span class="sxs-lookup"><span data-stu-id="2d2a1-117">Use the [/link (C# Compiler Options)](../../csharp/language-reference/compiler-options/link-compiler-option.md) or [/link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) compiler option with the interop assembly name to embed type information for COM types in your executables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d2a1-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2d2a1-118">See also</span></span>
- [<span data-ttu-id="2d2a1-119">Tür Kitaplığını Bütünleştirilmiş Kod Olarak İçeri Aktarma</span><span class="sxs-lookup"><span data-stu-id="2d2a1-119">Importing a Type Library as an Assembly</span></span>](importing-a-type-library-as-an-assembly.md)
- [<span data-ttu-id="2d2a1-120">COM Bileşenlerini .NET Framework'te Gösterme</span><span class="sxs-lookup"><span data-stu-id="2d2a1-120">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)
- <span data-ttu-id="2d2a1-121">[İzlenecek yol: Microsoft Office derlemelerinden tür bilgilerini katıştırma](https://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2d2a1-121">[Walkthrough: Embedding Type Information from Microsoft Office Assemblies](https://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3(v=vs.100))</span></span>
- [<span data-ttu-id="2d2a1-122">İzlenecek yol: Yönetilen derlemelerden türler katıştırma</span><span class="sxs-lookup"><span data-stu-id="2d2a1-122">Walkthrough: Embedding Types from Managed Assemblies</span></span>](https://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21)
- [<span data-ttu-id="2d2a1-123">/ Link (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="2d2a1-123">/link (C# Compiler Options)</span></span>](../../csharp/language-reference/compiler-options/link-compiler-option.md)
- [<span data-ttu-id="2d2a1-124">/ Link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2d2a1-124">/link (Visual Basic)</span></span>](../../visual-basic/reference/command-line-compiler/link.md)

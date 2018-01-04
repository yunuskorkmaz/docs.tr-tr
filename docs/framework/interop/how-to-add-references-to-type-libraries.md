---
title: "Nasıl yapılır: Tür Kitaplıklarına Başvurular Ekleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- type libraries
- COM interop, importing type library
ms.assetid: f5cfa6ba-cc25-4017-82cd-ba7391859113
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4e80c4bf5142a9bbbd2b7f75d67553db73f0ff22
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-references-to-type-libraries"></a><span data-ttu-id="524a4-102">Nasıl yapılır: Tür Kitaplıklarına Başvurular Ekleme</span><span class="sxs-lookup"><span data-stu-id="524a4-102">How to: Add References to Type Libraries</span></span>
<span data-ttu-id="524a4-103">Visual Studio bir tür kitaplığı başvuru eklediğinizde, meta verileri içeren bir birlikte çalışma derleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="524a4-103">Visual Studio generates an interop assembly containing metadata when you add a reference to a type library.</span></span> <span data-ttu-id="524a4-104">Birincil birlikte çalışma derlemesi varsa, Visual Studio yeni bir birlikte çalışma derleme oluşturmadan önce varolan derleme kullanır.</span><span class="sxs-lookup"><span data-stu-id="524a4-104">If a primary interop assembly is available, Visual Studio uses the existing assembly before generating a new interop assembly.</span></span>  
  
### <a name="to-add-a-reference-to-a-type-library-in-visual-studio"></a><span data-ttu-id="524a4-105">Visual Studio'da bir tür kitaplığı için bir başvuru eklemek için</span><span class="sxs-lookup"><span data-stu-id="524a4-105">To add a reference to a type library in Visual Studio</span></span>  
  
1.  <span data-ttu-id="524a4-106">Bir Windows Setup.exe dosyasını yükleme sizin için gerçekleştirir sürece, bilgisayarınızdaki COM DLL veya EXE dosyasını yükleyin.</span><span class="sxs-lookup"><span data-stu-id="524a4-106">Install the COM DLL or EXE file on your computer, unless a Windows Setup.exe file performs the installation for you.</span></span>  
  
2.  <span data-ttu-id="524a4-107">Seçin **proje**, **başvuru ekleme**.</span><span class="sxs-lookup"><span data-stu-id="524a4-107">Choose **Project**, **Add Reference**.</span></span>  
  
3.  <span data-ttu-id="524a4-108">Başvuru Yöneticisi'nde seçin **COM**.</span><span class="sxs-lookup"><span data-stu-id="524a4-108">In the Reference Manager, choose **COM**.</span></span>  
  
4.  <span data-ttu-id="524a4-109">Tür kitaplığını listeden seçin veya .tlb dosyasına göz atın.</span><span class="sxs-lookup"><span data-stu-id="524a4-109">Select the type library from the list, or browse for the .tlb file.</span></span>  
  
5.  <span data-ttu-id="524a4-110">Seçin **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="524a4-110">Choose **OK**.</span></span>  
  
6.  <span data-ttu-id="524a4-111">Çözüm Gezgini'nde eklenen yeni başvuru için kısayol menüsünü açın ve ardından **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="524a4-111">In Solution Explorer, open the shortcut menu for the reference you just added, and then choose **Properties**.</span></span>  
  
7.  <span data-ttu-id="524a4-112">İçinde **özellikleri** penceresinde olduğundan emin olun **birlikte çalışma türlerini katıştır** özelliği ayarlanmış **doğru**.</span><span class="sxs-lookup"><span data-stu-id="524a4-112">In the **Properties** window, make sure that the **Embed Interop Types** property is set to **True**.</span></span> <span data-ttu-id="524a4-113">Bu, uygulamanız ile birincil birlikte çalışma derlemeleri dağıtma gereğini ortadan kaldırır, yürütülebilir dosyalarında COM türleri için tür bilgisi katıştırmak Visual Studio neden olur.</span><span class="sxs-lookup"><span data-stu-id="524a4-113">This causes Visual Studio to embed type information for COM types in your executables, eliminating the need to deploy primary interop assemblies with your app.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="524a4-114">Menü ve iletişim kutusu seçenekleri kullanmakta olduğunuz Visual Studio sürümüne bağlı olarak değişebilir.</span><span class="sxs-lookup"><span data-stu-id="524a4-114">The menu and dialog box options may vary depending on the version of Visual Studio you're using.</span></span>  
  
### <a name="to-add-a-reference-to-a-type-library-for-command-line-compilation"></a><span data-ttu-id="524a4-115">Komut satırı derleme için bir tür kitaplığı için bir başvuru eklemek için</span><span class="sxs-lookup"><span data-stu-id="524a4-115">To add a reference to a type library for command-line compilation</span></span>  
  
1.  <span data-ttu-id="524a4-116">Birlikte çalışma bütünleştirilmiş açıklandığı gibi oluşturmak [nasıl yapılır: tür kitaplıklarından birlikte çalışma derlemeleri oluşturmak](../../../docs/framework/interop/how-to-generate-interop-assemblies-from-type-libraries.md).</span><span class="sxs-lookup"><span data-stu-id="524a4-116">Generate an interop assembly as described in [How to: Generate Interop Assemblies from Type Libraries](../../../docs/framework/interop/how-to-generate-interop-assemblies-from-type-libraries.md).</span></span>  
  
2.  <span data-ttu-id="524a4-117">Kullanım [/Link (C# Derleyici Seçenekleri)](~/docs/csharp/language-reference/compiler-options/link-compiler-option.md) veya [/Link (Visual Basic)](~/docs/visual-basic/reference/command-line-compiler/link.md) COM tür bilgileri katıştırmak için derleyici seçeneği ile birlikte çalışma derleme adı türleri, yürütülebilir.</span><span class="sxs-lookup"><span data-stu-id="524a4-117">Use the [/link (C# Compiler Options)](~/docs/csharp/language-reference/compiler-options/link-compiler-option.md) or [/link (Visual Basic)](~/docs/visual-basic/reference/command-line-compiler/link.md) compiler option with the interop assembly name to embed type information for COM types in your executables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="524a4-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="524a4-118">See Also</span></span>  
 [<span data-ttu-id="524a4-119">Tür Kitaplığını Bütünleştirilmiş Kod Olarak İçeri Aktarma</span><span class="sxs-lookup"><span data-stu-id="524a4-119">Importing a Type Library as an Assembly</span></span>](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)  
 [<span data-ttu-id="524a4-120">COM Bileşenlerini .NET Framework'te Gösterme</span><span class="sxs-lookup"><span data-stu-id="524a4-120">Exposing COM Components to the .NET Framework</span></span>](../../../docs/framework/interop/exposing-com-components.md)  
 [<span data-ttu-id="524a4-121">İzlenecek yol: Microsoft Office Bütünleştirilmiş Kodlarından Tür Bilgilerini Katıştırma</span><span class="sxs-lookup"><span data-stu-id="524a4-121">Walkthrough: Embedding Type Information from Microsoft Office Assemblies</span></span>](http://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3)  
 [<span data-ttu-id="524a4-122">İzlenecek yol: Yönetilen Bütünleştirilmiş Kodlardan Türler Katıştırma</span><span class="sxs-lookup"><span data-stu-id="524a4-122">Walkthrough: Embedding Types from Managed Assemblies</span></span>](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21)  
 [<span data-ttu-id="524a4-123">/ Link (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="524a4-123">/link (C# Compiler Options)</span></span>](~/docs/csharp/language-reference/compiler-options/link-compiler-option.md)  
 [<span data-ttu-id="524a4-124">/ Link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="524a4-124">/link (Visual Basic)</span></span>](~/docs/visual-basic/reference/command-line-compiler/link.md)

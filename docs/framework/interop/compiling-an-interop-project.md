---
title: Birlikte Çalışma Projesi Derleme
ms.date: 03/30/2017
helpviewer_keywords:
- interoperation with unmanaged code, compiling
- COM interop, compiling
- exposing COM components to .NET Framework
- compiling interop projects
- interoperation with unmanaged code, exposing COM components
- COM interop, exposing COM components
ms.assetid: 6fcf6588-5e25-41af-b4ae-780974f2c3df
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: db6630a6c1e68a776641db7ec7960f47fd260552
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64603279"
---
# <a name="compiling-an-interop-project"></a><span data-ttu-id="9776e-102">Birlikte Çalışma Projesi Derleme</span><span class="sxs-lookup"><span data-stu-id="9776e-102">Compiling an Interop Project</span></span>

<span data-ttu-id="9776e-103">İçeri aktarılan COM türlerini içeren bir veya daha fazla derlemelerine COM birlikte çalışma projelerini gibi yönetilen diğer proje derlenir.</span><span class="sxs-lookup"><span data-stu-id="9776e-103">COM interop projects that reference one or more assemblies containing imported COM types are compiled like any other managed project.</span></span> <span data-ttu-id="9776e-104">Visual Studio gibi geliştirme ortamında birlikte çalışma derlemelerini başvurabilir veya bir komut satırı derleyicisini kullanarak başvurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9776e-104">You can reference interop assemblies in a development environment such as Visual Studio, or you can reference them when you use a command-line compiler.</span></span> <span data-ttu-id="9776e-105">Her iki durumda da, diğer proje dosyaları ile aynı dizinde birlikte çalışma derlemesi doğru şekilde derlenmesi için olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9776e-105">In either case, to compile properly, the interop assembly must be in the same directory as the other project files.</span></span>

 <span data-ttu-id="9776e-106">Birlikte çalışma derlemelerini başvurmak için iki yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="9776e-106">There are two ways to reference interop assemblies:</span></span>

- <span data-ttu-id="9776e-107">Gömülü birlikte çalışma türleri: İle başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] ve Visual Studio 2010, derleyicinin tür bilgilerini birlikte çalışma bütünleştirilmiş kod yürütülebilir dosyanın içine gömmek için cmdlet'ten.</span><span class="sxs-lookup"><span data-stu-id="9776e-107">Embedded interop types: Beginning with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] and Visual Studio 2010, you can instruct the compiler to embed type information from an interop assembly into your executable.</span></span> <span data-ttu-id="9776e-108">Önerilen yöntem budur.</span><span class="sxs-lookup"><span data-stu-id="9776e-108">This is the recommended technique.</span></span>

- <span data-ttu-id="9776e-109">Birlikte çalışma derlemelerini dağıtma: Standart bir birlikte çalışma derlemesine başvuru oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9776e-109">Deploying interop assemblies: You can create a standard reference to an interop assembly.</span></span> <span data-ttu-id="9776e-110">Bu durumda, birlikte çalışma derlemesi uygulamanızla dağıtılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9776e-110">In this case, the interop assembly must be deployed with your application.</span></span>

 <span data-ttu-id="9776e-111">Bu iki teknik arasındaki farkları daha ayrıntılı olarak ele alınmıştır [kullanarak, yönetilen kodda COM türlerini](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="9776e-111">The differences between these two techniques are discussed in greater detail in [Using COM Types in Managed Code](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).</span></span>

 <span data-ttu-id="9776e-112">Visual Studio ile birlikte çalışma türlerini katıştırma içinde gösterilmiştir [izlenecek yol: Yönetilen derlemeler Visual Studio'da türler katıştırma (C#)](/docs/csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md), ve [izlenecek yol: Yönetilen türler katıştırma (Visual Basic) Visual Studio'da derlemeleri](/docs/visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="9776e-112">Embedding interop types with Visual Studio is demonstrated in [Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (C#)](/docs/csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md), and [Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (Visual Basic)](/docs/visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md).</span></span>

 <span data-ttu-id="9776e-113">Bir komut satırı derleyicisi ile birlikte çalışma derlemesine başvurmak ve, yürütülebilir dosyaların tür bilgilerini katıştırma için kullandığınız [/Link (C# Derleyici Seçenekleri)](../../csharp/language-reference/compiler-options/link-compiler-option.md) veya [/Link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) derleyici anahtarını ve birlikte çalışma derlemesi adı belirtin.</span><span class="sxs-lookup"><span data-stu-id="9776e-113">To reference an interop assembly with a command-line compiler and embed type information in your executables, use the [/link (C# Compiler Options)](../../csharp/language-reference/compiler-options/link-compiler-option.md) or the [/link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) compiler switch and specify the name of the interop assembly.</span></span>

> [!NOTE]
> <span data-ttu-id="9776e-114">Visual C++ uygulamalarını tür bilgileri katıştırılamıyor ancak uygulamaları veya yapan eklentiler ile çalışabilirler.</span><span class="sxs-lookup"><span data-stu-id="9776e-114">Visual C++ applications cannot embed type information, but they can interoperate with applications or add-ins that do.</span></span>

 <span data-ttu-id="9776e-115">Birincil birlikte çalışma derlemesi dağıtıldığında içeren bir uygulama derlemek için kullanın **/reference** derleyici geçiş ve birlikte çalışma derlemesi adı belirtin.</span><span class="sxs-lookup"><span data-stu-id="9776e-115">To compile an application that includes a primary interop assembly when it is deployed, use the **/reference** compiler switch and specify the name of the interop assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="9776e-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9776e-116">See also</span></span>

- [<span data-ttu-id="9776e-117">COM Bileşenlerini .NET Framework'te Gösterme</span><span class="sxs-lookup"><span data-stu-id="9776e-117">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)
- [<span data-ttu-id="9776e-118">Dil Bağımsızlığı ve Dilden Bağımsız Bileşenler</span><span class="sxs-lookup"><span data-stu-id="9776e-118">Language Independence and Language-Independent Components</span></span>](../../standard/language-independence-and-language-independent-components.md)
- <span data-ttu-id="9776e-119">[Yönetilen kodda COM türlerini kullanma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9776e-119">[Using COM Types in Managed Code](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))</span></span>
- [<span data-ttu-id="9776e-120">İzlenecek yol: Yönetilen derlemeler Visual Studio'da türler katıştırma (C#)</span><span class="sxs-lookup"><span data-stu-id="9776e-120">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (C#)</span></span>](/docs/csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)
- [<span data-ttu-id="9776e-121">İzlenecek yol: Visual Studio'da (Visual Basic) yönetilen derlemelerden türler katıştırma</span><span class="sxs-lookup"><span data-stu-id="9776e-121">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (Visual Basic)</span></span>](/docs/visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md)
- [<span data-ttu-id="9776e-122">Tür Kitaplığını Bütünleştirilmiş Kod Olarak İçeri Aktarma</span><span class="sxs-lookup"><span data-stu-id="9776e-122">Importing a Type Library as an Assembly</span></span>](importing-a-type-library-as-an-assembly.md)
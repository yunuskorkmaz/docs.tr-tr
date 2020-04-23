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
ms.openlocfilehash: 32102910ae674a97e941e1346a1898585f503527
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123680"
---
# <a name="compiling-an-interop-project"></a><span data-ttu-id="d59bb-102">Birlikte Çalışma Projesi Derleme</span><span class="sxs-lookup"><span data-stu-id="d59bb-102">Compiling an Interop Project</span></span>

<span data-ttu-id="d59bb-103">İçeri aktarılan COM türlerini içeren bir veya daha fazla derlemeye başvuran COM birlikte çalışma projeleri, diğer yönetilen projeler gibi derlenir.</span><span class="sxs-lookup"><span data-stu-id="d59bb-103">COM interop projects that reference one or more assemblies containing imported COM types are compiled like any other managed project.</span></span> <span data-ttu-id="d59bb-104">Birlikte Çalışma Derlemeleriyle Visual Studio gibi bir geliştirme ortamında başvurabilirsiniz veya bir komut satırı derleyicisi kullandığınızda bunlara başvurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d59bb-104">You can reference interop assemblies in a development environment such as Visual Studio, or you can reference them when you use a command-line compiler.</span></span> <span data-ttu-id="d59bb-105">Her iki durumda da, düzgün bir şekilde derlemek için birlikte çalışma derlemesinin diğer proje dosyalarıyla aynı dizinde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d59bb-105">In either case, to compile properly, the interop assembly must be in the same directory as the other project files.</span></span>

 <span data-ttu-id="d59bb-106">Birlikte çalışma derlemelerine başvurmanın iki yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="d59bb-106">There are two ways to reference interop assemblies:</span></span>

- <span data-ttu-id="d59bb-107">Gömülü birlikte çalışma türleri: .NET Framework 4 ve Visual Studio 2010 ile başlayarak, derleyicinin tür bilgilerini yürütülebilir bir derlemeden çalıştırılabilire katıştırmasını isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d59bb-107">Embedded interop types: Beginning with the .NET Framework 4 and Visual Studio 2010, you can instruct the compiler to embed type information from an interop assembly into your executable.</span></span> <span data-ttu-id="d59bb-108">Önerilen yöntem budur.</span><span class="sxs-lookup"><span data-stu-id="d59bb-108">This is the recommended technique.</span></span>

- <span data-ttu-id="d59bb-109">Birlikte çalışma derlemelerini dağıtma: birlikte çalışabilirlik derlemesine standart bir başvuru oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d59bb-109">Deploying interop assemblies: You can create a standard reference to an interop assembly.</span></span> <span data-ttu-id="d59bb-110">Bu durumda, birlikte çalışma derlemesinin uygulamanızla birlikte dağıtılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d59bb-110">In this case, the interop assembly must be deployed with your application.</span></span>

 <span data-ttu-id="d59bb-111">Bu iki teknik arasındaki farklılıklar, [yönetilen KODDAKI com türlerini kullanmayla](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))daha ayrıntılı bir şekilde ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="d59bb-111">The differences between these two techniques are discussed in greater detail in [Using COM Types in Managed Code](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).</span></span>

 <span data-ttu-id="d59bb-112">Visual Studio ile birlikte çalışma türlerini katıştırma [Izlenecek yol: Visual Studio 'Da yönetilen derlemelerden tür ekleme](../../standard/assembly/embed-types-visual-studio.md)gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d59bb-112">Embedding interop types with Visual Studio is demonstrated in [Walkthrough: Embedding Types from Managed Assemblies in Visual Studio](../../standard/assembly/embed-types-visual-studio.md).</span></span>

 <span data-ttu-id="d59bb-113">Bir komut satırı derleyicisi ile birlikte çalışma derlemesine başvurmak ve tür bilgilerini çalıştırılabilirlerinizde eklemek için [-Link (C# derleyici seçenekleri)](../../csharp/language-reference/compiler-options/link-compiler-option.md) veya [-Link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) derleyici anahtarını kullanın ve birlikte çalışma derlemesinin adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="d59bb-113">To reference an interop assembly with a command-line compiler and embed type information in your executables, use the [-link (C# Compiler Options)](../../csharp/language-reference/compiler-options/link-compiler-option.md) or the [-link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) compiler switch and specify the name of the interop assembly.</span></span>

> [!NOTE]
> <span data-ttu-id="d59bb-114">Visual C++ uygulamalar tür bilgilerini katıştıramazlar, ancak bunu yapan uygulamalarla veya eklentilerle birlikte çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="d59bb-114">Visual C++ applications cannot embed type information, but they can interoperate with applications or add-ins that do.</span></span>

 <span data-ttu-id="d59bb-115">Birincil birlikte çalışma derlemesini içeren bir uygulamayı dağıtıldığında derlemek için **/Reference** derleyici anahtarını kullanın ve birlikte çalışma derlemesinin adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="d59bb-115">To compile an application that includes a primary interop assembly when it is deployed, use the **/reference** compiler switch and specify the name of the interop assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="d59bb-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d59bb-116">See also</span></span>

- [<span data-ttu-id="d59bb-117">COM Bileşenlerini .NET Framework'te Gösterme</span><span class="sxs-lookup"><span data-stu-id="d59bb-117">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)
- [<span data-ttu-id="d59bb-118">Dil Bağımsızlığı ve Dilden Bağımsız Bileşenler</span><span class="sxs-lookup"><span data-stu-id="d59bb-118">Language Independence and Language-Independent Components</span></span>](../../standard/language-independence-and-language-independent-components.md)
- <span data-ttu-id="d59bb-119">[Yönetilen kodda COM türlerini kullanma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d59bb-119">[Using COM Types in Managed Code](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))</span></span>
- [<span data-ttu-id="d59bb-120">İzlenecek yol: Visual Studio’da Yönetilen Bütünleştirilmiş Kodlardan Türleri Katıştırma</span><span class="sxs-lookup"><span data-stu-id="d59bb-120">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio</span></span>](../../standard/assembly/embed-types-visual-studio.md)
- [<span data-ttu-id="d59bb-121">Tür Kitaplığını Derleme Olarak İçeri Aktarma</span><span class="sxs-lookup"><span data-stu-id="d59bb-121">Importing a Type Library as an Assembly</span></span>](importing-a-type-library-as-an-assembly.md)

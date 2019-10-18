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
ms.openlocfilehash: 5bc92eb9d4b7b0ae5db56303f3fbfa991c58e06a
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523837"
---
# <a name="compiling-an-interop-project"></a><span data-ttu-id="4a6d2-102">Birlikte Çalışma Projesi Derleme</span><span class="sxs-lookup"><span data-stu-id="4a6d2-102">Compiling an Interop Project</span></span>

<span data-ttu-id="4a6d2-103">İçeri aktarılan COM türlerini içeren bir veya daha fazla derlemeye başvuran COM birlikte çalışma projeleri, diğer yönetilen projeler gibi derlenir.</span><span class="sxs-lookup"><span data-stu-id="4a6d2-103">COM interop projects that reference one or more assemblies containing imported COM types are compiled like any other managed project.</span></span> <span data-ttu-id="4a6d2-104">Birlikte Çalışma Derlemeleriyle Visual Studio gibi bir geliştirme ortamında başvurabilirsiniz veya bir komut satırı derleyicisi kullandığınızda bunlara başvurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4a6d2-104">You can reference interop assemblies in a development environment such as Visual Studio, or you can reference them when you use a command-line compiler.</span></span> <span data-ttu-id="4a6d2-105">Her iki durumda da, düzgün bir şekilde derlemek için birlikte çalışma derlemesinin diğer proje dosyalarıyla aynı dizinde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4a6d2-105">In either case, to compile properly, the interop assembly must be in the same directory as the other project files.</span></span>

 <span data-ttu-id="4a6d2-106">Birlikte çalışma derlemelerine başvurmanın iki yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="4a6d2-106">There are two ways to reference interop assemblies:</span></span>

- <span data-ttu-id="4a6d2-107">Gömülü birlikte çalışma türleri: .NET Framework 4 ve Visual Studio 2010 ile başlayarak, derleyicinin tür bilgilerini yürütülebilir bir derlemeden çalıştırılabilire katıştırmasını isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4a6d2-107">Embedded interop types: Beginning with the .NET Framework 4 and Visual Studio 2010, you can instruct the compiler to embed type information from an interop assembly into your executable.</span></span> <span data-ttu-id="4a6d2-108">Önerilen yöntem budur.</span><span class="sxs-lookup"><span data-stu-id="4a6d2-108">This is the recommended technique.</span></span>

- <span data-ttu-id="4a6d2-109">Birlikte çalışma derlemelerini dağıtma: birlikte çalışabilirlik derlemesine standart bir başvuru oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4a6d2-109">Deploying interop assemblies: You can create a standard reference to an interop assembly.</span></span> <span data-ttu-id="4a6d2-110">Bu durumda, birlikte çalışma derlemesinin uygulamanızla birlikte dağıtılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4a6d2-110">In this case, the interop assembly must be deployed with your application.</span></span>

 <span data-ttu-id="4a6d2-111">Bu iki teknik arasındaki farklılıklar, [yönetilen KODDAKI com türlerini kullanmayla](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))daha ayrıntılı bir şekilde ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="4a6d2-111">The differences between these two techniques are discussed in greater detail in [Using COM Types in Managed Code](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).</span></span>

 <span data-ttu-id="4a6d2-112">Visual Studio ile birlikte çalışma türlerini katıştırma [Izlenecek yol: Visual Studio 'Da yönetilen derlemelerden tür ekleme](../../standard/assembly/embed-types-visual-studio.md)gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4a6d2-112">Embedding interop types with Visual Studio is demonstrated in [Walkthrough: Embedding Types from Managed Assemblies in Visual Studio](../../standard/assembly/embed-types-visual-studio.md).</span></span>

 <span data-ttu-id="4a6d2-113">Bir komut satırı derleyicisi ile birlikte çalışma derlemesine başvurmak ve tür bilgilerini çalıştırılabilirlerinizde eklemek için [-Link (C# derleyici seçenekleri)](../../csharp/language-reference/compiler-options/link-compiler-option.md) veya [-Link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) derleyici anahtarını kullanın ve birlikte çalışma derlemesinin adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="4a6d2-113">To reference an interop assembly with a command-line compiler and embed type information in your executables, use the [-link (C# Compiler Options)](../../csharp/language-reference/compiler-options/link-compiler-option.md) or the [-link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) compiler switch and specify the name of the interop assembly.</span></span>

> [!NOTE]
> <span data-ttu-id="4a6d2-114">Görsel C++ uygulamalar tür bilgilerini katıştıramazlar, ancak bunu yapan uygulamalarla veya eklentilerle birlikte çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="4a6d2-114">Visual C++ applications cannot embed type information, but they can interoperate with applications or add-ins that do.</span></span>

 <span data-ttu-id="4a6d2-115">Birincil birlikte çalışma derlemesini içeren bir uygulamayı dağıtıldığında derlemek için **/Reference** derleyici anahtarını kullanın ve birlikte çalışma derlemesinin adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="4a6d2-115">To compile an application that includes a primary interop assembly when it is deployed, use the **/reference** compiler switch and specify the name of the interop assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="4a6d2-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4a6d2-116">See also</span></span>

- [<span data-ttu-id="4a6d2-117">COM Bileşenlerini .NET Framework'te Gösterme</span><span class="sxs-lookup"><span data-stu-id="4a6d2-117">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)
- [<span data-ttu-id="4a6d2-118">Dil Bağımsızlığı ve Dilden Bağımsız Bileşenler</span><span class="sxs-lookup"><span data-stu-id="4a6d2-118">Language Independence and Language-Independent Components</span></span>](../../standard/language-independence-and-language-independent-components.md)
- <span data-ttu-id="4a6d2-119">[Yönetilen kodda COM türlerini kullanma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="4a6d2-119">[Using COM Types in Managed Code](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))</span></span>
- [<span data-ttu-id="4a6d2-120">İzlenecek yol: Visual Studio’da Yönetilen Bütünleştirilmiş Kodlardan Türleri Katıştırma</span><span class="sxs-lookup"><span data-stu-id="4a6d2-120">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio</span></span>](../../standard/assembly/embed-types-visual-studio.md)
- [<span data-ttu-id="4a6d2-121">Tür Kitaplığını Bütünleştirilmiş Kod Olarak İçeri Aktarma</span><span class="sxs-lookup"><span data-stu-id="4a6d2-121">Importing a Type Library as an Assembly</span></span>](importing-a-type-library-as-an-assembly.md)

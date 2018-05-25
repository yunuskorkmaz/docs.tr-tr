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
ms.openlocfilehash: 8a6099764fb98604726da99ef71b9c82e9a931bd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="compiling-an-interop-project"></a><span data-ttu-id="410e9-102">Birlikte Çalışma Projesi Derleme</span><span class="sxs-lookup"><span data-stu-id="410e9-102">Compiling an Interop Project</span></span>
<span data-ttu-id="410e9-103">İçeri aktarılan COM türlerini içeren bir veya daha fazla derlemeler başvuru COM birlikte çalışma projelerini gibi yönetilen diğer proje derlenir.</span><span class="sxs-lookup"><span data-stu-id="410e9-103">COM interop projects that reference one or more assemblies containing imported COM types are compiled like any other managed project.</span></span> <span data-ttu-id="410e9-104">Visual Studio gibi geliştirme ortamında birlikte çalışma derlemeleri başvurusu yapabilir veya komut satırı derleyicisi kullandığınızda başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="410e9-104">You can reference interop assemblies in a development environment such as Visual Studio, or you can reference them when you use a command-line compiler.</span></span> <span data-ttu-id="410e9-105">Her iki durumda da, diğer proje dosyaları ile aynı dizinde birlikte çalışma derlemesi düzgün derlemek için olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="410e9-105">In either case, to compile properly, the interop assembly must be in the same directory as the other project files.</span></span>  
  
 <span data-ttu-id="410e9-106">Birlikte çalışma derlemeleri başvurmak iki yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="410e9-106">There are two ways to reference interop assemblies:</span></span>  
  
-   <span data-ttu-id="410e9-107">Katıştırılmış birlikte çalışma türleri: itibaren [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] ve [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)], yürütülebilir dosyanın birlikte çalışma derlemeye tür bilgilerini katıştırma görevlendirin.</span><span class="sxs-lookup"><span data-stu-id="410e9-107">Embedded interop types: Beginning with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] and [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)], you can instruct the compiler to embed type information from an interop assembly into your executable.</span></span> <span data-ttu-id="410e9-108">Önerilen yöntem budur.</span><span class="sxs-lookup"><span data-stu-id="410e9-108">This is the recommended technique.</span></span>  
  
-   <span data-ttu-id="410e9-109">Birlikte çalışma derlemeleri dağıtma: birlikte çalışma derlemesi için standart bir başvuru oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="410e9-109">Deploying interop assemblies: You can create a standard reference to an interop assembly.</span></span> <span data-ttu-id="410e9-110">Bu durumda, uygulamanız ile birlikte çalışma derlemesi dağıtılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="410e9-110">In this case, the interop assembly must be deployed with your application.</span></span>  
  
 <span data-ttu-id="410e9-111">Bu iki teknikler arasındaki farklar daha ayrıntılı olarak ele alınmıştır [COM türlerinde kullanarak yönetilen kod](https://msdn.microsoft.com/library/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="410e9-111">The differences between these two techniques are discussed in greater detail in [Using COM Types in Managed Code](https://msdn.microsoft.com/library/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66(v=vs.100)).</span></span>  
  
 <span data-ttu-id="410e9-112">Visual Studio ile birlikte çalışma türlerini katıştırma içinde gösterilmiştir [izlenecek yol: Microsoft Office derlemelerinden tür bilgilerini katıştırma](https://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3(v=vs.100)) ve [izlenecek yol: yönetilen derlemelerden türler katıştırma](https://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21).</span><span class="sxs-lookup"><span data-stu-id="410e9-112">Embedding interop types with Visual Studio is demonstrated in [Walkthrough: Embedding Type Information from Microsoft Office Assemblies](https://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3(v=vs.100)) and [Walkthrough: Embedding Types from Managed Assemblies](https://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21).</span></span>  
  
 <span data-ttu-id="410e9-113">Komut satırı derleyicisi ile birlikte çalışma bir derleme başvurusu, yürütülebilir tür bilgilerini katıştırma, kullanın ve [/Link (C# Derleyici Seçenekleri)](../../csharp/language-reference/compiler-options/link-compiler-option.md) veya [/Link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) derleyici anahtar ve birlikte çalışma derlemesinin adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="410e9-113">To reference an interop assembly with a command-line compiler and embed type information in your executables, use the [/link (C# Compiler Options)](../../csharp/language-reference/compiler-options/link-compiler-option.md) or the [/link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) compiler switch and specify the name of the interop assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="410e9-114">Visual C++ uygulamalarını tür bilgilerini katıştırma olamaz, ancak uygulamalar veya yapmak eklentileri ile çalışabilirler.</span><span class="sxs-lookup"><span data-stu-id="410e9-114">Visual C++ applications cannot embed type information, but they can interoperate with applications or add-ins that do.</span></span>  
  
 <span data-ttu-id="410e9-115">Birincil birlikte çalışma derlemesi dağıtıldığında içeren bir uygulama derlemek için kullanmak **/reference** derleyici geçin ve birlikte çalışma derlemesinin adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="410e9-115">To compile an application that includes a primary interop assembly when it is deployed, use the **/reference** compiler switch and specify the name of the interop assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="410e9-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="410e9-116">See Also</span></span>  
 [<span data-ttu-id="410e9-117">COM Bileşenlerini .NET Framework'te Gösterme</span><span class="sxs-lookup"><span data-stu-id="410e9-117">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)  
 [<span data-ttu-id="410e9-118">Dil Bağımsızlığı ve Dilden Bağımsız Bileşenler</span><span class="sxs-lookup"><span data-stu-id="410e9-118">Language Independence and Language-Independent Components</span></span>](../../standard/language-independence-and-language-independent-components.md)  
 <span data-ttu-id="410e9-119">[Yönetilen kodda COM türlerini kullanma](https://msdn.microsoft.com/library/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="410e9-119">[Using COM Types in Managed Code](https://msdn.microsoft.com/library/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66(v=vs.100))</span></span>  
 <span data-ttu-id="410e9-120">[İzlenecek yol: Microsoft Office Bütünleştirilmiş Kodlarından Tür Bilgilerini Katıştırma](https://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="410e9-120">[Walkthrough: Embedding Type Information from Microsoft Office Assemblies](https://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3(v=vs.100))</span></span>  
 [<span data-ttu-id="410e9-121">İzlenecek yol: Yönetilen Bütünleştirilmiş Kodlardan Türler Katıştırma</span><span class="sxs-lookup"><span data-stu-id="410e9-121">Walkthrough: Embedding Types from Managed Assemblies</span></span>](https://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21)  
 [<span data-ttu-id="410e9-122">Tür Kitaplığını Bütünleştirilmiş Kod Olarak İçeri Aktarma</span><span class="sxs-lookup"><span data-stu-id="410e9-122">Importing a Type Library as an Assembly</span></span>](importing-a-type-library-as-an-assembly.md)

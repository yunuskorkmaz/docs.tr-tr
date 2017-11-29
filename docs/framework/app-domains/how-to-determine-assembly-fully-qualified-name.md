---
title: "Nasıl yapılır: bir derlemeyi &#39;belirlemek; s tam adı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- names [.NET Framework], fully qualified type names
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
ms.assetid: 009dae23-e1f6-4a64-9a9a-32e4c34802b0
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6e3736a1fa16b51262169d4d3efec56a958cedf6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-determine-an-assembly39s-fully-qualified-name"></a><span data-ttu-id="7fe92-102">Nasıl yapılır: bir derlemeyi &#39;belirlemek; s tam adı</span><span class="sxs-lookup"><span data-stu-id="7fe92-102">How to: Determine an Assembly&#39;s Fully Qualified Name</span></span>
<span data-ttu-id="7fe92-103">Bir derlemeyi genel derleme önbelleğinde tam adını bulmak için Genel Derleme Önbelleği aracı kullanın ([Gacutil.exe](../../../docs/framework/tools/gacutil-exe-gac-tool.md)).</span><span class="sxs-lookup"><span data-stu-id="7fe92-103">To discover the fully qualified name of an assembly in the global assembly cache, use the Global Assembly Cache Tool ([Gacutil.exe](../../../docs/framework/tools/gacutil-exe-gac-tool.md)).</span></span> <span data-ttu-id="7fe92-104">Bkz: [nasıl yapılır: genel derleme önbelleğinin içeriğini görüntüleme](../../../docs/framework/app-domains/how-to-view-the-contents-of-the-gac.md).</span><span class="sxs-lookup"><span data-stu-id="7fe92-104">See [How to: View the Contents of the Global Assembly Cache](../../../docs/framework/app-domains/how-to-view-the-contents-of-the-gac.md).</span></span>  
  
 <span data-ttu-id="7fe92-105">Genel derleme önbelleğinde olmayan derlemeler için çeşitli yollarla tam nitelikli derleme adı elde edebilirsiniz: kod konsol veya bir değişken için bilgileri çıkarmak için kullanabilir veya kullanabilirsiniz [Ildasm.exe (IL ayrıştırıcı)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)tam adı içeren derlemenin meta verilerini incelemek için.</span><span class="sxs-lookup"><span data-stu-id="7fe92-105">For assemblies that are not in the global assembly cache, you can get the fully qualified assembly name in a number of ways: can use code to output the information to the console or to a variable, or you can use the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to examine the assembly's metadata, which contains the fully qualified name.</span></span>  
  
-   <span data-ttu-id="7fe92-106">Derleme uygulama tarafından zaten yüklü değilse, değeri alabilirsiniz <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> tam adı alınacağı özellik.</span><span class="sxs-lookup"><span data-stu-id="7fe92-106">If the assembly is already loaded by the application, you can retrieve the value of the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> property to get the fully qualified name.</span></span> <span data-ttu-id="7fe92-107">Derlemesi GAC içinde olup olmadığını, bu yaklaşım kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7fe92-107">You can use this approach whether or not the assembly is in the GAC.</span></span> <span data-ttu-id="7fe92-108">Örnek, bir gösterim sağlar.</span><span class="sxs-lookup"><span data-stu-id="7fe92-108">The example provides an illustration.</span></span>  
  
-   <span data-ttu-id="7fe92-109">Derlemenin dosya sistemi yolu biliyorsanız, statik çağırabilirsiniz (`Shared` Visual Basic'te) <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> tam nitelikli derleme adı almak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7fe92-109">If you know the assembly's file system path, you can call the static (`Shared` in Visual Basic) <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> method to get the fully qualified assembly name.</span></span> <span data-ttu-id="7fe92-110">Basit bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7fe92-110">The following is a simple example.</span></span>  
  
     [!code-csharp[System.Reflection.AssemblyName.GetAssemblyName#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.reflection.assemblyname.getassemblyname/cs/getassemblyname1.cs#1)]
     [!code-vb[System.Reflection.AssemblyName.GetAssemblyName#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.reflection.assemblyname.getassemblyname/vb/getassemblyname1.vb#1)]  
  
-   <span data-ttu-id="7fe92-111">Kullanabileceğiniz [Ildasm.exe (IL ayrıştırıcı)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) tam adı içeren derlemenin meta verilerini incelemek için.</span><span class="sxs-lookup"><span data-stu-id="7fe92-111">You can use the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to examine the assembly's metadata, which contains the fully qualified name.</span></span>  
  
 <span data-ttu-id="7fe92-112">Sürüm, kültür ve derleme adı gibi ayarı derleme öznitelikleri hakkında daha fazla bilgi için bkz: [ayarı derleme özniteliklerinin](../../../docs/framework/app-domains/set-assembly-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="7fe92-112">For more information about setting assembly attributes such as version, culture, and assembly name, see [Setting Assembly Attributes](../../../docs/framework/app-domains/set-assembly-attributes.md).</span></span> <span data-ttu-id="7fe92-113">Bir derleme tanımlayıcı bir ad verip hakkında daha fazla bilgi için bkz: [bkz](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="7fe92-113">For more information about giving an assembly a strong name, see [Creating and Using Strong-Named Assemblies](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7fe92-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="7fe92-114">Example</span></span>  
 <span data-ttu-id="7fe92-115">Aşağıdaki kod örneği, belirtilen bir sınıfı içeren bir derlemenin tam olarak nitelendirilmiş adını konsolda nasıl görüntüleyeceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="7fe92-115">The following code example shows how to display the fully qualified name of an assembly containing a specified class to the console.</span></span> <span data-ttu-id="7fe92-116">Uygulama zaten yüklü bir derlemenin adını alır çünkü derlemesi GAC içinde olup olmadığını önemli değildir.</span><span class="sxs-lookup"><span data-stu-id="7fe92-116">Because it retrieves the name of an assembly that the app has already loaded, it does not matter whether the assembly is in the GAC.</span></span>  
  
 [!code-cpp[Assembly.Fullname#2](../../../samples/snippets/cpp/VS_Snippets_CLR/Assembly.FullName/CPP/example2.cpp#2)]
 [!code-csharp[Assembly.Fullname#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Assembly.FullName/CS/example2.cs#2)]
 [!code-vb[Assembly.Fullname#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Assembly.FullName/VB/example2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="7fe92-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7fe92-117">See Also</span></span>  
 [<span data-ttu-id="7fe92-118">Derleme adları</span><span class="sxs-lookup"><span data-stu-id="7fe92-118">Assembly Names</span></span>](../../../docs/framework/app-domains/assembly-names.md)  
 [<span data-ttu-id="7fe92-119">Derlemeleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="7fe92-119">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)  
 [<span data-ttu-id="7fe92-120">Oluşturma ve tanımlayıcı adlı derlemeler kullanma</span><span class="sxs-lookup"><span data-stu-id="7fe92-120">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)  
 [<span data-ttu-id="7fe92-121">Genel Derleme Önbelleği</span><span class="sxs-lookup"><span data-stu-id="7fe92-121">Global Assembly Cache</span></span>](../../../docs/framework/app-domains/gac.md)  
 [<span data-ttu-id="7fe92-122">Çalışma zamanı derlemeleri nasıl bulur</span><span class="sxs-lookup"><span data-stu-id="7fe92-122">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="7fe92-123">Derlemelerle programlama</span><span class="sxs-lookup"><span data-stu-id="7fe92-123">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)

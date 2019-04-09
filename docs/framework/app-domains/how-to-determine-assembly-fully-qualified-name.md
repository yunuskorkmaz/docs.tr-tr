---
title: 'Nasıl yapılır: Bir Derlemenin Tam Olarak Nitelenmiş Adını Belirleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- names [.NET Framework], fully qualified type names
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
ms.assetid: 009dae23-e1f6-4a64-9a9a-32e4c34802b0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 60a4ef1f5bde121d5773925437307b2749aa7282
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59097544"
---
# <a name="how-to-determine-an-assemblys-fully-qualified-name"></a><span data-ttu-id="7164c-102">Nasıl yapılır: Bir Derlemenin Tam Olarak Nitelenmiş Adını Belirleme</span><span class="sxs-lookup"><span data-stu-id="7164c-102">How to: Determine an Assembly's Fully Qualified Name</span></span>
<span data-ttu-id="7164c-103">Genel Derleme Önbelleği Aracı genel bütünleştirilmiş kod önbelleğindeki bir derleme tam olarak nitelenmiş adını bulmak için kullanın ([Gacutil.exe](../../../docs/framework/tools/gacutil-exe-gac-tool.md)).</span><span class="sxs-lookup"><span data-stu-id="7164c-103">To discover the fully qualified name of an assembly in the global assembly cache, use the Global Assembly Cache Tool ([Gacutil.exe](../../../docs/framework/tools/gacutil-exe-gac-tool.md)).</span></span> <span data-ttu-id="7164c-104">Bkz: [nasıl yapılır: Genel derleme önbelleğinin içeriğini görüntülemek](../../../docs/framework/app-domains/how-to-view-the-contents-of-the-gac.md).</span><span class="sxs-lookup"><span data-stu-id="7164c-104">See [How to: View the Contents of the Global Assembly Cache](../../../docs/framework/app-domains/how-to-view-the-contents-of-the-gac.md).</span></span>  
  
 <span data-ttu-id="7164c-105">Genel derleme önbelleğinde bulunmayan derlemeler için çeşitli yollarla tam derleme adını alabilirsiniz: kod, bilgileri konsola veya bir değişkene çıkarmak için kullanabilirsiniz veya kullanabileceğiniz [Ildasm.exe (IL ayrıştırıcı)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)tam adını içeren derlemenin meta verilerini incelemek için.</span><span class="sxs-lookup"><span data-stu-id="7164c-105">For assemblies that are not in the global assembly cache, you can get the fully qualified assembly name in a number of ways: can use code to output the information to the console or to a variable, or you can use the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to examine the assembly's metadata, which contains the fully qualified name.</span></span>  
  
-   <span data-ttu-id="7164c-106">Derleme uygulama tarafından zaten yüklü değilse, değeri alabilir <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> tam olarak nitelenmiş adını almak için özellik.</span><span class="sxs-lookup"><span data-stu-id="7164c-106">If the assembly is already loaded by the application, you can retrieve the value of the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> property to get the fully qualified name.</span></span> <span data-ttu-id="7164c-107">Derlemeyi GAC içinde olup olmadığını bu yaklaşımı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7164c-107">You can use this approach whether or not the assembly is in the GAC.</span></span> <span data-ttu-id="7164c-108">Örnek, bir gösterim sağlar.</span><span class="sxs-lookup"><span data-stu-id="7164c-108">The example provides an illustration.</span></span>  
  
-   <span data-ttu-id="7164c-109">Derlemenin dosya sistemi yolu biliyorsanız, statik çağırabilir (`Shared` Visual Basic'te) <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> tam derleme adını almak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7164c-109">If you know the assembly's file system path, you can call the static (`Shared` in Visual Basic) <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> method to get the fully qualified assembly name.</span></span> <span data-ttu-id="7164c-110">Basit bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7164c-110">The following is a simple example.</span></span>  
  
     [!code-csharp[System.Reflection.AssemblyName.GetAssemblyName#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.reflection.assemblyname.getassemblyname/cs/getassemblyname1.cs#1)]
     [!code-vb[System.Reflection.AssemblyName.GetAssemblyName#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.reflection.assemblyname.getassemblyname/vb/getassemblyname1.vb#1)]  
  
-   <span data-ttu-id="7164c-111">Kullanabileceğiniz [Ildasm.exe (IL ayrıştırıcı)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) tam adını içeren derlemenin meta verilerini incelemek için.</span><span class="sxs-lookup"><span data-stu-id="7164c-111">You can use the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to examine the assembly's metadata, which contains the fully qualified name.</span></span>  
  
 <span data-ttu-id="7164c-112">Sürüm, kültür ve derleme adı gibi derleme özniteliklerinin ayarlanması hakkında daha fazla bilgi için bkz: [derleme özniteliklerini ayarlama](../../../docs/framework/app-domains/set-assembly-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="7164c-112">For more information about setting assembly attributes such as version, culture, and assembly name, see [Setting Assembly Attributes](../../../docs/framework/app-domains/set-assembly-attributes.md).</span></span> <span data-ttu-id="7164c-113">Bir derlemeyi güçlü bir isim verilmesi hakkında daha fazla bilgi için bkz. [bkz](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="7164c-113">For more information about giving an assembly a strong name, see [Creating and Using Strong-Named Assemblies](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7164c-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="7164c-114">Example</span></span>  
 <span data-ttu-id="7164c-115">Aşağıdaki kod örneği, belirtilen bir sınıfı içeren bir derlemenin tam olarak nitelendirilmiş adını konsolda nasıl görüntüleyeceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="7164c-115">The following code example shows how to display the fully qualified name of an assembly containing a specified class to the console.</span></span> <span data-ttu-id="7164c-116">Uygulama zaten yüklü bir derlemenin adını alır çünkü derlemeyi GAC'ye olup bir önemi yoktur.</span><span class="sxs-lookup"><span data-stu-id="7164c-116">Because it retrieves the name of an assembly that the app has already loaded, it does not matter whether the assembly is in the GAC.</span></span>  
  
 [!code-cpp[Assembly.Fullname#2](../../../samples/snippets/cpp/VS_Snippets_CLR/Assembly.FullName/CPP/example2.cpp#2)]
 [!code-csharp[Assembly.Fullname#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Assembly.FullName/CS/example2.cs#2)]
 [!code-vb[Assembly.Fullname#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Assembly.FullName/VB/example2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="7164c-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7164c-117">See also</span></span>

- [<span data-ttu-id="7164c-118">Derleme Adları</span><span class="sxs-lookup"><span data-stu-id="7164c-118">Assembly Names</span></span>](../../../docs/framework/app-domains/assembly-names.md)
- [<span data-ttu-id="7164c-119">Derlemeler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="7164c-119">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)
- [<span data-ttu-id="7164c-120">Tanımlayıcı Adlı Derlemeler Oluşturma ve Kullanma</span><span class="sxs-lookup"><span data-stu-id="7164c-120">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
- [<span data-ttu-id="7164c-121">Genel Derleme Önbelleği</span><span class="sxs-lookup"><span data-stu-id="7164c-121">Global Assembly Cache</span></span>](../../../docs/framework/app-domains/gac.md)
- [<span data-ttu-id="7164c-122">Çalışma Zamanının Derlemelerin Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="7164c-122">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="7164c-123">Derlemelerle Programlama</span><span class="sxs-lookup"><span data-stu-id="7164c-123">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)

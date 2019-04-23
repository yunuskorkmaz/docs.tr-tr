---
title: .NET Framework Bileşenlerini COM'da Gösterme
ms.date: 03/30/2017
helpviewer_keywords:
- exposing .NET Framework components to COM
- interoperation with unmanaged code, exposing .NET Framework components
- COM interop, exposing COM components
ms.assetid: e42a65f7-1e61-411f-b09a-aca1bbce24c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: db0493f437d2546302a10bf52aebf326ea8a694c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59345774"
---
# <a name="exposing-net-framework-components-to-com"></a><span data-ttu-id="0a73f-102">.NET Framework Bileşenlerini COM'da Gösterme</span><span class="sxs-lookup"><span data-stu-id="0a73f-102">Exposing .NET Framework Components to COM</span></span>
<span data-ttu-id="0a73f-103">.NET türüne yazma ve bu tür, yönetilmeyen koddan kullanan geliştiriciler için ayrı etkinliklerdir.</span><span class="sxs-lookup"><span data-stu-id="0a73f-103">Writing a .NET type and consuming that type from unmanaged code are distinct activities for developers.</span></span> <span data-ttu-id="0a73f-104">Bu bölümde, COM istemcileri ile birlikte çalışan yönetilen kod yazma için bazı ipuçları açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="0a73f-104">This section describes several tips for writing managed code that interoperates with COM clients:</span></span>  
  
-   <span data-ttu-id="0a73f-105">[Birlikte çalışma için .NET türlerini niteleme](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md).</span><span class="sxs-lookup"><span data-stu-id="0a73f-105">[Qualifying .NET types for interoperation](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md).</span></span>  
  
     <span data-ttu-id="0a73f-106">Tüm yönetilen türleri, yöntemleri, özellikleri, alanları ve COM öğesine göstermek istediğiniz olayların ortak olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0a73f-106">All managed types, methods, properties, fields, and events that you want to expose to COM must be public.</span></span> <span data-ttu-id="0a73f-107">Türler, COM içinden çağrılabilen tek Oluşturucu olan bir genel varsayılan oluşturucuya sahip olmalıdır</span><span class="sxs-lookup"><span data-stu-id="0a73f-107">Types must have a public default constructor, which is the only constructor that can be invoked through COM.</span></span>  
  
-   <span data-ttu-id="0a73f-108">[Birlikte çalışma özniteliklerini uygulama](../../../docs/framework/interop/applying-interop-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="0a73f-108">[Applying interop attributes](../../../docs/framework/interop/applying-interop-attributes.md).</span></span>  
  
     <span data-ttu-id="0a73f-109">Yönetilen kod içinde özel öznitelikler, bir bileşenin birlikte çalışabilirliği geliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0a73f-109">Custom attributes within managed code can enhance the interoperability of a component.</span></span>  
  
-   <span data-ttu-id="0a73f-110">[COM için derlemeyi paketleme](../../../docs/framework/interop/packaging-an-assembly-for-com.md).</span><span class="sxs-lookup"><span data-stu-id="0a73f-110">[Packaging an assembly for COM](../../../docs/framework/interop/packaging-an-assembly-for-com.md).</span></span>  
  
     <span data-ttu-id="0a73f-111">COM geliştiriciler, başvuru ve bütünleştirilmiş kodlarınızı dağıtma adımlarını özetleyen gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="0a73f-111">COM developers might require that you summarize the steps involved in referencing and deploying your assemblies.</span></span>  
  
 <span data-ttu-id="0a73f-112">Ayrıca, bu bölümü, COM istemciden yönetilen bir tür kullanan için ilgili görevleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0a73f-112">Additionally, this section identifies the tasks related to consuming a managed type from a COM client.</span></span>  
  
#### <a name="to-consume-a-managed-type-from-com"></a><span data-ttu-id="0a73f-113">Yönetilen bir COM türünden kullanma</span><span class="sxs-lookup"><span data-stu-id="0a73f-113">To consume a managed type from COM</span></span>  
  
1. <span data-ttu-id="0a73f-114">[Derlemeleri COM ile kaydetme](../../../docs/framework/interop/registering-assemblies-with-com.md).</span><span class="sxs-lookup"><span data-stu-id="0a73f-114">[Register assemblies with COM](../../../docs/framework/interop/registering-assemblies-with-com.md).</span></span>  
  
     <span data-ttu-id="0a73f-115">Tasarım zamanında bir derleme (ve tür kitaplıklarını) türlerinde kayıtlı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0a73f-115">Types in an assembly (and type libraries) must be registered at design time.</span></span> <span data-ttu-id="0a73f-116">Bir yükleyici bütünleştirilmiş kod kaydedilmiyorsa COM geliştiriciler Regasm.exe isteyin.</span><span class="sxs-lookup"><span data-stu-id="0a73f-116">If an installer does not register the assembly, instruct COM developers to use Regasm.exe.</span></span>  
  
2. <span data-ttu-id="0a73f-117">[Com'dan .NET türlerine başvurma](../../../docs/framework/interop/how-to-reference-net-types-from-com.md).</span><span class="sxs-lookup"><span data-stu-id="0a73f-117">[Reference .NET types from COM](../../../docs/framework/interop/how-to-reference-net-types-from-com.md).</span></span>  
  
     <span data-ttu-id="0a73f-118">Aynı araçları ve bugün kullandıkları teknikleri kullanarak derlemedeki türleri COM geliştiriciler başvurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0a73f-118">COM developers can reference types in an assembly using the same tools and techniques they use today.</span></span>  
  
3. <span data-ttu-id="0a73f-119">[Bir .NET nesnesini çağırma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="0a73f-119">[Call a .NET object](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100)).</span></span>  
  
     <span data-ttu-id="0a73f-120">COM geliştiriciler, bunlar herhangi bir yönetilmeyen türü üzerinde yöntemleri çağırmak aynı şekilde .NET nesne üzerinde yöntemleri çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="0a73f-120">COM developers can call methods on the .NET object the same way they call methods on any unmanaged type.</span></span> <span data-ttu-id="0a73f-121">Örneğin, COM **CoCreateInstance** API .NET nesneleri etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="0a73f-121">For example, the COM **CoCreateInstance** API activates .NET objects.</span></span>  
  
4. <span data-ttu-id="0a73f-122">[COM erişimi için bir uygulamayı dağıtmak](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="0a73f-122">[Deploy an application for COM access](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100)).</span></span>  
  
     <span data-ttu-id="0a73f-123">Bir katı adlı derleme genel derleme önbelleğinde yüklü ve yayımcısını imzasının gerektirir.</span><span class="sxs-lookup"><span data-stu-id="0a73f-123">A strong-named assembly can be installed in the global assembly cache and requires a signature from its publisher.</span></span> <span data-ttu-id="0a73f-124">İstemci uygulama dizininde olmayan kesin adlı derlemeler yüklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="0a73f-124">Assemblies that are not strong named must be installed in the application directory of the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a73f-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0a73f-125">See also</span></span>

- [<span data-ttu-id="0a73f-126">Yönetilmeyen Kod ile Birlikte Çalışma</span><span class="sxs-lookup"><span data-stu-id="0a73f-126">Interoperating with Unmanaged Code</span></span>](../../../docs/framework/interop/index.md)
- [<span data-ttu-id="0a73f-127">COM birlikte çalışma örneği: COM istemcisi ve .NET sunucusu</span><span class="sxs-lookup"><span data-stu-id="0a73f-127">COM Interop Sample: COM Client and .NET Server</span></span>](../../../docs/framework/interop/com-interop-sample-com-client-and-net-server.md)

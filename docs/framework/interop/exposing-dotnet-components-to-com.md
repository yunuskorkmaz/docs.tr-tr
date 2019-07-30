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
ms.openlocfilehash: c88466df32a4167b2b32a7cc0f64eb306e392611
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629351"
---
# <a name="exposing-net-framework-components-to-com"></a><span data-ttu-id="cef22-102">.NET Framework Bileşenlerini COM'da Gösterme</span><span class="sxs-lookup"><span data-stu-id="cef22-102">Exposing .NET Framework Components to COM</span></span>
<span data-ttu-id="cef22-103">.NET türü yazmak ve yönetilmeyen koddan Bu türün kullanılması, geliştiriciler için ayrı etkinliklerdir.</span><span class="sxs-lookup"><span data-stu-id="cef22-103">Writing a .NET type and consuming that type from unmanaged code are distinct activities for developers.</span></span> <span data-ttu-id="cef22-104">Bu bölümde, COM istemcileriyle birlikte çalışan yönetilen kod yazmak için çeşitli ipuçları açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="cef22-104">This section describes several tips for writing managed code that interoperates with COM clients:</span></span>  
  
- <span data-ttu-id="cef22-105">[Birlikte çalışma için .NET türlerini niteleme](../../../docs/standard/native-interop/qualify-net-types-for-interoperation.md).</span><span class="sxs-lookup"><span data-stu-id="cef22-105">[Qualifying .NET types for interoperation](../../../docs/standard/native-interop/qualify-net-types-for-interoperation.md).</span></span>  
  
     <span data-ttu-id="cef22-106">COM 'da kullanıma sunmak istediğiniz tüm yönetilen türler, Yöntemler, özellikler, alanlar ve olaylar ortak olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cef22-106">All managed types, methods, properties, fields, and events that you want to expose to COM must be public.</span></span> <span data-ttu-id="cef22-107">Türler, COM ile çağrılabilen tek Oluşturucu olan ortak parametresiz bir oluşturucuya sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cef22-107">Types must have a public parameterless constructor, which is the only constructor that can be invoked through COM.</span></span>  
  
- <span data-ttu-id="cef22-108">[Birlikte çalışma öznitelikleri uygulanıyor](../../../docs/standard/native-interop/apply-interop-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="cef22-108">[Applying interop attributes](../../../docs/standard/native-interop/apply-interop-attributes.md).</span></span>  
  
     <span data-ttu-id="cef22-109">Yönetilen kod içindeki özel öznitelikler bir bileşenin birlikte çalışabilirliğini artırabilir.</span><span class="sxs-lookup"><span data-stu-id="cef22-109">Custom attributes within managed code can enhance the interoperability of a component.</span></span>  
  
- <span data-ttu-id="cef22-110">[Com için bir derleme paketleniyor](../../../docs/framework/interop/packaging-an-assembly-for-com.md).</span><span class="sxs-lookup"><span data-stu-id="cef22-110">[Packaging an assembly for COM](../../../docs/framework/interop/packaging-an-assembly-for-com.md).</span></span>  
  
     <span data-ttu-id="cef22-111">COM geliştiricileri, derlemelerinizi başvurma ve dağıtma konusunda yer alan adımları özetlemenizi gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="cef22-111">COM developers might require that you summarize the steps involved in referencing and deploying your assemblies.</span></span>  
  
 <span data-ttu-id="cef22-112">Ayrıca, bu bölüm bir COM istemcisinden yönetilen bir tür tüketme ile ilgili görevleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="cef22-112">Additionally, this section identifies the tasks related to consuming a managed type from a COM client.</span></span>  
  
#### <a name="to-consume-a-managed-type-from-com"></a><span data-ttu-id="cef22-113">COM 'dan yönetilen bir tür kullanmak için</span><span class="sxs-lookup"><span data-stu-id="cef22-113">To consume a managed type from COM</span></span>  
  
1. <span data-ttu-id="cef22-114">[DERLEMELERI com Ile kaydedin](../../../docs/framework/interop/registering-assemblies-with-com.md).</span><span class="sxs-lookup"><span data-stu-id="cef22-114">[Register assemblies with COM](../../../docs/framework/interop/registering-assemblies-with-com.md).</span></span>  
  
     <span data-ttu-id="cef22-115">Bir derlemedeki türlerin (ve tür kitaplıklarının) tasarım zamanında kayıtlı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="cef22-115">Types in an assembly (and type libraries) must be registered at design time.</span></span> <span data-ttu-id="cef22-116">Bir yükleyici derlemeyi KAYDETMEZSE, COM geliştiricilerine Regasm. exe kullanmayı söyleyin.</span><span class="sxs-lookup"><span data-stu-id="cef22-116">If an installer does not register the assembly, instruct COM developers to use Regasm.exe.</span></span>  
  
2. <span data-ttu-id="cef22-117">[Com 'dan .net türlerine başvurun](../../../docs/framework/interop/how-to-reference-net-types-from-com.md).</span><span class="sxs-lookup"><span data-stu-id="cef22-117">[Reference .NET types from COM](../../../docs/framework/interop/how-to-reference-net-types-from-com.md).</span></span>  
  
     <span data-ttu-id="cef22-118">COM geliştiricileri, günümüzde kullandıkları aynı araçları ve teknikleri kullanarak bir derlemedeki türlere başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="cef22-118">COM developers can reference types in an assembly using the same tools and techniques they use today.</span></span>  
  
3. <span data-ttu-id="cef22-119">[.Net nesnesi çağırma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="cef22-119">[Call a .NET object](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100)).</span></span>  
  
     <span data-ttu-id="cef22-120">COM geliştiricileri, hiçbir yönetilmeyen türdeki yöntemleri çağırdıkları şekilde .NET nesnesi üzerinde Yöntemler çağırabilirler.</span><span class="sxs-lookup"><span data-stu-id="cef22-120">COM developers can call methods on the .NET object the same way they call methods on any unmanaged type.</span></span> <span data-ttu-id="cef22-121">Örneğin, COM **Cocreateınstance** API 'si .net nesnelerini etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="cef22-121">For example, the COM **CoCreateInstance** API activates .NET objects.</span></span>  
  
4. <span data-ttu-id="cef22-122">[Com erişimi için bir uygulamayı dağıtın](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="cef22-122">[Deploy an application for COM access](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100)).</span></span>  
  
     <span data-ttu-id="cef22-123">Tanımlayıcı adlı bir derleme, genel derleme önbelleğine yüklenebilir ve yayımcısından imza gerektirir.</span><span class="sxs-lookup"><span data-stu-id="cef22-123">A strong-named assembly can be installed in the global assembly cache and requires a signature from its publisher.</span></span> <span data-ttu-id="cef22-124">Tanımlayıcı olarak adlandırılmış olmayan derlemeler istemcinin uygulama dizininde yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cef22-124">Assemblies that are not strong named must be installed in the application directory of the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cef22-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cef22-125">See also</span></span>

- [<span data-ttu-id="cef22-126">Yönetilmeyen Kod ile Birlikte Çalışma</span><span class="sxs-lookup"><span data-stu-id="cef22-126">Interoperating with Unmanaged Code</span></span>](../../../docs/framework/interop/index.md)
- [<span data-ttu-id="cef22-127">COM birlikte çalışma örneği: COM Istemcisi ve .NET sunucusu</span><span class="sxs-lookup"><span data-stu-id="cef22-127">COM Interop Sample: COM Client and .NET Server</span></span>](../../../docs/framework/interop/com-interop-sample-com-client-and-net-server.md)

---
title: .NET bileşenlerini COM 'a gösterme
ms.date: 03/30/2017
helpviewer_keywords:
- exposing .NET Framework components to COM
- interoperation with unmanaged code, exposing .NET Framework components
- COM interop, exposing COM components
ms.assetid: e42a65f7-1e61-411f-b09a-aca1bbce24c6
ms.openlocfilehash: 09045fb455a2163641d6f4af0ba07520ead59f1e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123481"
---
# <a name="exposing-net-components-to-com"></a><span data-ttu-id="65175-102">.NET bileşenlerini COM 'a gösterme</span><span class="sxs-lookup"><span data-stu-id="65175-102">Exposing .NET components to COM</span></span>

<span data-ttu-id="65175-103">.NET türü yazmak ve yönetilmeyen koddan Bu türün kullanılması, geliştiriciler için ayrı etkinliklerdir.</span><span class="sxs-lookup"><span data-stu-id="65175-103">Writing a .NET type and consuming that type from unmanaged code are distinct activities for developers.</span></span> <span data-ttu-id="65175-104">Bu bölümde, COM istemcileriyle birlikte çalışan yönetilen kod yazmak için çeşitli ipuçları açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="65175-104">This section describes several tips for writing managed code that interoperates with COM clients:</span></span>

- <span data-ttu-id="65175-105">[Birlikte çalışma için .NET türlerini niteleme](../../standard/native-interop/qualify-net-types-for-interoperation.md).</span><span class="sxs-lookup"><span data-stu-id="65175-105">[Qualifying .NET types for interoperation](../../standard/native-interop/qualify-net-types-for-interoperation.md).</span></span>

     <span data-ttu-id="65175-106">COM 'da kullanıma sunmak istediğiniz tüm yönetilen türler, Yöntemler, özellikler, alanlar ve olaylar ortak olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="65175-106">All managed types, methods, properties, fields, and events that you want to expose to COM must be public.</span></span> <span data-ttu-id="65175-107">Türler, COM ile çağrılabilen tek Oluşturucu olan ortak parametresiz bir oluşturucuya sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="65175-107">Types must have a public parameterless constructor, which is the only constructor that can be invoked through COM.</span></span>

- <span data-ttu-id="65175-108">[Birlikte çalışma öznitelikleri uygulanıyor](../../standard/native-interop/apply-interop-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="65175-108">[Applying interop attributes](../../standard/native-interop/apply-interop-attributes.md).</span></span>

     <span data-ttu-id="65175-109">Yönetilen kod içindeki özel öznitelikler bir bileşenin birlikte çalışabilirliğini artırabilir.</span><span class="sxs-lookup"><span data-stu-id="65175-109">Custom attributes within managed code can enhance the interoperability of a component.</span></span>

- <span data-ttu-id="65175-110">[Com için bir derleme paketleniyor](packaging-an-assembly-for-com.md).</span><span class="sxs-lookup"><span data-stu-id="65175-110">[Packaging an assembly for COM](packaging-an-assembly-for-com.md).</span></span>

     <span data-ttu-id="65175-111">COM geliştiricileri, derlemelerinizi başvurma ve dağıtma konusunda yer alan adımları özetlemenizi gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="65175-111">COM developers might require that you summarize the steps involved in referencing and deploying your assemblies.</span></span>

 <span data-ttu-id="65175-112">Ayrıca, bu bölüm bir COM istemcisinden yönetilen bir tür tüketme ile ilgili görevleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="65175-112">Additionally, this section identifies the tasks related to consuming a managed type from a COM client.</span></span>

## <a name="to-consume-a-managed-type-from-com"></a><span data-ttu-id="65175-113">COM 'dan yönetilen bir tür kullanmak için</span><span class="sxs-lookup"><span data-stu-id="65175-113">To consume a managed type from COM</span></span>

1. <span data-ttu-id="65175-114">[DERLEMELERI com Ile kaydedin](registering-assemblies-with-com.md).</span><span class="sxs-lookup"><span data-stu-id="65175-114">[Register assemblies with COM](registering-assemblies-with-com.md).</span></span>

     <span data-ttu-id="65175-115">Bir derlemedeki türlerin (ve tür kitaplıklarının) tasarım zamanında kayıtlı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="65175-115">Types in an assembly (and type libraries) must be registered at design time.</span></span> <span data-ttu-id="65175-116">Bir yükleyici derlemeyi KAYDETMEZSE, COM geliştiricilerine Regasm. exe kullanmayı söyleyin.</span><span class="sxs-lookup"><span data-stu-id="65175-116">If an installer does not register the assembly, instruct COM developers to use Regasm.exe.</span></span>

2. <span data-ttu-id="65175-117">[Com 'dan .net türlerine başvurun](how-to-reference-net-types-from-com.md).</span><span class="sxs-lookup"><span data-stu-id="65175-117">[Reference .NET types from COM](how-to-reference-net-types-from-com.md).</span></span>

     <span data-ttu-id="65175-118">COM geliştiricileri, günümüzde kullandıkları aynı araçları ve teknikleri kullanarak bir derlemedeki türlere başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="65175-118">COM developers can reference types in an assembly using the same tools and techniques they use today.</span></span>

3. <span data-ttu-id="65175-119">[.Net nesnesi çağırma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="65175-119">[Call a .NET object](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100)).</span></span>

     <span data-ttu-id="65175-120">COM geliştiricileri, hiçbir yönetilmeyen türdeki yöntemleri çağırdıkları şekilde .NET nesnesi üzerinde Yöntemler çağırabilirler.</span><span class="sxs-lookup"><span data-stu-id="65175-120">COM developers can call methods on the .NET object the same way they call methods on any unmanaged type.</span></span> <span data-ttu-id="65175-121">Örneğin, COM **Cocreateınstance** API 'si .net nesnelerini etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="65175-121">For example, the COM **CoCreateInstance** API activates .NET objects.</span></span>

4. <span data-ttu-id="65175-122">[Com erişimi için bir uygulamayı dağıtın](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="65175-122">[Deploy an application for COM access](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100)).</span></span>

     <span data-ttu-id="65175-123">Tanımlayıcı adlı bir derleme, genel derleme önbelleğine yüklenebilir ve yayımcısından imza gerektirir.</span><span class="sxs-lookup"><span data-stu-id="65175-123">A strong-named assembly can be installed in the global assembly cache and requires a signature from its publisher.</span></span> <span data-ttu-id="65175-124">Tanımlayıcı olarak adlandırılmış olmayan derlemeler istemcinin uygulama dizininde yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="65175-124">Assemblies that are not strong named must be installed in the application directory of the client.</span></span>

## <a name="see-also"></a><span data-ttu-id="65175-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="65175-125">See also</span></span>

- [<span data-ttu-id="65175-126">Yönetilmeyen Kod ile Birlikte Çalışma</span><span class="sxs-lookup"><span data-stu-id="65175-126">Interoperating with Unmanaged Code</span></span>](index.md)
- [<span data-ttu-id="65175-127">COM Birlikte Çalışma Örneği: COM İstemcisi ve .NET Sunucusu</span><span class="sxs-lookup"><span data-stu-id="65175-127">COM Interop Sample: COM Client and .NET Server</span></span>](com-interop-sample-com-client-and-net-server.md)

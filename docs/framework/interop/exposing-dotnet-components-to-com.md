---
title: .NET bileşenlerini COM 'a gösterme
description: .NET bileşenlerini COM 'a sunun. Birlikte çalışma için .NET türlerini niteleyin. Birlikte çalışma özniteliklerini uygulayın. COM için bir derlemeyi paketleyin. COM 'dan yönetilen bir tür kullanın.
ms.date: 03/30/2017
helpviewer_keywords:
- exposing .NET Framework components to COM
- interoperation with unmanaged code, exposing .NET Framework components
- COM interop, exposing COM components
ms.assetid: e42a65f7-1e61-411f-b09a-aca1bbce24c6
ms.openlocfilehash: dc808f3e8d6bd89ba979d43e5b4ec9d787bd09b1
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90545265"
---
# <a name="exposing-net-components-to-com"></a><span data-ttu-id="657a0-107">.NET bileşenlerini COM 'a gösterme</span><span class="sxs-lookup"><span data-stu-id="657a0-107">Exposing .NET components to COM</span></span>

<span data-ttu-id="657a0-108">.NET türü yazmak ve yönetilmeyen koddan Bu türün kullanılması, geliştiriciler için ayrı etkinliklerdir.</span><span class="sxs-lookup"><span data-stu-id="657a0-108">Writing a .NET type and consuming that type from unmanaged code are distinct activities for developers.</span></span> <span data-ttu-id="657a0-109">Bu bölümde, COM istemcileriyle birlikte çalışan yönetilen kod yazmak için çeşitli ipuçları açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="657a0-109">This section describes several tips for writing managed code that interoperates with COM clients:</span></span>

- <span data-ttu-id="657a0-110">[Birlikte çalışma için .NET türlerini niteleme](../../standard/native-interop/qualify-net-types-for-interoperation.md).</span><span class="sxs-lookup"><span data-stu-id="657a0-110">[Qualifying .NET types for interoperation](../../standard/native-interop/qualify-net-types-for-interoperation.md).</span></span>

     <span data-ttu-id="657a0-111">COM 'da kullanıma sunmak istediğiniz tüm yönetilen türler, Yöntemler, özellikler, alanlar ve olaylar ortak olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="657a0-111">All managed types, methods, properties, fields, and events that you want to expose to COM must be public.</span></span> <span data-ttu-id="657a0-112">Türler, COM ile çağrılabilen tek Oluşturucu olan ortak parametresiz bir oluşturucuya sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="657a0-112">Types must have a public parameterless constructor, which is the only constructor that can be invoked through COM.</span></span>

- <span data-ttu-id="657a0-113">[Birlikte çalışma öznitelikleri uygulanıyor](../../standard/native-interop/apply-interop-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="657a0-113">[Applying interop attributes](../../standard/native-interop/apply-interop-attributes.md).</span></span>

     <span data-ttu-id="657a0-114">Yönetilen kod içindeki özel öznitelikler bir bileşenin birlikte çalışabilirliğini artırabilir.</span><span class="sxs-lookup"><span data-stu-id="657a0-114">Custom attributes within managed code can enhance the interoperability of a component.</span></span>

- <span data-ttu-id="657a0-115">[Com için bir derleme paketleniyor](packaging-an-assembly-for-com.md).</span><span class="sxs-lookup"><span data-stu-id="657a0-115">[Packaging an assembly for COM](packaging-an-assembly-for-com.md).</span></span>

     <span data-ttu-id="657a0-116">COM geliştiricileri, derlemelerinizi başvurma ve dağıtma konusunda yer alan adımları özetlemenizi gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="657a0-116">COM developers might require that you summarize the steps involved in referencing and deploying your assemblies.</span></span>

 <span data-ttu-id="657a0-117">Ayrıca, bu bölüm bir COM istemcisinden yönetilen bir tür tüketme ile ilgili görevleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="657a0-117">Additionally, this section identifies the tasks related to consuming a managed type from a COM client.</span></span>

## <a name="to-consume-a-managed-type-from-com"></a><span data-ttu-id="657a0-118">COM 'dan yönetilen bir tür kullanmak için</span><span class="sxs-lookup"><span data-stu-id="657a0-118">To consume a managed type from COM</span></span>

1. <span data-ttu-id="657a0-119">[DERLEMELERI com Ile kaydedin](registering-assemblies-with-com.md).</span><span class="sxs-lookup"><span data-stu-id="657a0-119">[Register assemblies with COM](registering-assemblies-with-com.md).</span></span>

     <span data-ttu-id="657a0-120">Bir derlemedeki türlerin (ve tür kitaplıklarının) tasarım zamanında kayıtlı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="657a0-120">Types in an assembly (and type libraries) must be registered at design time.</span></span> <span data-ttu-id="657a0-121">Bir yükleyici derlemeyi KAYDETMEZSE, COM geliştiricilerine Regasm.exe kullanmalarını söyleyin.</span><span class="sxs-lookup"><span data-stu-id="657a0-121">If an installer does not register the assembly, instruct COM developers to use Regasm.exe.</span></span>

2. <span data-ttu-id="657a0-122">[Com 'dan .net türlerine başvurun](how-to-reference-net-types-from-com.md).</span><span class="sxs-lookup"><span data-stu-id="657a0-122">[Reference .NET types from COM](how-to-reference-net-types-from-com.md).</span></span>

     <span data-ttu-id="657a0-123">COM geliştiricileri, günümüzde kullandıkları aynı araçları ve teknikleri kullanarak bir derlemedeki türlere başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="657a0-123">COM developers can reference types in an assembly using the same tools and techniques they use today.</span></span>

3. <span data-ttu-id="657a0-124">[.Net nesnesi çağırma](/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="657a0-124">[Call a .NET object](/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100)).</span></span>

     <span data-ttu-id="657a0-125">COM geliştiricileri, hiçbir yönetilmeyen türdeki yöntemleri çağırdıkları şekilde .NET nesnesi üzerinde Yöntemler çağırabilirler.</span><span class="sxs-lookup"><span data-stu-id="657a0-125">COM developers can call methods on the .NET object the same way they call methods on any unmanaged type.</span></span> <span data-ttu-id="657a0-126">Örneğin, COM **Cocreateınstance** API 'si .net nesnelerini etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="657a0-126">For example, the COM **CoCreateInstance** API activates .NET objects.</span></span>

4. <span data-ttu-id="657a0-127">[Com erişimi için bir uygulamayı dağıtın](/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="657a0-127">[Deploy an application for COM access](/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100)).</span></span>

     <span data-ttu-id="657a0-128">Tanımlayıcı adlı bir derleme, genel derleme önbelleğine yüklenebilir ve yayımcısından imza gerektirir.</span><span class="sxs-lookup"><span data-stu-id="657a0-128">A strong-named assembly can be installed in the global assembly cache and requires a signature from its publisher.</span></span> <span data-ttu-id="657a0-129">Tanımlayıcı olarak adlandırılmış olmayan derlemeler istemcinin uygulama dizininde yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="657a0-129">Assemblies that are not strong named must be installed in the application directory of the client.</span></span>

## <a name="see-also"></a><span data-ttu-id="657a0-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="657a0-130">See also</span></span>

- [<span data-ttu-id="657a0-131">Yönetilmeyen Kod ile Birlikte Çalışma</span><span class="sxs-lookup"><span data-stu-id="657a0-131">Interoperating with Unmanaged Code</span></span>](index.md)
- [<span data-ttu-id="657a0-132">COM Birlikte Çalışma Örneği: COM İstemcisi ve .NET Sunucusu</span><span class="sxs-lookup"><span data-stu-id="657a0-132">COM Interop Sample: COM Client and .NET Server</span></span>](com-interop-sample-com-client-and-net-server.md)

---
title: COM için bir .NET Framework derlemesi paketleme
ms.date: 03/30/2017
helpviewer_keywords:
- exposing .NET Framework components to COM
- COM interop, packaging assemblies
- packaging assemblies for COM
- Tlbexp.exe
- TypeLibConverter class
- .NET Services Installation tool
- Assembly Registration tool
- Type Library Exporter
- Reqsvcs.exe
- interoperation with unmanaged code, exposing .NET Framework components
- interoperation with unmanaged code, packaging assemblies
- COM interop, exposing COM components
- Reqasm.exe
ms.assetid: 39dc55aa-f2a1-4093-87bb-f1c0edb6e761
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 11777f21d34da8b529352122bbf185f1938d3eb5
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/17/2019
ms.locfileid: "69567236"
---
# <a name="packaging-a-net-framework-assembly-for-com"></a><span data-ttu-id="9a740-102">COM için bir .NET Framework derlemesi paketleme</span><span class="sxs-lookup"><span data-stu-id="9a740-102">Packaging a .NET Framework Assembly for COM</span></span>

<span data-ttu-id="9a740-103">COM geliştiricileri, uygulamasında dahil etmek üzere plantıkları yönetilen türler hakkında aşağıdaki bilgilerden faydalanabilir:</span><span class="sxs-lookup"><span data-stu-id="9a740-103">COM developers can benefit from the following information about the managed types they plan to incorporate in their application:</span></span>

- <span data-ttu-id="9a740-104">COM uygulamalarının tüketebileceği türlerin listesi</span><span class="sxs-lookup"><span data-stu-id="9a740-104">A list of types that COM applications can consume</span></span>

  <span data-ttu-id="9a740-105">Bazı yönetilen türler COM 'a görünmez; Bazıları görünür ancak creatable değildir; ve bazıları hem görünür hem de creatable.</span><span class="sxs-lookup"><span data-stu-id="9a740-105">Some managed types are invisible to COM; some are visible but not creatable; and some are both visible and creatable.</span></span> <span data-ttu-id="9a740-106">Bir bütünleştirilmiş kod, görünmeyen, Visible, oluşturulabilir ve oluşturulabilir türlerinin herhangi bir birleşimini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="9a740-106">An assembly can comprise any combination of invisible, visible, not creatable, and creatable types.</span></span> <span data-ttu-id="9a740-107">Tamamlananlar için, özellikle bu türler .NET Framework gösterilen türlerin bir alt kümesi olduğunda, COM 'da kullanıma sunmayı planladığınız bir derlemede bulunan türleri yapın.</span><span class="sxs-lookup"><span data-stu-id="9a740-107">For completeness, identify the types in an assembly that you intend to expose to COM, especially when those types are a subset of the types exposed to the .NET Framework.</span></span>

  <span data-ttu-id="9a740-108">Daha fazla bilgi için bkz. [birlikte çalışma için .NET türlerini niteleme](../../../docs/standard/native-interop/qualify-net-types-for-interoperation.md).</span><span class="sxs-lookup"><span data-stu-id="9a740-108">For additional information, see [Qualifying .NET Types for Interoperation](../../../docs/standard/native-interop/qualify-net-types-for-interoperation.md).</span></span>

- <span data-ttu-id="9a740-109">Sürüm oluşturma yönergeleri</span><span class="sxs-lookup"><span data-stu-id="9a740-109">Versioning instructions</span></span>

  <span data-ttu-id="9a740-110">Sınıf arabirimini uygulayan yönetilen sınıflar (COM birlikte çalışma tarafından oluşturulan bir arabirim) sürüm oluşturma kısıtlamalarına tabidir.</span><span class="sxs-lookup"><span data-stu-id="9a740-110">Managed classes that implement the class interface (a COM interop-generated interface) are subject to versioning restrictions.</span></span>

  <span data-ttu-id="9a740-111">Sınıf arabirimini kullanma hakkında yönergeler için bkz. [sınıf arabirimine giriş](../../../docs/standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface).</span><span class="sxs-lookup"><span data-stu-id="9a740-111">For guidelines on using the class interface, see [Introducing the class interface](../../../docs/standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface).</span></span>

- <span data-ttu-id="9a740-112">Dağıtım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="9a740-112">Deployment instructions</span></span>

  <span data-ttu-id="9a740-113">Yayımcı tarafından imzalanan tanımlayıcı adlandırılmış derlemeler, genel derleme önbelleğine yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="9a740-113">Strong-named assemblies that are signed by a publisher can be installed into the global assembly cache.</span></span> <span data-ttu-id="9a740-114">İmzasız derlemelerin Kullanıcı makinesine özel derlemeler olarak yüklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="9a740-114">Unsigned assemblies must be installed on the user's machine as private assemblies.</span></span>

  <span data-ttu-id="9a740-115">Daha fazla bilgi için bkz. [bütünleştirilmiş kod güvenliği konuları](../app-domains/assembly-security-considerations.md).</span><span class="sxs-lookup"><span data-stu-id="9a740-115">For additional information, see [Assembly Security Considerations](../app-domains/assembly-security-considerations.md).</span></span>

- <span data-ttu-id="9a740-116">Tür kitaplığı ekleme</span><span class="sxs-lookup"><span data-stu-id="9a740-116">Type library inclusion</span></span>

  <span data-ttu-id="9a740-117">Çoğu tür bir COM uygulaması tarafından tüketilirken bir tür kitaplığı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="9a740-117">Most types require a type library when consumed by a COM application.</span></span> <span data-ttu-id="9a740-118">Bir tür kitaplığı oluşturabilir veya COM geliştiricilerinin bu görevi gerçekleştirmesini sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a740-118">You can generate a type library or have COM developers perform this task.</span></span> <span data-ttu-id="9a740-119">Windows SDK, bir tür kitaplığı oluşturmak için aşağıdaki seçenekleri sağlar:</span><span class="sxs-lookup"><span data-stu-id="9a740-119">The Windows SDK provides the following options for generating a type library:</span></span>

  - [<span data-ttu-id="9a740-120">Tür kitaplığı verme programı</span><span class="sxs-lookup"><span data-stu-id="9a740-120">Type Library Exporter</span></span>](#cpconpackagingassemblyforcomanchor1)

  - [<span data-ttu-id="9a740-121">TypeLibConverter sınıfı</span><span class="sxs-lookup"><span data-stu-id="9a740-121">TypeLibConverter Class</span></span>](#cpconpackagingassemblyforcomanchor2)

  - [<span data-ttu-id="9a740-122">Derleme Kayıt Aracı</span><span class="sxs-lookup"><span data-stu-id="9a740-122">Assembly Registration Tool</span></span>](#cpconpackagingassemblyforcomanchor3)

  - [<span data-ttu-id="9a740-123">.NET Hizmetleri Yükleme Aracı</span><span class="sxs-lookup"><span data-stu-id="9a740-123">.NET Services Installation Tool</span></span>](#cpconpackagingassemblyforcomanchor4)

  <span data-ttu-id="9a740-124">Seçtiğiniz mekanizmaya bakılmaksızın, yalnızca sağladığınız derlemede tanımlanan ortak türler oluşturulan tür kitaplığına dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="9a740-124">Regardless of the mechanism you choose, only public types defined in the assembly you supply are included in the generated type library.</span></span>

<span data-ttu-id="9a740-125">Yönergeler için bkz [. nasıl yapılır: Tür kitaplıklarını ' de Win32 kaynakları olarak ekleyin. NET tabanlı uygulamalar](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="9a740-125">For instructions, see [How to: Embed Type Libraries as Win32 Resources in .NET-Based Applications](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100)).</span></span>

<a name="cpconpackagingassemblyforcomanchor1"></a>

## <a name="type-library-exporter"></a><span data-ttu-id="9a740-126">Tür Kitaplığı Dışarı Aktarıcı</span><span class="sxs-lookup"><span data-stu-id="9a740-126">Type Library Exporter</span></span>

<span data-ttu-id="9a740-127">[Tür kitaplığı verme programı (Tlbexp. exe)](../tools/tlbexp-exe-type-library-exporter.md) , bir derlemede bulunan sınıfları ve arabirimleri com tür kitaplığına dönüştüren bir komut satırı aracıdır.</span><span class="sxs-lookup"><span data-stu-id="9a740-127">The [Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md) is a command-line tool that converts the classes and interfaces contained in an assembly to a COM type library.</span></span> <span data-ttu-id="9a740-128">Sınıfın tür bilgileri kullanılabilir olduğunda, COM istemcileri .NET sınıfının bir örneğini oluşturabilir ve tıpkı bir COM nesnesi gibi, örneğin yöntemlerini çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="9a740-128">Once the type information of the class is available, COM clients can create an instance of the .NET class and call the methods of the instance, just as if it were a COM object.</span></span> <span data-ttu-id="9a740-129">Tlbexp. exe bir derlemeyi tek seferde dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="9a740-129">Tlbexp.exe converts an entire assembly at one time.</span></span> <span data-ttu-id="9a740-130">Derlemede tanımlanan türlerin bir alt kümesi için tür bilgisi üretmek üzere Tlbexp.exe'yi kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="9a740-130">You cannot use Tlbexp.exe to generate type information for a subset of the types defined in an assembly.</span></span>

<a name="cpconpackagingassemblyforcomanchor2"></a>

## <a name="typelibconverter-class"></a><span data-ttu-id="9a740-131">TypeLibConverter sınıfı</span><span class="sxs-lookup"><span data-stu-id="9a740-131">TypeLibConverter Class</span></span>

<span data-ttu-id="9a740-132">**System. Runtime. Interop** ad alanında bulunan sınıfı,birderlemedebulunansınıflarıvearabirimleribircomtürkitaplığınadönüştürür.<xref:System.Runtime.InteropServices.TypeLibConverter></span><span class="sxs-lookup"><span data-stu-id="9a740-132">The <xref:System.Runtime.InteropServices.TypeLibConverter> class, located in the **System.Runtime.Interop** namespace, converts the classes and interfaces contained in an assembly to a COM type library.</span></span> <span data-ttu-id="9a740-133">Bu API, önceki bölümde açıklanan tür kitaplığı verme programı ile aynı tür bilgilerini üretir.</span><span class="sxs-lookup"><span data-stu-id="9a740-133">This API produces the same type information as the Type Library Exporter, described in the previous section.</span></span>

<span data-ttu-id="9a740-134">**TypeLibConverter sınıfı** öğesini uygular <xref:System.Runtime.InteropServices.ITypeLibConverter>.</span><span class="sxs-lookup"><span data-stu-id="9a740-134">The **TypeLibConverter class** implements the <xref:System.Runtime.InteropServices.ITypeLibConverter>.</span></span>

<a name="cpconpackagingassemblyforcomanchor3"></a>

## <a name="assembly-registration-tool"></a><span data-ttu-id="9a740-135">Derleme Kayıt Aracı</span><span class="sxs-lookup"><span data-stu-id="9a740-135">Assembly Registration Tool</span></span>

<span data-ttu-id="9a740-136">[Derleme Kayıt Aracı (Regasm. exe)](../tools/regasm-exe-assembly-registration-tool.md) , **/tlb:** seçeneğini uyguladığınızda bir tür kitaplığı oluşturup kaydedebilir.</span><span class="sxs-lookup"><span data-stu-id="9a740-136">The [Assembly Registration Tool (Regasm.exe)](../tools/regasm-exe-assembly-registration-tool.md) can generate and register a type library when you apply the **/tlb:** option.</span></span> <span data-ttu-id="9a740-137">COM istemcileri, tür kitaplıklarının Windows kayıt defteri 'nde yüklü olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="9a740-137">COM clients require that type libraries be installed in the Windows registry.</span></span> <span data-ttu-id="9a740-138">Bu seçenek olmadan, Regasm. exe türleri tür kitaplığına değil, yalnızca bir derlemeye kaydeder.</span><span class="sxs-lookup"><span data-stu-id="9a740-138">Without this option, Regasm.exe only registers the types in an assembly, not the type library.</span></span> <span data-ttu-id="9a740-139">Türlerin bir derlemeye kaydedilmesi ve tür kitaplığının kaydedilmesi ayrı etkinliklerdir.</span><span class="sxs-lookup"><span data-stu-id="9a740-139">Registering the types in an assembly and registering the type library are distinct activities.</span></span>

<a name="cpconpackagingassemblyforcomanchor4"></a>

## <a name="net-services-installation-tool"></a><span data-ttu-id="9a740-140">.NET Hizmetleri Yükleme Aracı</span><span class="sxs-lookup"><span data-stu-id="9a740-140">.NET Services Installation Tool</span></span>

<span data-ttu-id="9a740-141">[.Net Hizmetleri Yükleme Aracı (RegSvcs. exe)](../tools/regsvcs-exe-net-services-installation-tool.md) , Windows 2000 Bileşen hizmetlerine yönetilen sınıflar ekler ve tek bir araç içinde çeşitli görevleri birleştirir.</span><span class="sxs-lookup"><span data-stu-id="9a740-141">The [.NET Services Installation Tool (Regsvcs.exe)](../tools/regsvcs-exe-net-services-installation-tool.md) adds managed classes to Windows 2000 Component Services and combines several tasks within a single tool.</span></span> <span data-ttu-id="9a740-142">RegSvcs. exe, bir derlemeyi yüklemeye ve kaydetmeye ek olarak, tür kitaplığını var olan bir COM+ 1,0 uygulamasına oluşturabilir, kaydedebilir ve yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="9a740-142">In addition to loading and registering an assembly, Regsvcs.exe can generate, register, and install the type library into an existing COM+ 1.0 application.</span></span>

## <a name="see-also"></a><span data-ttu-id="9a740-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9a740-143">See also</span></span>

- <xref:System.Runtime.InteropServices.TypeLibConverter>
- <xref:System.Runtime.InteropServices.ITypeLibConverter>
- [<span data-ttu-id="9a740-144">.NET Framework Bileşenlerini COM'da Gösterme</span><span class="sxs-lookup"><span data-stu-id="9a740-144">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="9a740-145">Birlikte Çalışma için .NET Türlerini Niteleme</span><span class="sxs-lookup"><span data-stu-id="9a740-145">Qualifying .NET Types for Interoperation</span></span>](../../../docs/standard/native-interop/qualify-net-types-for-interoperation.md)
- [<span data-ttu-id="9a740-146">Sınıf arabirimine giriş</span><span class="sxs-lookup"><span data-stu-id="9a740-146">Introducing the class interface</span></span>](../../../docs/standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface)
- [<span data-ttu-id="9a740-147">Bütünleştirilmiş Kod Güvenliği Konuları</span><span class="sxs-lookup"><span data-stu-id="9a740-147">Assembly Security Considerations</span></span>](../app-domains/assembly-security-considerations.md)
- [<span data-ttu-id="9a740-148">Tlbexp.exe (Tür Kitaplığı Dışarı Aktarıcı)</span><span class="sxs-lookup"><span data-stu-id="9a740-148">Tlbexp.exe (Type Library Exporter)</span></span>](../tools/tlbexp-exe-type-library-exporter.md)
- [<span data-ttu-id="9a740-149">Bütünleştirilmiş Kodları COM ile Kaydetme</span><span class="sxs-lookup"><span data-stu-id="9a740-149">Registering Assemblies with COM</span></span>](registering-assemblies-with-com.md)
- <span data-ttu-id="9a740-150">[Nasıl yapılır: Tür kitaplıklarını uygulamalarda Win32 kaynakları olarak ekleme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9a740-150">[How to: Embed Type Libraries as Win32 Resources in Applications](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100))</span></span>

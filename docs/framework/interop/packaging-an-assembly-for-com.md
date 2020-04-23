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
ms.openlocfilehash: 6866da283cc7cdd180aada252007d67bd72cd862
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124091"
---
# <a name="packaging-a-net-framework-assembly-for-com"></a><span data-ttu-id="23463-102">COM için bir .NET Framework derlemesi paketleme</span><span class="sxs-lookup"><span data-stu-id="23463-102">Packaging a .NET Framework Assembly for COM</span></span>

<span data-ttu-id="23463-103">COM geliştiricileri, uygulamasında dahil etmek üzere plantıkları yönetilen türler hakkında aşağıdaki bilgilerden faydalanabilir:</span><span class="sxs-lookup"><span data-stu-id="23463-103">COM developers can benefit from the following information about the managed types they plan to incorporate in their application:</span></span>

- <span data-ttu-id="23463-104">COM uygulamalarının tüketebileceği türlerin listesi</span><span class="sxs-lookup"><span data-stu-id="23463-104">A list of types that COM applications can consume</span></span>

  <span data-ttu-id="23463-105">Bazı yönetilen türler COM 'a görünmez; Bazıları görünür ancak creatable değildir; ve bazıları hem görünür hem de creatable.</span><span class="sxs-lookup"><span data-stu-id="23463-105">Some managed types are invisible to COM; some are visible but not creatable; and some are both visible and creatable.</span></span> <span data-ttu-id="23463-106">Bir bütünleştirilmiş kod, görünmeyen, Visible, oluşturulabilir ve oluşturulabilir türlerinin herhangi bir birleşimini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="23463-106">An assembly can comprise any combination of invisible, visible, not creatable, and creatable types.</span></span> <span data-ttu-id="23463-107">Tamamlananlar için, özellikle bu türler .NET Framework gösterilen türlerin bir alt kümesi olduğunda, COM 'da kullanıma sunmayı planladığınız bir derlemede bulunan türleri yapın.</span><span class="sxs-lookup"><span data-stu-id="23463-107">For completeness, identify the types in an assembly that you intend to expose to COM, especially when those types are a subset of the types exposed to the .NET Framework.</span></span>

  <span data-ttu-id="23463-108">Daha fazla bilgi için bkz. [birlikte çalışma için .NET türlerini niteleme](../../standard/native-interop/qualify-net-types-for-interoperation.md).</span><span class="sxs-lookup"><span data-stu-id="23463-108">For additional information, see [Qualifying .NET Types for Interoperation](../../standard/native-interop/qualify-net-types-for-interoperation.md).</span></span>

- <span data-ttu-id="23463-109">Sürüm oluşturma yönergeleri</span><span class="sxs-lookup"><span data-stu-id="23463-109">Versioning instructions</span></span>

  <span data-ttu-id="23463-110">Sınıf arabirimini uygulayan yönetilen sınıflar (COM birlikte çalışma tarafından oluşturulan bir arabirim) sürüm oluşturma kısıtlamalarına tabidir.</span><span class="sxs-lookup"><span data-stu-id="23463-110">Managed classes that implement the class interface (a COM interop-generated interface) are subject to versioning restrictions.</span></span>

  <span data-ttu-id="23463-111">Sınıf arabirimini kullanma hakkında yönergeler için bkz. [sınıf arabirimine giriş](../../standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface).</span><span class="sxs-lookup"><span data-stu-id="23463-111">For guidelines on using the class interface, see [Introducing the class interface](../../standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface).</span></span>

- <span data-ttu-id="23463-112">Dağıtım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="23463-112">Deployment instructions</span></span>

  <span data-ttu-id="23463-113">Yayımcı tarafından imzalanan tanımlayıcı adlandırılmış derlemeler, genel derleme önbelleğine yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="23463-113">Strong-named assemblies that are signed by a publisher can be installed into the global assembly cache.</span></span> <span data-ttu-id="23463-114">İmzasız derlemelerin Kullanıcı makinesine özel derlemeler olarak yüklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="23463-114">Unsigned assemblies must be installed on the user's machine as private assemblies.</span></span>

  <span data-ttu-id="23463-115">Daha fazla bilgi için bkz. [bütünleştirilmiş kod güvenliği konuları](../../standard/assembly/security-considerations.md).</span><span class="sxs-lookup"><span data-stu-id="23463-115">For additional information, see [Assembly Security Considerations](../../standard/assembly/security-considerations.md).</span></span>

- <span data-ttu-id="23463-116">Tür kitaplığı ekleme</span><span class="sxs-lookup"><span data-stu-id="23463-116">Type library inclusion</span></span>

  <span data-ttu-id="23463-117">Çoğu tür bir COM uygulaması tarafından tüketilirken bir tür kitaplığı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="23463-117">Most types require a type library when consumed by a COM application.</span></span> <span data-ttu-id="23463-118">Bir tür kitaplığı oluşturabilir veya COM geliştiricilerinin bu görevi gerçekleştirmesini sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="23463-118">You can generate a type library or have COM developers perform this task.</span></span> <span data-ttu-id="23463-119">Windows SDK, bir tür kitaplığı oluşturmak için aşağıdaki seçenekleri sağlar:</span><span class="sxs-lookup"><span data-stu-id="23463-119">The Windows SDK provides the following options for generating a type library:</span></span>

  - [<span data-ttu-id="23463-120">Tür Kitaplığı Dışarı Aktarıcı</span><span class="sxs-lookup"><span data-stu-id="23463-120">Type Library Exporter</span></span>](#cpconpackagingassemblyforcomanchor1)

  - [<span data-ttu-id="23463-121">TypeLibConverter sınıfı</span><span class="sxs-lookup"><span data-stu-id="23463-121">TypeLibConverter Class</span></span>](#cpconpackagingassemblyforcomanchor2)

  - [<span data-ttu-id="23463-122">Derleme Kayıt Aracı</span><span class="sxs-lookup"><span data-stu-id="23463-122">Assembly Registration Tool</span></span>](#cpconpackagingassemblyforcomanchor3)

  - [<span data-ttu-id="23463-123">.NET Hizmetleri Yükleme Aracı</span><span class="sxs-lookup"><span data-stu-id="23463-123">.NET Services Installation Tool</span></span>](#cpconpackagingassemblyforcomanchor4)

  <span data-ttu-id="23463-124">Seçtiğiniz mekanizmaya bakılmaksızın, yalnızca sağladığınız derlemede tanımlanan ortak türler oluşturulan tür kitaplığına dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="23463-124">Regardless of the mechanism you choose, only public types defined in the assembly you supply are included in the generated type library.</span></span>

<span data-ttu-id="23463-125">Yönergeler için bkz [. nasıl yapılır: tür kitaplıklarını Win32 kaynakları olarak ekleme. NET tabanlı uygulamalar](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="23463-125">For instructions, see [How to: Embed Type Libraries as Win32 Resources in .NET-Based Applications](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100)).</span></span>

<a name="cpconpackagingassemblyforcomanchor1"></a>

## <a name="type-library-exporter"></a><span data-ttu-id="23463-126">Tür Kitaplığı Dışarı Aktarıcı</span><span class="sxs-lookup"><span data-stu-id="23463-126">Type Library Exporter</span></span>

<span data-ttu-id="23463-127">[Tür kitaplığı verme programı (Tlbexp. exe)](../tools/tlbexp-exe-type-library-exporter.md) , bir derlemede bulunan sınıfları ve arabirimleri com tür kitaplığına dönüştüren bir komut satırı aracıdır.</span><span class="sxs-lookup"><span data-stu-id="23463-127">The [Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md) is a command-line tool that converts the classes and interfaces contained in an assembly to a COM type library.</span></span> <span data-ttu-id="23463-128">Sınıfın tür bilgileri kullanılabilir olduğunda, COM istemcileri .NET sınıfının bir örneğini oluşturabilir ve tıpkı bir COM nesnesi gibi, örneğin yöntemlerini çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="23463-128">Once the type information of the class is available, COM clients can create an instance of the .NET class and call the methods of the instance, just as if it were a COM object.</span></span> <span data-ttu-id="23463-129">Tlbexp. exe bir derlemeyi tek seferde dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="23463-129">Tlbexp.exe converts an entire assembly at one time.</span></span> <span data-ttu-id="23463-130">Derlemede tanımlanan türlerin bir alt kümesi için tür bilgisi üretmek üzere Tlbexp.exe'yi kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="23463-130">You cannot use Tlbexp.exe to generate type information for a subset of the types defined in an assembly.</span></span>

<a name="cpconpackagingassemblyforcomanchor2"></a>

## <a name="typelibconverter-class"></a><span data-ttu-id="23463-131">TypeLibConverter sınıfı</span><span class="sxs-lookup"><span data-stu-id="23463-131">TypeLibConverter Class</span></span>

<span data-ttu-id="23463-132"><xref:System.Runtime.InteropServices.TypeLibConverter> **System. Runtime. Interop** ad alanında bulunan sınıfı, bir derlemede bulunan SıNıFLARı ve arabirimleri bir com tür kitaplığına dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="23463-132">The <xref:System.Runtime.InteropServices.TypeLibConverter> class, located in the **System.Runtime.Interop** namespace, converts the classes and interfaces contained in an assembly to a COM type library.</span></span> <span data-ttu-id="23463-133">Bu API, önceki bölümde açıklanan tür kitaplığı verme programı ile aynı tür bilgilerini üretir.</span><span class="sxs-lookup"><span data-stu-id="23463-133">This API produces the same type information as the Type Library Exporter, described in the previous section.</span></span>

<span data-ttu-id="23463-134">**TypeLibConverter sınıfı** öğesini uygular <xref:System.Runtime.InteropServices.ITypeLibConverter>.</span><span class="sxs-lookup"><span data-stu-id="23463-134">The **TypeLibConverter class** implements the <xref:System.Runtime.InteropServices.ITypeLibConverter>.</span></span>

<a name="cpconpackagingassemblyforcomanchor3"></a>

## <a name="assembly-registration-tool"></a><span data-ttu-id="23463-135">Derleme Kayıt Aracı</span><span class="sxs-lookup"><span data-stu-id="23463-135">Assembly Registration Tool</span></span>

<span data-ttu-id="23463-136">[Derleme Kayıt Aracı (Regasm. exe)](../tools/regasm-exe-assembly-registration-tool.md) , **/tlb:** seçeneğini uyguladığınızda bir tür kitaplığı oluşturup kaydedebilir.</span><span class="sxs-lookup"><span data-stu-id="23463-136">The [Assembly Registration Tool (Regasm.exe)](../tools/regasm-exe-assembly-registration-tool.md) can generate and register a type library when you apply the **/tlb:** option.</span></span> <span data-ttu-id="23463-137">COM istemcileri, tür kitaplıklarının Windows kayıt defteri 'nde yüklü olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="23463-137">COM clients require that type libraries be installed in the Windows registry.</span></span> <span data-ttu-id="23463-138">Bu seçenek olmadan, Regasm. exe türleri tür kitaplığına değil, yalnızca bir derlemeye kaydeder.</span><span class="sxs-lookup"><span data-stu-id="23463-138">Without this option, Regasm.exe only registers the types in an assembly, not the type library.</span></span> <span data-ttu-id="23463-139">Türlerin bir derlemeye kaydedilmesi ve tür kitaplığının kaydedilmesi ayrı etkinliklerdir.</span><span class="sxs-lookup"><span data-stu-id="23463-139">Registering the types in an assembly and registering the type library are distinct activities.</span></span>

<a name="cpconpackagingassemblyforcomanchor4"></a>

## <a name="net-services-installation-tool"></a><span data-ttu-id="23463-140">.NET Hizmetleri Yükleme Aracı</span><span class="sxs-lookup"><span data-stu-id="23463-140">.NET Services Installation Tool</span></span>

<span data-ttu-id="23463-141">[.Net Hizmetleri Yükleme Aracı (RegSvcs. exe)](../tools/regsvcs-exe-net-services-installation-tool.md) , Windows 2000 Bileşen hizmetlerine yönetilen sınıflar ekler ve tek bir araç içinde çeşitli görevleri birleştirir.</span><span class="sxs-lookup"><span data-stu-id="23463-141">The [.NET Services Installation Tool (Regsvcs.exe)](../tools/regsvcs-exe-net-services-installation-tool.md) adds managed classes to Windows 2000 Component Services and combines several tasks within a single tool.</span></span> <span data-ttu-id="23463-142">RegSvcs. exe, bir derlemeyi yüklemeye ve kaydetmeye ek olarak, tür kitaplığını var olan bir COM+ 1,0 uygulamasına oluşturabilir, kaydedebilir ve yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="23463-142">In addition to loading and registering an assembly, Regsvcs.exe can generate, register, and install the type library into an existing COM+ 1.0 application.</span></span>

## <a name="see-also"></a><span data-ttu-id="23463-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="23463-143">See also</span></span>

- <xref:System.Runtime.InteropServices.TypeLibConverter>
- <xref:System.Runtime.InteropServices.ITypeLibConverter>
- [<span data-ttu-id="23463-144">.NET Framework Bileşenlerini COM'da Gösterme</span><span class="sxs-lookup"><span data-stu-id="23463-144">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="23463-145">Birlikte Çalışma için Niteleyici .NET Türleri</span><span class="sxs-lookup"><span data-stu-id="23463-145">Qualifying .NET Types for Interoperation</span></span>](../../standard/native-interop/qualify-net-types-for-interoperation.md)
- [<span data-ttu-id="23463-146">Sınıf arabirimine giriş</span><span class="sxs-lookup"><span data-stu-id="23463-146">Introducing the class interface</span></span>](../../standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface)
- [<span data-ttu-id="23463-147">Bütünleştirilmiş kod güvenliği konuları</span><span class="sxs-lookup"><span data-stu-id="23463-147">Assembly Security Considerations</span></span>](../../standard/assembly/security-considerations.md)
- [<span data-ttu-id="23463-148">Tlbexp. exe (tür kitaplığı Dışarı Aktarıcı)</span><span class="sxs-lookup"><span data-stu-id="23463-148">Tlbexp.exe (Type Library Exporter)</span></span>](../tools/tlbexp-exe-type-library-exporter.md)
- [<span data-ttu-id="23463-149">Derlemeleri COM ile Kaydetme</span><span class="sxs-lookup"><span data-stu-id="23463-149">Registering Assemblies with COM</span></span>](registering-assemblies-with-com.md)
- <span data-ttu-id="23463-150">[Nasıl yapılır: uygulamalarda tür kitaplıklarını Win32 kaynakları olarak katıştırma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="23463-150">[How to: Embed Type Libraries as Win32 Resources in Applications](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100))</span></span>

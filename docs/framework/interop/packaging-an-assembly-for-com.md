---
title: COM için bir .NET Framework derlemesi paketleme
description: COM için bir .NET derlemesi paketleyin. COM uygulamalarının tüketebileceği türlerin listesini, sürüm oluşturmayı ve dağıtım yönergelerini ve tür kitaplığını toplayın.
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
ms.openlocfilehash: 4963892419fd1caec4483123f820d62967a87dd6
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620839"
---
# <a name="packaging-a-net-framework-assembly-for-com"></a><span data-ttu-id="83ed3-104">COM için bir .NET Framework derlemesi paketleme</span><span class="sxs-lookup"><span data-stu-id="83ed3-104">Packaging a .NET Framework Assembly for COM</span></span>

<span data-ttu-id="83ed3-105">COM geliştiricileri, uygulamasında dahil etmek üzere plantıkları yönetilen türler hakkında aşağıdaki bilgilerden faydalanabilir:</span><span class="sxs-lookup"><span data-stu-id="83ed3-105">COM developers can benefit from the following information about the managed types they plan to incorporate in their application:</span></span>

- <span data-ttu-id="83ed3-106">COM uygulamalarının tüketebileceği türlerin listesi</span><span class="sxs-lookup"><span data-stu-id="83ed3-106">A list of types that COM applications can consume</span></span>

  <span data-ttu-id="83ed3-107">Bazı yönetilen türler COM 'a görünmez; Bazıları görünür ancak creatable değildir; ve bazıları hem görünür hem de creatable.</span><span class="sxs-lookup"><span data-stu-id="83ed3-107">Some managed types are invisible to COM; some are visible but not creatable; and some are both visible and creatable.</span></span> <span data-ttu-id="83ed3-108">Bir bütünleştirilmiş kod, görünmeyen, Visible, oluşturulabilir ve oluşturulabilir türlerinin herhangi bir birleşimini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="83ed3-108">An assembly can comprise any combination of invisible, visible, not creatable, and creatable types.</span></span> <span data-ttu-id="83ed3-109">Tamamlananlar için, özellikle bu türler .NET Framework gösterilen türlerin bir alt kümesi olduğunda, COM 'da kullanıma sunmayı planladığınız bir derlemede bulunan türleri yapın.</span><span class="sxs-lookup"><span data-stu-id="83ed3-109">For completeness, identify the types in an assembly that you intend to expose to COM, especially when those types are a subset of the types exposed to the .NET Framework.</span></span>

  <span data-ttu-id="83ed3-110">Daha fazla bilgi için bkz. [birlikte çalışma için .NET türlerini niteleme](../../standard/native-interop/qualify-net-types-for-interoperation.md).</span><span class="sxs-lookup"><span data-stu-id="83ed3-110">For additional information, see [Qualifying .NET Types for Interoperation](../../standard/native-interop/qualify-net-types-for-interoperation.md).</span></span>

- <span data-ttu-id="83ed3-111">Sürüm oluşturma yönergeleri</span><span class="sxs-lookup"><span data-stu-id="83ed3-111">Versioning instructions</span></span>

  <span data-ttu-id="83ed3-112">Sınıf arabirimini uygulayan yönetilen sınıflar (COM birlikte çalışma tarafından oluşturulan bir arabirim) sürüm oluşturma kısıtlamalarına tabidir.</span><span class="sxs-lookup"><span data-stu-id="83ed3-112">Managed classes that implement the class interface (a COM interop-generated interface) are subject to versioning restrictions.</span></span>

  <span data-ttu-id="83ed3-113">Sınıf arabirimini kullanma hakkında yönergeler için bkz. [sınıf arabirimine giriş](../../standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface).</span><span class="sxs-lookup"><span data-stu-id="83ed3-113">For guidelines on using the class interface, see [Introducing the class interface](../../standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface).</span></span>

- <span data-ttu-id="83ed3-114">Dağıtım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="83ed3-114">Deployment instructions</span></span>

  <span data-ttu-id="83ed3-115">Yayımcı tarafından imzalanan tanımlayıcı adlandırılmış derlemeler, genel derleme önbelleğine yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="83ed3-115">Strong-named assemblies that are signed by a publisher can be installed into the global assembly cache.</span></span> <span data-ttu-id="83ed3-116">İmzasız derlemelerin Kullanıcı makinesine özel derlemeler olarak yüklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="83ed3-116">Unsigned assemblies must be installed on the user's machine as private assemblies.</span></span>

  <span data-ttu-id="83ed3-117">Daha fazla bilgi için bkz. [bütünleştirilmiş kod güvenliği konuları](../../standard/assembly/security-considerations.md).</span><span class="sxs-lookup"><span data-stu-id="83ed3-117">For additional information, see [Assembly Security Considerations](../../standard/assembly/security-considerations.md).</span></span>

- <span data-ttu-id="83ed3-118">Tür kitaplığı ekleme</span><span class="sxs-lookup"><span data-stu-id="83ed3-118">Type library inclusion</span></span>

  <span data-ttu-id="83ed3-119">Çoğu tür bir COM uygulaması tarafından tüketilirken bir tür kitaplığı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="83ed3-119">Most types require a type library when consumed by a COM application.</span></span> <span data-ttu-id="83ed3-120">Bir tür kitaplığı oluşturabilir veya COM geliştiricilerinin bu görevi gerçekleştirmesini sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="83ed3-120">You can generate a type library or have COM developers perform this task.</span></span> <span data-ttu-id="83ed3-121">Windows SDK, bir tür kitaplığı oluşturmak için aşağıdaki seçenekleri sağlar:</span><span class="sxs-lookup"><span data-stu-id="83ed3-121">The Windows SDK provides the following options for generating a type library:</span></span>

  - [<span data-ttu-id="83ed3-122">Tür Kitaplığı Dışarı Aktarıcı</span><span class="sxs-lookup"><span data-stu-id="83ed3-122">Type Library Exporter</span></span>](#cpconpackagingassemblyforcomanchor1)

  - [<span data-ttu-id="83ed3-123">TypeLibConverter sınıfı</span><span class="sxs-lookup"><span data-stu-id="83ed3-123">TypeLibConverter Class</span></span>](#cpconpackagingassemblyforcomanchor2)

  - [<span data-ttu-id="83ed3-124">Derleme Kayıt Aracı</span><span class="sxs-lookup"><span data-stu-id="83ed3-124">Assembly Registration Tool</span></span>](#cpconpackagingassemblyforcomanchor3)

  - [<span data-ttu-id="83ed3-125">.NET Hizmetleri Yükleme Aracı</span><span class="sxs-lookup"><span data-stu-id="83ed3-125">.NET Services Installation Tool</span></span>](#cpconpackagingassemblyforcomanchor4)

  <span data-ttu-id="83ed3-126">Seçtiğiniz mekanizmaya bakılmaksızın, yalnızca sağladığınız derlemede tanımlanan ortak türler oluşturulan tür kitaplığına dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="83ed3-126">Regardless of the mechanism you choose, only public types defined in the assembly you supply are included in the generated type library.</span></span>

<span data-ttu-id="83ed3-127">Yönergeler için bkz [. nasıl yapılır: tür kitaplıklarını Win32 kaynakları olarak ekleme. NET tabanlı uygulamalar](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="83ed3-127">For instructions, see [How to: Embed Type Libraries as Win32 Resources in .NET-Based Applications](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100)).</span></span>

<a name="cpconpackagingassemblyforcomanchor1"></a>

## <a name="type-library-exporter"></a><span data-ttu-id="83ed3-128">Tür Kitaplığı Dışarı Aktarıcı</span><span class="sxs-lookup"><span data-stu-id="83ed3-128">Type Library Exporter</span></span>

<span data-ttu-id="83ed3-129">[Tür kitaplığı verme programı (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md) , bir derlemede bulunan sınıfları ve arabirimleri com tür kitaplığına dönüştüren bir komut satırı aracıdır.</span><span class="sxs-lookup"><span data-stu-id="83ed3-129">The [Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md) is a command-line tool that converts the classes and interfaces contained in an assembly to a COM type library.</span></span> <span data-ttu-id="83ed3-130">Sınıfın tür bilgileri kullanılabilir olduğunda, COM istemcileri .NET sınıfının bir örneğini oluşturabilir ve tıpkı bir COM nesnesi gibi, örneğin yöntemlerini çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="83ed3-130">Once the type information of the class is available, COM clients can create an instance of the .NET class and call the methods of the instance, just as if it were a COM object.</span></span> <span data-ttu-id="83ed3-131">Tlbexp.exe tüm derlemeyi tek seferde dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="83ed3-131">Tlbexp.exe converts an entire assembly at one time.</span></span> <span data-ttu-id="83ed3-132">Derlemede tanımlanan türlerin bir alt kümesi için tür bilgisi üretmek üzere Tlbexp.exe'yi kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="83ed3-132">You cannot use Tlbexp.exe to generate type information for a subset of the types defined in an assembly.</span></span>

<a name="cpconpackagingassemblyforcomanchor2"></a>

## <a name="typelibconverter-class"></a><span data-ttu-id="83ed3-133">TypeLibConverter sınıfı</span><span class="sxs-lookup"><span data-stu-id="83ed3-133">TypeLibConverter Class</span></span>

<span data-ttu-id="83ed3-134"><xref:System.Runtime.InteropServices.TypeLibConverter> **System. Runtime. Interop** ad alanında bulunan sınıfı, bir derlemede bulunan sınıfları ve arabirimleri bir com tür kitaplığına dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="83ed3-134">The <xref:System.Runtime.InteropServices.TypeLibConverter> class, located in the **System.Runtime.Interop** namespace, converts the classes and interfaces contained in an assembly to a COM type library.</span></span> <span data-ttu-id="83ed3-135">Bu API, önceki bölümde açıklanan tür kitaplığı verme programı ile aynı tür bilgilerini üretir.</span><span class="sxs-lookup"><span data-stu-id="83ed3-135">This API produces the same type information as the Type Library Exporter, described in the previous section.</span></span>

<span data-ttu-id="83ed3-136">**TypeLibConverter sınıfı** öğesini uygular <xref:System.Runtime.InteropServices.ITypeLibConverter> .</span><span class="sxs-lookup"><span data-stu-id="83ed3-136">The **TypeLibConverter class** implements the <xref:System.Runtime.InteropServices.ITypeLibConverter>.</span></span>

<a name="cpconpackagingassemblyforcomanchor3"></a>

## <a name="assembly-registration-tool"></a><span data-ttu-id="83ed3-137">Derleme Kayıt Aracı</span><span class="sxs-lookup"><span data-stu-id="83ed3-137">Assembly Registration Tool</span></span>

<span data-ttu-id="83ed3-138">[Derleme Kayıt Aracı (Regasm.exe)](../tools/regasm-exe-assembly-registration-tool.md) , **/tlb:** seçeneğini uyguladığınızda bir tür kitaplığı oluşturabilir ve kaydedebilir.</span><span class="sxs-lookup"><span data-stu-id="83ed3-138">The [Assembly Registration Tool (Regasm.exe)](../tools/regasm-exe-assembly-registration-tool.md) can generate and register a type library when you apply the **/tlb:** option.</span></span> <span data-ttu-id="83ed3-139">COM istemcileri, tür kitaplıklarının Windows kayıt defteri 'nde yüklü olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="83ed3-139">COM clients require that type libraries be installed in the Windows registry.</span></span> <span data-ttu-id="83ed3-140">Bu seçenek olmadan Regasm.exe, türleri tür kitaplığına değil, yalnızca bir derlemeye kaydeder.</span><span class="sxs-lookup"><span data-stu-id="83ed3-140">Without this option, Regasm.exe only registers the types in an assembly, not the type library.</span></span> <span data-ttu-id="83ed3-141">Türlerin bir derlemeye kaydedilmesi ve tür kitaplığının kaydedilmesi ayrı etkinliklerdir.</span><span class="sxs-lookup"><span data-stu-id="83ed3-141">Registering the types in an assembly and registering the type library are distinct activities.</span></span>

<a name="cpconpackagingassemblyforcomanchor4"></a>

## <a name="net-services-installation-tool"></a><span data-ttu-id="83ed3-142">.NET Hizmetleri Yükleme Aracı</span><span class="sxs-lookup"><span data-stu-id="83ed3-142">.NET Services Installation Tool</span></span>

<span data-ttu-id="83ed3-143">[.Net Hizmetleri Yükleme Aracı (Regsvcs.exe)](../tools/regsvcs-exe-net-services-installation-tool.md) , Windows 2000 Bileşen hizmetlerine yönetilen sınıflar ekler ve tek bir araç içinde birkaç görevi birleştirir.</span><span class="sxs-lookup"><span data-stu-id="83ed3-143">The [.NET Services Installation Tool (Regsvcs.exe)](../tools/regsvcs-exe-net-services-installation-tool.md) adds managed classes to Windows 2000 Component Services and combines several tasks within a single tool.</span></span> <span data-ttu-id="83ed3-144">Regsvcs.exe bir derlemeyi yüklemeye ve kaydetmeye ek olarak, tür kitaplığını var olan bir COM+ 1,0 uygulamasına oluşturabilir, kaydedebilir ve yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="83ed3-144">In addition to loading and registering an assembly, Regsvcs.exe can generate, register, and install the type library into an existing COM+ 1.0 application.</span></span>

## <a name="see-also"></a><span data-ttu-id="83ed3-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="83ed3-145">See also</span></span>

- <xref:System.Runtime.InteropServices.TypeLibConverter>
- <xref:System.Runtime.InteropServices.ITypeLibConverter>
- [<span data-ttu-id="83ed3-146">.NET Framework Bileşenlerini COM'da Gösterme</span><span class="sxs-lookup"><span data-stu-id="83ed3-146">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="83ed3-147">Birlikte Çalışma için Niteleyici .NET Türleri</span><span class="sxs-lookup"><span data-stu-id="83ed3-147">Qualifying .NET Types for Interoperation</span></span>](../../standard/native-interop/qualify-net-types-for-interoperation.md)
- [<span data-ttu-id="83ed3-148">Sınıf arabirimine giriş</span><span class="sxs-lookup"><span data-stu-id="83ed3-148">Introducing the class interface</span></span>](../../standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface)
- [<span data-ttu-id="83ed3-149">Bütünleştirilmiş kod güvenliği konuları</span><span class="sxs-lookup"><span data-stu-id="83ed3-149">Assembly Security Considerations</span></span>](../../standard/assembly/security-considerations.md)
- [<span data-ttu-id="83ed3-150">Tlbexp.exe (tür kitaplığı verme programı)</span><span class="sxs-lookup"><span data-stu-id="83ed3-150">Tlbexp.exe (Type Library Exporter)</span></span>](../tools/tlbexp-exe-type-library-exporter.md)
- [<span data-ttu-id="83ed3-151">Derlemeleri COM ile Kaydetme</span><span class="sxs-lookup"><span data-stu-id="83ed3-151">Registering Assemblies with COM</span></span>](registering-assemblies-with-com.md)
- <span data-ttu-id="83ed3-152">[Nasıl yapılır: uygulamalarda tür kitaplıklarını Win32 kaynakları olarak katıştırma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="83ed3-152">[How to: Embed Type Libraries as Win32 Resources in Applications](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100))</span></span>

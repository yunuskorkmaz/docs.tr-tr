---
title: COM için Derlemeyi Paketleme
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
ms.openlocfilehash: 453ace4af7ce07c8d81b6d7ece71140e04bfa9bc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54531518"
---
# <a name="packaging-an-assembly-for-com"></a><span data-ttu-id="a9ae7-102">COM için Derlemeyi Paketleme</span><span class="sxs-lookup"><span data-stu-id="a9ae7-102">Packaging an Assembly for COM</span></span>
<span data-ttu-id="a9ae7-103">COM geliştiricilerin uygulamalarında birleştirmek planladıkları yönetilen türleri hakkında aşağıdaki bilgileri yararlı olabilir:</span><span class="sxs-lookup"><span data-stu-id="a9ae7-103">COM developers can benefit from the following information about the managed types they plan to incorporate in their application:</span></span>  
  
-   <span data-ttu-id="a9ae7-104">COM uygulamaları tüketebileceği türlerinin bir listesi</span><span class="sxs-lookup"><span data-stu-id="a9ae7-104">A list of types that COM applications can consume</span></span>  
  
     <span data-ttu-id="a9ae7-105">Bazı yönetilen türlerin, COM görünmez; Bazı görünür ancak değil; ve bazı görünür ve oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="a9ae7-105">Some managed types are invisible to COM; some are visible but not creatable; and some are both visible and creatable.</span></span> <span data-ttu-id="a9ae7-106">Derleme türleri görünmez, görünür değil ve oluşturulabilir herhangi bir birleşimini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="a9ae7-106">An assembly can comprise any combination of invisible, visible, not creatable, and creatable types.</span></span> <span data-ttu-id="a9ae7-107">Eksiksiz olması için özellikle bu türleri .NET Framework için kullanıma türlerin bir alt kümesi olduğunda, COM kullanıma sunmak istediğiniz derleme türlerini tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="a9ae7-107">For completeness, identify the types in an assembly that you intend to expose to COM, especially when those types are a subset of the types exposed to the .NET Framework.</span></span>  
  
     <span data-ttu-id="a9ae7-108">Ek bilgi için bkz: [birlikte çalışma için .NET türlerini niteleme](qualifying-net-types-for-interoperation.md).</span><span class="sxs-lookup"><span data-stu-id="a9ae7-108">For additional information, see [Qualifying .NET Types for Interoperation](qualifying-net-types-for-interoperation.md).</span></span>  
  
-   <span data-ttu-id="a9ae7-109">Sürüm oluşturma yönergeleri</span><span class="sxs-lookup"><span data-stu-id="a9ae7-109">Versioning instructions</span></span>  
  
     <span data-ttu-id="a9ae7-110">(Bir COM birlikte çalışma tarafından üretilen arabirimi) sınıf arabirimi uygulayan yönetilen sınıflar, sürüm oluşturma kısıtlamalar geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="a9ae7-110">Managed classes that implement the class interface (a COM interop-generated interface) are subject to versioning restrictions.</span></span>  
  
     <span data-ttu-id="a9ae7-111">Sınıf arabirimi kullanma ile ilgili yönergeler için bkz: [sınıf arabirimine giriş](com-callable-wrapper.md#introducing-the-class-interface).</span><span class="sxs-lookup"><span data-stu-id="a9ae7-111">For guidelines on using the class interface, see [Introducing the class interface](com-callable-wrapper.md#introducing-the-class-interface).</span></span>  
  
-   <span data-ttu-id="a9ae7-112">Dağıtım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="a9ae7-112">Deployment instructions</span></span>  
  
     <span data-ttu-id="a9ae7-113">Bir yayımcı tarafından imzalanmış tanımlayıcı adlandırılmış derlemeler genel derleme önbelleğine yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="a9ae7-113">Strong-named assemblies that are signed by a publisher can be installed into the global assembly cache.</span></span> <span data-ttu-id="a9ae7-114">İmzasız derlemeler kullanıcının makinesine özel derlemeler yüklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="a9ae7-114">Unsigned assemblies must be installed on the user's machine as private assemblies.</span></span>  
  
     <span data-ttu-id="a9ae7-115">Ek bilgi için bkz: [derleme güvenlik konuları](../app-domains/assembly-security-considerations.md).</span><span class="sxs-lookup"><span data-stu-id="a9ae7-115">For additional information, see [Assembly Security Considerations](../app-domains/assembly-security-considerations.md).</span></span>  
  
-   <span data-ttu-id="a9ae7-116">Tür kitaplığı ekleme</span><span class="sxs-lookup"><span data-stu-id="a9ae7-116">Type library inclusion</span></span>  
  
     <span data-ttu-id="a9ae7-117">Çoğu türleri COM uygulama tarafından kullanılan, bir tür kitaplığı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="a9ae7-117">Most types require a type library when consumed by a COM application.</span></span> <span data-ttu-id="a9ae7-118">Bir tür kitaplığı oluşturabilir veya bu görevi gerçekleştirmek COM geliştiriciler.</span><span class="sxs-lookup"><span data-stu-id="a9ae7-118">You can generate a type library or have COM developers perform this task.</span></span> <span data-ttu-id="a9ae7-119">[!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] Bir tür kitaplığı oluşturmak için aşağıdaki seçenekleri sağlar:</span><span class="sxs-lookup"><span data-stu-id="a9ae7-119">The [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] provides the following options for generating a type library:</span></span>  
  
    -   [<span data-ttu-id="a9ae7-120">Tür kitaplığı dışarı Aktarıcı</span><span class="sxs-lookup"><span data-stu-id="a9ae7-120">Type Library Exporter</span></span>](#cpconpackagingassemblyforcomanchor1)  
  
    -   [<span data-ttu-id="a9ae7-121">TypeLibConverter sınıfı</span><span class="sxs-lookup"><span data-stu-id="a9ae7-121">TypeLibConverter Class</span></span>](#cpconpackagingassemblyforcomanchor2)  
  
    -   [<span data-ttu-id="a9ae7-122">Derleme kayıt aracı</span><span class="sxs-lookup"><span data-stu-id="a9ae7-122">Assembly Registration Tool</span></span>](#cpconpackagingassemblyforcomanchor3)  
  
    -   [<span data-ttu-id="a9ae7-123">.NET Hizmetleri Yükleme aracı</span><span class="sxs-lookup"><span data-stu-id="a9ae7-123">.NET Services Installation Tool</span></span>](#cpconpackagingassemblyforcomanchor4)  
  
     <span data-ttu-id="a9ae7-124">Seçtiğiniz mekanizması bağımsız olarak, oluşturulan tür kitaplığı'nda yalnızca sağladığınız derlemede tanımlanan ortak türler dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="a9ae7-124">Regardless of the mechanism you choose, only public types defined in the assembly you supply are included in the generated type library.</span></span>  
  
     <span data-ttu-id="a9ae7-125">Ayrı bir dosya olarak bir tür kitaplığı paketi veya Win32 kaynak dosyası içinde olarak ekleme bir. AĞ tabanlı bir uygulama.</span><span class="sxs-lookup"><span data-stu-id="a9ae7-125">You can package a type library as a separate file or embed it as Win32 resource file within a .NET-based application.</span></span> <span data-ttu-id="a9ae7-126">Microsoft Visual Basic 6.0 bu işi sizin için otomatik olarak yapılır; Ancak, kullanırken [!INCLUDE[vbprvbext](../../../includes/vbprvbext-md.md)], tür kitaplığı el ile eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a9ae7-126">Microsoft Visual Basic 6.0 performed this task for you automatically; however, when using [!INCLUDE[vbprvbext](../../../includes/vbprvbext-md.md)], you must embed your type library manually.</span></span> <span data-ttu-id="a9ae7-127">Yönergeler için [nasıl yapılır: Tür kitaplıkları Win32 kaynakları olarak ekleyin. AĞ tabanlı uygulamalar](https://msdn.microsoft.com/library/c97b4b8c-2ab7-4ac7-8fc8-0ba5c5d59c44(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="a9ae7-127">For instructions, see [How to: Embed Type Libraries as Win32 Resources in .NET-Based Applications](https://msdn.microsoft.com/library/c97b4b8c-2ab7-4ac7-8fc8-0ba5c5d59c44(v=vs.100)).</span></span>  
  
<a name="cpconpackagingassemblyforcomanchor1"></a>   
## <a name="type-library-exporter"></a><span data-ttu-id="a9ae7-128">Tür Kitaplığı Dışarı Aktarıcı</span><span class="sxs-lookup"><span data-stu-id="a9ae7-128">Type Library Exporter</span></span>  
 <span data-ttu-id="a9ae7-129">[Tür kitaplığı dışarı Aktarıcı (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md) sınıflar ve arabirimler COM türü kitaplık bir derlemede yer alan dönüştürür bir komut satırı aracıdır.</span><span class="sxs-lookup"><span data-stu-id="a9ae7-129">The [Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md) is a command-line tool that converts the classes and interfaces contained in an assembly to a COM type library.</span></span> <span data-ttu-id="a9ae7-130">Sınıf türü bilgileri kullanılabilir olduğunda, COM istemcilerinin .NET sınıfının bir örneğini oluşturabilir ve bir COM nesnesi sanki olarak örnek yöntemlerini çağırmaya.</span><span class="sxs-lookup"><span data-stu-id="a9ae7-130">Once the type information of the class is available, COM clients can create an instance of the .NET class and call the methods of the instance, just as if it were a COM object.</span></span> <span data-ttu-id="a9ae7-131">Tlbexp.exe, tek seferde tüm bütünleştirilmiş dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="a9ae7-131">Tlbexp.exe converts an entire assembly at one time.</span></span> <span data-ttu-id="a9ae7-132">Derlemede tanımlanan türlerin bir alt kümesi için tür bilgisi üretmek üzere Tlbexp.exe'yi kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="a9ae7-132">You cannot use Tlbexp.exe to generate type information for a subset of the types defined in an assembly.</span></span>  
  
<a name="cpconpackagingassemblyforcomanchor2"></a>   
## <a name="typelibconverter-class"></a><span data-ttu-id="a9ae7-133">TypeLibConverter sınıfı</span><span class="sxs-lookup"><span data-stu-id="a9ae7-133">TypeLibConverter Class</span></span>  
 <span data-ttu-id="a9ae7-134"><xref:System.Runtime.InteropServices.TypeLibConverter> Bulunan sınıf **System.Runtime.Interop** ad alanı, sınıflar ve arabirimler COM türü kitaplık bir derlemede yer alan dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="a9ae7-134">The <xref:System.Runtime.InteropServices.TypeLibConverter> class, located in the **System.Runtime.Interop** namespace, converts the classes and interfaces contained in an assembly to a COM type library.</span></span> <span data-ttu-id="a9ae7-135">Bu API önceki bölümde açıklanan tür kitaplığı verici aynı tür bilgileri üretir.</span><span class="sxs-lookup"><span data-stu-id="a9ae7-135">This API produces the same type information as the Type Library Exporter, described in the previous section.</span></span>  
  
 <span data-ttu-id="a9ae7-136">**TypeLibConverter sınıfı** uygulayan <xref:System.Runtime.InteropServices.ITypeLibConverter>.</span><span class="sxs-lookup"><span data-stu-id="a9ae7-136">The **TypeLibConverter class** implements the <xref:System.Runtime.InteropServices.ITypeLibConverter>.</span></span>  
  
<a name="cpconpackagingassemblyforcomanchor3"></a>   
## <a name="assembly-registration-tool"></a><span data-ttu-id="a9ae7-137">Derleme kayıt aracı</span><span class="sxs-lookup"><span data-stu-id="a9ae7-137">Assembly Registration Tool</span></span>  
 <span data-ttu-id="a9ae7-138">[Derleme Kayıt Aracı (Regasm.exe)](../tools/regasm-exe-assembly-registration-tool.md) oluşturabilir ve uyguladığınızda, tür kitaplığını kaydetmek **/TLB:** seçeneği.</span><span class="sxs-lookup"><span data-stu-id="a9ae7-138">The [Assembly Registration Tool (Regasm.exe)](../tools/regasm-exe-assembly-registration-tool.md) can generate and register a type library when you apply the **/tlb:** option.</span></span> <span data-ttu-id="a9ae7-139">COM istemcileri Windows kayıt defterinde tür kitaplıkları yüklü olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="a9ae7-139">COM clients require that type libraries be installed in the Windows registry.</span></span> <span data-ttu-id="a9ae7-140">Bu seçenek olmadan, Regasm.exe türleri yalnızca bir derleme, tür kitaplığını kaydeder.</span><span class="sxs-lookup"><span data-stu-id="a9ae7-140">Without this option, Regasm.exe only registers the types in an assembly, not the type library.</span></span> <span data-ttu-id="a9ae7-141">Bir derlemede türlerini kaydetme ve tür kitaplığı kaydı ayrı etkinliklerdir.</span><span class="sxs-lookup"><span data-stu-id="a9ae7-141">Registering the types in an assembly and registering the type library are distinct activities.</span></span>  
  
<a name="cpconpackagingassemblyforcomanchor4"></a>   
## <a name="net-services-installation-tool"></a><span data-ttu-id="a9ae7-142">.NET Hizmetleri Yükleme aracı</span><span class="sxs-lookup"><span data-stu-id="a9ae7-142">.NET Services Installation Tool</span></span>  
 <span data-ttu-id="a9ae7-143">[.NET Hizmetleri Yükleme aracı (Regsvcs.exe)](../tools/regsvcs-exe-net-services-installation-tool.md) yönetilen sınıflar için Windows 2000 Bileşen Hizmetleri ekler ve tek bir araçla içindeki çeşitli görevleri birleştirir.</span><span class="sxs-lookup"><span data-stu-id="a9ae7-143">The [.NET Services Installation Tool (Regsvcs.exe)](../tools/regsvcs-exe-net-services-installation-tool.md) adds managed classes to Windows 2000 Component Services and combines several tasks within a single tool.</span></span> <span data-ttu-id="a9ae7-144">Yükleme ve derlemeyi kaydettirdikten ek olarak, Regsvcs.exe oluşturmak, kaydedin ve var olan bir COM + 1.0 uygulamasına tür kitaplığını yükleyin.</span><span class="sxs-lookup"><span data-stu-id="a9ae7-144">In addition to loading and registering an assembly, Regsvcs.exe can generate, register, and install the type library into an existing COM+ 1.0 application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9ae7-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a9ae7-145">See also</span></span>
- <xref:System.Runtime.InteropServices.TypeLibConverter>
- <xref:System.Runtime.InteropServices.ITypeLibConverter>
- [<span data-ttu-id="a9ae7-146">.NET Framework Bileşenlerini COM'da Gösterme</span><span class="sxs-lookup"><span data-stu-id="a9ae7-146">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="a9ae7-147">Birlikte Çalışma için .NET Türlerini Niteleme</span><span class="sxs-lookup"><span data-stu-id="a9ae7-147">Qualifying .NET Types for Interoperation</span></span>](qualifying-net-types-for-interoperation.md)
- [<span data-ttu-id="a9ae7-148">Sınıf arabirimine giriş</span><span class="sxs-lookup"><span data-stu-id="a9ae7-148">Introducing the class interface</span></span>](com-callable-wrapper.md#introducing-the-class-interface)
- [<span data-ttu-id="a9ae7-149">Bütünleştirilmiş Kod Güvenliği Konuları</span><span class="sxs-lookup"><span data-stu-id="a9ae7-149">Assembly Security Considerations</span></span>](../app-domains/assembly-security-considerations.md)
- [<span data-ttu-id="a9ae7-150">Tlbexp.exe (Tür Kitaplığı Dışarı Aktarıcı)</span><span class="sxs-lookup"><span data-stu-id="a9ae7-150">Tlbexp.exe (Type Library Exporter)</span></span>](../tools/tlbexp-exe-type-library-exporter.md)
- [<span data-ttu-id="a9ae7-151">Bütünleştirilmiş Kodları COM ile Kaydetme</span><span class="sxs-lookup"><span data-stu-id="a9ae7-151">Registering Assemblies with COM</span></span>](registering-assemblies-with-com.md)
- <span data-ttu-id="a9ae7-152">[Nasıl yapılır: Tür kitaplıklarını uygulamalarda Win32 kaynakları olarak katıştırma](https://msdn.microsoft.com/library/c97b4b8c-2ab7-4ac7-8fc8-0ba5c5d59c44(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a9ae7-152">[How to: Embed Type Libraries as Win32 Resources in Applications](https://msdn.microsoft.com/library/c97b4b8c-2ab7-4ac7-8fc8-0ba5c5d59c44(v=vs.100))</span></span>

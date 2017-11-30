---
title: "COM için Derlemeyi Paketleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 149d0c2595844c5b71767e2ea3ee5b0c6002c080
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="packaging-an-assembly-for-com"></a><span data-ttu-id="29a83-102">COM için Derlemeyi Paketleme</span><span class="sxs-lookup"><span data-stu-id="29a83-102">Packaging an Assembly for COM</span></span>
<span data-ttu-id="29a83-103">COM geliştiricilerin uygulamalarında eklemenizi planladıkları yönetilen türleri hakkında aşağıdaki bilgileri yararlı:</span><span class="sxs-lookup"><span data-stu-id="29a83-103">COM developers can benefit from the following information about the managed types they plan to incorporate in their application:</span></span>  
  
-   <span data-ttu-id="29a83-104">COM uygulamaları tüketebileceği türlerinin listesi</span><span class="sxs-lookup"><span data-stu-id="29a83-104">A list of types that COM applications can consume</span></span>  
  
     <span data-ttu-id="29a83-105">Bazı yönetilen türler COM görünmez; Bazı görünür ancak değil creatable; ve görünür ve creatable bazılarıdır.</span><span class="sxs-lookup"><span data-stu-id="29a83-105">Some managed types are invisible to COM; some are visible but not creatable; and some are both visible and creatable.</span></span> <span data-ttu-id="29a83-106">Bir derlemeyi görünmez, görünür, değil creatable ve creatable türleri herhangi bir birleşimini kapsayabilir.</span><span class="sxs-lookup"><span data-stu-id="29a83-106">An assembly can comprise any combination of invisible, visible, not creatable, and creatable types.</span></span> <span data-ttu-id="29a83-107">Eksiksiz olması için özellikle bu türleri için .NET Framework sunulan türlerinin bir alt olduğunda, COM kullanıma sunmak istediğiniz bir derlemesi türlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="29a83-107">For completeness, identify the types in an assembly that you intend to expose to COM, especially when those types are a subset of the types exposed to the .NET Framework.</span></span>  
  
     <span data-ttu-id="29a83-108">Ek bilgi için bkz: [birlikte çalışma için .NET türlerini niteleme](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md).</span><span class="sxs-lookup"><span data-stu-id="29a83-108">For additional information, see [Qualifying .NET Types for Interoperation](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md).</span></span>  
  
-   <span data-ttu-id="29a83-109">Sürüm oluşturma yönergeleri</span><span class="sxs-lookup"><span data-stu-id="29a83-109">Versioning instructions</span></span>  
  
     <span data-ttu-id="29a83-110">Sınıf arabirimini (COM birlikte çalışma oluşturulan arabirimi) yönetilen sınıflar sürüm kısıtlamalar geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="29a83-110">Managed classes that implement the class interface (a COM interop-generated interface) are subject to versioning restrictions.</span></span>  
  
     <span data-ttu-id="29a83-111">Sınıf arabirimi kullanma ile ilgili yönergeler için bkz: [sınıf arabirimi Tanıtımı](http://msdn.microsoft.com/en-us/733c0dd2-12e5-46e6-8de1-39d5b25df024).</span><span class="sxs-lookup"><span data-stu-id="29a83-111">For guidelines on using the class interface, see [Introducing the Class Interface](http://msdn.microsoft.com/en-us/733c0dd2-12e5-46e6-8de1-39d5b25df024).</span></span>  
  
-   <span data-ttu-id="29a83-112">Dağıtım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="29a83-112">Deployment instructions</span></span>  
  
     <span data-ttu-id="29a83-113">Bir yayımcı tarafından imzalanan tanımlayıcı adlı derlemeler genel derleme önbelleğine yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="29a83-113">Strong-named assemblies that are signed by a publisher can be installed into the global assembly cache.</span></span> <span data-ttu-id="29a83-114">İmzasız derlemeler kullanıcının makinesinde özel derlemeler yüklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="29a83-114">Unsigned assemblies must be installed on the user's machine as private assemblies.</span></span>  
  
     <span data-ttu-id="29a83-115">Ek bilgi için bkz: [derleme güvenliği konuları](../../../docs/framework/app-domains/assembly-security-considerations.md).</span><span class="sxs-lookup"><span data-stu-id="29a83-115">For additional information, see [Assembly Security Considerations](../../../docs/framework/app-domains/assembly-security-considerations.md).</span></span>  
  
-   <span data-ttu-id="29a83-116">Tür kitaplığı ekleme</span><span class="sxs-lookup"><span data-stu-id="29a83-116">Type library inclusion</span></span>  
  
     <span data-ttu-id="29a83-117">Çoğu türleri COM uygulama tarafından tüketilen olduğunda bir tür kitaplığı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="29a83-117">Most types require a type library when consumed by a COM application.</span></span> <span data-ttu-id="29a83-118">Bu görevi gerçekleştirmek COM geliştiriciler veya bir tür kitaplığı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="29a83-118">You can generate a type library or have COM developers perform this task.</span></span> <span data-ttu-id="29a83-119">[!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] Bir tür kitaplığı oluşturmak için aşağıdaki seçenekleri sağlar:</span><span class="sxs-lookup"><span data-stu-id="29a83-119">The [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] provides the following options for generating a type library:</span></span>  
  
    -   [<span data-ttu-id="29a83-120">Tür kitaplığı dışarı Aktarıcı</span><span class="sxs-lookup"><span data-stu-id="29a83-120">Type Library Exporter</span></span>](#cpconpackagingassemblyforcomanchor1)  
  
    -   [<span data-ttu-id="29a83-121">TypeLibConverter sınıfı</span><span class="sxs-lookup"><span data-stu-id="29a83-121">TypeLibConverter Class</span></span>](#cpconpackagingassemblyforcomanchor2)  
  
    -   [<span data-ttu-id="29a83-122">Derleme kayıt aracı</span><span class="sxs-lookup"><span data-stu-id="29a83-122">Assembly Registration Tool</span></span>](#cpconpackagingassemblyforcomanchor3)  
  
    -   [<span data-ttu-id="29a83-123">.NET Hizmetleri Yükleme aracı</span><span class="sxs-lookup"><span data-stu-id="29a83-123">.NET Services Installation Tool</span></span>](#cpconpackagingassemblyforcomanchor4)  
  
     <span data-ttu-id="29a83-124">Seçtiğiniz mekanizması bağımsız olarak, yalnızca genel türleri sağladığınız derlemede tanımlanan oluşturulan tür kitaplığı'nda bulunur.</span><span class="sxs-lookup"><span data-stu-id="29a83-124">Regardless of the mechanism you choose, only public types defined in the assembly you supply are included in the generated type library.</span></span>  
  
     <span data-ttu-id="29a83-125">Tür kitaplığı ayrı bir dosya olarak paketini veya içinde Win32 kaynak dosyası olarak katıştırmak bir. NET tabanlı bir uygulama.</span><span class="sxs-lookup"><span data-stu-id="29a83-125">You can package a type library as a separate file or embed it as Win32 resource file within a .NET-based application.</span></span> <span data-ttu-id="29a83-126">Microsoft Visual Basic 6.0 Bu görev sizin için otomatik olarak gerçekleştirilebilir; Ancak, kullanırken [!INCLUDE[vbprvbext](../../../includes/vbprvbext-md.md)], tür kitaplığı el ile ekleme.</span><span class="sxs-lookup"><span data-stu-id="29a83-126">Microsoft Visual Basic 6.0 performed this task for you automatically; however, when using [!INCLUDE[vbprvbext](../../../includes/vbprvbext-md.md)], you must embed your type library manually.</span></span> <span data-ttu-id="29a83-127">Yönergeler için bkz [nasıl yapılır: tür kitaplıklarını Win32 kaynak olarak ekleme. NET tabanlı uygulamalar](http://msdn.microsoft.com/en-us/c97b4b8c-2ab7-4ac7-8fc8-0ba5c5d59c44).</span><span class="sxs-lookup"><span data-stu-id="29a83-127">For instructions, see [How to: Embed Type Libraries as Win32 Resources in .NET-Based Applications](http://msdn.microsoft.com/en-us/c97b4b8c-2ab7-4ac7-8fc8-0ba5c5d59c44).</span></span>  
  
<a name="cpconpackagingassemblyforcomanchor1"></a>   
## <a name="type-library-exporter"></a><span data-ttu-id="29a83-128">Tür Kitaplığı Dışarı Aktarıcı</span><span class="sxs-lookup"><span data-stu-id="29a83-128">Type Library Exporter</span></span>  
 <span data-ttu-id="29a83-129">[Tür kitaplığı dışarı Aktarıcı (Tlbexp.exe)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) sınıflar ve arabirimler COM tür kitaplığının derlemedeki bulunan dönüştüren bir komut satırı aracıdır.</span><span class="sxs-lookup"><span data-stu-id="29a83-129">The [Type Library Exporter (Tlbexp.exe)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) is a command-line tool that converts the classes and interfaces contained in an assembly to a COM type library.</span></span> <span data-ttu-id="29a83-130">Sınıf türü bilgileri kullanılabilir olduğunda, COM istemcileri .NET sınıfının bir örneği oluşturun ve yeni bir COM nesnesi kabul edildiğinde örneğinin yöntemlerini çağırın.</span><span class="sxs-lookup"><span data-stu-id="29a83-130">Once the type information of the class is available, COM clients can create an instance of the .NET class and call the methods of the instance, just as if it were a COM object.</span></span> <span data-ttu-id="29a83-131">Tlbexp.exe aynı anda tüm bütünleştirilmiş dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="29a83-131">Tlbexp.exe converts an entire assembly at one time.</span></span> <span data-ttu-id="29a83-132">Derlemede tanımlanan türlerin bir alt kümesi için tür bilgisi üretmek üzere Tlbexp.exe'yi kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="29a83-132">You cannot use Tlbexp.exe to generate type information for a subset of the types defined in an assembly.</span></span>  
  
<a name="cpconpackagingassemblyforcomanchor2"></a>   
## <a name="typelibconverter-class"></a><span data-ttu-id="29a83-133">TypeLibConverter sınıfı</span><span class="sxs-lookup"><span data-stu-id="29a83-133">TypeLibConverter Class</span></span>  
 <span data-ttu-id="29a83-134"><xref:System.Runtime.InteropServices.TypeLibConverter> Bulunan sınıfı **System.Runtime.Interop** ad alanı, sınıflar ve arabirimler COM tür kitaplığının derlemedeki bulunan dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="29a83-134">The <xref:System.Runtime.InteropServices.TypeLibConverter> class, located in the **System.Runtime.Interop** namespace, converts the classes and interfaces contained in an assembly to a COM type library.</span></span> <span data-ttu-id="29a83-135">Bu API önceki bölümde açıklanan tür kitaplığı verici aynı tür bilgileri üretir.</span><span class="sxs-lookup"><span data-stu-id="29a83-135">This API produces the same type information as the Type Library Exporter, described in the previous section.</span></span>  
  
 <span data-ttu-id="29a83-136">**TypeLibConverter sınıfı** uygulayan <xref:System.Runtime.InteropServices.ITypeLibConverter>.</span><span class="sxs-lookup"><span data-stu-id="29a83-136">The **TypeLibConverter class** implements the <xref:System.Runtime.InteropServices.ITypeLibConverter>.</span></span>  
  
<a name="cpconpackagingassemblyforcomanchor3"></a>   
## <a name="assembly-registration-tool"></a><span data-ttu-id="29a83-137">Derleme kayıt aracı</span><span class="sxs-lookup"><span data-stu-id="29a83-137">Assembly Registration Tool</span></span>  
 <span data-ttu-id="29a83-138">[Derleme Kayıt Aracı (Regasm.exe)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) oluşturabilir ve, uyguladığınızda tür kitaplığının kaydı **TLB:** seçeneği.</span><span class="sxs-lookup"><span data-stu-id="29a83-138">The [Assembly Registration Tool (Regasm.exe)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) can generate and register a type library when you apply the **/tlb:** option.</span></span> <span data-ttu-id="29a83-139">COM istemcileri tür kitaplıklarının Windows Kayıt Defteri'nde yüklü olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="29a83-139">COM clients require that type libraries be installed in the Windows registry.</span></span> <span data-ttu-id="29a83-140">Bu seçenek olmadan Regasm.exe türleri yalnızca bir derleme, tür kitaplığı kaydeder.</span><span class="sxs-lookup"><span data-stu-id="29a83-140">Without this option, Regasm.exe only registers the types in an assembly, not the type library.</span></span> <span data-ttu-id="29a83-141">Bir derlemede türlerini kaydetme ve tür kitaplığını kaydetmede ayrı etkinliklerdir.</span><span class="sxs-lookup"><span data-stu-id="29a83-141">Registering the types in an assembly and registering the type library are distinct activities.</span></span>  
  
<a name="cpconpackagingassemblyforcomanchor4"></a>   
## <a name="net-services-installation-tool"></a><span data-ttu-id="29a83-142">.NET Hizmetleri Yükleme aracı</span><span class="sxs-lookup"><span data-stu-id="29a83-142">.NET Services Installation Tool</span></span>  
 <span data-ttu-id="29a83-143">[.NET Hizmetleri Yükleme aracı (Regsvcs.exe)](../../../docs/framework/tools/regsvcs-exe-net-services-installation-tool.md) yönetilen sınıflar Windows 2000 Bileşen Hizmetleri'ne ekler ve tek bir aracı içindeki çeşitli görevleri birleştirir.</span><span class="sxs-lookup"><span data-stu-id="29a83-143">The [.NET Services Installation Tool (Regsvcs.exe)](../../../docs/framework/tools/regsvcs-exe-net-services-installation-tool.md) adds managed classes to Windows 2000 Component Services and combines several tasks within a single tool.</span></span> <span data-ttu-id="29a83-144">Yükleme ve bir derlemeyi kaydetme ek olarak, Regsvcs.exe oluşturmak, kaydetme ve var olan bir COM + 1.0 uygulamasına tür kitaplığı yükleyin.</span><span class="sxs-lookup"><span data-stu-id="29a83-144">In addition to loading and registering an assembly, Regsvcs.exe can generate, register, and install the type library into an existing COM+ 1.0 application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29a83-145">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="29a83-145">See Also</span></span>  
 <xref:System.Runtime.InteropServices.TypeLibConverter>  
 <xref:System.Runtime.InteropServices.ITypeLibConverter>  
 [<span data-ttu-id="29a83-146">.NET Framework bileşenlerini COM'da gösterme</span><span class="sxs-lookup"><span data-stu-id="29a83-146">Exposing .NET Framework Components to COM</span></span>](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [<span data-ttu-id="29a83-147">Birlikte çalışma için .NET türlerini niteleme</span><span class="sxs-lookup"><span data-stu-id="29a83-147">Qualifying .NET Types for Interoperation</span></span>](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md)  
 [<span data-ttu-id="29a83-148">Sınıf arabirimi Tanıtımı</span><span class="sxs-lookup"><span data-stu-id="29a83-148">Introducing the Class Interface</span></span>](http://msdn.microsoft.com/en-us/733c0dd2-12e5-46e6-8de1-39d5b25df024)  
 [<span data-ttu-id="29a83-149">Derleme güvenliği konuları</span><span class="sxs-lookup"><span data-stu-id="29a83-149">Assembly Security Considerations</span></span>](../../../docs/framework/app-domains/assembly-security-considerations.md)  
 [<span data-ttu-id="29a83-150">Tlbexp.exe (tür kitaplığı dışarı Aktarıcı)</span><span class="sxs-lookup"><span data-stu-id="29a83-150">Tlbexp.exe (Type Library Exporter)</span></span>](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)  
 [<span data-ttu-id="29a83-151">Derlemeleri COM ile kaydetme</span><span class="sxs-lookup"><span data-stu-id="29a83-151">Registering Assemblies with COM</span></span>](../../../docs/framework/interop/registering-assemblies-with-com.md)  
 [<span data-ttu-id="29a83-152">Nasıl yapılır: tür kitaplıklarını uygulamalarında Win32 kaynaklar olarak ekleme</span><span class="sxs-lookup"><span data-stu-id="29a83-152">How to: Embed Type Libraries as Win32 Resources in Applications</span></span>](http://msdn.microsoft.com/en-us/c97b4b8c-2ab7-4ac7-8fc8-0ba5c5d59c44)

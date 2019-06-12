---
title: COM Birlikte Çalışma ile Verileri Sıralama
ms.date: 09/07/2017
helpviewer_keywords:
- COM interop, data marshaling
- marshaling data, COM interop
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d16f94e8b85a1bedb8b7791c2b7fcaf6d154ba1b
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833533"
---
# <a name="marshaling-data-with-com-interop"></a><span data-ttu-id="8c8d1-102">COM Birlikte Çalışma ile Verileri Sıralama</span><span class="sxs-lookup"><span data-stu-id="8c8d1-102">Marshaling Data with COM Interop</span></span>
<span data-ttu-id="8c8d1-103">COM birlikte çalışma COM nesnelerine yönetilen COM nesneleri yönetilen kod kullanarak hem de kullanıma sunmak için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="8c8d1-103">COM interop provides support for both using COM objects from managed code and exposing managed objects to COM.</span></span> <span data-ttu-id="8c8d1-104">COM veri hazırlama için destek kapsamlı ve neredeyse her zaman doğru sıralama davranışını sağlar.</span><span class="sxs-lookup"><span data-stu-id="8c8d1-104">Support for marshaling data to and from COM is extensive and almost always provides the correct marshaling behavior.</span></span>  
  
 <span data-ttu-id="8c8d1-105">Windows Yazılım Geliştirme Seti (SDK) aşağıdaki COM birlikte çalışma araçları içerir:</span><span class="sxs-lookup"><span data-stu-id="8c8d1-105">The Windows Software Development Kit (SDK) includes the following COM interop tools:</span></span>  
  
- <span data-ttu-id="8c8d1-106">[Tür kitaplığı alma programı (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md), birlikte çalışma derlemesi için bir COM tür kitaplığı dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="8c8d1-106">[Type Library Importer (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md), which converts a COM type library to an interop assembly.</span></span> <span data-ttu-id="8c8d1-107">Bu derleme, birlikte çalışma hazırlama hizmeti veri arasında yönetilen ve yönetilmeyen bellek hazırlama gerçekleştirmek sarmalayıcıları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8c8d1-107">From this assembly, the interop marshaling service generates wrappers that perform data marshaling between managed and unmanaged memory.</span></span>  
  
- <span data-ttu-id="8c8d1-108">[Tür kitaplığı dışarı Aktarıcı (Tlbexp.exe)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), bir derlemeden bir COM tür kitaplığı üretir ve yöntem çağrıları sırasında hazırlama gerçekleştiren bir sarmalayıcı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8c8d1-108">[Type Library Exporter (Tlbexp.exe)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), which produces a COM type library from an assembly and generates a wrapper that performs marshaling during method calls.</span></span>  
  
 <span data-ttu-id="8c8d1-109">Aşağıdaki bölümlerde, ek türü bilgilerini ile Sıralayıcı sağladığınız olabilir veya gerekir, birlikte çalışma sarmalayıcılarını özelleştirme işlemleri açıklayan konulara bağlayın.</span><span class="sxs-lookup"><span data-stu-id="8c8d1-109">The following sections link to topics that describe the processes for customizing interop wrappers when you can (or must) supply the marshaler with additional type information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8c8d1-110">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="8c8d1-110">In This Section</span></span>  
<span data-ttu-id="8c8d1-111">[Nasıl yapılır: Sarmalayıcıları elle oluşturma](how-to-create-wrappers-manually.md) </span><span class="sxs-lookup"><span data-stu-id="8c8d1-111">[How to: Create Wrappers Manually](how-to-create-wrappers-manually.md) </span></span>  
<span data-ttu-id="8c8d1-112">Bir COM sarmalayıcı yönetilen kaynak kodunda el ile oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="8c8d1-112">Describes how to create a COM wrapper manually in managed source code.</span></span> 
 
 [<span data-ttu-id="8c8d1-113">Nasıl yapılır: Yönetilen kodu DCOM'dan WCF'ye geçirme</span><span class="sxs-lookup"><span data-stu-id="8c8d1-113">How to: Migrate Managed-Code DCOM to WCF</span></span>](../../../docs/framework/interop/how-to-migrate-managed-code-dcom-to-wcf.md)  
 <span data-ttu-id="8c8d1-114">DCOM yönetilen kod için en güvenli çözümü için WCF geçişi işlemi açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8c8d1-114">Describes how to migrate managed DCOM code to WCF for the most secure solution.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8c8d1-115">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="8c8d1-115">Related Sections</span></span>  
 <span data-ttu-id="8c8d1-116">[COM veri türleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8c8d1-116">[COM Data Types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))</span></span>  
 <span data-ttu-id="8c8d1-117">Karşılık gelen yönetilen ve yönetilmeyen veri türleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="8c8d1-117">Provides corresponding managed and unmanaged data types.</span></span>  
  
 <span data-ttu-id="8c8d1-118">[COM aranabilir sarmalayıcılarını özelleştirme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3bwc828w(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8c8d1-118">[Customizing COM Callable Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3bwc828w(v=vs.100))</span></span>  
 <span data-ttu-id="8c8d1-119">Veri türleri kullanılarak açıkça hazırlanacağını açıklar <xref:System.Runtime.InteropServices.MarshalAsAttribute> tasarım zamanında özniteliği.</span><span class="sxs-lookup"><span data-stu-id="8c8d1-119">Describes how to explicitly marshal data types using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute at design time.</span></span>  
  
 <span data-ttu-id="8c8d1-120">[Çalışma zamanı aranabilir sarmalayıcılarını özelleştirme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8c8d1-120">[Customizing Runtime Callable Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))</span></span>  
 <span data-ttu-id="8c8d1-121">Bir birlikte çalışma bütünleştirilmiş kodundaki türler sıralama davranışını ayarlama ve COM türlerini manuel olarak tanımlamak nasıl açıklar.</span><span class="sxs-lookup"><span data-stu-id="8c8d1-121">Describes how to adjust the marshaling behavior of types in an interop assembly and how to define COM types manually.</span></span>  
  
 <span data-ttu-id="8c8d1-122">[Gelişmiş COM birlikte çalışabilirliği](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8c8d1-122">[Advanced COM Interoperability](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span></span>  
 <span data-ttu-id="8c8d1-123">COM bileşenlerini .NET Framework'te uygulamanıza ekleme hakkında daha fazla bilgi için bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="8c8d1-123">Provides links to more information about incorporating COM components into your .NET Framework application.</span></span>  
  
 <span data-ttu-id="8c8d1-124">[Derlemeden tür kitaplığına dönüştürme özeti](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8c8d1-124">[Assembly to Type Library Conversion Summary](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))</span></span>  
 <span data-ttu-id="8c8d1-125">Derleme, tür kitaplığı dışarı aktarma dönüştürme işlemi için açıklar.</span><span class="sxs-lookup"><span data-stu-id="8c8d1-125">Describes the assembly to type library export conversion process.</span></span>  
  
 <span data-ttu-id="8c8d1-126">[Tür kitaplığını derlemeye dönüştürme özeti](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8c8d1-126">[Type Library to Assembly Conversion Summary](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))</span></span>  
 <span data-ttu-id="8c8d1-127">Tür kitaplığını derleme içeri aktarma dönüştürme işlemi için açıklar.</span><span class="sxs-lookup"><span data-stu-id="8c8d1-127">Describes the type library to assembly import conversion process.</span></span>  
  
 <span data-ttu-id="8c8d1-128">[Genel türleri kullanarak birlikte çalışma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8c8d1-128">[Interoperating Using Generic Types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100))</span></span>  
 <span data-ttu-id="8c8d1-129">Hangi eylemler genel türler COM birlikte çalışabilirlik için kullanılırken desteklenen açıklar.</span><span class="sxs-lookup"><span data-stu-id="8c8d1-129">Describes which actions are supported when using generic types for COM interoperability.</span></span>

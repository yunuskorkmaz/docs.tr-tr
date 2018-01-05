---
title: "COM Birlikte Çalışma ile Verileri Hazırlama"
ms.custom: 
ms.date: 09/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- COM interop, data marshaling
- marshaling data, COM interop
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a2af80ddb558959171c255a61fae460729306e0e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="marshaling-data-with-com-interop"></a><span data-ttu-id="8fe98-102">COM Birlikte Çalışma ile Verileri Hazırlama</span><span class="sxs-lookup"><span data-stu-id="8fe98-102">Marshaling Data with COM Interop</span></span>
<span data-ttu-id="8fe98-103">COM birlikte çalışma COM nesnelerine yönetilen COM nesneleri yönetilen koddan kullanarak hem gösterme desteği sağlar</span><span class="sxs-lookup"><span data-stu-id="8fe98-103">COM interop provides support for both using COM objects from managed code and exposing managed objects to COM.</span></span> <span data-ttu-id="8fe98-104">Verileri için ve COM hazırlama desteği kapsamlı ve neredeyse her zaman doğru hazırlama davranışı sağlar.</span><span class="sxs-lookup"><span data-stu-id="8fe98-104">Support for marshaling data to and from COM is extensive and almost always provides the correct marshaling behavior.</span></span>  
  
 <span data-ttu-id="8fe98-105">[!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] Aşağıdaki COM birlikte çalışma araçları içerir:</span><span class="sxs-lookup"><span data-stu-id="8fe98-105">The [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] includes the following COM interop tools:</span></span>  
  
-   <span data-ttu-id="8fe98-106">[Tür kitaplığı içeri Aktarıcı (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md), birlikte çalışabilirlik bütünleştirilmiş COM tür kitaplığı dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="8fe98-106">[Type Library Importer (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md), which converts a COM type library to an interop assembly.</span></span> <span data-ttu-id="8fe98-107">Bu derlemedeki, hizmet hazırlama birlikte çalışabilirliği veri yönetilen ve yönetilmeyen bellek arasında sıralama gerçekleştirmek sarmalayıcılar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8fe98-107">From this assembly, the interop marshaling service generates wrappers that perform data marshaling between managed and unmanaged memory.</span></span>  
  
-   <span data-ttu-id="8fe98-108">[Tür kitaplığı dışarı Aktarıcı (Tlbexp.exe)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), COM tür kitaplığından derleme üretir ve yöntem çağrılarını sırasında hazırlama gerçekleştiren bir sarmalayıcı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8fe98-108">[Type Library Exporter (Tlbexp.exe)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), which produces a COM type library from an assembly and generates a wrapper that performs marshaling during method calls.</span></span>  
  
 <span data-ttu-id="8fe98-109">Aşağıdaki bölümlerde ek türü bilgilerle Sıralayıcı sağlayın ya da gerekir, birlikte çalışabilirlik sarmalayıcıları özelleştirme işlemleri açıklayan konulara bağlayın.</span><span class="sxs-lookup"><span data-stu-id="8fe98-109">The following sections link to topics that describe the processes for customizing interop wrappers when you can (or must) supply the marshaler with additional type information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8fe98-110">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="8fe98-110">In This Section</span></span>  
<span data-ttu-id="8fe98-111">[Nasıl yapılır: sarmalayıcıları elle oluşturma](how-to-create-wrappers-manually.md) </span><span class="sxs-lookup"><span data-stu-id="8fe98-111">[How to: Create Wrappers Manually](how-to-create-wrappers-manually.md) </span></span>  
<span data-ttu-id="8fe98-112">Bir COM sarmalayıcı elle yönetilen kaynak kodunda nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="8fe98-112">Describes how to create a COM wrapper manually in managed source code.</span></span> 
 
 [<span data-ttu-id="8fe98-113">Nasıl yapılır: Yönetilen Kodu DCOM’dan WCF’ye Geçirme</span><span class="sxs-lookup"><span data-stu-id="8fe98-113">How to: Migrate Managed-Code DCOM to WCF</span></span>](../../../docs/framework/interop/how-to-migrate-managed-code-dcom-to-wcf.md)  
 <span data-ttu-id="8fe98-114">WCF için en güvenli çözüm için yönetilen DCOM kod geçirmeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="8fe98-114">Describes how to migrate managed DCOM code to WCF for the most secure solution.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8fe98-115">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="8fe98-115">Related Sections</span></span>  
 <span data-ttu-id="8fe98-116">[COM veri türleri](https://msdn.microsoft.com/en-us/library/sak564ww(v=vs.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="8fe98-116">[COM Data Types](https://msdn.microsoft.com/en-us/library/sak564ww(v=vs.100).aspx)</span></span>  
 <span data-ttu-id="8fe98-117">Karşılık gelen yönetilen ve yönetilmeyen veri türleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="8fe98-117">Provides corresponding managed and unmanaged data types.</span></span>  
  
 <span data-ttu-id="8fe98-118">[COM aranabilir sarmalayıcılar özelleştirme](https://msdn.microsoft.com/en-us/library/3bwc828w(v=vs.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="8fe98-118">[Customizing COM Callable Wrappers](https://msdn.microsoft.com/en-us/library/3bwc828w(v=vs.100).aspx)</span></span>  
 <span data-ttu-id="8fe98-119">Veri türleri kullanılarak açıkça hazırlanacağını açıklar <xref:System.Runtime.InteropServices.MarshalAsAttribute> tasarım zamanında özniteliği.</span><span class="sxs-lookup"><span data-stu-id="8fe98-119">Describes how to explicitly marshal data types using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute at design time.</span></span>  
  
 <span data-ttu-id="8fe98-120">[Çalışma zamanı aranabilir sarmalayıcıları özelleştirme](https://msdn.microsoft.com/en-us/library/e753eftz(v=vs.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="8fe98-120">[Customizing Runtime Callable Wrappers](https://msdn.microsoft.com/en-us/library/e753eftz(v=vs.100).aspx)</span></span>  
 <span data-ttu-id="8fe98-121">Birlikte çalışma derlemedeki türleri hazırlama davranışı ayarlamak ve COM türlerini manuel olarak tanımlamak açıklar.</span><span class="sxs-lookup"><span data-stu-id="8fe98-121">Describes how to adjust the marshaling behavior of types in an interop assembly and how to define COM types manually.</span></span>  
  
 <span data-ttu-id="8fe98-122">[Gelişmiş COM birlikte çalışabilirliği](https://msdn.microsoft.com/en-us/library/bd9cdfyx(v=vs.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="8fe98-122">[Advanced COM Interoperability](https://msdn.microsoft.com/en-us/library/bd9cdfyx(v=vs.100).aspx)</span></span>  
 <span data-ttu-id="8fe98-123">COM bileşenlerini .NET Framework uygulamasına ekleme hakkında daha fazla bilgi için bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="8fe98-123">Provides links to more information about incorporating COM components into your .NET Framework application.</span></span>  
  
 <span data-ttu-id="8fe98-124">[Derleme Kitaplığı dönüştürme özeti yazın](https://msdn.microsoft.com/en-us/library/xk1120c3(v=vs.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="8fe98-124">[Assembly to Type Library Conversion Summary](https://msdn.microsoft.com/en-us/library/xk1120c3(v=vs.100).aspx)</span></span>  
 <span data-ttu-id="8fe98-125">Kitaplık dışarı aktarma dönüştürme işlemini yazmak için derlemeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="8fe98-125">Describes the assembly to type library export conversion process.</span></span>  
  
 <span data-ttu-id="8fe98-126">[Derleme dönüştürme özeti için tür kitaplığı](https://msdn.microsoft.com/en-us/library/k83zzh38(v=vs.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="8fe98-126">[Type Library to Assembly Conversion Summary](https://msdn.microsoft.com/en-us/library/k83zzh38(v=vs.100).aspx)</span></span>  
 <span data-ttu-id="8fe98-127">Tür kitaplığını derleme alma dönüştürme işlemi için açıklar.</span><span class="sxs-lookup"><span data-stu-id="8fe98-127">Describes the type library to assembly import conversion process.</span></span>  
  
 <span data-ttu-id="8fe98-128">[Genel türler kullanma birlikte çalışma](https://msdn.microsoft.com/en-us/library/ms229590(v=vs.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="8fe98-128">[Interoperating Using Generic Types](https://msdn.microsoft.com/en-us/library/ms229590(v=vs.100).aspx)</span></span>  
 <span data-ttu-id="8fe98-129">Genel türler COM birlikte çalışabilirlik için kullanılırken hangi eylemleri desteklenen açıklar.</span><span class="sxs-lookup"><span data-stu-id="8fe98-129">Describes which actions are supported when using generic types for COM interoperability.</span></span>

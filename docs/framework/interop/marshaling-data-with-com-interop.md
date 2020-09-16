---
title: COM Birlikte Çalışma ile Verileri Sıralama
description: COM birlikte çalışabilirliğine sahip verilerin sıralamasını kapsayan makalelere göz atın. Tlbimp.exe ve Tlbexp.exe araçları bir COM tür kitaplığı ve birlikte çalışma derlemesi arasında dönüştürülür.
ms.date: 09/07/2017
helpviewer_keywords:
- COM interop, data marshaling
- marshaling data, COM interop
ms.openlocfilehash: 94149e0c444cad7e32f959eaedd55bf14acb1ecb
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90547850"
---
# <a name="marshaling-data-with-com-interop"></a><span data-ttu-id="87e72-104">COM Birlikte Çalışma ile Verileri Sıralama</span><span class="sxs-lookup"><span data-stu-id="87e72-104">Marshaling Data with COM Interop</span></span>
<span data-ttu-id="87e72-105">COM birlikte çalışma, yönetilen koddan COM nesnelerini kullanarak ve yönetilen nesneleri COM 'a açığa çıkarmak için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="87e72-105">COM interop provides support for both using COM objects from managed code and exposing managed objects to COM.</span></span> <span data-ttu-id="87e72-106">COM 'a ve sürümünden veri sıralama desteği kapsamlıdır ve neredeyse her zaman doğru sıralama davranışını sağlar.</span><span class="sxs-lookup"><span data-stu-id="87e72-106">Support for marshaling data to and from COM is extensive and almost always provides the correct marshaling behavior.</span></span>  
  
 <span data-ttu-id="87e72-107">Windows SDK aşağıdaki COM birlikte çalışma araçlarını içerir:</span><span class="sxs-lookup"><span data-stu-id="87e72-107">The Windows SDK includes the following COM interop tools:</span></span>  
  
- <span data-ttu-id="87e72-108">COM tür kitaplığını birlikte çalışma derlemesine dönüştüren [tür kitaplığı alma programı (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md).</span><span class="sxs-lookup"><span data-stu-id="87e72-108">[Type Library Importer (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md), which converts a COM type library to an interop assembly.</span></span> <span data-ttu-id="87e72-109">Bu derlemeden birlikte çalışma hazırlama hizmeti yönetilen ve yönetilmeyen bellek arasında veri hazırlama işlemi gerçekleştiren sarmalayıcılar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="87e72-109">From this assembly, the interop marshaling service generates wrappers that perform data marshaling between managed and unmanaged memory.</span></span>  
  
- <span data-ttu-id="87e72-110">Bir derlemeden COM tür kitaplığı üreten ve Yöntem çağrıları sırasında sıralama gerçekleştiren bir sarmalayıcı oluşturan [tür kitaplığı verme programı (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md).</span><span class="sxs-lookup"><span data-stu-id="87e72-110">[Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md), which produces a COM type library from an assembly and generates a wrapper that performs marshaling during method calls.</span></span>  
  
 <span data-ttu-id="87e72-111">Aşağıdaki bölümler, ek tür bilgileri ile Sıralayıcı sağlamanız (veya yapmanız gerektiğinde) birlikte çalışma sarmalayıcılarını özelleştirmek için süreçler tanımlayan konuların bağlantısını ele vermektedir.</span><span class="sxs-lookup"><span data-stu-id="87e72-111">The following sections link to topics that describe the processes for customizing interop wrappers when you can (or must) supply the marshaler with additional type information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="87e72-112">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="87e72-112">In This Section</span></span>  
<span data-ttu-id="87e72-113">[Nasıl yapılır: sarmalayıcıları El Ile oluşturma](how-to-create-wrappers-manually.md) Yönetilen kaynak kodunda el ile bir COM sarmalayıcı oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="87e72-113">[How to: Create Wrappers Manually](how-to-create-wrappers-manually.md) Describes how to create a COM wrapper manually in managed source code.</span></span>

 [<span data-ttu-id="87e72-114">Nasıl yapılır: Yönetilen Kodu DCOM’dan WCF’ye Geçirme</span><span class="sxs-lookup"><span data-stu-id="87e72-114">How to: Migrate Managed-Code DCOM to WCF</span></span>](how-to-migrate-managed-code-dcom-to-wcf.md)  
 <span data-ttu-id="87e72-115">En güvenli çözüm için yönetilen DCOM kodunun WCF 'ye nasıl geçirileceğiyle ilgili açıklar.</span><span class="sxs-lookup"><span data-stu-id="87e72-115">Describes how to migrate managed DCOM code to WCF for the most secure solution.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="87e72-116">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="87e72-116">Related Sections</span></span>  
 <span data-ttu-id="87e72-117">[COM veri türleri](/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="87e72-117">[COM Data Types](/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))</span></span>  
 <span data-ttu-id="87e72-118">Karşılık gelen yönetilen ve yönetilmeyen veri türlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="87e72-118">Provides corresponding managed and unmanaged data types.</span></span>  
  
 <span data-ttu-id="87e72-119">[COM çağrılabilir sarmalayıcıları özelleştirme](/previous-versions/dotnet/netframework-4.0/3bwc828w(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="87e72-119">[Customizing COM Callable Wrappers](/previous-versions/dotnet/netframework-4.0/3bwc828w(v=vs.100))</span></span>  
 <span data-ttu-id="87e72-120">Tasarım zamanında özniteliği kullanılarak veri türlerinin açıkça nasıl hazırlanacağını açıklar <xref:System.Runtime.InteropServices.MarshalAsAttribute> .</span><span class="sxs-lookup"><span data-stu-id="87e72-120">Describes how to explicitly marshal data types using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute at design time.</span></span>  
  
 <span data-ttu-id="87e72-121">[Çalışma zamanı çağrılabilir sarmalayıcıları özelleştirme](/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="87e72-121">[Customizing Runtime Callable Wrappers](/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))</span></span>  
 <span data-ttu-id="87e72-122">Birlikte çalışma derlemesindeki türlerin sıralama davranışının nasıl ayarlanacağını ve COM türlerinin el ile nasıl tanımlanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="87e72-122">Describes how to adjust the marshaling behavior of types in an interop assembly and how to define COM types manually.</span></span>  
  
 <span data-ttu-id="87e72-123">[Gelişmiş COM birlikte çalışabilirlik](/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="87e72-123">[Advanced COM Interoperability](/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span></span>  
 <span data-ttu-id="87e72-124">.NET Framework uygulamanıza COM bileşenlerini ekleme hakkında daha fazla bilgi için bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="87e72-124">Provides links to more information about incorporating COM components into your .NET Framework application.</span></span>  
  
 <span data-ttu-id="87e72-125">[Derlemeden tür kitaplığına dönüştürme Özeti](/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="87e72-125">[Assembly to Type Library Conversion Summary](/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))</span></span>  
 <span data-ttu-id="87e72-126">Kitaplık dışarı aktarma dönüştürme işlemini yazmak için bütünleştirilmiş kodu açıklar.</span><span class="sxs-lookup"><span data-stu-id="87e72-126">Describes the assembly to type library export conversion process.</span></span>  
  
 <span data-ttu-id="87e72-127">[Tür kitaplığını derlemeye dönüştürme Özeti](/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="87e72-127">[Type Library to Assembly Conversion Summary](/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))</span></span>  
 <span data-ttu-id="87e72-128">Derleme içeri aktarma dönüştürme işlemine tür kitaplığını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="87e72-128">Describes the type library to assembly import conversion process.</span></span>  
  
 <span data-ttu-id="87e72-129">[Genel türler kullanılarak birlikte çalışma](/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="87e72-129">[Interoperating Using Generic Types](/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100))</span></span>  
 <span data-ttu-id="87e72-130">COM birlikte çalışabilirlik için genel türler kullanılırken hangi eylemlerin desteklendiğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="87e72-130">Describes which actions are supported when using generic types for COM interoperability.</span></span>

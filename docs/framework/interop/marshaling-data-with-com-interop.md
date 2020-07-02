---
title: COM Birlikte Çalışma ile Verileri Sıralama
description: COM birlikte çalışabilirliğine sahip verilerin sıralamasını kapsayan makalelere göz atın. Tlbimp.exe ve Tlbexp.exe araçları bir COM tür kitaplığı ve birlikte çalışma derlemesi arasında dönüştürülür.
ms.date: 09/07/2017
helpviewer_keywords:
- COM interop, data marshaling
- marshaling data, COM interop
ms.openlocfilehash: eedfb60a75e2fe5fafdaa786dbb54adddf28400e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621515"
---
# <a name="marshaling-data-with-com-interop"></a><span data-ttu-id="7a1f8-104">COM Birlikte Çalışma ile Verileri Sıralama</span><span class="sxs-lookup"><span data-stu-id="7a1f8-104">Marshaling Data with COM Interop</span></span>
<span data-ttu-id="7a1f8-105">COM birlikte çalışma, yönetilen koddan COM nesnelerini kullanarak ve yönetilen nesneleri COM 'a açığa çıkarmak için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="7a1f8-105">COM interop provides support for both using COM objects from managed code and exposing managed objects to COM.</span></span> <span data-ttu-id="7a1f8-106">COM 'a ve sürümünden veri sıralama desteği kapsamlıdır ve neredeyse her zaman doğru sıralama davranışını sağlar.</span><span class="sxs-lookup"><span data-stu-id="7a1f8-106">Support for marshaling data to and from COM is extensive and almost always provides the correct marshaling behavior.</span></span>  
  
 <span data-ttu-id="7a1f8-107">Windows SDK aşağıdaki COM birlikte çalışma araçlarını içerir:</span><span class="sxs-lookup"><span data-stu-id="7a1f8-107">The Windows SDK includes the following COM interop tools:</span></span>  
  
- <span data-ttu-id="7a1f8-108">COM tür kitaplığını birlikte çalışma derlemesine dönüştüren [tür kitaplığı alma programı (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md).</span><span class="sxs-lookup"><span data-stu-id="7a1f8-108">[Type Library Importer (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md), which converts a COM type library to an interop assembly.</span></span> <span data-ttu-id="7a1f8-109">Bu derlemeden birlikte çalışma hazırlama hizmeti yönetilen ve yönetilmeyen bellek arasında veri hazırlama işlemi gerçekleştiren sarmalayıcılar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7a1f8-109">From this assembly, the interop marshaling service generates wrappers that perform data marshaling between managed and unmanaged memory.</span></span>  
  
- <span data-ttu-id="7a1f8-110">Bir derlemeden COM tür kitaplığı üreten ve Yöntem çağrıları sırasında sıralama gerçekleştiren bir sarmalayıcı oluşturan [tür kitaplığı verme programı (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md).</span><span class="sxs-lookup"><span data-stu-id="7a1f8-110">[Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md), which produces a COM type library from an assembly and generates a wrapper that performs marshaling during method calls.</span></span>  
  
 <span data-ttu-id="7a1f8-111">Aşağıdaki bölümler, ek tür bilgileri ile Sıralayıcı sağlamanız (veya yapmanız gerektiğinde) birlikte çalışma sarmalayıcılarını özelleştirmek için süreçler tanımlayan konuların bağlantısını ele vermektedir.</span><span class="sxs-lookup"><span data-stu-id="7a1f8-111">The following sections link to topics that describe the processes for customizing interop wrappers when you can (or must) supply the marshaler with additional type information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7a1f8-112">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="7a1f8-112">In This Section</span></span>  
<span data-ttu-id="7a1f8-113">[Nasıl yapılır: sarmalayıcıları El Ile oluşturma](how-to-create-wrappers-manually.md) Yönetilen kaynak kodunda el ile bir COM sarmalayıcı oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="7a1f8-113">[How to: Create Wrappers Manually](how-to-create-wrappers-manually.md) Describes how to create a COM wrapper manually in managed source code.</span></span>

 [<span data-ttu-id="7a1f8-114">Nasıl yapılır: Yönetilen Kodu DCOM’dan WCF’ye Geçirme</span><span class="sxs-lookup"><span data-stu-id="7a1f8-114">How to: Migrate Managed-Code DCOM to WCF</span></span>](how-to-migrate-managed-code-dcom-to-wcf.md)  
 <span data-ttu-id="7a1f8-115">En güvenli çözüm için yönetilen DCOM kodunun WCF 'ye nasıl geçirileceğiyle ilgili açıklar.</span><span class="sxs-lookup"><span data-stu-id="7a1f8-115">Describes how to migrate managed DCOM code to WCF for the most secure solution.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7a1f8-116">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="7a1f8-116">Related Sections</span></span>  
 <span data-ttu-id="7a1f8-117">[COM veri türleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7a1f8-117">[COM Data Types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))</span></span>  
 <span data-ttu-id="7a1f8-118">Karşılık gelen yönetilen ve yönetilmeyen veri türlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="7a1f8-118">Provides corresponding managed and unmanaged data types.</span></span>  
  
 <span data-ttu-id="7a1f8-119">[COM çağrılabilir sarmalayıcıları özelleştirme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3bwc828w(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7a1f8-119">[Customizing COM Callable Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3bwc828w(v=vs.100))</span></span>  
 <span data-ttu-id="7a1f8-120">Tasarım zamanında özniteliği kullanılarak veri türlerinin açıkça nasıl hazırlanacağını açıklar <xref:System.Runtime.InteropServices.MarshalAsAttribute> .</span><span class="sxs-lookup"><span data-stu-id="7a1f8-120">Describes how to explicitly marshal data types using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute at design time.</span></span>  
  
 <span data-ttu-id="7a1f8-121">[Çalışma zamanı çağrılabilir sarmalayıcıları özelleştirme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7a1f8-121">[Customizing Runtime Callable Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))</span></span>  
 <span data-ttu-id="7a1f8-122">Birlikte çalışma derlemesindeki türlerin sıralama davranışının nasıl ayarlanacağını ve COM türlerinin el ile nasıl tanımlanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="7a1f8-122">Describes how to adjust the marshaling behavior of types in an interop assembly and how to define COM types manually.</span></span>  
  
 <span data-ttu-id="7a1f8-123">[Gelişmiş COM birlikte çalışabilirlik](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7a1f8-123">[Advanced COM Interoperability](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span></span>  
 <span data-ttu-id="7a1f8-124">.NET Framework uygulamanıza COM bileşenlerini ekleme hakkında daha fazla bilgi için bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="7a1f8-124">Provides links to more information about incorporating COM components into your .NET Framework application.</span></span>  
  
 <span data-ttu-id="7a1f8-125">[Derlemeden tür kitaplığına dönüştürme Özeti](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7a1f8-125">[Assembly to Type Library Conversion Summary](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))</span></span>  
 <span data-ttu-id="7a1f8-126">Kitaplık dışarı aktarma dönüştürme işlemini yazmak için bütünleştirilmiş kodu açıklar.</span><span class="sxs-lookup"><span data-stu-id="7a1f8-126">Describes the assembly to type library export conversion process.</span></span>  
  
 <span data-ttu-id="7a1f8-127">[Tür kitaplığını derlemeye dönüştürme Özeti](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7a1f8-127">[Type Library to Assembly Conversion Summary](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))</span></span>  
 <span data-ttu-id="7a1f8-128">Derleme içeri aktarma dönüştürme işlemine tür kitaplığını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7a1f8-128">Describes the type library to assembly import conversion process.</span></span>  
  
 <span data-ttu-id="7a1f8-129">[Genel türler kullanılarak birlikte çalışma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7a1f8-129">[Interoperating Using Generic Types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100))</span></span>  
 <span data-ttu-id="7a1f8-130">COM birlikte çalışabilirlik için genel türler kullanılırken hangi eylemlerin desteklendiğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="7a1f8-130">Describes which actions are supported when using generic types for COM interoperability.</span></span>

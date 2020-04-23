---
title: COM Birlikte Çalışma ile Verileri Sıralama
ms.date: 09/07/2017
helpviewer_keywords:
- COM interop, data marshaling
- marshaling data, COM interop
ms.openlocfilehash: ae41713d5349321725599c0c38d7c6fc515c374b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181379"
---
# <a name="marshaling-data-with-com-interop"></a><span data-ttu-id="8624b-102">COM Birlikte Çalışma ile Verileri Sıralama</span><span class="sxs-lookup"><span data-stu-id="8624b-102">Marshaling Data with COM Interop</span></span>
<span data-ttu-id="8624b-103">COM birlikte çalışma, yönetilen koddan COM nesnelerini kullanarak ve yönetilen nesneleri COM 'a açığa çıkarmak için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="8624b-103">COM interop provides support for both using COM objects from managed code and exposing managed objects to COM.</span></span> <span data-ttu-id="8624b-104">COM 'a ve sürümünden veri sıralama desteği kapsamlıdır ve neredeyse her zaman doğru sıralama davranışını sağlar.</span><span class="sxs-lookup"><span data-stu-id="8624b-104">Support for marshaling data to and from COM is extensive and almost always provides the correct marshaling behavior.</span></span>  
  
 <span data-ttu-id="8624b-105">Windows SDK aşağıdaki COM birlikte çalışma araçlarını içerir:</span><span class="sxs-lookup"><span data-stu-id="8624b-105">The Windows SDK includes the following COM interop tools:</span></span>  
  
- <span data-ttu-id="8624b-106">COM tür kitaplığını birlikte çalışma derlemesine dönüştüren [tür kitaplığı alma programı (Tlbimp. exe)](../tools/tlbimp-exe-type-library-importer.md).</span><span class="sxs-lookup"><span data-stu-id="8624b-106">[Type Library Importer (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md), which converts a COM type library to an interop assembly.</span></span> <span data-ttu-id="8624b-107">Bu derlemeden birlikte çalışma hazırlama hizmeti yönetilen ve yönetilmeyen bellek arasında veri hazırlama işlemi gerçekleştiren sarmalayıcılar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8624b-107">From this assembly, the interop marshaling service generates wrappers that perform data marshaling between managed and unmanaged memory.</span></span>  
  
- <span data-ttu-id="8624b-108">Bir derlemeden COM tür kitaplığı üreten ve Yöntem çağrıları sırasında sıralama gerçekleştiren bir sarmalayıcı oluşturan [tür kitaplığı verme programı (Tlbexp. exe)](../tools/tlbexp-exe-type-library-exporter.md).</span><span class="sxs-lookup"><span data-stu-id="8624b-108">[Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md), which produces a COM type library from an assembly and generates a wrapper that performs marshaling during method calls.</span></span>  
  
 <span data-ttu-id="8624b-109">Aşağıdaki bölümler, ek tür bilgileri ile Sıralayıcı sağlamanız (veya yapmanız gerektiğinde) birlikte çalışma sarmalayıcılarını özelleştirmek için süreçler tanımlayan konuların bağlantısını ele vermektedir.</span><span class="sxs-lookup"><span data-stu-id="8624b-109">The following sections link to topics that describe the processes for customizing interop wrappers when you can (or must) supply the marshaler with additional type information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8624b-110">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="8624b-110">In This Section</span></span>  
<span data-ttu-id="8624b-111">[Nasıl yapılır: sarmalayıcıları El Ile oluşturma](how-to-create-wrappers-manually.md) Yönetilen kaynak kodunda el ile bir COM sarmalayıcı oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="8624b-111">[How to: Create Wrappers Manually](how-to-create-wrappers-manually.md) Describes how to create a COM wrapper manually in managed source code.</span></span>

 [<span data-ttu-id="8624b-112">Nasıl yapılır: Yönetilen Kodu DCOM’dan WCF’ye Geçirme</span><span class="sxs-lookup"><span data-stu-id="8624b-112">How to: Migrate Managed-Code DCOM to WCF</span></span>](how-to-migrate-managed-code-dcom-to-wcf.md)  
 <span data-ttu-id="8624b-113">En güvenli çözüm için yönetilen DCOM kodunun WCF 'ye nasıl geçirileceğiyle ilgili açıklar.</span><span class="sxs-lookup"><span data-stu-id="8624b-113">Describes how to migrate managed DCOM code to WCF for the most secure solution.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8624b-114">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="8624b-114">Related Sections</span></span>  
 <span data-ttu-id="8624b-115">[COM veri türleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8624b-115">[COM Data Types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))</span></span>  
 <span data-ttu-id="8624b-116">Karşılık gelen yönetilen ve yönetilmeyen veri türlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="8624b-116">Provides corresponding managed and unmanaged data types.</span></span>  
  
 <span data-ttu-id="8624b-117">[COM çağrılabilir sarmalayıcıları özelleştirme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3bwc828w(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8624b-117">[Customizing COM Callable Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3bwc828w(v=vs.100))</span></span>  
 <span data-ttu-id="8624b-118">Tasarım zamanında <xref:System.Runtime.InteropServices.MarshalAsAttribute> özniteliği kullanılarak veri türlerinin açıkça nasıl hazırlanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="8624b-118">Describes how to explicitly marshal data types using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute at design time.</span></span>  
  
 <span data-ttu-id="8624b-119">[Çalışma zamanı çağrılabilir sarmalayıcıları özelleştirme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8624b-119">[Customizing Runtime Callable Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))</span></span>  
 <span data-ttu-id="8624b-120">Birlikte çalışma derlemesindeki türlerin sıralama davranışının nasıl ayarlanacağını ve COM türlerinin el ile nasıl tanımlanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="8624b-120">Describes how to adjust the marshaling behavior of types in an interop assembly and how to define COM types manually.</span></span>  
  
 <span data-ttu-id="8624b-121">[Gelişmiş COM birlikte çalışabilirlik](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8624b-121">[Advanced COM Interoperability](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span></span>  
 <span data-ttu-id="8624b-122">.NET Framework uygulamanıza COM bileşenlerini ekleme hakkında daha fazla bilgi için bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="8624b-122">Provides links to more information about incorporating COM components into your .NET Framework application.</span></span>  
  
 <span data-ttu-id="8624b-123">[Derlemeden tür kitaplığına dönüştürme Özeti](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8624b-123">[Assembly to Type Library Conversion Summary](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))</span></span>  
 <span data-ttu-id="8624b-124">Kitaplık dışarı aktarma dönüştürme işlemini yazmak için bütünleştirilmiş kodu açıklar.</span><span class="sxs-lookup"><span data-stu-id="8624b-124">Describes the assembly to type library export conversion process.</span></span>  
  
 <span data-ttu-id="8624b-125">[Tür kitaplığını derlemeye dönüştürme Özeti](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8624b-125">[Type Library to Assembly Conversion Summary](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))</span></span>  
 <span data-ttu-id="8624b-126">Derleme içeri aktarma dönüştürme işlemine tür kitaplığını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8624b-126">Describes the type library to assembly import conversion process.</span></span>  
  
 <span data-ttu-id="8624b-127">[Genel türler kullanılarak birlikte çalışma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8624b-127">[Interoperating Using Generic Types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100))</span></span>  
 <span data-ttu-id="8624b-128">COM birlikte çalışabilirlik için genel türler kullanılırken hangi eylemlerin desteklendiğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="8624b-128">Describes which actions are supported when using generic types for COM interoperability.</span></span>

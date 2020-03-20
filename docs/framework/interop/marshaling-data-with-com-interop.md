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
# <a name="marshaling-data-with-com-interop"></a><span data-ttu-id="f7b4e-102">COM Birlikte Çalışma ile Verileri Sıralama</span><span class="sxs-lookup"><span data-stu-id="f7b4e-102">Marshaling Data with COM Interop</span></span>
<span data-ttu-id="f7b4e-103">COM interop, yönetilen koddaki COM nesnelerini kullanmak ve yönetilen nesneleri COM'a teşhir etmek için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="f7b4e-103">COM interop provides support for both using COM objects from managed code and exposing managed objects to COM.</span></span> <span data-ttu-id="f7b4e-104">Com'a ve COM'dan veri mareşallik desteği kapsamlıdır ve hemen hemen her zaman doğru mareşaldavranışını sağlar.</span><span class="sxs-lookup"><span data-stu-id="f7b4e-104">Support for marshaling data to and from COM is extensive and almost always provides the correct marshaling behavior.</span></span>  
  
 <span data-ttu-id="f7b4e-105">Windows SDK aşağıdaki COM interop araçlarını içerir:</span><span class="sxs-lookup"><span data-stu-id="f7b4e-105">The Windows SDK includes the following COM interop tools:</span></span>  
  
- <span data-ttu-id="f7b4e-106">Com türü kitaplığını interop derlemesine dönüştüren [Kitaplık İthalatçısı (Tlbimp.exe) türü.](../tools/tlbimp-exe-type-library-importer.md)</span><span class="sxs-lookup"><span data-stu-id="f7b4e-106">[Type Library Importer (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md), which converts a COM type library to an interop assembly.</span></span> <span data-ttu-id="f7b4e-107">Bu derlemeden, interop mareşallik hizmeti, yönetilen ve yönetilmeyen bellek arasında veri mareşalleme gerçekleştiren sarmalayıcılar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f7b4e-107">From this assembly, the interop marshaling service generates wrappers that perform data marshaling between managed and unmanaged memory.</span></span>  
  
- <span data-ttu-id="f7b4e-108">Bir derlemeden COM türü kitaplığı üreten ve yöntem aramaları sırasında mareşallik gerçekleştiren bir sarmalayıcı üreten [Tip Kitaplık İhracatçısı (Tlbexp.exe).](../tools/tlbexp-exe-type-library-exporter.md)</span><span class="sxs-lookup"><span data-stu-id="f7b4e-108">[Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md), which produces a COM type library from an assembly and generates a wrapper that performs marshaling during method calls.</span></span>  
  
 <span data-ttu-id="f7b4e-109">Aşağıdaki bölümler, mareşale ek tür bilgileri sağlayabildiğinizde (veya sağlamanız gerektiğinde) interop sarmalayıcılarını özelleştirme süreçlerini açıklayan konulara bağlantı eder.</span><span class="sxs-lookup"><span data-stu-id="f7b4e-109">The following sections link to topics that describe the processes for customizing interop wrappers when you can (or must) supply the marshaler with additional type information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f7b4e-110">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="f7b4e-110">In This Section</span></span>  
<span data-ttu-id="f7b4e-111">[Nasıl yapılır: Sarmalayıcıları El ile Oluştur](how-to-create-wrappers-manually.md) Yönetilen kaynak kodunda el ile com sarıcı nın nasıl oluşturuluruz açıklanır.</span><span class="sxs-lookup"><span data-stu-id="f7b4e-111">[How to: Create Wrappers Manually](how-to-create-wrappers-manually.md) Describes how to create a COM wrapper manually in managed source code.</span></span>

 [<span data-ttu-id="f7b4e-112">Nasıl yapılır: Yönetilen Kodu DCOM’dan WCF’ye Geçirme</span><span class="sxs-lookup"><span data-stu-id="f7b4e-112">How to: Migrate Managed-Code DCOM to WCF</span></span>](how-to-migrate-managed-code-dcom-to-wcf.md)  
 <span data-ttu-id="f7b4e-113">Yönetilen DCOM kodunun en güvenli çözüm için WCF'ye nasıl geçirilen bir şekilde geçirilen açıklanır.</span><span class="sxs-lookup"><span data-stu-id="f7b4e-113">Describes how to migrate managed DCOM code to WCF for the most secure solution.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f7b4e-114">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="f7b4e-114">Related Sections</span></span>  
 <span data-ttu-id="f7b4e-115">[COM Veri Türleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f7b4e-115">[COM Data Types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))</span></span>  
 <span data-ttu-id="f7b4e-116">Karşılık gelen yönetilen ve yönetilmeyen veri türleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="f7b4e-116">Provides corresponding managed and unmanaged data types.</span></span>  
  
 <span data-ttu-id="f7b4e-117">[COM Çağrılabilir Sarmalayıcıları Özelleştirme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3bwc828w(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f7b4e-117">[Customizing COM Callable Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3bwc828w(v=vs.100))</span></span>  
 <span data-ttu-id="f7b4e-118">Tasarım zamanında özniteliği kullanarak veri <xref:System.Runtime.InteropServices.MarshalAsAttribute> türlerini açıkça nasıl keşe edilebildiğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="f7b4e-118">Describes how to explicitly marshal data types using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute at design time.</span></span>  
  
 <span data-ttu-id="f7b4e-119">[Runtime Çağrılanabilir Sarmalayıcıları Özelleştirme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f7b4e-119">[Customizing Runtime Callable Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))</span></span>  
 <span data-ttu-id="f7b4e-120">Bir interop derlemesindeki türlerin mareşaldavranışını nasıl ayarlayacaklarını ve COM türlerini el ile nasıl tanımlayacaklarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="f7b4e-120">Describes how to adjust the marshaling behavior of types in an interop assembly and how to define COM types manually.</span></span>  
  
 <span data-ttu-id="f7b4e-121">[Gelişmiş COM Birlikte Çalışabilirlik](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f7b4e-121">[Advanced COM Interoperability](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span></span>  
 <span data-ttu-id="f7b4e-122">COM bileşenlerini .NET Framework uygulamanıza dahil etme hakkında daha fazla bilgiye bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="f7b4e-122">Provides links to more information about incorporating COM components into your .NET Framework application.</span></span>  
  
 <span data-ttu-id="f7b4e-123">[Derleme den Türe Dönüşüm Özeti](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f7b4e-123">[Assembly to Type Library Conversion Summary](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))</span></span>  
 <span data-ttu-id="f7b4e-124">Kitaplık dışa aktarma dönüşüm işlemini yazmak için derlemeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="f7b4e-124">Describes the assembly to type library export conversion process.</span></span>  
  
 <span data-ttu-id="f7b4e-125">[Tür Kitaplığı ndan Montaja Dönüşüm Özeti](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f7b4e-125">[Type Library to Assembly Conversion Summary](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))</span></span>  
 <span data-ttu-id="f7b4e-126">Derleme alma dönüştürme işlemine tür kitaplığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="f7b4e-126">Describes the type library to assembly import conversion process.</span></span>  
  
 <span data-ttu-id="f7b4e-127">[Genel Türleri Kullanarak Ara Çalışma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f7b4e-127">[Interoperating Using Generic Types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100))</span></span>  
 <span data-ttu-id="f7b4e-128">COM birlikte çalışabilirliği için genel türleri kullanırken hangi eylemlerin desteklenir açıklar.</span><span class="sxs-lookup"><span data-stu-id="f7b4e-128">Describes which actions are supported when using generic types for COM interoperability.</span></span>

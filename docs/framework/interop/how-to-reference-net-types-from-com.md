---
title: "Nasıl yapılır: COM'dan .NET Türlerine Başvurma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
helpviewer_keywords:
- importing type library
- COM interop, referencing .NET types
- interoperation with unmanaged code, referencing .NET types
- referencing .NET types
- interoperation with unmanaged code, importing type library
- type libraries
- COM interop, importing type library
ms.assetid: 54917f6f-cb18-4103-b622-856b55da93f3
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3c6427254aeec1a9e272579665fcd9893daa2316
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-reference-net-types-from-com"></a><span data-ttu-id="2486d-102">Nasıl yapılır: COM'dan .NET Türlerine Başvurma</span><span class="sxs-lookup"><span data-stu-id="2486d-102">How to: Reference .NET Types from COM</span></span>
<span data-ttu-id="2486d-103">İstemci ve sunucu kodu point of görünümünü COM ve .NET Framework arasındaki farklar büyük ölçüde görünmez.</span><span class="sxs-lookup"><span data-stu-id="2486d-103">From the point of view of client and server code, the differences between COM and the .NET Framework are largely invisible.</span></span> <span data-ttu-id="2486d-104">Microsoft Visual Basic istemcileri .NET nesnesi sözdizimi, özelliklerini ve nesne yöntemleri sunar ve tam olarak herhangi bir COM nesnesi gibi alanları nesne tarayıcısında görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2486d-104">Microsoft Visual Basic clients can view a .NET object in the object browser, which exposes the object methods and syntax, properties, and fields exactly as if it were any other COM object.</span></span>  
  
 <span data-ttu-id="2486d-105">Tür kitaplığını içeri aktarma işlemi C++ istemcileri için biraz daha karmaşık olsa meta verileri için bir COM tür kitaplığı dışarı aktarmak için aynı araçlarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="2486d-105">The process for importing a type library is slightly more complicated for C++ clients, although you use the same tools to export metadata to a COM type library.</span></span> <span data-ttu-id="2486d-106">Yönetilmeyen bir C++ istemciden .NET nesne üyeleri başvurmak için ile (Tlbexp.exe ile üretilen) TLB dosya başvuru **#import** yönergesi.</span><span class="sxs-lookup"><span data-stu-id="2486d-106">To reference .NET object members from an unmanaged C++ client, reference the TLB file (produced with Tlbexp.exe) with the **#import** directive.</span></span> <span data-ttu-id="2486d-107">C++ içinden bir tür kitaplığı başvuru yapıldığında, ya da belirtmeniz gerekir **raw_interfaces_only** seçeneğini veya Mscorlib.tlb temel sınıf kitaplığı'nda tanımını içeri aktarın.</span><span class="sxs-lookup"><span data-stu-id="2486d-107">When referencing a type library from C++, you must either specify the **raw_interfaces_only** option or import the definitions in the base class library, Mscorlib.tlb.</span></span>  
  
### <a name="to-import-a-library"></a><span data-ttu-id="2486d-108">Bir kitaplık içeri aktarmak için</span><span class="sxs-lookup"><span data-stu-id="2486d-108">To import a library</span></span>  
  
-   <span data-ttu-id="2486d-109">Belirtin **raw_interfaces_only** seçeneğini **#import** yönergesi.</span><span class="sxs-lookup"><span data-stu-id="2486d-109">Specify the **raw_interfaces_only** option in the **#import** directive.</span></span> <span data-ttu-id="2486d-110">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="2486d-110">For example:</span></span>  
  
    ```cpp  
    #import "..\LoanLib\LoanLib.tlb" raw_interfaces_only  
    ```  
  
     <span data-ttu-id="2486d-111">veya</span><span class="sxs-lookup"><span data-stu-id="2486d-111">-or-</span></span>  
  
-   <span data-ttu-id="2486d-112">#İmport yönergesi için Mscorlib.tlb içerir.</span><span class="sxs-lookup"><span data-stu-id="2486d-112">Include an #import directive for Mscorlib.tlb.</span></span> <span data-ttu-id="2486d-113">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="2486d-113">For example:</span></span>  
  
    ```cpp  
    #import "mscorlib.tlb"  
    #import "..\LoanLib\LoanLib.tlb"  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="2486d-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2486d-114">See Also</span></span>  
 [<span data-ttu-id="2486d-115">.NET Framework Bileşenlerini COM'da Gösterme</span><span class="sxs-lookup"><span data-stu-id="2486d-115">Exposing .NET Framework Components to COM</span></span>](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [<span data-ttu-id="2486d-116">Bütünleştirilmiş Kodları COM ile Kaydetme</span><span class="sxs-lookup"><span data-stu-id="2486d-116">Registering Assemblies with COM</span></span>](../../../docs/framework/interop/registering-assemblies-with-com.md)  
 [<span data-ttu-id="2486d-117">Bir .NET nesnesini çağırma</span><span class="sxs-lookup"><span data-stu-id="2486d-117">Calling a .NET Object</span></span>](http://msdn.microsoft.com/en-us/40c9626c-aea6-4bad-b8f0-c1de462efd33)  
 [<span data-ttu-id="2486d-118">COM erişim için bir uygulama dağıtma</span><span class="sxs-lookup"><span data-stu-id="2486d-118">Deploying an Application for COM Access</span></span>](http://msdn.microsoft.com/en-us/fb63564c-c1b9-4655-a094-a235625882ce)

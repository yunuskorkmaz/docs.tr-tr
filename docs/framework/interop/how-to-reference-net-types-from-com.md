---
title: 'Nasıl yapılır: COM başvurusu .NET türlerinden'
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- importing type library
- COM interop, referencing .NET types
- interoperation with unmanaged code, referencing .NET types
- referencing .NET types
- interoperation with unmanaged code, importing type library
- type libraries
- COM interop, importing type library
ms.assetid: 54917f6f-cb18-4103-b622-856b55da93f3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9826f8af06693fdff0d5bea75cfa3f2586faa4f6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54582130"
---
# <a name="how-to-reference-net-types-from-com"></a><span data-ttu-id="051d9-102">Nasıl yapılır: COM başvurusu .NET türlerinden</span><span class="sxs-lookup"><span data-stu-id="051d9-102">How to: Reference .NET Types from COM</span></span>
<span data-ttu-id="051d9-103">Bakış açısıyla, istemci ve sunucu kodu, COM ve .NET Framework arasındaki farklar büyük ölçüde görünmez.</span><span class="sxs-lookup"><span data-stu-id="051d9-103">From the point of view of client and server code, the differences between COM and the .NET Framework are largely invisible.</span></span> <span data-ttu-id="051d9-104">Microsoft Visual Basic istemciler, bir .NET nesnesini sözdizimi, özelliklerini ve nesne yöntemleri ve tam olarak bunu herhangi bir COM nesnesi gibi alanlar nesne tarayıcısında görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="051d9-104">Microsoft Visual Basic clients can view a .NET object in the object browser, which exposes the object methods and syntax, properties, and fields exactly as if it were any other COM object.</span></span>  
  
 <span data-ttu-id="051d9-105">Meta veriler için bir COM tür kitaplığı dışarı aktarmak için aynı araçları kullanmanıza rağmen bir tür kitaplığını içeri aktarma işlemi C++ istemciler için biraz daha karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="051d9-105">The process for importing a type library is slightly more complicated for C++ clients, although you use the same tools to export metadata to a COM type library.</span></span> <span data-ttu-id="051d9-106">.NET nesne üyeleri bir yönetilmeyen C++ istemcisinden başvurmak için ile (Tlbexp.exe ile üretilen) TLB dosyasına başvurmak **#import** yönergesi.</span><span class="sxs-lookup"><span data-stu-id="051d9-106">To reference .NET object members from an unmanaged C++ client, reference the TLB file (produced with Tlbexp.exe) with the **#import** directive.</span></span> <span data-ttu-id="051d9-107">Bir tür kitaplığı C++'tan başvururken ya da belirtmelisiniz **raw_interfaces_only** seçeneğini veya Mscorlib.tlb temel sınıf kitaplığı'nda tanımlarını içe aktarın.</span><span class="sxs-lookup"><span data-stu-id="051d9-107">When referencing a type library from C++, you must either specify the **raw_interfaces_only** option or import the definitions in the base class library, Mscorlib.tlb.</span></span>  
  
### <a name="to-import-a-library"></a><span data-ttu-id="051d9-108">Bir kitaplığı içeri aktarmak için</span><span class="sxs-lookup"><span data-stu-id="051d9-108">To import a library</span></span>  
  
-   <span data-ttu-id="051d9-109">Belirtin **raw_interfaces_only** seçeneğini **#import** yönergesi.</span><span class="sxs-lookup"><span data-stu-id="051d9-109">Specify the **raw_interfaces_only** option in the **#import** directive.</span></span> <span data-ttu-id="051d9-110">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="051d9-110">For example:</span></span>  
  
    ```cpp  
    #import "..\LoanLib\LoanLib.tlb" raw_interfaces_only  
    ```  
  
     <span data-ttu-id="051d9-111">-veya-</span><span class="sxs-lookup"><span data-stu-id="051d9-111">-or-</span></span>  
  
-   <span data-ttu-id="051d9-112">#İmport yönergesi için Mscorlib.tlb içerir.</span><span class="sxs-lookup"><span data-stu-id="051d9-112">Include an #import directive for Mscorlib.tlb.</span></span> <span data-ttu-id="051d9-113">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="051d9-113">For example:</span></span>  
  
    ```cpp  
    #import "mscorlib.tlb"  
    #import "..\LoanLib\LoanLib.tlb"  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="051d9-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="051d9-114">See also</span></span>
- [<span data-ttu-id="051d9-115">.NET Framework Bileşenlerini COM'da Gösterme</span><span class="sxs-lookup"><span data-stu-id="051d9-115">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="051d9-116">Bütünleştirilmiş Kodları COM ile Kaydetme</span><span class="sxs-lookup"><span data-stu-id="051d9-116">Registering Assemblies with COM</span></span>](registering-assemblies-with-com.md)
- <span data-ttu-id="051d9-117">[Bir .NET nesnesini çağırma](https://msdn.microsoft.com/library/40c9626c-aea6-4bad-b8f0-c1de462efd33(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="051d9-117">[Calling a .NET Object](https://msdn.microsoft.com/library/40c9626c-aea6-4bad-b8f0-c1de462efd33(v=vs.100))</span></span>
- <span data-ttu-id="051d9-118">[COM erişimi için bir uygulama dağıtma](https://msdn.microsoft.com/library/fb63564c-c1b9-4655-a094-a235625882ce(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="051d9-118">[Deploying an Application for COM Access](https://msdn.microsoft.com/library/fb63564c-c1b9-4655-a094-a235625882ce(v=vs.100))</span></span>

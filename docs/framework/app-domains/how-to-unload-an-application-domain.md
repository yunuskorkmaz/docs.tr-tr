---
title: 'Nasıl yapılır: Bir uygulama etki alanını boşaltma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Unload method
- application domains, unloading
- unloading application domains
ms.assetid: f356116d-e415-4f7c-a332-6e6a60227192
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 42356348ba454ffe0c3778e23dc9a0ff272c9f64
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54727748"
---
# <a name="how-to-unload-an-application-domain"></a><span data-ttu-id="92eaa-102">Nasıl yapılır: Bir uygulama etki alanını boşaltma</span><span class="sxs-lookup"><span data-stu-id="92eaa-102">How to: Unload an Application Domain</span></span>
<span data-ttu-id="92eaa-103">Uygulama etki alanı kullanarak tamamladığınızda kullanarak kaldırma <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="92eaa-103">When you have finished using an application domain, unload it using the <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="92eaa-104">**Kaldırma** yöntemi düzgün bir şekilde belirtilen uygulama etki alanı kapatır.</span><span class="sxs-lookup"><span data-stu-id="92eaa-104">The **Unload** method gracefully shuts down the specified application domain.</span></span> <span data-ttu-id="92eaa-105">Kaldırma işlemi sırasında hiçbir yeni iş parçacığı uygulama etki alanı erişebilir ve tüm uygulama etki alanına özgü veri yapıları serbest.</span><span class="sxs-lookup"><span data-stu-id="92eaa-105">During the unloading process, no new threads can access the application domain, and all application domain–specific data structures are freed.</span></span>  
  
 <span data-ttu-id="92eaa-106">Uygulama etki alanına yüklenen derlemelerin kaldırılır ve artık kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="92eaa-106">Assemblies loaded into the application domain are removed and are no longer available.</span></span> <span data-ttu-id="92eaa-107">Uygulama etki alanındaki bir derleme etki alanından bağımsız ise, derleme için veri işlem kapatılana kadar bellekte kalır.</span><span class="sxs-lookup"><span data-stu-id="92eaa-107">If an assembly in the application domain is domain-neutral, data for the assembly remains in memory until the entire process is shut down.</span></span> <span data-ttu-id="92eaa-108">Tüm işlemi kapatma dışındaki bir etki alanından bağımsız derleme kaldırmak için bir mekanizma yoktur.</span><span class="sxs-lookup"><span data-stu-id="92eaa-108">There is no mechanism to unload a domain-neutral assembly other than shutting down the entire process.</span></span> <span data-ttu-id="92eaa-109">Burada, bir uygulama etki alanını boşaltma isteği çalışmıyor ve sonuçlanır durumlar vardır bir <xref:System.CannotUnloadAppDomainException>.</span><span class="sxs-lookup"><span data-stu-id="92eaa-109">There are situations where the request to unload an application domain does not work and results in a <xref:System.CannotUnloadAppDomainException>.</span></span>  
  
 <span data-ttu-id="92eaa-110">Aşağıdaki örnekte adlı yeni bir uygulama etki alanı oluşturur `MyDomain`bazı bilgileri konsola yazdırır ve ardından uygulama etki alanını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="92eaa-110">The following example creates a new application domain called `MyDomain`, prints some information to the console, and then unloads the application domain.</span></span> <span data-ttu-id="92eaa-111">Kodu daha sonra konsola bellekten uygulama etki alanının kolay adını yazdırmak çalışır olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="92eaa-111">Note that the code then attempts to print the friendly name of the unloaded application domain to the console.</span></span> <span data-ttu-id="92eaa-112">Bu eylem, programın sonunda try/catch deyimleri tarafından işlenen özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="92eaa-112">This action generates an exception that is handled by the try/catch statements at the end of the program.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92eaa-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="92eaa-113">Example</span></span>  
 [!code-cpp[System.AppDomain.Load#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source3.cpp#3)]
 [!code-csharp[System.AppDomain.Load#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source3.cs#3)]
 [!code-vb[System.AppDomain.Load#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source3.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="92eaa-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="92eaa-114">See also</span></span>
- [<span data-ttu-id="92eaa-115">Uygulama etki alanlarıyla programlama</span><span class="sxs-lookup"><span data-stu-id="92eaa-115">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="92eaa-116">Nasıl yapılır: Bir uygulama etki alanı oluşturma</span><span class="sxs-lookup"><span data-stu-id="92eaa-116">How to: Create an Application Domain</span></span>](../../../docs/framework/app-domains/how-to-create-an-application-domain.md)
- [<span data-ttu-id="92eaa-117">Uygulama Etki Alanlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="92eaa-117">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)

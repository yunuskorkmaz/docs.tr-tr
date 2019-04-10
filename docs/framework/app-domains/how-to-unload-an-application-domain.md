---
title: 'Nasıl yapılır: Uygulama Etki Alanını Boşaltma'
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
ms.openlocfilehash: f3011bd0327440cd04d5eccf5f88c036ddd76267
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59212186"
---
# <a name="how-to-unload-an-application-domain"></a><span data-ttu-id="c581b-102">Nasıl yapılır: Uygulama Etki Alanını Boşaltma</span><span class="sxs-lookup"><span data-stu-id="c581b-102">How to: Unload an Application Domain</span></span>
<span data-ttu-id="c581b-103">Uygulama etki alanı kullanarak tamamladığınızda kullanarak kaldırma <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c581b-103">When you have finished using an application domain, unload it using the <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="c581b-104">**Kaldırma** yöntemi düzgün bir şekilde belirtilen uygulama etki alanı kapatır.</span><span class="sxs-lookup"><span data-stu-id="c581b-104">The **Unload** method gracefully shuts down the specified application domain.</span></span> <span data-ttu-id="c581b-105">Kaldırma işlemi sırasında hiçbir yeni iş parçacığı uygulama etki alanı erişebilir ve tüm uygulama etki alanına özgü veri yapıları serbest.</span><span class="sxs-lookup"><span data-stu-id="c581b-105">During the unloading process, no new threads can access the application domain, and all application domain–specific data structures are freed.</span></span>  
  
 <span data-ttu-id="c581b-106">Uygulama etki alanına yüklenen derlemelerin kaldırılır ve artık kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="c581b-106">Assemblies loaded into the application domain are removed and are no longer available.</span></span> <span data-ttu-id="c581b-107">Uygulama etki alanındaki bir derleme etki alanından bağımsız ise, derleme için veri işlem kapatılana kadar bellekte kalır.</span><span class="sxs-lookup"><span data-stu-id="c581b-107">If an assembly in the application domain is domain-neutral, data for the assembly remains in memory until the entire process is shut down.</span></span> <span data-ttu-id="c581b-108">Tüm işlemi kapatma dışındaki bir etki alanından bağımsız derleme kaldırmak için bir mekanizma yoktur.</span><span class="sxs-lookup"><span data-stu-id="c581b-108">There is no mechanism to unload a domain-neutral assembly other than shutting down the entire process.</span></span> <span data-ttu-id="c581b-109">Burada, bir uygulama etki alanını boşaltma isteği çalışmıyor ve sonuçlanır durumlar vardır bir <xref:System.CannotUnloadAppDomainException>.</span><span class="sxs-lookup"><span data-stu-id="c581b-109">There are situations where the request to unload an application domain does not work and results in a <xref:System.CannotUnloadAppDomainException>.</span></span>  
  
 <span data-ttu-id="c581b-110">Aşağıdaki örnekte adlı yeni bir uygulama etki alanı oluşturur `MyDomain`bazı bilgileri konsola yazdırır ve ardından uygulama etki alanını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="c581b-110">The following example creates a new application domain called `MyDomain`, prints some information to the console, and then unloads the application domain.</span></span> <span data-ttu-id="c581b-111">Kodu daha sonra konsola bellekten uygulama etki alanının kolay adını yazdırmak çalışır olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c581b-111">Note that the code then attempts to print the friendly name of the unloaded application domain to the console.</span></span> <span data-ttu-id="c581b-112">Bu eylem, programın sonunda try/catch deyimleri tarafından işlenen özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c581b-112">This action generates an exception that is handled by the try/catch statements at the end of the program.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c581b-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="c581b-113">Example</span></span>  
 [!code-cpp[System.AppDomain.Load#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source3.cpp#3)]
 [!code-csharp[System.AppDomain.Load#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source3.cs#3)]
 [!code-vb[System.AppDomain.Load#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source3.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="c581b-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c581b-114">See also</span></span>

- [<span data-ttu-id="c581b-115">Uygulama Etki Alanlarıyla Programlama</span><span class="sxs-lookup"><span data-stu-id="c581b-115">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="c581b-116">Nasıl yapılır: Uygulama Etki Alanı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c581b-116">How to: Create an Application Domain</span></span>](../../../docs/framework/app-domains/how-to-create-an-application-domain.md)
- [<span data-ttu-id="c581b-117">Uygulama Etki Alanlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="c581b-117">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)

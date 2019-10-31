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
ms.openlocfilehash: 4d5f98229c3a9da69a350ae325cd42e8deb6b7bc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119842"
---
# <a name="how-to-unload-an-application-domain"></a><span data-ttu-id="5babf-102">Nasıl yapılır: Uygulama Etki Alanını Boşaltma</span><span class="sxs-lookup"><span data-stu-id="5babf-102">How to: Unload an Application Domain</span></span>
<span data-ttu-id="5babf-103">Bir uygulama etki alanını kullanmayı bitirdiğinizde <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> yöntemini kullanarak kaldırın.</span><span class="sxs-lookup"><span data-stu-id="5babf-103">When you have finished using an application domain, unload it using the <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="5babf-104">**Unload** yöntemi, belirtilen uygulama etki alanını düzgün bir şekilde kapatır.</span><span class="sxs-lookup"><span data-stu-id="5babf-104">The **Unload** method gracefully shuts down the specified application domain.</span></span> <span data-ttu-id="5babf-105">Kaldırma işlemi sırasında, uygulama etki alanına hiçbir yeni iş parçacığı erişemez ve tüm uygulama etki alanına özgü veri yapıları serbest bırakılır.</span><span class="sxs-lookup"><span data-stu-id="5babf-105">During the unloading process, no new threads can access the application domain, and all application domain–specific data structures are freed.</span></span>  
  
 <span data-ttu-id="5babf-106">Uygulama etki alanına yüklenen derlemeler kaldırılır ve artık kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="5babf-106">Assemblies loaded into the application domain are removed and are no longer available.</span></span> <span data-ttu-id="5babf-107">Uygulama etki alanındaki bir derleme etki alanı Tarafsız ise, derleme verileri tüm işlem kapanana kadar bellekte kalır.</span><span class="sxs-lookup"><span data-stu-id="5babf-107">If an assembly in the application domain is domain-neutral, data for the assembly remains in memory until the entire process is shut down.</span></span> <span data-ttu-id="5babf-108">İşlemin tamamını kapatmaktan başka bir etki alanı nötr derlemeyi kaldırma mekanizması yoktur.</span><span class="sxs-lookup"><span data-stu-id="5babf-108">There is no mechanism to unload a domain-neutral assembly other than shutting down the entire process.</span></span> <span data-ttu-id="5babf-109">Bir uygulama etki alanını kaldırma isteğinin çalışmamasına ve <xref:System.CannotUnloadAppDomainException>neden olduğu durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="5babf-109">There are situations where the request to unload an application domain does not work and results in a <xref:System.CannotUnloadAppDomainException>.</span></span>  
  
 <span data-ttu-id="5babf-110">Aşağıdaki örnek `MyDomain`adlı yeni bir uygulama etki alanı oluşturur, konsola bazı bilgileri yazdırır ve ardından uygulama etki alanını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="5babf-110">The following example creates a new application domain called `MyDomain`, prints some information to the console, and then unloads the application domain.</span></span> <span data-ttu-id="5babf-111">Kodu daha sonra, kaldırılan uygulama etki alanının kolay adını konsola yazdırmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="5babf-111">Note that the code then attempts to print the friendly name of the unloaded application domain to the console.</span></span> <span data-ttu-id="5babf-112">Bu eylem, programın sonundaki try/catch deyimleri tarafından işlenen bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5babf-112">This action generates an exception that is handled by the try/catch statements at the end of the program.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5babf-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="5babf-113">Example</span></span>  
 [!code-cpp[System.AppDomain.Load#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source3.cpp#3)]
 [!code-csharp[System.AppDomain.Load#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source3.cs#3)]
 [!code-vb[System.AppDomain.Load#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source3.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="5babf-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5babf-114">See also</span></span>

- [<span data-ttu-id="5babf-115">Uygulama etki alanlarıyla programlama</span><span class="sxs-lookup"><span data-stu-id="5babf-115">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="5babf-116">Nasıl yapılır: Uygulama Etki Alanı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5babf-116">How to: Create an Application Domain</span></span>](how-to-create-an-application-domain.md)
- [<span data-ttu-id="5babf-117">Uygulama Etki Alanlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="5babf-117">Using Application Domains</span></span>](use.md)

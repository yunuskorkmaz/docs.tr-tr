---
title: 'Nasıl yapılır: Uygulama Etki Alanını Boşaltma'
description: Belirtilen uygulama etki alanını düzgün bir şekilde kapatmak için AppDomain. Unload metodunu kullanarak .NET 'teki bir uygulama etki alanını nasıl kaldırabileceğini okuyun.
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
ms.openlocfilehash: b64a9553f63aa4a8deb57f23a97fa464edd64fee
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104674"
---
# <a name="how-to-unload-an-application-domain"></a><span data-ttu-id="6893a-103">Nasıl yapılır: Uygulama Etki Alanını Boşaltma</span><span class="sxs-lookup"><span data-stu-id="6893a-103">How to: Unload an Application Domain</span></span>
<span data-ttu-id="6893a-104">Bir uygulama etki alanını kullanmayı bitirdiğinizde metodunu kullanarak kaldırın <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="6893a-104">When you have finished using an application domain, unload it using the <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="6893a-105">**Unload** yöntemi, belirtilen uygulama etki alanını düzgün bir şekilde kapatır.</span><span class="sxs-lookup"><span data-stu-id="6893a-105">The **Unload** method gracefully shuts down the specified application domain.</span></span> <span data-ttu-id="6893a-106">Kaldırma işlemi sırasında, uygulama etki alanına hiçbir yeni iş parçacığı erişemez ve tüm uygulama etki alanına özgü veri yapıları serbest bırakılır.</span><span class="sxs-lookup"><span data-stu-id="6893a-106">During the unloading process, no new threads can access the application domain, and all application domain–specific data structures are freed.</span></span>  
  
 <span data-ttu-id="6893a-107">Uygulama etki alanına yüklenen derlemeler kaldırılır ve artık kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="6893a-107">Assemblies loaded into the application domain are removed and are no longer available.</span></span> <span data-ttu-id="6893a-108">Uygulama etki alanındaki bir derleme etki alanı Tarafsız ise, derleme verileri tüm işlem kapanana kadar bellekte kalır.</span><span class="sxs-lookup"><span data-stu-id="6893a-108">If an assembly in the application domain is domain-neutral, data for the assembly remains in memory until the entire process is shut down.</span></span> <span data-ttu-id="6893a-109">İşlemin tamamını kapatmaktan başka bir etki alanı nötr derlemeyi kaldırma mekanizması yoktur.</span><span class="sxs-lookup"><span data-stu-id="6893a-109">There is no mechanism to unload a domain-neutral assembly other than shutting down the entire process.</span></span> <span data-ttu-id="6893a-110">Bir uygulama etki alanını kaldırma isteğinin çalışmamasına ve bir ile sonuçlanmasına neden olan durumlar vardır <xref:System.CannotUnloadAppDomainException> .</span><span class="sxs-lookup"><span data-stu-id="6893a-110">There are situations where the request to unload an application domain does not work and results in a <xref:System.CannotUnloadAppDomainException>.</span></span>  
  
 <span data-ttu-id="6893a-111">Aşağıdaki örnek adlı yeni bir uygulama etki alanı oluşturur `MyDomain` , konsola bazı bilgileri yazdırır ve ardından uygulama etki alanını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="6893a-111">The following example creates a new application domain called `MyDomain`, prints some information to the console, and then unloads the application domain.</span></span> <span data-ttu-id="6893a-112">Kodu daha sonra, kaldırılan uygulama etki alanının kolay adını konsola yazdırmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="6893a-112">Note that the code then attempts to print the friendly name of the unloaded application domain to the console.</span></span> <span data-ttu-id="6893a-113">Bu eylem, programın sonundaki try/catch deyimleri tarafından işlenen bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6893a-113">This action generates an exception that is handled by the try/catch statements at the end of the program.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6893a-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="6893a-114">Example</span></span>  
 [!code-cpp[System.AppDomain.Load#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source3.cpp#3)]
 [!code-csharp[System.AppDomain.Load#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source3.cs#3)]
 [!code-vb[System.AppDomain.Load#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source3.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="6893a-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6893a-115">See also</span></span>

- [<span data-ttu-id="6893a-116">Uygulama etki alanlarıyla programlama</span><span class="sxs-lookup"><span data-stu-id="6893a-116">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="6893a-117">Nasıl yapılır: Uygulama Etki Alanı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="6893a-117">How to: Create an Application Domain</span></span>](how-to-create-an-application-domain.md)
- [<span data-ttu-id="6893a-118">Uygulama Etki Alanlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="6893a-118">Using Application Domains</span></span>](use.md)

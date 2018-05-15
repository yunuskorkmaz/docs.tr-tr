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
ms.openlocfilehash: 0a9e5ee865b5e0ac9ec0214a4a0b5194bbcd9f30
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-unload-an-application-domain"></a><span data-ttu-id="2820b-102">Nasıl yapılır: Uygulama Etki Alanını Boşaltma</span><span class="sxs-lookup"><span data-stu-id="2820b-102">How to: Unload an Application Domain</span></span>
<span data-ttu-id="2820b-103">Uygulama etki alanı ile işiniz bittiğinde, kullanarak unload <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2820b-103">When you have finished using an application domain, unload it using the <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="2820b-104">**Unload** yöntemi, belirtilen uygulama etki alanı düzgün biçimde kapatır.</span><span class="sxs-lookup"><span data-stu-id="2820b-104">The **Unload** method gracefully shuts down the specified application domain.</span></span> <span data-ttu-id="2820b-105">Kaldırma işlemi sırasında hiçbir yeni iş parçacıkları uygulama etki alanı erişebilir ve tüm uygulama etki alanı – özel veri yapıları serbest.</span><span class="sxs-lookup"><span data-stu-id="2820b-105">During the unloading process, no new threads can access the application domain, and all application domain–specific data structures are freed.</span></span>  
  
 <span data-ttu-id="2820b-106">Uygulama etki alanına yüklenmiş derlemeleri kaldırılır ve artık kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="2820b-106">Assemblies loaded into the application domain are removed and are no longer available.</span></span> <span data-ttu-id="2820b-107">Bütünleştirilmiş uygulama etki alanındaki etki alanı neutral ise, veri derleme için bütün işlem kapatılana kadar bellekte kalır.</span><span class="sxs-lookup"><span data-stu-id="2820b-107">If an assembly in the application domain is domain-neutral, data for the assembly remains in memory until the entire process is shut down.</span></span> <span data-ttu-id="2820b-108">Tüm işlem kapatılıyor dışında bir etki alanı Tarafsız derleme kaldırmak için bir mekanizma yoktur.</span><span class="sxs-lookup"><span data-stu-id="2820b-108">There is no mechanism to unload a domain-neutral assembly other than shutting down the entire process.</span></span> <span data-ttu-id="2820b-109">Burada bir uygulama etki alanını boşaltma isteği çalışmaz ve sonuçlanır durumlar vardır bir <xref:System.CannotUnloadAppDomainException>.</span><span class="sxs-lookup"><span data-stu-id="2820b-109">There are situations where the request to unload an application domain does not work and results in a <xref:System.CannotUnloadAppDomainException>.</span></span>  
  
 <span data-ttu-id="2820b-110">Aşağıdaki örnek olarak adlandırılan yeni bir uygulama etki alanı oluşturur `MyDomain`, bazı bilgileri konsola yazdırır ve uygulama etki alanı kaldırır.</span><span class="sxs-lookup"><span data-stu-id="2820b-110">The following example creates a new application domain called `MyDomain`, prints some information to the console, and then unloads the application domain.</span></span> <span data-ttu-id="2820b-111">Kodu daha sonra konsola bellekten uygulama etki alanı kolay adını yazdırmak çalışır olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2820b-111">Note that the code then attempts to print the friendly name of the unloaded application domain to the console.</span></span> <span data-ttu-id="2820b-112">Bu eylem, program sonunda try/catch deyimleri tarafından işlenen bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2820b-112">This action generates an exception that is handled by the try/catch statements at the end of the program.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2820b-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="2820b-113">Example</span></span>  
 [!code-cpp[System.AppDomain.Load#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source3.cpp#3)]
 [!code-csharp[System.AppDomain.Load#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source3.cs#3)]
 [!code-vb[System.AppDomain.Load#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source3.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="2820b-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2820b-114">See Also</span></span>  
 [<span data-ttu-id="2820b-115">Uygulama etki alanları ile programlama</span><span class="sxs-lookup"><span data-stu-id="2820b-115">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)  
 [<span data-ttu-id="2820b-116">Nasıl yapılır: Uygulama Etki Alanı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="2820b-116">How to: Create an Application Domain</span></span>](../../../docs/framework/app-domains/how-to-create-an-application-domain.md)  
 [<span data-ttu-id="2820b-117">Uygulama Etki Alanlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="2820b-117">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)

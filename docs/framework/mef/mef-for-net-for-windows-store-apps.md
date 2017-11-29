---
title: "Windows mağazası uygulamaları için .NET için MEF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7667770e-d163-4ad6-a303-085cf73db2f2
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7f427656f9b385214db5b3bd26c4addb1122b35a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="mef-for-net-for-windows-store-apps"></a><span data-ttu-id="db5e3-102">Windows mağazası uygulamaları için .NET için MEF</span><span class="sxs-lookup"><span data-stu-id="db5e3-102">MEF for .NET for Windows Store Apps</span></span>
<span data-ttu-id="db5e3-103"><xref:System.Composition?displayProperty=nameWithType>ve onun alt ad alanları içeren geliştirmek için Genişletilebilir türleri [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamaları Yönetilen Genişletilebilirlik Çerçevesi (MEF) sahip.</span><span class="sxs-lookup"><span data-stu-id="db5e3-103"><xref:System.Composition?displayProperty=nameWithType> and its child namespaces contain types for developing extensible [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps with Managed Extensibility Framework (MEF).</span></span> <span data-ttu-id="db5e3-104">Bu ad alanları parçası olan [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] alt için [!INCLUDE[win8](../../../includes/win8-md.md)] işletim sistemi.</span><span class="sxs-lookup"><span data-stu-id="db5e3-104">These namespaces are part of the [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] subset for the [!INCLUDE[win8](../../../includes/win8-md.md)] operating system.</span></span>  
  
 <span data-ttu-id="db5e3-105">Bu ad alanları .NET Framework ile dağıtılan çekirdek sınıf kitaplığına parçası değildir.</span><span class="sxs-lookup"><span data-stu-id="db5e3-105">These namespaces are not part of the core class library distributed with the .NET Framework.</span></span> <span data-ttu-id="db5e3-106">Bu ad alanları yüklemek için projenizi açın [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], seçin **NuGet paketlerini Yönet** gelen **proje** menü ve çevrimiçi Microsoft.Composition paketi için arama.</span><span class="sxs-lookup"><span data-stu-id="db5e3-106">To install these namespaces, open your project in [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], choose **Manage NuGet Packages** from the **Project** menu, and search online for the Microsoft.Composition package.</span></span>  
  
-   <span data-ttu-id="db5e3-107"><xref:System.Composition?displayProperty=nameWithType>MEF çekirdek oluşturan sınıflar sağlar için [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="db5e3-107"><xref:System.Composition?displayProperty=nameWithType> provides classes that constitute the core MEF for [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps.</span></span>  
  
-   <span data-ttu-id="db5e3-108"><xref:System.Composition.Convention?displayProperty=nameWithType>bir kurala dayalı yapılandırma modeliyle MEF kullanarak destekleyen türler sağlar.</span><span class="sxs-lookup"><span data-stu-id="db5e3-108"><xref:System.Composition.Convention?displayProperty=nameWithType> provides types that support using MEF with a convention-based configuration model.</span></span>  
  
-   <span data-ttu-id="db5e3-109"><xref:System.Composition.Hosting?displayProperty=nameWithType>ana bilgisayar uygulaması geliştiricileri için faydalı MEF türler sağlar.</span><span class="sxs-lookup"><span data-stu-id="db5e3-109"><xref:System.Composition.Hosting?displayProperty=nameWithType> provides MEF types that are useful to developers of host applications.</span></span>  
  
-   <span data-ttu-id="db5e3-110"><xref:System.Composition.Hosting.Core?displayProperty=nameWithType>bileşim motoru tarafından dahili olarak kullanılan MEF türler sağlar.</span><span class="sxs-lookup"><span data-stu-id="db5e3-110"><xref:System.Composition.Hosting.Core?displayProperty=nameWithType> provides MEF types used internally by the composition engine.</span></span>  
  
 <span data-ttu-id="db5e3-111">Hakkında daha fazla bilgi için [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] ve ad alanları ve içerdiği türleri listesini görmek [.NET için Windows mağazası uygulamalarına genel bakış](http://go.microsoft.com/fwlink/p/?LinkID=238312) Windows geliştirme Merkezi'ndeki.</span><span class="sxs-lookup"><span data-stu-id="db5e3-111">For more information about [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] and a list of namespaces and types that it contains, see [.NET for Windows Store apps overview](http://go.microsoft.com/fwlink/p/?LinkID=238312) in the Windows Dev Center.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db5e3-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="db5e3-112">See Also</span></span>  
 [<span data-ttu-id="db5e3-113">.NET için Windows mağazası uygulamalarına genel bakış</span><span class="sxs-lookup"><span data-stu-id="db5e3-113">.NET for Windows Store apps overview</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=238312)  
 [<span data-ttu-id="db5e3-114">.NET için Windows mağazası uygulamaları – desteklenen API'leri</span><span class="sxs-lookup"><span data-stu-id="db5e3-114">.NET for Windows Store apps – supported APIs</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=247912)  
 [<span data-ttu-id="db5e3-115">Yönetilen Genişletilebilirlik Çerçevesi (MEF)</span><span class="sxs-lookup"><span data-stu-id="db5e3-115">Managed Extensibility Framework (MEF)</span></span>](../../../docs/framework/mef/index.md)

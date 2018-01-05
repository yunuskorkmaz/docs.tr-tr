---
title: ".NET Framework'te Güvenlik Değişiklikleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Allow Partially Trusted Callers attribute
- .NET Framework 4, security changes
- .NET Framework security
- security-transparent code
- security-critical code
- code access security, changes
ms.assetid: 5e87881c-9c13-4b52-8ad1-e34bb46e8aaa
caps.latest.revision: "52"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0777b2566337427abd116bb3584bc19e67d34803
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="security-changes-in-the-net-framework"></a><span data-ttu-id="d9ba2-102">.NET Framework'te Güvenlik Değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="d9ba2-102">Security Changes in the .NET Framework</span></span>
<span data-ttu-id="d9ba2-103">Güvenlik için en önemli bir değişiklik [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] güçlü adlandırma içinde değil.</span><span class="sxs-lookup"><span data-stu-id="d9ba2-103">The most important change to security in the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] is in strong naming.</span></span> <span data-ttu-id="d9ba2-104">Bkz: [Gelişmiş tanımlayıcı adlandırma](../../../docs/framework/app-domains/enhanced-strong-naming.md) bu değişikliklerin bir açıklaması için.</span><span class="sxs-lookup"><span data-stu-id="d9ba2-104">See [Enhanced Strong Naming](../../../docs/framework/app-domains/enhanced-strong-naming.md) for a description of those changes.</span></span>  
  
 <span data-ttu-id="d9ba2-105">.NET Framework, yönetilen uygulamaları için iki katmanlı güvenlik modeli sağlar.</span><span class="sxs-lookup"><span data-stu-id="d9ba2-105">The .NET Framework provides a two-tier security model for managed applications.</span></span> [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]<span data-ttu-id="d9ba2-106"> uygulamaları, kaynaklara erişimi sınırlayan bir Windows güvenlik kapsayıcısında çalışır.</span><span class="sxs-lookup"><span data-stu-id="d9ba2-106"> apps run in a Windows security container that limits access to resources.</span></span> <span data-ttu-id="d9ba2-107">Bu kapsayıcıda yönetilen uygulamaların tam olarak güvenilmeyen çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d9ba2-107">Within that container, managed applications run fully trusted.</span></span> <span data-ttu-id="d9ba2-108">Kod erişim güvenliği (CAS) açısından, hiçbir şey yoktur Geliştirici ayrıcalık yükseltme yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d9ba2-108">From a code access security (CAS) perspective, there is nothing a developer can do to elevate privileges.</span></span> <span data-ttu-id="d9ba2-109">Windows tarafından verilen izinler hakkında daha fazla bilgi için bkz: [uygulama yeteneği bildirimleri (Windows mağazası uygulamaları)](http://go.microsoft.com/fwlink/?LinkId=230436) Windows geliştirme Merkezi'ndeki.</span><span class="sxs-lookup"><span data-stu-id="d9ba2-109">For information about the privileges granted by Windows, see [App capability declarations (Windows Store apps)](http://go.microsoft.com/fwlink/?LinkId=230436) in the Windows Dev Center.</span></span> <span data-ttu-id="d9ba2-110">Oluşturma hakkında daha fazla bilgi için bir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulama, bkz: [C# veya Visual Basic kullanarak ilk Windows mağazası uygulamanızı oluşturma](http://go.microsoft.com/fwlink/?LinkId=230461).</span><span class="sxs-lookup"><span data-stu-id="d9ba2-110">For information about creating a [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app, see [Create your first Windows Store app using C# or Visual Basic](http://go.microsoft.com/fwlink/?LinkId=230461).</span></span>

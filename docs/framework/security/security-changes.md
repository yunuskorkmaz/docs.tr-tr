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
ms.openlocfilehash: c1a96e30527aa3da4274ed55059b24aa5a7eeb47
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="security-changes-in-the-net-framework"></a><span data-ttu-id="1f987-102">.NET Framework'te Güvenlik Değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="1f987-102">Security Changes in the .NET Framework</span></span>
<span data-ttu-id="1f987-103">Güvenlik için en önemli bir değişiklik [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] güçlü adlandırma içinde değil.</span><span class="sxs-lookup"><span data-stu-id="1f987-103">The most important change to security in the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] is in strong naming.</span></span> <span data-ttu-id="1f987-104">Bkz: [Gelişmiş tanımlayıcı adlandırma](../../../docs/framework/app-domains/enhanced-strong-naming.md) bu değişikliklerin bir açıklaması için.</span><span class="sxs-lookup"><span data-stu-id="1f987-104">See [Enhanced Strong Naming](../../../docs/framework/app-domains/enhanced-strong-naming.md) for a description of those changes.</span></span>  
  
 <span data-ttu-id="1f987-105">.NET Framework, yönetilen uygulamaları için iki katmanlı güvenlik modeli sağlar.</span><span class="sxs-lookup"><span data-stu-id="1f987-105">The .NET Framework provides a two-tier security model for managed applications.</span></span> [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]<span data-ttu-id="1f987-106"> uygulamaları, kaynaklara erişimi sınırlayan bir Windows güvenlik kapsayıcısında çalışır.</span><span class="sxs-lookup"><span data-stu-id="1f987-106"> apps run in a Windows security container that limits access to resources.</span></span> <span data-ttu-id="1f987-107">Bu kapsayıcıda yönetilen uygulamaların tam olarak güvenilmeyen çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1f987-107">Within that container, managed applications run fully trusted.</span></span> <span data-ttu-id="1f987-108">Kod erişim güvenliği (CAS) açısından, hiçbir şey yoktur Geliştirici ayrıcalık yükseltme yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1f987-108">From a code access security (CAS) perspective, there is nothing a developer can do to elevate privileges.</span></span> <span data-ttu-id="1f987-109">Windows tarafından verilen izinler hakkında daha fazla bilgi için bkz: [uygulama yeteneği bildirimleri (Windows mağazası uygulamaları)](http://go.microsoft.com/fwlink/?LinkId=230436) Windows geliştirme Merkezi'ndeki.</span><span class="sxs-lookup"><span data-stu-id="1f987-109">For information about the privileges granted by Windows, see [App capability declarations (Windows Store apps)](http://go.microsoft.com/fwlink/?LinkId=230436) in the Windows Dev Center.</span></span> <span data-ttu-id="1f987-110">Oluşturma hakkında daha fazla bilgi için bir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulama, bkz: [C# veya Visual Basic kullanarak ilk Windows mağazası uygulamanızı oluşturma](http://go.microsoft.com/fwlink/?LinkId=230461).</span><span class="sxs-lookup"><span data-stu-id="1f987-110">For information about creating a [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app, see [Create your first Windows Store app using C# or Visual Basic](http://go.microsoft.com/fwlink/?LinkId=230461).</span></span>

---
title: .NET Framework'te Güvenlik Değişiklikleri
ms.date: 03/30/2017
helpviewer_keywords:
- Allow Partially Trusted Callers attribute
- .NET Framework 4, security changes
- .NET Framework security
- security-transparent code
- security-critical code
- code access security, changes
ms.assetid: 5e87881c-9c13-4b52-8ad1-e34bb46e8aaa
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 61f9e68bcc554dc3e4a4878e575d3f046a8ef9f5
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66378600"
---
# <a name="security-changes-in-the-net-framework"></a><span data-ttu-id="1da9b-102">.NET Framework'te Güvenlik Değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="1da9b-102">Security Changes in the .NET Framework</span></span>
<span data-ttu-id="1da9b-103">En önemli .NET Framework 4. 5'deki güvenlik tanımlayıcı adlandırma değişikliktir.</span><span class="sxs-lookup"><span data-stu-id="1da9b-103">The most important change to security in the .NET Framework 4.5 is in strong naming.</span></span> <span data-ttu-id="1da9b-104">Bkz: [Gelişmiş kesin adlandırma](../../../docs/framework/app-domains/enhanced-strong-naming.md) bu değişikliklerin bir açıklaması için.</span><span class="sxs-lookup"><span data-stu-id="1da9b-104">See [Enhanced Strong Naming](../../../docs/framework/app-domains/enhanced-strong-naming.md) for a description of those changes.</span></span>  
  
 <span data-ttu-id="1da9b-105">.NET Framework yönetilen uygulamalar için iki katmanlı güvenlik modeli sağlar.</span><span class="sxs-lookup"><span data-stu-id="1da9b-105">The .NET Framework provides a two-tier security model for managed applications.</span></span> [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] <span data-ttu-id="1da9b-106">uygulamaları, kaynaklara erişimi sınırlayan bir Windows güvenlik kapsayıcısında çalışır.</span><span class="sxs-lookup"><span data-stu-id="1da9b-106">apps run in a Windows security container that limits access to resources.</span></span> <span data-ttu-id="1da9b-107">Bu kapsayıcı içinde yönetilen uygulamaların tam olarak güvenilen çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1da9b-107">Within that container, managed applications run fully trusted.</span></span> <span data-ttu-id="1da9b-108">Bir kod erişimi güvenliği (CAS) açısından bakıldığında, hiçbir şey yoktur bir geliştirici ayrıcalıklarını yükseltme yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1da9b-108">From a code access security (CAS) perspective, there is nothing a developer can do to elevate privileges.</span></span> <span data-ttu-id="1da9b-109">Windows tarafından verilen izinler hakkında daha fazla bilgi için bkz. [uygulama yeteneği bildirimleri (Windows Store apps)](https://go.microsoft.com/fwlink/?LinkId=230436) Windows geliştirme Merkezi'nde.</span><span class="sxs-lookup"><span data-stu-id="1da9b-109">For information about the privileges granted by Windows, see [App capability declarations (Windows Store apps)](https://go.microsoft.com/fwlink/?LinkId=230436) in the Windows Dev Center.</span></span> <span data-ttu-id="1da9b-110">Oluşturma hakkında daha fazla bilgi için bir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulaması, bakın [C# veya Visual Basic kullanarak ilk Windows Store uygulamasını oluşturma](https://go.microsoft.com/fwlink/?LinkId=230461).</span><span class="sxs-lookup"><span data-stu-id="1da9b-110">For information about creating a [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app, see [Create your first Windows Store app using C# or Visual Basic](https://go.microsoft.com/fwlink/?LinkId=230461).</span></span>

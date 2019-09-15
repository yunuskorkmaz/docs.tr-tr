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
ms.openlocfilehash: bfc48d4fed127b288353f0295f2de1ca33e0a8fe
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70971205"
---
# <a name="security-changes-in-the-net-framework"></a><span data-ttu-id="ddd37-102">.NET Framework'te Güvenlik Değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="ddd37-102">Security Changes in the .NET Framework</span></span>
<span data-ttu-id="ddd37-103">.NET Framework 4,5 ' de güvenlikle olan en önemli değişiklik, tanımlayıcı adlandırmada.</span><span class="sxs-lookup"><span data-stu-id="ddd37-103">The most important change to security in the .NET Framework 4.5 is in strong naming.</span></span> <span data-ttu-id="ddd37-104">Bu değişikliklerin bir açıklaması için bkz. [Gelişmiş tanımlayıcı adlandırma](../../standard/assembly/enhanced-strong-naming.md) .</span><span class="sxs-lookup"><span data-stu-id="ddd37-104">See [Enhanced Strong Naming](../../standard/assembly/enhanced-strong-naming.md) for a description of those changes.</span></span>  
  
 <span data-ttu-id="ddd37-105">.NET Framework yönetilen uygulamalar için iki katmanlı bir güvenlik modeli sağlar.</span><span class="sxs-lookup"><span data-stu-id="ddd37-105">The .NET Framework provides a two-tier security model for managed applications.</span></span> [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] <span data-ttu-id="ddd37-106">uygulamaları, kaynaklara erişimi sınırlayan bir Windows güvenlik kapsayıcısında çalışır.</span><span class="sxs-lookup"><span data-stu-id="ddd37-106">apps run in a Windows security container that limits access to resources.</span></span> <span data-ttu-id="ddd37-107">Bu kapsayıcı içinde yönetilen uygulamalar tam olarak güvenilir çalışır.</span><span class="sxs-lookup"><span data-stu-id="ddd37-107">Within that container, managed applications run fully trusted.</span></span> <span data-ttu-id="ddd37-108">Bir kod erişimi güvenliği (CAS) perspektifinden, bir geliştiricinin ayrıcalıkları yükseltmek için yapabileceği bir şey yoktur.</span><span class="sxs-lookup"><span data-stu-id="ddd37-108">From a code access security (CAS) perspective, there is nothing a developer can do to elevate privileges.</span></span> <span data-ttu-id="ddd37-109">Windows tarafından verilen ayrıcalıklar hakkında daha fazla bilgi için, bkz. Windows Geliştirme Merkezi 'nde [uygulama yetenek bildirimleri (Windows Mağazası uygulamaları)](https://go.microsoft.com/fwlink/?LinkId=230436) .</span><span class="sxs-lookup"><span data-stu-id="ddd37-109">For information about the privileges granted by Windows, see [App capability declarations (Windows Store apps)](https://go.microsoft.com/fwlink/?LinkId=230436) in the Windows Dev Center.</span></span> <span data-ttu-id="ddd37-110">[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] Uygulama oluşturma hakkında daha fazla bilgi için, bkz. [veya Visual Basic kullanarak C# ilk Windows mağazası uygulamanızı oluşturma](https://go.microsoft.com/fwlink/?LinkId=230461).</span><span class="sxs-lookup"><span data-stu-id="ddd37-110">For information about creating a [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app, see [Create your first Windows Store app using C# or Visual Basic](https://go.microsoft.com/fwlink/?LinkId=230461).</span></span>

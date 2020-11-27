---
title: ClickOnce ile WCF Uygulamaları Dağıtma
ms.date: 03/30/2017
ms.assetid: 1a11feee-2a47-4d3e-a28a-ad69d5ff93e0
ms.openlocfilehash: ad4c603d07885aa16640b71d43038746d3702b05
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96260867"
---
# <a name="deploying-wcf-applications-with-clickonce"></a><span data-ttu-id="9b5cd-102">ClickOnce ile WCF Uygulamaları Dağıtma</span><span class="sxs-lookup"><span data-stu-id="9b5cd-102">Deploying WCF Applications with ClickOnce</span></span>

<span data-ttu-id="9b5cd-103">Windows Communication Foundation (WCF) kullanan istemci uygulamaları ClickOnce teknolojisi kullanılarak dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="9b5cd-103">Client applications using Windows Communication Foundation (WCF) may be deployed using ClickOnce technology.</span></span> <span data-ttu-id="9b5cd-104">Bu teknoloji, güvenilir bir sertifikayla dijital olarak imzalanmaları kaydıyla, kod erişim güvenliği tarafından belirtilen çalışma zamanı güvenlik korumalarının avantajlarından yararlanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="9b5cd-104">This technology allows them to take advantage of the runtime security protections provided by Code Access Security, provided that they are digitally signed with a trusted certificate.</span></span> <span data-ttu-id="9b5cd-105">ClickOnce uygulamasını imzalamak için kullanılan sertifika güvenilen yayımcı deposunda bulunmalı ve istemci makinesindeki yerel güvenlik ilkesinin, yayımcının sertifikasıyla imzalanmış uygulamalara tam güven izinleri verecek şekilde yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9b5cd-105">The certificate used to sign the ClickOnce application must reside in the Trusted Publisher store, and the local security policy on the client machine must be configured to grant Full Trust permissions to applications signed with the publisher's certificate.</span></span>  
  
 <span data-ttu-id="9b5cd-106">ClickOnce uygulamalarını ve güvenilir yayımcıları yapılandırma hakkında daha fazla bilgi için bkz. [ClickOnce güvenilir yayımcıları yapılandırma](/previous-versions/dotnet/articles/ms996418(v=msdn.10)).</span><span class="sxs-lookup"><span data-stu-id="9b5cd-106">For information on configuring ClickOnce applications and trusted publishers, see [Configuring ClickOnce Trusted Publishers](/previous-versions/dotnet/articles/ms996418(v=msdn.10)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b5cd-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9b5cd-107">See also</span></span>

- [<span data-ttu-id="9b5cd-108">Güvenilen uygulama dağıtımına genel bakış</span><span class="sxs-lookup"><span data-stu-id="9b5cd-108">Trusted Application Deployment Overview</span></span>](/visualstudio/deployment/trusted-application-deployment-overview)
- <span data-ttu-id="9b5cd-109">[Windows Forms uygulamalar için ClickOnce dağıtımı](/previous-versions/visualstudio/visual-studio-2008/wh45kb66(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="9b5cd-109">[ClickOnce Deployment for Windows Forms Applications](/previous-versions/visualstudio/visual-studio-2008/wh45kb66(v=vs.90))</span></span>

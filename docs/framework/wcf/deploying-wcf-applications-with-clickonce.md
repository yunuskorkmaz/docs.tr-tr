---
title: ClickOnce ile WCF Uygulamaları Dağıtma
ms.date: 03/30/2017
ms.assetid: 1a11feee-2a47-4d3e-a28a-ad69d5ff93e0
ms.openlocfilehash: b520931751bbba00d440b46657962ad3f1e41cd3
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802228"
---
# <a name="deploying-wcf-applications-with-clickonce"></a><span data-ttu-id="761e2-102">ClickOnce ile WCF Uygulamaları Dağıtma</span><span class="sxs-lookup"><span data-stu-id="761e2-102">Deploying WCF Applications with ClickOnce</span></span>
<span data-ttu-id="761e2-103">Windows Communication Foundation (WCF) kullanan istemci uygulamaları ClickOnce teknolojisi kullanılarak dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="761e2-103">Client applications using Windows Communication Foundation (WCF) may be deployed using ClickOnce technology.</span></span> <span data-ttu-id="761e2-104">Bu teknoloji, güvenilir bir sertifikayla dijital olarak imzalanmaları kaydıyla, kod erişim güvenliği tarafından belirtilen çalışma zamanı güvenlik korumalarının avantajlarından yararlanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="761e2-104">This technology allows them to take advantage of the runtime security protections provided by Code Access Security, provided that they are digitally signed with a trusted certificate.</span></span> <span data-ttu-id="761e2-105">ClickOnce uygulamasını imzalamak için kullanılan sertifika güvenilen yayımcı deposunda bulunmalı ve istemci makinesindeki yerel güvenlik ilkesinin, yayımcının sertifikasıyla imzalanmış uygulamalara tam güven izinleri verecek şekilde yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="761e2-105">The certificate used to sign the ClickOnce application must reside in the Trusted Publisher store, and the local security policy on the client machine must be configured to grant Full Trust permissions to applications signed with the publisher's certificate.</span></span>  
  
 <span data-ttu-id="761e2-106">ClickOnce uygulamalarını ve güvenilir yayımcıları yapılandırma hakkında daha fazla bilgi için bkz. [ClickOnce güvenilir yayımcıları yapılandırma](https://docs.microsoft.com/previous-versions/dotnet/articles/ms996418(v=msdn.10)).</span><span class="sxs-lookup"><span data-stu-id="761e2-106">For information on configuring ClickOnce applications and trusted publishers, see [Configuring ClickOnce Trusted Publishers](https://docs.microsoft.com/previous-versions/dotnet/articles/ms996418(v=msdn.10)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="761e2-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="761e2-107">See also</span></span>

- [<span data-ttu-id="761e2-108">Güvenilir Uygulama Dağıtımına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="761e2-108">Trusted Application Deployment Overview</span></span>](/visualstudio/deployment/trusted-application-deployment-overview)
- <span data-ttu-id="761e2-109">[Windows Forms uygulamalar için ClickOnce dağıtımı](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/wh45kb66(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="761e2-109">[ClickOnce Deployment for Windows Forms Applications](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/wh45kb66(v=vs.90))</span></span>

---
title: ClickOnce ile WCF Uygulamaları Dağıtma
ms.date: 03/30/2017
ms.assetid: 1a11feee-2a47-4d3e-a28a-ad69d5ff93e0
ms.openlocfilehash: ceb652eed1a7cc377538f5d693dcb85ed99da4b3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33456702"
---
# <a name="deploying-wcf-applications-with-clickonce"></a><span data-ttu-id="91ecf-102">ClickOnce ile WCF Uygulamaları Dağıtma</span><span class="sxs-lookup"><span data-stu-id="91ecf-102">Deploying WCF Applications with ClickOnce</span></span>
<span data-ttu-id="91ecf-103">Windows Communication Foundation (WCF) kullanan istemci uygulamalar ClickOnce teknolojisi kullanılarak dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="91ecf-103">Client applications using Windows Communication Foundation (WCF) may be deployed using ClickOnce technology.</span></span> <span data-ttu-id="91ecf-104">Bu teknoloji güvenilir bir sertifika ile dijital olarak imzalanmış olması koşuluyla çalışma zamanı kod erişim güvenliği tarafından sağlanan güvenlik korumaları yararlanmak sağlar.</span><span class="sxs-lookup"><span data-stu-id="91ecf-104">This technology allows them to take advantage of the runtime security protections provided by Code Access Security, provided that they are digitally signed with a trusted certificate.</span></span> <span data-ttu-id="91ecf-105">ClickOnce uygulamayı imzalamak için kullanılan sertifikanın güvenilir yayımcı depoda bulunmalıdır ve istemci makinesinde yerel güvenlik ilkesi publisher'ın sertifikayla imzalanan uygulamaların tam güven izinleri vermek için yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="91ecf-105">The certificate used to sign the ClickOnce application must reside in the Trusted Publisher store, and the local security policy on the client machine must be configured to grant Full Trust permissions to applications signed with the publisher's certificate.</span></span>  
  
 <span data-ttu-id="91ecf-106">ClickOnce uygulamaları ve güvenilen yayımcılar yapılandırma hakkında daha fazla bilgi için bkz: [ClickOnce Güvenilen Yayımcılar yapılandırma](http://go.microsoft.com/fwlink/?LinkId=94774).</span><span class="sxs-lookup"><span data-stu-id="91ecf-106">For information on configuring ClickOnce applications and trusted publishers, see [Configuring ClickOnce Trusted Publishers](http://go.microsoft.com/fwlink/?LinkId=94774).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91ecf-107">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="91ecf-107">See Also</span></span>  
 [<span data-ttu-id="91ecf-108">Güvenilir Uygulama Dağıtımına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="91ecf-108">Trusted Application Deployment Overview</span></span>](http://go.microsoft.com/fwlink/?LinkId=94775)  
 [<span data-ttu-id="91ecf-109">ClickOnce dağıtımı Windows Forms uygulamaları</span><span class="sxs-lookup"><span data-stu-id="91ecf-109">ClickOnce Deployment for Windows Forms Applications</span></span>](http://go.microsoft.com/fwlink/?LinkId=94776)

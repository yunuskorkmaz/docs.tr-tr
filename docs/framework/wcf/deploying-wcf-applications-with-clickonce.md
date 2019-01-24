---
title: ClickOnce ile WCF Uygulamaları Dağıtma
ms.date: 03/30/2017
ms.assetid: 1a11feee-2a47-4d3e-a28a-ad69d5ff93e0
ms.openlocfilehash: 91c03ee2fa33541e917e44583c5fa20173aec34e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54680981"
---
# <a name="deploying-wcf-applications-with-clickonce"></a><span data-ttu-id="c01cd-102">ClickOnce ile WCF Uygulamaları Dağıtma</span><span class="sxs-lookup"><span data-stu-id="c01cd-102">Deploying WCF Applications with ClickOnce</span></span>
<span data-ttu-id="c01cd-103">Windows Communication Foundation (WCF) kullanan istemci uygulamalar, ClickOnce teknolojisi kullanılarak dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="c01cd-103">Client applications using Windows Communication Foundation (WCF) may be deployed using ClickOnce technology.</span></span> <span data-ttu-id="c01cd-104">Bu teknoloji koşuluyla güvenilir bir sertifika ile imzalanmış çalışma zamanı kod erişim güvenliği tarafından sunulan güvenlik koruması yararlanmasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="c01cd-104">This technology allows them to take advantage of the runtime security protections provided by Code Access Security, provided that they are digitally signed with a trusted certificate.</span></span> <span data-ttu-id="c01cd-105">ClickOnce uygulamayı imzalamak için kullanılan sertifikanın güvenilir yayımcı deposunda bulunmalıdır ve yayımcının sertifikayla imzalanan uygulamaların tam güven izni vermek için Yerel Güvenlik İlkesi istemci makinede yapılandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c01cd-105">The certificate used to sign the ClickOnce application must reside in the Trusted Publisher store, and the local security policy on the client machine must be configured to grant Full Trust permissions to applications signed with the publisher's certificate.</span></span>  
  
 <span data-ttu-id="c01cd-106">ClickOnce uygulamaları ve güvenilen yayımcılar yapılandırma hakkında daha fazla bilgi için bkz: [ClickOnce Güvenilen Yayımcılar yapılandırma](https://go.microsoft.com/fwlink/?LinkId=94774).</span><span class="sxs-lookup"><span data-stu-id="c01cd-106">For information on configuring ClickOnce applications and trusted publishers, see [Configuring ClickOnce Trusted Publishers](https://go.microsoft.com/fwlink/?LinkId=94774).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c01cd-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c01cd-107">See also</span></span>
- [<span data-ttu-id="c01cd-108">Güvenilir Uygulama Dağıtımına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c01cd-108">Trusted Application Deployment Overview</span></span>](https://go.microsoft.com/fwlink/?LinkId=94775)
- [<span data-ttu-id="c01cd-109">ClickOnce dağıtımı için Windows Forms uygulamaları</span><span class="sxs-lookup"><span data-stu-id="c01cd-109">ClickOnce Deployment for Windows Forms Applications</span></span>](https://go.microsoft.com/fwlink/?LinkId=94776)

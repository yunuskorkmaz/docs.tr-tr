---
title: ClickOnce ile WCF Uygulamaları Dağıtma
ms.date: 03/30/2017
ms.assetid: 1a11feee-2a47-4d3e-a28a-ad69d5ff93e0
ms.openlocfilehash: 1820b00aa903633750f74f319f9cf8038ba2b043
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59086240"
---
# <a name="deploying-wcf-applications-with-clickonce"></a><span data-ttu-id="5598a-102">ClickOnce ile WCF Uygulamaları Dağıtma</span><span class="sxs-lookup"><span data-stu-id="5598a-102">Deploying WCF Applications with ClickOnce</span></span>
<span data-ttu-id="5598a-103">Windows Communication Foundation (WCF) kullanan istemci uygulamalar, ClickOnce teknolojisi kullanılarak dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="5598a-103">Client applications using Windows Communication Foundation (WCF) may be deployed using ClickOnce technology.</span></span> <span data-ttu-id="5598a-104">Bu teknoloji koşuluyla güvenilir bir sertifika ile imzalanmış çalışma zamanı kod erişim güvenliği tarafından sunulan güvenlik koruması yararlanmasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="5598a-104">This technology allows them to take advantage of the runtime security protections provided by Code Access Security, provided that they are digitally signed with a trusted certificate.</span></span> <span data-ttu-id="5598a-105">ClickOnce uygulamayı imzalamak için kullanılan sertifikanın güvenilir yayımcı deposunda bulunmalıdır ve yayımcının sertifikayla imzalanan uygulamaların tam güven izni vermek için Yerel Güvenlik İlkesi istemci makinede yapılandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5598a-105">The certificate used to sign the ClickOnce application must reside in the Trusted Publisher store, and the local security policy on the client machine must be configured to grant Full Trust permissions to applications signed with the publisher's certificate.</span></span>  
  
 <span data-ttu-id="5598a-106">ClickOnce uygulamaları ve güvenilen yayımcılar yapılandırma hakkında daha fazla bilgi için bkz: [ClickOnce Güvenilen Yayımcılar yapılandırma](https://go.microsoft.com/fwlink/?LinkId=94774).</span><span class="sxs-lookup"><span data-stu-id="5598a-106">For information on configuring ClickOnce applications and trusted publishers, see [Configuring ClickOnce Trusted Publishers](https://go.microsoft.com/fwlink/?LinkId=94774).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5598a-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5598a-107">See also</span></span>

- [<span data-ttu-id="5598a-108">Güvenilir Uygulama Dağıtımına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5598a-108">Trusted Application Deployment Overview</span></span>](https://go.microsoft.com/fwlink/?LinkId=94775)
- [<span data-ttu-id="5598a-109">ClickOnce dağıtımı için Windows Forms uygulamaları</span><span class="sxs-lookup"><span data-stu-id="5598a-109">ClickOnce Deployment for Windows Forms Applications</span></span>](https://go.microsoft.com/fwlink/?LinkId=94776)

---
title: ClickOnce ile WCF Uygulamaları Dağıtma
ms.date: 03/30/2017
ms.assetid: 1a11feee-2a47-4d3e-a28a-ad69d5ff93e0
ms.openlocfilehash: 1820b00aa903633750f74f319f9cf8038ba2b043
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785099"
---
# <a name="deploying-wcf-applications-with-clickonce"></a><span data-ttu-id="fdbb2-102">ClickOnce ile WCF Uygulamaları Dağıtma</span><span class="sxs-lookup"><span data-stu-id="fdbb2-102">Deploying WCF Applications with ClickOnce</span></span>
<span data-ttu-id="fdbb2-103">Windows Communication Foundation (WCF) kullanan istemci uygulamalar, ClickOnce teknolojisi kullanılarak dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="fdbb2-103">Client applications using Windows Communication Foundation (WCF) may be deployed using ClickOnce technology.</span></span> <span data-ttu-id="fdbb2-104">Bu teknoloji koşuluyla güvenilir bir sertifika ile imzalanmış çalışma zamanı kod erişim güvenliği tarafından sunulan güvenlik koruması yararlanmasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="fdbb2-104">This technology allows them to take advantage of the runtime security protections provided by Code Access Security, provided that they are digitally signed with a trusted certificate.</span></span> <span data-ttu-id="fdbb2-105">ClickOnce uygulamayı imzalamak için kullanılan sertifikanın güvenilir yayımcı deposunda bulunmalıdır ve yayımcının sertifikayla imzalanan uygulamaların tam güven izni vermek için Yerel Güvenlik İlkesi istemci makinede yapılandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fdbb2-105">The certificate used to sign the ClickOnce application must reside in the Trusted Publisher store, and the local security policy on the client machine must be configured to grant Full Trust permissions to applications signed with the publisher's certificate.</span></span>  
  
 <span data-ttu-id="fdbb2-106">ClickOnce uygulamaları ve güvenilen yayımcılar yapılandırma hakkında daha fazla bilgi için bkz: [ClickOnce Güvenilen Yayımcılar yapılandırma](https://go.microsoft.com/fwlink/?LinkId=94774).</span><span class="sxs-lookup"><span data-stu-id="fdbb2-106">For information on configuring ClickOnce applications and trusted publishers, see [Configuring ClickOnce Trusted Publishers](https://go.microsoft.com/fwlink/?LinkId=94774).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdbb2-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fdbb2-107">See also</span></span>

- [<span data-ttu-id="fdbb2-108">Güvenilir Uygulama Dağıtımına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="fdbb2-108">Trusted Application Deployment Overview</span></span>](https://go.microsoft.com/fwlink/?LinkId=94775)
- [<span data-ttu-id="fdbb2-109">ClickOnce dağıtımı için Windows Forms uygulamaları</span><span class="sxs-lookup"><span data-stu-id="fdbb2-109">ClickOnce Deployment for Windows Forms Applications</span></span>](https://go.microsoft.com/fwlink/?LinkId=94776)

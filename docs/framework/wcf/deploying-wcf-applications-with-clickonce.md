---
title: ClickOnce ile WCF Uygulamaları Dağıtma
ms.date: 03/30/2017
ms.assetid: 1a11feee-2a47-4d3e-a28a-ad69d5ff93e0
ms.openlocfilehash: d733c6f523393737418c6394707c1d4e6e9c1710
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45529087"
---
# <a name="deploying-wcf-applications-with-clickonce"></a><span data-ttu-id="85a0b-102">ClickOnce ile WCF Uygulamaları Dağıtma</span><span class="sxs-lookup"><span data-stu-id="85a0b-102">Deploying WCF Applications with ClickOnce</span></span>
<span data-ttu-id="85a0b-103">Windows Communication Foundation (WCF) kullanan istemci uygulamalar, ClickOnce teknolojisi kullanılarak dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="85a0b-103">Client applications using Windows Communication Foundation (WCF) may be deployed using ClickOnce technology.</span></span> <span data-ttu-id="85a0b-104">Bu teknoloji koşuluyla güvenilir bir sertifika ile imzalanmış çalışma zamanı kod erişim güvenliği tarafından sunulan güvenlik koruması yararlanmasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="85a0b-104">This technology allows them to take advantage of the runtime security protections provided by Code Access Security, provided that they are digitally signed with a trusted certificate.</span></span> <span data-ttu-id="85a0b-105">ClickOnce uygulamayı imzalamak için kullanılan sertifikanın güvenilir yayımcı deposunda bulunmalıdır ve yayımcının sertifikayla imzalanan uygulamaların tam güven izni vermek için Yerel Güvenlik İlkesi istemci makinede yapılandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="85a0b-105">The certificate used to sign the ClickOnce application must reside in the Trusted Publisher store, and the local security policy on the client machine must be configured to grant Full Trust permissions to applications signed with the publisher's certificate.</span></span>  
  
 <span data-ttu-id="85a0b-106">ClickOnce uygulamaları ve güvenilen yayımcılar yapılandırma hakkında daha fazla bilgi için bkz: [ClickOnce Güvenilen Yayımcılar yapılandırma](https://go.microsoft.com/fwlink/?LinkId=94774).</span><span class="sxs-lookup"><span data-stu-id="85a0b-106">For information on configuring ClickOnce applications and trusted publishers, see [Configuring ClickOnce Trusted Publishers](https://go.microsoft.com/fwlink/?LinkId=94774).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85a0b-107">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="85a0b-107">See Also</span></span>  
 [<span data-ttu-id="85a0b-108">Güvenilir Uygulama Dağıtımına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="85a0b-108">Trusted Application Deployment Overview</span></span>](https://go.microsoft.com/fwlink/?LinkId=94775)  
 [<span data-ttu-id="85a0b-109">ClickOnce dağıtımı için Windows Forms uygulamaları</span><span class="sxs-lookup"><span data-stu-id="85a0b-109">ClickOnce Deployment for Windows Forms Applications</span></span>](https://go.microsoft.com/fwlink/?LinkId=94776)

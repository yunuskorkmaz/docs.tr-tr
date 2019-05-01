---
title: System.ServiceModel.TxFailedToNegotiateOleTx
ms.date: 03/30/2017
ms.assetid: 3f0f0b4b-a1ad-4704-8329-455daf54892d
ms.openlocfilehash: 2de1aa51d58d9d86f953e027fd3f7f172e3887d3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61917065"
---
# <a name="systemservicemodeltxfailedtonegotiateoletx"></a><span data-ttu-id="50486-102">System.ServiceModel.TxFailedToNegotiateOleTx</span><span class="sxs-lookup"><span data-stu-id="50486-102">System.ServiceModel.TxFailedToNegotiateOleTx</span></span>
<span data-ttu-id="50486-103">Belirtilen düzenleme bağlamı OleTransactions Protokolü anlaşmasını tamamlayamadı.</span><span class="sxs-lookup"><span data-stu-id="50486-103">The OleTransactions protocol negotiation failed to complete for the specified coordination context.</span></span>  
  
## <a name="description"></a><span data-ttu-id="50486-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="50486-104">Description</span></span>  
 <span data-ttu-id="50486-105">Gelen bir işlem OleTx bilgilerle eklenen OleTx bilgiler kullanamaz ve fall WS-AT bunun yerine geri izlenen.</span><span class="sxs-lookup"><span data-stu-id="50486-105">Traced when an incoming transaction with OleTx information is unable to use the attached OleTx information, and will fall-back to using WS-AT instead.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="50486-106">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="50486-106">Troubleshooting</span></span>  
 <span data-ttu-id="50486-107">MSDTC RPC iletişimi makineler arasındaki olası bir sorun olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="50486-107">Indicates a potential problem with MSDTC RPC communication between the machines.</span></span> <span data-ttu-id="50486-108">Bu izlemeler birçoğu günlüğünde görünürse, güçlü bir performans düşüklüğü neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="50486-108">If many of these traces appear in the log, a drastic decrease in performance can result.</span></span>  <span data-ttu-id="50486-109">OleTx istenildiği gibi değilse, ayarlama `OleTxUpgradeEnabled` 0 WS-AT kayıt defteri yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="50486-109">If OleTx is not desired, set `OleTxUpgradeEnabled` to 0 in the WS-AT registry configuration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50486-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="50486-110">See also</span></span>

- [<span data-ttu-id="50486-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="50486-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="50486-112">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="50486-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="50486-113">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="50486-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)

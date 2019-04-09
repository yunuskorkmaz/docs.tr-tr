---
title: System.ServiceModel.TxFailedToNegotiateOleTx
ms.date: 03/30/2017
ms.assetid: 3f0f0b4b-a1ad-4704-8329-455daf54892d
ms.openlocfilehash: 2de1aa51d58d9d86f953e027fd3f7f172e3887d3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59097570"
---
# <a name="systemservicemodeltxfailedtonegotiateoletx"></a><span data-ttu-id="59a43-102">System.ServiceModel.TxFailedToNegotiateOleTx</span><span class="sxs-lookup"><span data-stu-id="59a43-102">System.ServiceModel.TxFailedToNegotiateOleTx</span></span>
<span data-ttu-id="59a43-103">Belirtilen düzenleme bağlamı OleTransactions Protokolü anlaşmasını tamamlayamadı.</span><span class="sxs-lookup"><span data-stu-id="59a43-103">The OleTransactions protocol negotiation failed to complete for the specified coordination context.</span></span>  
  
## <a name="description"></a><span data-ttu-id="59a43-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="59a43-104">Description</span></span>  
 <span data-ttu-id="59a43-105">Gelen bir işlem OleTx bilgilerle eklenen OleTx bilgiler kullanamaz ve fall WS-AT bunun yerine geri izlenen.</span><span class="sxs-lookup"><span data-stu-id="59a43-105">Traced when an incoming transaction with OleTx information is unable to use the attached OleTx information, and will fall-back to using WS-AT instead.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="59a43-106">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="59a43-106">Troubleshooting</span></span>  
 <span data-ttu-id="59a43-107">MSDTC RPC iletişimi makineler arasındaki olası bir sorun olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="59a43-107">Indicates a potential problem with MSDTC RPC communication between the machines.</span></span> <span data-ttu-id="59a43-108">Bu izlemeler birçoğu günlüğünde görünürse, güçlü bir performans düşüklüğü neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="59a43-108">If many of these traces appear in the log, a drastic decrease in performance can result.</span></span>  <span data-ttu-id="59a43-109">OleTx istenildiği gibi değilse, ayarlama `OleTxUpgradeEnabled` 0 WS-AT kayıt defteri yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="59a43-109">If OleTx is not desired, set `OleTxUpgradeEnabled` to 0 in the WS-AT registry configuration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59a43-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="59a43-110">See also</span></span>

- [<span data-ttu-id="59a43-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="59a43-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="59a43-112">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="59a43-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="59a43-113">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="59a43-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)

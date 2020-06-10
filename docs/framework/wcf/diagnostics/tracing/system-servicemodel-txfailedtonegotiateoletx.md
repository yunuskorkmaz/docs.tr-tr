---
title: System.ServiceModel.TxFailedToNegotiateOleTx
ms.date: 03/30/2017
ms.assetid: 3f0f0b4b-a1ad-4704-8329-455daf54892d
ms.openlocfilehash: 2c9ea77cdd76d4593c2ee5b09a4b917677b8925f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601419"
---
# <a name="systemservicemodeltxfailedtonegotiateoletx"></a><span data-ttu-id="e57ee-102">System.ServiceModel.TxFailedToNegotiateOleTx</span><span class="sxs-lookup"><span data-stu-id="e57ee-102">System.ServiceModel.TxFailedToNegotiateOleTx</span></span>
<span data-ttu-id="e57ee-103">OleTransactions protokol anlaşması belirtilen düzenleme bağlamı için başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="e57ee-103">The OleTransactions protocol negotiation failed to complete for the specified coordination context.</span></span>  
  
## <a name="description"></a><span data-ttu-id="e57ee-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e57ee-104">Description</span></span>  
 <span data-ttu-id="e57ee-105">OleTx bilgilerine sahip bir gelen işlem eklenen OleTx bilgilerini kullanamadığı ve bunun yerine WS-AT kullanmaya geri dönecektir.</span><span class="sxs-lookup"><span data-stu-id="e57ee-105">Traced when an incoming transaction with OleTx information is unable to use the attached OleTx information, and will fall-back to using WS-AT instead.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="e57ee-106">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="e57ee-106">Troubleshooting</span></span>  
 <span data-ttu-id="e57ee-107">Makineler arasındaki MSDTC RPC iletişimi ile ilgili olası bir sorunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="e57ee-107">Indicates a potential problem with MSDTC RPC communication between the machines.</span></span> <span data-ttu-id="e57ee-108">Bu İzlemelerden birçoğu günlükte görünüyorsa, performansın çok fazla azalmasını sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="e57ee-108">If many of these traces appear in the log, a drastic decrease in performance can result.</span></span>  <span data-ttu-id="e57ee-109">OleTx istenmiyorsa, `OleTxUpgradeEnabled` ws-at kayıt defteri yapılandırmasında 0 olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e57ee-109">If OleTx is not desired, set `OleTxUpgradeEnabled` to 0 in the WS-AT registry configuration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e57ee-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e57ee-110">See also</span></span>

- [<span data-ttu-id="e57ee-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="e57ee-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="e57ee-112">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="e57ee-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="e57ee-113">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="e57ee-113">Administration and Diagnostics</span></span>](../index.md)

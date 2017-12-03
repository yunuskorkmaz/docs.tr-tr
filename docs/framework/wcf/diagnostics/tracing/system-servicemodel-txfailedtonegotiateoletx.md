---
title: System.ServiceModel.TxFailedToNegotiateOleTx
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f0f0b4b-a1ad-4704-8329-455daf54892d
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6c0e688e1f24171494b4adaae964ac1fc2be2309
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodeltxfailedtonegotiateoletx"></a><span data-ttu-id="ee5a0-102">System.ServiceModel.TxFailedToNegotiateOleTx</span><span class="sxs-lookup"><span data-stu-id="ee5a0-102">System.ServiceModel.TxFailedToNegotiateOleTx</span></span>
<span data-ttu-id="ee5a0-103">OleTransactions Protokolü anlaşması için belirtilen koordinasyon bağlamı tamamlayamadı.</span><span class="sxs-lookup"><span data-stu-id="ee5a0-103">The OleTransactions protocol negotiation failed to complete for the specified coordination context.</span></span>  
  
## <a name="description"></a><span data-ttu-id="ee5a0-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ee5a0-104">Description</span></span>  
 <span data-ttu-id="ee5a0-105">Gelen bir işlem OleTx bilgilerle eklenen OleTx bilgiler kullanamadı ve sonbaharda WS-AT kullanmaya geri izlenen.</span><span class="sxs-lookup"><span data-stu-id="ee5a0-105">Traced when an incoming transaction with OleTx information is unable to use the attached OleTx information, and will fall-back to using WS-AT instead.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="ee5a0-106">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="ee5a0-106">Troubleshooting</span></span>  
 <span data-ttu-id="ee5a0-107">MSDTC RPC iletişimi makineler arasındaki olası bir sorun olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ee5a0-107">Indicates a potential problem with MSDTC RPC communication between the machines.</span></span> <span data-ttu-id="ee5a0-108">Bu izlemeler çoğunu günlüğünde görünür, performans kazanmadan ciddi bir düşüş ortaya çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="ee5a0-108">If many of these traces appear in the log, a drastic decrease in performance can result.</span></span>  <span data-ttu-id="ee5a0-109">OleTx değil istenirse, ayarlamak `OleTxUpgradeEnabled` 0 WS-AT kayıt defteri yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="ee5a0-109">If OleTx is not desired, set `OleTxUpgradeEnabled` to 0 in the WS-AT registry configuration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee5a0-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ee5a0-110">See Also</span></span>  
 [<span data-ttu-id="ee5a0-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="ee5a0-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="ee5a0-112">Uygulamanızda sorun giderme için izlemeyi kullanma</span><span class="sxs-lookup"><span data-stu-id="ee5a0-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="ee5a0-113">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="ee5a0-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)

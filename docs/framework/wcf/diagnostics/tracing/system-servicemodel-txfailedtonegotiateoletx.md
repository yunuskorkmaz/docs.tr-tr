---
description: 'Daha fazla bilgi edinin: System. ServiceModel. TxFailedToNegotiateOleTx'
title: System.ServiceModel.TxFailedToNegotiateOleTx
ms.date: 03/30/2017
ms.assetid: 3f0f0b4b-a1ad-4704-8329-455daf54892d
ms.openlocfilehash: c7f18ef73ff9c09cc51ad3aa6c54c2bd672d0cc3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99735575"
---
# <a name="systemservicemodeltxfailedtonegotiateoletx"></a><span data-ttu-id="f503b-103">System.ServiceModel.TxFailedToNegotiateOleTx</span><span class="sxs-lookup"><span data-stu-id="f503b-103">System.ServiceModel.TxFailedToNegotiateOleTx</span></span>

<span data-ttu-id="f503b-104">OleTransactions protokol anlaşması belirtilen düzenleme bağlamı için başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="f503b-104">The OleTransactions protocol negotiation failed to complete for the specified coordination context.</span></span>  
  
## <a name="description"></a><span data-ttu-id="f503b-105">Description</span><span class="sxs-lookup"><span data-stu-id="f503b-105">Description</span></span>  

 <span data-ttu-id="f503b-106">OleTx bilgilerine sahip bir gelen işlem eklenen OleTx bilgilerini kullanamadığı ve bunun yerine WS-AT kullanmaya geri dönecektir.</span><span class="sxs-lookup"><span data-stu-id="f503b-106">Traced when an incoming transaction with OleTx information is unable to use the attached OleTx information, and will fall-back to using WS-AT instead.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="f503b-107">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="f503b-107">Troubleshooting</span></span>  

 <span data-ttu-id="f503b-108">Makineler arasındaki MSDTC RPC iletişimi ile ilgili olası bir sorunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="f503b-108">Indicates a potential problem with MSDTC RPC communication between the machines.</span></span> <span data-ttu-id="f503b-109">Bu İzlemelerden birçoğu günlükte görünüyorsa, performansın çok fazla azalmasını sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="f503b-109">If many of these traces appear in the log, a drastic decrease in performance can result.</span></span>  <span data-ttu-id="f503b-110">OleTx istenmiyorsa, `OleTxUpgradeEnabled` ws-at kayıt defteri yapılandırmasında 0 olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="f503b-110">If OleTx is not desired, set `OleTxUpgradeEnabled` to 0 in the WS-AT registry configuration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f503b-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f503b-111">See also</span></span>

- [<span data-ttu-id="f503b-112">İzleme</span><span class="sxs-lookup"><span data-stu-id="f503b-112">Tracing</span></span>](index.md)
- [<span data-ttu-id="f503b-113">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="f503b-113">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="f503b-114">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="f503b-114">Administration and Diagnostics</span></span>](../index.md)

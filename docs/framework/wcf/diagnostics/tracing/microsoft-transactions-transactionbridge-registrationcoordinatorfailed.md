---
title: Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFailed
ms.date: 03/30/2017
ms.assetid: 96474056-0418-41e4-8c75-bbc0a853eaba
ms.openlocfilehash: 5c8592ac34375445964b3dbcbbd4800c47e53850
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54515056"
---
# <a name="microsofttransactionstransactionbridgeregistrationcoordinatorfailed"></a><span data-ttu-id="4055f-102">Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFailed</span><span class="sxs-lookup"><span data-stu-id="4055f-102">Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFailed</span></span>
<span data-ttu-id="4055f-103">WS-AT protokolü hizmetini ilgili düzenleyiciye bir kayıt iletisi gönderilemedi</span><span class="sxs-lookup"><span data-stu-id="4055f-103">The WS-AT protocol service failed to send a Register message to its coordinator</span></span>  
  
## <a name="description"></a><span data-ttu-id="4055f-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4055f-104">Description</span></span>  
 <span data-ttu-id="4055f-105">Yerel TransactionManager, üstün TransactionManager ileti göndermek için bağlantı kurma sorunu nedeniyle kaydı mümkün değilse, izlenen.</span><span class="sxs-lookup"><span data-stu-id="4055f-105">Traced if the local TransactionManager is not able to Register with its superior TransactionManager due to the inability to send a message.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="4055f-106">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="4055f-106">Troubleshooting</span></span>  
 <span data-ttu-id="4055f-107">İleti gönderme hatası neden olan özel durumu için izleme iletisi inceleyin</span><span class="sxs-lookup"><span data-stu-id="4055f-107">Inspect the trace message for the exception causing the message send failure</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4055f-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4055f-108">See also</span></span>
- [<span data-ttu-id="4055f-109">İzleme</span><span class="sxs-lookup"><span data-stu-id="4055f-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="4055f-110">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="4055f-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="4055f-111">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="4055f-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)

---
title: Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFailed
ms.date: 03/30/2017
ms.assetid: 96474056-0418-41e4-8c75-bbc0a853eaba
ms.openlocfilehash: dec86141a19c3e5edf5d13ed1ef8d2e8f2b38fba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33475660"
---
# <a name="microsofttransactionstransactionbridgeregistrationcoordinatorfailed"></a><span data-ttu-id="ebbaa-102">Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFailed</span><span class="sxs-lookup"><span data-stu-id="ebbaa-102">Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFailed</span></span>
<span data-ttu-id="ebbaa-103">WS-AT protokolü hizmeti ilgili düzenleyiciye bir kayıt iletisi gönderilemedi</span><span class="sxs-lookup"><span data-stu-id="ebbaa-103">The WS-AT protocol service failed to send a Register message to its coordinator</span></span>  
  
## <a name="description"></a><span data-ttu-id="ebbaa-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ebbaa-104">Description</span></span>  
 <span data-ttu-id="ebbaa-105">Yerel TransactionManager kendi üst TransactionManager nedeniyle bir ileti göndermek için kullanamama kaydı mümkün değilse, izlenen.</span><span class="sxs-lookup"><span data-stu-id="ebbaa-105">Traced if the local TransactionManager is not able to Register with its superior TransactionManager due to the inability to send a message.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="ebbaa-106">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="ebbaa-106">Troubleshooting</span></span>  
 <span data-ttu-id="ebbaa-107">İleti gönderme hataya neden olan özel durum izleme iletisi inceleyin.</span><span class="sxs-lookup"><span data-stu-id="ebbaa-107">Inspect the trace message for the exception causing the message send failure</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebbaa-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ebbaa-108">See Also</span></span>  
 [<span data-ttu-id="ebbaa-109">İzleme</span><span class="sxs-lookup"><span data-stu-id="ebbaa-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="ebbaa-110">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="ebbaa-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="ebbaa-111">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="ebbaa-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)

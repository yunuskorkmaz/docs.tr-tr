---
title: Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFaulted
ms.date: 03/30/2017
ms.assetid: 8193027e-9db2-4af9-a072-27300cd24330
ms.openlocfilehash: f634816b2459d2e0b6137e2e87fef907824af017
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59163039"
---
# <a name="microsofttransactionstransactionbridgeregistrationcoordinatorfaulted"></a><span data-ttu-id="8e914-102">Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFaulted</span><span class="sxs-lookup"><span data-stu-id="8e914-102">Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFaulted</span></span>
<span data-ttu-id="8e914-103">WS-AT protokolü hizmetini düzenleyicisiyle bir kayıt iletiye yanıt olarak bir hata aldı.</span><span class="sxs-lookup"><span data-stu-id="8e914-103">The WS-AT protocol service received a fault from its coordinator in response to a Register message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="8e914-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8e914-104">Description</span></span>  
 <span data-ttu-id="8e914-105">Yerel TransactionManager, üstün TransactionManager döndürülen bir hata nedeniyle kaydı mümkün değilse, izlenen.</span><span class="sxs-lookup"><span data-stu-id="8e914-105">Traced if the local TransactionManager is not able to Register with its superior TransactionManager due to a fault being returned.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="8e914-106">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="8e914-106">Troubleshooting</span></span>  
 <span data-ttu-id="8e914-107">Döndürülen hata izleme iletisi inceleyin.</span><span class="sxs-lookup"><span data-stu-id="8e914-107">Inspect the trace message for the fault returned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e914-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8e914-108">See also</span></span>

- [<span data-ttu-id="8e914-109">İzleme</span><span class="sxs-lookup"><span data-stu-id="8e914-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="8e914-110">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="8e914-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="8e914-111">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="8e914-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)

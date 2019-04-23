---
title: Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFailed
ms.date: 03/30/2017
ms.assetid: 96474056-0418-41e4-8c75-bbc0a853eaba
ms.openlocfilehash: 3745c542986d405312a308fcf50ba6d7b6f93a1c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59074189"
---
# <a name="microsofttransactionstransactionbridgeregistrationcoordinatorfailed"></a><span data-ttu-id="abe54-102">Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFailed</span><span class="sxs-lookup"><span data-stu-id="abe54-102">Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFailed</span></span>
<span data-ttu-id="abe54-103">WS-AT protokolü hizmetini ilgili düzenleyiciye bir kayıt iletisi gönderilemedi</span><span class="sxs-lookup"><span data-stu-id="abe54-103">The WS-AT protocol service failed to send a Register message to its coordinator</span></span>  
  
## <a name="description"></a><span data-ttu-id="abe54-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="abe54-104">Description</span></span>  
 <span data-ttu-id="abe54-105">Yerel TransactionManager, üstün TransactionManager ileti göndermek için bağlantı kurma sorunu nedeniyle kaydı mümkün değilse, izlenen.</span><span class="sxs-lookup"><span data-stu-id="abe54-105">Traced if the local TransactionManager is not able to Register with its superior TransactionManager due to the inability to send a message.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="abe54-106">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="abe54-106">Troubleshooting</span></span>  
 <span data-ttu-id="abe54-107">İleti gönderme hatası neden olan özel durumu için izleme iletisi inceleyin</span><span class="sxs-lookup"><span data-stu-id="abe54-107">Inspect the trace message for the exception causing the message send failure</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abe54-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="abe54-108">See also</span></span>

- [<span data-ttu-id="abe54-109">İzleme</span><span class="sxs-lookup"><span data-stu-id="abe54-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="abe54-110">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="abe54-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="abe54-111">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="abe54-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)

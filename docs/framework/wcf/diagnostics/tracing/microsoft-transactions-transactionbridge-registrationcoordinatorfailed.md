---
title: Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFailed
ms.date: 03/30/2017
ms.assetid: 96474056-0418-41e4-8c75-bbc0a853eaba
ms.openlocfilehash: 83bb67f2a5eb1a9353129bce9ec22f18eb382259
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96251977"
---
# <a name="microsofttransactionstransactionbridgeregistrationcoordinatorfailed"></a><span data-ttu-id="50187-102">Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFailed</span><span class="sxs-lookup"><span data-stu-id="50187-102">Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFailed</span></span>

<span data-ttu-id="50187-103">WS-AT protokol hizmeti, düzenleyicisine bir kayıt iletisi gönderemedi</span><span class="sxs-lookup"><span data-stu-id="50187-103">The WS-AT protocol service failed to send a Register message to its coordinator</span></span>  
  
## <a name="description"></a><span data-ttu-id="50187-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="50187-104">Description</span></span>  

 <span data-ttu-id="50187-105">Yerel TransactionManager, bir ileti gönderememe nedeniyle kendi üst TransactionManager 'a Kaydolamadıysanız izleniyor.</span><span class="sxs-lookup"><span data-stu-id="50187-105">Traced if the local TransactionManager is not able to Register with its superior TransactionManager due to the inability to send a message.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="50187-106">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="50187-106">Troubleshooting</span></span>  

 <span data-ttu-id="50187-107">İleti gönderme hatasına neden olan özel durum için izleme iletisini inceleyin</span><span class="sxs-lookup"><span data-stu-id="50187-107">Inspect the trace message for the exception causing the message send failure</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50187-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="50187-108">See also</span></span>

- [<span data-ttu-id="50187-109">İzleme</span><span class="sxs-lookup"><span data-stu-id="50187-109">Tracing</span></span>](index.md)
- [<span data-ttu-id="50187-110">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="50187-110">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="50187-111">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="50187-111">Administration and Diagnostics</span></span>](../index.md)

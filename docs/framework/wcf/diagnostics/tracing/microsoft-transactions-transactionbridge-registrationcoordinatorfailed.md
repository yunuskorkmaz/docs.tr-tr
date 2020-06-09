---
title: Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFailed
ms.date: 03/30/2017
ms.assetid: 96474056-0418-41e4-8c75-bbc0a853eaba
ms.openlocfilehash: faab1927f75a33b6a6950f8f4baf758e7418547a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599704"
---
# <a name="microsofttransactionstransactionbridgeregistrationcoordinatorfailed"></a><span data-ttu-id="13adf-102">Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFailed</span><span class="sxs-lookup"><span data-stu-id="13adf-102">Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFailed</span></span>
<span data-ttu-id="13adf-103">WS-AT protokol hizmeti, düzenleyicisine bir kayıt iletisi gönderemedi</span><span class="sxs-lookup"><span data-stu-id="13adf-103">The WS-AT protocol service failed to send a Register message to its coordinator</span></span>  
  
## <a name="description"></a><span data-ttu-id="13adf-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="13adf-104">Description</span></span>  
 <span data-ttu-id="13adf-105">Yerel TransactionManager, bir ileti gönderememe nedeniyle kendi üst TransactionManager 'a Kaydolamadıysanız izleniyor.</span><span class="sxs-lookup"><span data-stu-id="13adf-105">Traced if the local TransactionManager is not able to Register with its superior TransactionManager due to the inability to send a message.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="13adf-106">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="13adf-106">Troubleshooting</span></span>  
 <span data-ttu-id="13adf-107">İleti gönderme hatasına neden olan özel durum için izleme iletisini inceleyin</span><span class="sxs-lookup"><span data-stu-id="13adf-107">Inspect the trace message for the exception causing the message send failure</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13adf-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13adf-108">See also</span></span>

- [<span data-ttu-id="13adf-109">İzleme</span><span class="sxs-lookup"><span data-stu-id="13adf-109">Tracing</span></span>](index.md)
- [<span data-ttu-id="13adf-110">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="13adf-110">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="13adf-111">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="13adf-111">Administration and Diagnostics</span></span>](../index.md)

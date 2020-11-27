---
title: Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFaulted
ms.date: 03/30/2017
ms.assetid: 8193027e-9db2-4af9-a072-27300cd24330
ms.openlocfilehash: 5066501faf4c336e095910e7e2d8ba1186ba3386
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96251873"
---
# <a name="microsofttransactionstransactionbridgeregistrationcoordinatorfaulted"></a><span data-ttu-id="8b9b4-102">Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFaulted</span><span class="sxs-lookup"><span data-stu-id="8b9b4-102">Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFaulted</span></span>

<span data-ttu-id="8b9b4-103">WS-AT protokol hizmeti, bir yazmaç iletisine yanıt olarak düzenleyicinden bir hata aldı.</span><span class="sxs-lookup"><span data-stu-id="8b9b4-103">The WS-AT protocol service received a fault from its coordinator in response to a Register message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="8b9b4-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8b9b4-104">Description</span></span>  

 <span data-ttu-id="8b9b4-105">Yerel TransactionManager, döndürülmekte olan bir hata nedeniyle üst işlemi ile kayıt yapamezse izleniyor.</span><span class="sxs-lookup"><span data-stu-id="8b9b4-105">Traced if the local TransactionManager is not able to Register with its superior TransactionManager due to a fault being returned.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="8b9b4-106">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="8b9b4-106">Troubleshooting</span></span>  

 <span data-ttu-id="8b9b4-107">Döndürülen hata için izleme iletisini inceleyin.</span><span class="sxs-lookup"><span data-stu-id="8b9b4-107">Inspect the trace message for the fault returned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b9b4-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8b9b4-108">See also</span></span>

- [<span data-ttu-id="8b9b4-109">İzleme</span><span class="sxs-lookup"><span data-stu-id="8b9b4-109">Tracing</span></span>](index.md)
- [<span data-ttu-id="8b9b4-110">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="8b9b4-110">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="8b9b4-111">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="8b9b4-111">Administration and Diagnostics</span></span>](../index.md)

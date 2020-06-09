---
title: Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFaulted
ms.date: 03/30/2017
ms.assetid: 8193027e-9db2-4af9-a072-27300cd24330
ms.openlocfilehash: ad9d82162313e46626e5e2fa6f4ef99bf0139162
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599665"
---
# <a name="microsofttransactionstransactionbridgeregistrationcoordinatorfaulted"></a><span data-ttu-id="73c57-102">Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFaulted</span><span class="sxs-lookup"><span data-stu-id="73c57-102">Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFaulted</span></span>
<span data-ttu-id="73c57-103">WS-AT protokol hizmeti, bir yazmaç iletisine yanıt olarak düzenleyicinden bir hata aldı.</span><span class="sxs-lookup"><span data-stu-id="73c57-103">The WS-AT protocol service received a fault from its coordinator in response to a Register message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="73c57-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="73c57-104">Description</span></span>  
 <span data-ttu-id="73c57-105">Yerel TransactionManager, döndürülmekte olan bir hata nedeniyle üst işlemi ile kayıt yapamezse izleniyor.</span><span class="sxs-lookup"><span data-stu-id="73c57-105">Traced if the local TransactionManager is not able to Register with its superior TransactionManager due to a fault being returned.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="73c57-106">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="73c57-106">Troubleshooting</span></span>  
 <span data-ttu-id="73c57-107">Döndürülen hata için izleme iletisini inceleyin.</span><span class="sxs-lookup"><span data-stu-id="73c57-107">Inspect the trace message for the fault returned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73c57-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="73c57-108">See also</span></span>

- [<span data-ttu-id="73c57-109">İzleme</span><span class="sxs-lookup"><span data-stu-id="73c57-109">Tracing</span></span>](index.md)
- [<span data-ttu-id="73c57-110">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="73c57-110">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="73c57-111">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="73c57-111">Administration and Diagnostics</span></span>](../index.md)

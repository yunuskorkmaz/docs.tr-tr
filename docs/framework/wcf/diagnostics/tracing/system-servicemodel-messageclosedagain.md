---
title: System.ServiceModel.MessageClosedAgain
ms.date: 03/30/2017
ms.assetid: 24c274d4-65cd-4c91-9869-bc6eb34ef979
ms.openlocfilehash: a8aa5e600789df1b64a8a3f1a6355aaae6a6cf4b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294436"
---
# <a name="systemservicemodelmessageclosedagain"></a><span data-ttu-id="0bb46-102">System.ServiceModel.MessageClosedAgain</span><span class="sxs-lookup"><span data-stu-id="0bb46-102">System.ServiceModel.MessageClosedAgain</span></span>

<span data-ttu-id="0bb46-103">System.ServiceModel.MessageClosedAgain</span><span class="sxs-lookup"><span data-stu-id="0bb46-103">System.ServiceModel.MessageClosedAgain</span></span>  
  
## <a name="description"></a><span data-ttu-id="0bb46-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0bb46-104">Description</span></span>  

 <span data-ttu-id="0bb46-105">Bir ileti yeniden kapatıldı.</span><span class="sxs-lookup"><span data-stu-id="0bb46-105">A message was closed again.</span></span>  
  
 <span data-ttu-id="0bb46-106">Bir ileti yalnızca bir kez kapatılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0bb46-106">A message should be closed only once.</span></span> <span data-ttu-id="0bb46-107">Bu izleme Kullanıcı uzantısı koduna yayılmışsa, Kullanıcı uzantısı kodunun zaten kapatılmış olan bir iletiyi kapattığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0bb46-107">If this trace is being emitted in user extension code, it indicates that the user extension code is closing a message that has already been closed.</span></span> <span data-ttu-id="0bb46-108">Bu izleme ürün kodu aracılığıyla yayılmakta ise, Kullanıcı uzantısı kodunun bir iletiyi çok erken kapatmayabileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0bb46-108">If this trace is being emitted through product code, it indicates that the user extension code could potentially be closing a message too early.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bb46-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0bb46-109">See also</span></span>

- [<span data-ttu-id="0bb46-110">İzleme</span><span class="sxs-lookup"><span data-stu-id="0bb46-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="0bb46-111">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="0bb46-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="0bb46-112">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="0bb46-112">Administration and Diagnostics</span></span>](../index.md)

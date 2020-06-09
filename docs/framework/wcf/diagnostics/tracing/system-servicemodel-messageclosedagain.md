---
title: System.ServiceModel.MessageClosedAgain
ms.date: 03/30/2017
ms.assetid: 24c274d4-65cd-4c91-9869-bc6eb34ef979
ms.openlocfilehash: d341953b8e12b14e6a3fe8a477c16a1b3a4454ae
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84580443"
---
# <a name="systemservicemodelmessageclosedagain"></a><span data-ttu-id="02b31-102">System.ServiceModel.MessageClosedAgain</span><span class="sxs-lookup"><span data-stu-id="02b31-102">System.ServiceModel.MessageClosedAgain</span></span>
<span data-ttu-id="02b31-103">System.ServiceModel.MessageClosedAgain</span><span class="sxs-lookup"><span data-stu-id="02b31-103">System.ServiceModel.MessageClosedAgain</span></span>  
  
## <a name="description"></a><span data-ttu-id="02b31-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="02b31-104">Description</span></span>  
 <span data-ttu-id="02b31-105">Bir ileti yeniden kapatıldı.</span><span class="sxs-lookup"><span data-stu-id="02b31-105">A message was closed again.</span></span>  
  
 <span data-ttu-id="02b31-106">Bir ileti yalnızca bir kez kapatılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="02b31-106">A message should be closed only once.</span></span> <span data-ttu-id="02b31-107">Bu izleme Kullanıcı uzantısı koduna yayılmışsa, Kullanıcı uzantısı kodunun zaten kapatılmış olan bir iletiyi kapattığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="02b31-107">If this trace is being emitted in user extension code, it indicates that the user extension code is closing a message that has already been closed.</span></span> <span data-ttu-id="02b31-108">Bu izleme ürün kodu aracılığıyla yayılmakta ise, Kullanıcı uzantısı kodunun bir iletiyi çok erken kapatmayabileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="02b31-108">If this trace is being emitted through product code, it indicates that the user extension code could potentially be closing a message too early.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02b31-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="02b31-109">See also</span></span>

- [<span data-ttu-id="02b31-110">İzleme</span><span class="sxs-lookup"><span data-stu-id="02b31-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="02b31-111">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="02b31-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="02b31-112">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="02b31-112">Administration and Diagnostics</span></span>](../index.md)

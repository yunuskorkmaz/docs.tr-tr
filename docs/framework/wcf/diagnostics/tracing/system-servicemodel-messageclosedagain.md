---
title: System.ServiceModel.MessageClosedAgain
ms.date: 03/30/2017
ms.assetid: 24c274d4-65cd-4c91-9869-bc6eb34ef979
ms.openlocfilehash: bcac4683655476c6aa868232b0483336b815b6cc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54705988"
---
# <a name="systemservicemodelmessageclosedagain"></a><span data-ttu-id="4dd07-102">System.ServiceModel.MessageClosedAgain</span><span class="sxs-lookup"><span data-stu-id="4dd07-102">System.ServiceModel.MessageClosedAgain</span></span>
<span data-ttu-id="4dd07-103">System.ServiceModel.MessageClosedAgain</span><span class="sxs-lookup"><span data-stu-id="4dd07-103">System.ServiceModel.MessageClosedAgain</span></span>  
  
## <a name="description"></a><span data-ttu-id="4dd07-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4dd07-104">Description</span></span>  
 <span data-ttu-id="4dd07-105">Bir ileti yeniden kapatıldı.</span><span class="sxs-lookup"><span data-stu-id="4dd07-105">A message was closed again.</span></span>  
  
 <span data-ttu-id="4dd07-106">Bir ileti yalnızca bir kez kapatılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4dd07-106">A message should be closed only once.</span></span> <span data-ttu-id="4dd07-107">Kullanıcı uzantı kodunda yayılan bu izleme, kullanıcı uzantı kodu zaten kapatılmış olan bir ileti kapatmakta olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="4dd07-107">If this trace is being emitted in user extension code, it indicates that the user extension code is closing a message that has already been closed.</span></span> <span data-ttu-id="4dd07-108">Ürün kodu yayılan bu izleme, kullanıcı uzantı kodu potansiyel olarak bir ileti çok erken kapatma olması olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="4dd07-108">If this trace is being emitted through product code, it indicates that the user extension code could potentially be closing a message too early.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4dd07-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4dd07-109">See also</span></span>
- [<span data-ttu-id="4dd07-110">İzleme</span><span class="sxs-lookup"><span data-stu-id="4dd07-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="4dd07-111">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="4dd07-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="4dd07-112">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="4dd07-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)

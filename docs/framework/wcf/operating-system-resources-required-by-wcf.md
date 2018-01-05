---
title: "WCF Tarafından Gerektirilen İşletim Sistemi Kaynakları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cdd9a331-53fe-4e0d-bdfe-782264aec5c9
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fde00011a7fffde4c4c75f9605758971b42627f4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="operating-system-resources-required-by-wcf"></a><span data-ttu-id="58114-102">WCF Tarafından Gerektirilen İşletim Sistemi Kaynakları</span><span class="sxs-lookup"><span data-stu-id="58114-102">Operating System Resources Required by WCF</span></span>
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]<span data-ttu-id="58114-103">işlev işletim sistemi tarafından sağlanan bazı kaynaklar bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="58114-103"> depends on several resources that are provided by the operating system to function.</span></span> <span data-ttu-id="58114-104">Aşağıdaki tabloda, bu kaynakları listeler.</span><span class="sxs-lookup"><span data-stu-id="58114-104">The following table lists those resources.</span></span>  
  
|<span data-ttu-id="58114-105">Kaynak</span><span class="sxs-lookup"><span data-stu-id="58114-105">Resource</span></span>|<span data-ttu-id="58114-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="58114-106">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="58114-107">Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC)</span><span class="sxs-lookup"><span data-stu-id="58114-107">Microsoft Distributed Transaction Coordinator (MSDTC)</span></span>|<span data-ttu-id="58114-108">OleTx işlemleri desteklemek için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="58114-108">Required to support OleTx transactions.</span></span>|  
|<span data-ttu-id="58114-109">Internet Information Services (IIS)</span><span class="sxs-lookup"><span data-stu-id="58114-109">Internet Information Services (IIS)</span></span>|<span data-ttu-id="58114-110">Uygulamanızı barındırmak için IIS kullanmak istiyorsanız gereklidir.</span><span class="sxs-lookup"><span data-stu-id="58114-110">Required if you want to use IIS to host your application.</span></span>|  
|<span data-ttu-id="58114-111">Windows İşlem Etkinleştirme Hizmeti (WAS)</span><span class="sxs-lookup"><span data-stu-id="58114-111">Windows Process Activation Service (WAS)</span></span>|<span data-ttu-id="58114-112">WAS uygulamanızı barındırmak için kullanmak istiyorsanız gereklidir.</span><span class="sxs-lookup"><span data-stu-id="58114-112">Required if you want to use WAS to host your application.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="58114-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="58114-113">See Also</span></span>  
 [<span data-ttu-id="58114-114">Sistem Gereksinimleri</span><span class="sxs-lookup"><span data-stu-id="58114-114">System Requirements</span></span>](../../../docs/framework/wcf/wcf-system-requirements.md)

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
ms.openlocfilehash: 31006331f5e8a71bf3f4fb9a68c31cb32d0b6f2b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="operating-system-resources-required-by-wcf"></a><span data-ttu-id="55de4-102">WCF Tarafından Gerektirilen İşletim Sistemi Kaynakları</span><span class="sxs-lookup"><span data-stu-id="55de4-102">Operating System Resources Required by WCF</span></span>
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]<span data-ttu-id="55de4-103">işlev işletim sistemi tarafından sağlanan bazı kaynaklar bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="55de4-103"> depends on several resources that are provided by the operating system to function.</span></span> <span data-ttu-id="55de4-104">Aşağıdaki tabloda, bu kaynakları listeler.</span><span class="sxs-lookup"><span data-stu-id="55de4-104">The following table lists those resources.</span></span>  
  
|<span data-ttu-id="55de4-105">Kaynak</span><span class="sxs-lookup"><span data-stu-id="55de4-105">Resource</span></span>|<span data-ttu-id="55de4-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="55de4-106">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="55de4-107">Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC)</span><span class="sxs-lookup"><span data-stu-id="55de4-107">Microsoft Distributed Transaction Coordinator (MSDTC)</span></span>|<span data-ttu-id="55de4-108">OleTx işlemleri desteklemek için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="55de4-108">Required to support OleTx transactions.</span></span>|  
|<span data-ttu-id="55de4-109">Internet Information Services (IIS)</span><span class="sxs-lookup"><span data-stu-id="55de4-109">Internet Information Services (IIS)</span></span>|<span data-ttu-id="55de4-110">Uygulamanızı barındırmak için IIS kullanmak istiyorsanız gereklidir.</span><span class="sxs-lookup"><span data-stu-id="55de4-110">Required if you want to use IIS to host your application.</span></span>|  
|<span data-ttu-id="55de4-111">Windows İşlem Etkinleştirme Hizmeti (WAS)</span><span class="sxs-lookup"><span data-stu-id="55de4-111">Windows Process Activation Service (WAS)</span></span>|<span data-ttu-id="55de4-112">WAS uygulamanızı barındırmak için kullanmak istiyorsanız gereklidir.</span><span class="sxs-lookup"><span data-stu-id="55de4-112">Required if you want to use WAS to host your application.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="55de4-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="55de4-113">See Also</span></span>  
 [<span data-ttu-id="55de4-114">Sistem Gereksinimleri</span><span class="sxs-lookup"><span data-stu-id="55de4-114">System Requirements</span></span>](../../../docs/framework/wcf/wcf-system-requirements.md)

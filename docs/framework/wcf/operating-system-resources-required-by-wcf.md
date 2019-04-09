---
title: WCF Tarafından Gerektirilen İşletim Sistemi Kaynakları
ms.date: 03/30/2017
ms.assetid: cdd9a331-53fe-4e0d-bdfe-782264aec5c9
ms.openlocfilehash: 828d656370efd7638fa4cf367b84ee7b316b89bb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59100957"
---
# <a name="operating-system-resources-required-by-wcf"></a><span data-ttu-id="72c02-102">WCF Tarafından Gerektirilen İşletim Sistemi Kaynakları</span><span class="sxs-lookup"><span data-stu-id="72c02-102">Operating System Resources Required by WCF</span></span>
<span data-ttu-id="72c02-103">Windows Communication Foundation (WCF), işlev işletim sistemi tarafından sağlanan çeşitli kaynaklar bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="72c02-103">Windows Communication Foundation (WCF) depends on several resources that are provided by the operating system to function.</span></span> <span data-ttu-id="72c02-104">Aşağıdaki tabloda, bu kaynakları listeler.</span><span class="sxs-lookup"><span data-stu-id="72c02-104">The following table lists those resources.</span></span>  
  
|<span data-ttu-id="72c02-105">Kaynak</span><span class="sxs-lookup"><span data-stu-id="72c02-105">Resource</span></span>|<span data-ttu-id="72c02-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="72c02-106">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="72c02-107">Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC)</span><span class="sxs-lookup"><span data-stu-id="72c02-107">Microsoft Distributed Transaction Coordinator (MSDTC)</span></span>|<span data-ttu-id="72c02-108">OleTx işlemleri desteklemek için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="72c02-108">Required to support OleTx transactions.</span></span>|  
|<span data-ttu-id="72c02-109">Internet Information Services (IIS)</span><span class="sxs-lookup"><span data-stu-id="72c02-109">Internet Information Services (IIS)</span></span>|<span data-ttu-id="72c02-110">IIS uygulamanızı barındırmak için kullanmak istiyorsanız gereklidir.</span><span class="sxs-lookup"><span data-stu-id="72c02-110">Required if you want to use IIS to host your application.</span></span>|  
|<span data-ttu-id="72c02-111">Windows İşlem Etkinleştirme Hizmeti (WAS)</span><span class="sxs-lookup"><span data-stu-id="72c02-111">Windows Process Activation Service (WAS)</span></span>|<span data-ttu-id="72c02-112">WAS uygulamanızı barındırmak için kullanmak istiyorsanız gereklidir.</span><span class="sxs-lookup"><span data-stu-id="72c02-112">Required if you want to use WAS to host your application.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="72c02-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="72c02-113">See also</span></span>

- [<span data-ttu-id="72c02-114">Sistem Gereksinimleri</span><span class="sxs-lookup"><span data-stu-id="72c02-114">System Requirements</span></span>](../../../docs/framework/wcf/wcf-system-requirements.md)

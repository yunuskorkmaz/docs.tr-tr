---
title: WCF Tarafından Gerektirilen İşletim Sistemi Kaynakları
ms.date: 03/30/2017
ms.assetid: cdd9a331-53fe-4e0d-bdfe-782264aec5c9
ms.openlocfilehash: 828d656370efd7638fa4cf367b84ee7b316b89bb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59100957"
---
# <a name="operating-system-resources-required-by-wcf"></a><span data-ttu-id="26ade-102">WCF Tarafından Gerektirilen İşletim Sistemi Kaynakları</span><span class="sxs-lookup"><span data-stu-id="26ade-102">Operating System Resources Required by WCF</span></span>
<span data-ttu-id="26ade-103">Windows Communication Foundation (WCF), işlev işletim sistemi tarafından sağlanan çeşitli kaynaklar bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="26ade-103">Windows Communication Foundation (WCF) depends on several resources that are provided by the operating system to function.</span></span> <span data-ttu-id="26ade-104">Aşağıdaki tabloda, bu kaynakları listeler.</span><span class="sxs-lookup"><span data-stu-id="26ade-104">The following table lists those resources.</span></span>  
  
|<span data-ttu-id="26ade-105">Kaynak</span><span class="sxs-lookup"><span data-stu-id="26ade-105">Resource</span></span>|<span data-ttu-id="26ade-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="26ade-106">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="26ade-107">Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC)</span><span class="sxs-lookup"><span data-stu-id="26ade-107">Microsoft Distributed Transaction Coordinator (MSDTC)</span></span>|<span data-ttu-id="26ade-108">OleTx işlemleri desteklemek için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="26ade-108">Required to support OleTx transactions.</span></span>|  
|<span data-ttu-id="26ade-109">Internet Information Services (IIS)</span><span class="sxs-lookup"><span data-stu-id="26ade-109">Internet Information Services (IIS)</span></span>|<span data-ttu-id="26ade-110">IIS uygulamanızı barındırmak için kullanmak istiyorsanız gereklidir.</span><span class="sxs-lookup"><span data-stu-id="26ade-110">Required if you want to use IIS to host your application.</span></span>|  
|<span data-ttu-id="26ade-111">Windows İşlem Etkinleştirme Hizmeti (WAS)</span><span class="sxs-lookup"><span data-stu-id="26ade-111">Windows Process Activation Service (WAS)</span></span>|<span data-ttu-id="26ade-112">WAS uygulamanızı barındırmak için kullanmak istiyorsanız gereklidir.</span><span class="sxs-lookup"><span data-stu-id="26ade-112">Required if you want to use WAS to host your application.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="26ade-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="26ade-113">See also</span></span>

- [<span data-ttu-id="26ade-114">Sistem Gereksinimleri</span><span class="sxs-lookup"><span data-stu-id="26ade-114">System Requirements</span></span>](../../../docs/framework/wcf/wcf-system-requirements.md)

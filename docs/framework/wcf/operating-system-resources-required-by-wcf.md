---
title: WCF Tarafından Gerektirilen İşletim Sistemi Kaynakları
ms.date: 03/30/2017
ms.assetid: cdd9a331-53fe-4e0d-bdfe-782264aec5c9
ms.openlocfilehash: ac9bd5ed7c2092720c6521d0f78185c3fbf9f94b
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72318938"
---
# <a name="operating-system-resources-required-by-wcf"></a><span data-ttu-id="00105-102">WCF Tarafından Gerektirilen İşletim Sistemi Kaynakları</span><span class="sxs-lookup"><span data-stu-id="00105-102">Operating System Resources Required by WCF</span></span>
<span data-ttu-id="00105-103">Windows Communication Foundation (WCF), işletim sistemi tarafından çalışması için sunulan çeşitli kaynaklara bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="00105-103">Windows Communication Foundation (WCF) depends on several resources that are provided by the operating system to function.</span></span> <span data-ttu-id="00105-104">Aşağıdaki tabloda bu kaynaklar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="00105-104">The following table lists those resources.</span></span>  
  
|<span data-ttu-id="00105-105">Kaynak</span><span class="sxs-lookup"><span data-stu-id="00105-105">Resource</span></span>|<span data-ttu-id="00105-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="00105-106">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="00105-107">Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC)</span><span class="sxs-lookup"><span data-stu-id="00105-107">Microsoft Distributed Transaction Coordinator (MSDTC)</span></span>|<span data-ttu-id="00105-108">OleTx işlemlerini desteklemek için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="00105-108">Required to support OleTx transactions.</span></span>|  
|<span data-ttu-id="00105-109">Internet Information Services (IIS)</span><span class="sxs-lookup"><span data-stu-id="00105-109">Internet Information Services (IIS)</span></span>|<span data-ttu-id="00105-110">Uygulamanızı barındırmak için IIS kullanmak istiyorsanız gereklidir.</span><span class="sxs-lookup"><span data-stu-id="00105-110">Required if you want to use IIS to host your application.</span></span>|  
|<span data-ttu-id="00105-111">Windows Işlem etkinleştirme hizmeti (WAS)</span><span class="sxs-lookup"><span data-stu-id="00105-111">Windows Process Activation Service (WAS)</span></span>|<span data-ttu-id="00105-112">Uygulamanızı barındırmak için kullanmak istiyorsanız gereklidir.</span><span class="sxs-lookup"><span data-stu-id="00105-112">Required if you want to use WAS to host your application.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="00105-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="00105-113">See also</span></span>

- [<span data-ttu-id="00105-114">Sistem Gereksinimleri</span><span class="sxs-lookup"><span data-stu-id="00105-114">System Requirements</span></span>](wcf-system-requirements.md)

---
title: Durum Verilerinin Güvenliğini Sağlama
description: Durum verilerini, erişimi sınırlandırmak için özel veya iç değişkenler olarak bildirin. Bu verilere, hala yansıma, serileştirme ve hata ayıklama aracılığıyla erişilebilir.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- security [.NET], state data
- code security, state data
- secure coding, state data
- state data security
ms.assetid: 12671309-2877-43fe-a3df-6863507e712d
ms.openlocfilehash: 73bd0ace28e5b9661cc86d6749ceef9aa4c9ac92
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87557131"
---
# <a name="securing-state-data"></a><span data-ttu-id="c7180-104">Durum Verilerinin Güvenliğini Sağlama</span><span class="sxs-lookup"><span data-stu-id="c7180-104">Securing State Data</span></span>

<span data-ttu-id="c7180-105">Hassas verileri işleyen veya herhangi bir tür güvenlik kararı veren uygulamalar, bu verileri kendi denetimleri altında tutmanız gerekir ve diğer olası kötü amaçlı kodun verilere doğrudan erişmesine izin vermez.</span><span class="sxs-lookup"><span data-stu-id="c7180-105">Applications that handle sensitive data or make any kind of security decisions need to keep that data under their own control and cannot allow other potentially malicious code to access the data directly.</span></span> <span data-ttu-id="c7180-106">Bellekteki verileri korumanın en iyi yolu, verileri özel veya iç (aynı derleme ile sınırlı olan) değişkenleriyle bildirmenin en iyi yoludur.</span><span class="sxs-lookup"><span data-stu-id="c7180-106">The best way to protect data in memory is to declare the data as private or internal (with scope limited to the same assembly) variables.</span></span> <span data-ttu-id="c7180-107">Bununla birlikte, bu veriler Access 'e bağlı olsa da şunları göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="c7180-107">However, even this data is subject to access you should be aware of:</span></span>  
  
- <span data-ttu-id="c7180-108">Yansıma mekanizmalarını kullanarak, nesnenizin başvurmasına başvuran, son derece güvenilen kod özel üyeleri alabilir ve ayarlayabilir.</span><span class="sxs-lookup"><span data-stu-id="c7180-108">Using reflection mechanisms, highly trusted code that can reference your object can get and set private members.</span></span>  
  
- <span data-ttu-id="c7180-109">Serileştirme kullanımı, son derece güvenilen kod, nesnenin serileştirilmiş formundaki karşılık gelen verilere erişebiliyorsa, etkin bir şekilde özel Üyeler alabilir ve ayarlayabilir.</span><span class="sxs-lookup"><span data-stu-id="c7180-109">Using serialization, highly trusted code can effectively get and set private members if it can access the corresponding data in the serialized form of the object.</span></span>  
  
- <span data-ttu-id="c7180-110">Hata ayıklama altında bu veriler okunabilir.</span><span class="sxs-lookup"><span data-stu-id="c7180-110">Under debugging, this data can be read.</span></span>  
  
 <span data-ttu-id="c7180-111">Kendi yöntemlerinizin veya özelliklerinin hiçbirinin bu değerleri istemeden açığa çıkardığı emin olun.</span><span class="sxs-lookup"><span data-stu-id="c7180-111">Make sure none of your own methods or properties exposes these values unintentionally.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7180-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c7180-112">See also</span></span>

- [<span data-ttu-id="c7180-113">Güvenli Kodlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="c7180-113">Secure Coding Guidelines</span></span>](secure-coding-guidelines.md)
- [<span data-ttu-id="c7180-114">ASP.NET Core güvenliği</span><span class="sxs-lookup"><span data-stu-id="c7180-114">ASP.NET Core Security</span></span>](/aspnet/core/security/)

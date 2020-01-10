---
title: Durum Verilerinin Güvenliğini Sağlama
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- security [.NET Framework], state data
- code security, state data
- secure coding, state data
- state data security
ms.assetid: 12671309-2877-43fe-a3df-6863507e712d
ms.openlocfilehash: c30bd2fe9e1ed371be2db60739d3b329fea788c7
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705905"
---
# <a name="securing-state-data"></a><span data-ttu-id="06879-102">Durum Verilerinin Güvenliğini Sağlama</span><span class="sxs-lookup"><span data-stu-id="06879-102">Securing State Data</span></span>
<span data-ttu-id="06879-103">Hassas verileri işleyen veya herhangi bir tür güvenlik kararı veren uygulamalar, bu verileri kendi denetimleri altında tutmanız gerekir ve diğer olası kötü amaçlı kodun verilere doğrudan erişmesine izin vermez.</span><span class="sxs-lookup"><span data-stu-id="06879-103">Applications that handle sensitive data or make any kind of security decisions need to keep that data under their own control and cannot allow other potentially malicious code to access the data directly.</span></span> <span data-ttu-id="06879-104">Bellekteki verileri korumanın en iyi yolu, verileri özel veya iç (aynı derleme ile sınırlı olan) değişkenleriyle bildirmenin en iyi yoludur.</span><span class="sxs-lookup"><span data-stu-id="06879-104">The best way to protect data in memory is to declare the data as private or internal (with scope limited to the same assembly) variables.</span></span> <span data-ttu-id="06879-105">Bununla birlikte, bu veriler Access 'e bağlı olsa da şunları göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="06879-105">However, even this data is subject to access you should be aware of:</span></span>  
  
- <span data-ttu-id="06879-106">Yansıma mekanizmalarını kullanarak, nesnenizin başvurmasına başvuran, son derece güvenilen kod özel üyeleri alabilir ve ayarlayabilir.</span><span class="sxs-lookup"><span data-stu-id="06879-106">Using reflection mechanisms, highly trusted code that can reference your object can get and set private members.</span></span>  
  
- <span data-ttu-id="06879-107">Serileştirme kullanımı, son derece güvenilen kod, nesnenin serileştirilmiş formundaki karşılık gelen verilere erişebiliyorsa, etkin bir şekilde özel Üyeler alabilir ve ayarlayabilir.</span><span class="sxs-lookup"><span data-stu-id="06879-107">Using serialization, highly trusted code can effectively get and set private members if it can access the corresponding data in the serialized form of the object.</span></span>  
  
- <span data-ttu-id="06879-108">Hata ayıklama altında bu veriler okunabilir.</span><span class="sxs-lookup"><span data-stu-id="06879-108">Under debugging, this data can be read.</span></span>  
  
 <span data-ttu-id="06879-109">Kendi yöntemlerinizin veya özelliklerinin hiçbirinin bu değerleri istemeden açığa çıkardığı emin olun.</span><span class="sxs-lookup"><span data-stu-id="06879-109">Make sure none of your own methods or properties exposes these values unintentionally.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06879-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="06879-110">See also</span></span>

- [<span data-ttu-id="06879-111">Güvenli Kodlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="06879-111">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)

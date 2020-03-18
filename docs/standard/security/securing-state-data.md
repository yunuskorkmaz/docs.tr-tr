---
title: Durum Verilerinin Güvenliğini Sağlama
description: Erişimi sınırlamak için durum verilerini özel veya dahili değişkenler olarak bildirin. Bu tür verilere yansıma, serileştirme ve hata ayıklama yoluyla erişilebilir.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- security [.NET Framework], state data
- code security, state data
- secure coding, state data
- state data security
ms.assetid: 12671309-2877-43fe-a3df-6863507e712d
ms.openlocfilehash: f95bf409f7eef8c2636d3c180d2bbd95fbc689c1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186819"
---
# <a name="securing-state-data"></a><span data-ttu-id="fb604-104">Durum Verilerinin Güvenliğini Sağlama</span><span class="sxs-lookup"><span data-stu-id="fb604-104">Securing State Data</span></span>
<span data-ttu-id="fb604-105">Hassas verileri işleyen veya her türlü güvenlik kararı veren uygulamaların bu verileri kendi denetimleri altında tutması gerekir ve diğer kötü amaçlı olabilecek kodların verilere doğrudan erişmesine izin veremez.</span><span class="sxs-lookup"><span data-stu-id="fb604-105">Applications that handle sensitive data or make any kind of security decisions need to keep that data under their own control and cannot allow other potentially malicious code to access the data directly.</span></span> <span data-ttu-id="fb604-106">Bellekteki verileri korumanın en iyi yolu, verileri özel veya dahili (kapsamı aynı derlemeyle sınırlı) değişkenler olarak bildirmektir.</span><span class="sxs-lookup"><span data-stu-id="fb604-106">The best way to protect data in memory is to declare the data as private or internal (with scope limited to the same assembly) variables.</span></span> <span data-ttu-id="fb604-107">Ancak, bu veriler bile sizin bilmeniz gereken erişime tabidir:</span><span class="sxs-lookup"><span data-stu-id="fb604-107">However, even this data is subject to access you should be aware of:</span></span>  
  
- <span data-ttu-id="fb604-108">Yansıma mekanizmaları kullanarak, nesnenize başvurulabilen son derece güvenilir kod özel üyeler alabilir ve ayarlayabilir.</span><span class="sxs-lookup"><span data-stu-id="fb604-108">Using reflection mechanisms, highly trusted code that can reference your object can get and set private members.</span></span>  
  
- <span data-ttu-id="fb604-109">Serileştirme kullanarak, yüksek güvenilen kod, nesnenin serileştirilmiş biçiminde karşılık gelen verilere erişebiliyorsa, özel üyeleri etkili bir şekilde alabilir ve ayarlayabilir.</span><span class="sxs-lookup"><span data-stu-id="fb604-109">Using serialization, highly trusted code can effectively get and set private members if it can access the corresponding data in the serialized form of the object.</span></span>  
  
- <span data-ttu-id="fb604-110">Hata ayıklama altında, bu veriler okunabilir.</span><span class="sxs-lookup"><span data-stu-id="fb604-110">Under debugging, this data can be read.</span></span>  
  
 <span data-ttu-id="fb604-111">Kendi yöntemlerinizin veya özelliklerinizin bu değerleri istemeden ortaya çıkarmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="fb604-111">Make sure none of your own methods or properties exposes these values unintentionally.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb604-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fb604-112">See also</span></span>

- [<span data-ttu-id="fb604-113">Güvenli Kodlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="fb604-113">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)

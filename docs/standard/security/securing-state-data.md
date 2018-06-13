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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fe941fff7091fb579e41a3c417dbb2129bcf3e8c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33580789"
---
# <a name="securing-state-data"></a><span data-ttu-id="c9e56-102">Durum Verilerinin Güvenliğini Sağlama</span><span class="sxs-lookup"><span data-stu-id="c9e56-102">Securing State Data</span></span>
<span data-ttu-id="c9e56-103">Hassas verileri işlemek veya herhangi bir tür güvenlik kararları olun uygulamalar bu verileri kendi denetimi altında tutmanız gerekir ve diğer kötü amaçlı kodlar verilere doğrudan erişmek izin veremez.</span><span class="sxs-lookup"><span data-stu-id="c9e56-103">Applications that handle sensitive data or make any kind of security decisions need to keep that data under their own control and cannot allow other potentially malicious code to access the data directly.</span></span> <span data-ttu-id="c9e56-104">Bellek verileri korumak için en iyi yolu veri özel veya dahili olarak (kapsamla aynı bütünleştirilmiş sınırlı) bildirmektir değişkenleri.</span><span class="sxs-lookup"><span data-stu-id="c9e56-104">The best way to protect data in memory is to declare the data as private or internal (with scope limited to the same assembly) variables.</span></span> <span data-ttu-id="c9e56-105">Ancak, bile bu verileri bilincinde olmanız gereken erişim tabi şöyledir:</span><span class="sxs-lookup"><span data-stu-id="c9e56-105">However, even this data is subject to access you should be aware of:</span></span>  
  
-   <span data-ttu-id="c9e56-106">Yansıma mekanizmalarını kullanarak, nesnenizin başvurabilir yüksek derecede güvenilen kodu alın ve özel üyelerin ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c9e56-106">Using reflection mechanisms, highly trusted code that can reference your object can get and set private members.</span></span>  
  
-   <span data-ttu-id="c9e56-107">Seri hale getirme kullanarak yüksek derecede güvenilen kod etkili bir şekilde almak ve karşılık gelen verilerin nesne seri hale getirilmiş biçiminde erişebiliyorsa özel üyeler ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c9e56-107">Using serialization, highly trusted code can effectively get and set private members if it can access the corresponding data in the serialized form of the object.</span></span>  
  
-   <span data-ttu-id="c9e56-108">Hata ayıklama altında bu verileri okunabilir.</span><span class="sxs-lookup"><span data-stu-id="c9e56-108">Under debugging, this data can be read.</span></span>  
  
 <span data-ttu-id="c9e56-109">Kendi yöntemlerin hiçbiri emin olun veya özellikler bu değerleri kasıtsız olarak kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="c9e56-109">Make sure none of your own methods or properties exposes these values unintentionally.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9e56-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c9e56-110">See Also</span></span>  
 [<span data-ttu-id="c9e56-111">Güvenli Kodlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="c9e56-111">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)

---
title: "Durum Verilerinin Güvenliğini Sağlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [.NET Framework], state data
- code security, state data
- secure coding, state data
- state data security
ms.assetid: 12671309-2877-43fe-a3df-6863507e712d
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bd41f5174f426e723ea7e069eaee8f2d367625a1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="securing-state-data"></a><span data-ttu-id="a137c-102">Durum Verilerinin Güvenliğini Sağlama</span><span class="sxs-lookup"><span data-stu-id="a137c-102">Securing State Data</span></span>
<span data-ttu-id="a137c-103">Hassas verileri işlemek veya herhangi bir tür güvenlik kararları olun uygulamalar bu verileri kendi denetimi altında tutmanız gerekir ve diğer kötü amaçlı kodlar verilere doğrudan erişmek izin veremez.</span><span class="sxs-lookup"><span data-stu-id="a137c-103">Applications that handle sensitive data or make any kind of security decisions need to keep that data under their own control and cannot allow other potentially malicious code to access the data directly.</span></span> <span data-ttu-id="a137c-104">Bellek verileri korumak için en iyi yolu veri özel veya dahili olarak (kapsamla aynı bütünleştirilmiş sınırlı) bildirmektir değişkenleri.</span><span class="sxs-lookup"><span data-stu-id="a137c-104">The best way to protect data in memory is to declare the data as private or internal (with scope limited to the same assembly) variables.</span></span> <span data-ttu-id="a137c-105">Ancak, bile bu verileri bilincinde olmanız gereken erişim tabi şöyledir:</span><span class="sxs-lookup"><span data-stu-id="a137c-105">However, even this data is subject to access you should be aware of:</span></span>  
  
-   <span data-ttu-id="a137c-106">Yansıma mekanizmalarını kullanarak, nesnenizin başvurabilir yüksek derecede güvenilen kodu alın ve özel üyelerin ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a137c-106">Using reflection mechanisms, highly trusted code that can reference your object can get and set private members.</span></span>  
  
-   <span data-ttu-id="a137c-107">Seri hale getirme kullanarak yüksek derecede güvenilen kod etkili bir şekilde almak ve karşılık gelen verilerin nesne seri hale getirilmiş biçiminde erişebiliyorsa özel üyeler ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a137c-107">Using serialization, highly trusted code can effectively get and set private members if it can access the corresponding data in the serialized form of the object.</span></span>  
  
-   <span data-ttu-id="a137c-108">Hata ayıklama altında bu verileri okunabilir.</span><span class="sxs-lookup"><span data-stu-id="a137c-108">Under debugging, this data can be read.</span></span>  
  
 <span data-ttu-id="a137c-109">Kendi yöntemlerin hiçbiri emin olun veya özellikler bu değerleri kasıtsız olarak kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="a137c-109">Make sure none of your own methods or properties exposes these values unintentionally.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a137c-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a137c-110">See Also</span></span>  
 [<span data-ttu-id="a137c-111">Güvenli kodlama yönergeleri</span><span class="sxs-lookup"><span data-stu-id="a137c-111">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)

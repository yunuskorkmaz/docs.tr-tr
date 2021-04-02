---
author: dotpaul
ms.author: paulming
ms.date: 04/05/2019
ms.topic: include
ms.openlocfilehash: 9235f1bcda7529b71aef542d3a49da08a9d4b59e
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/30/2021
ms.locfileid: "96588727"
---
<span data-ttu-id="e407a-101">Güvenilmeyen verilerin serisi kaldırılırken güvenli olmayan seri hale getiriciler savunmasızdır.</span><span class="sxs-lookup"><span data-stu-id="e407a-101">Insecure deserializers are vulnerable when deserializing untrusted data.</span></span> <span data-ttu-id="e407a-102">Saldırgan, kötü amaçlı yan etkileri olan nesneleri eklemek için seri hale getirilmiş verileri beklenmedik türleri içerecek şekilde değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="e407a-102">An attacker could modify the serialized data to include unexpected types to inject objects with malicious side effects.</span></span> <span data-ttu-id="e407a-103">Güvenli olmayan bir seri hale getiriciye karşı saldırı, örneğin, temel alınan işletim sisteminde komutlar yürütme, ağ üzerinden iletişim kurma veya dosyaları silme gibi bir saldırı olabilir.</span><span class="sxs-lookup"><span data-stu-id="e407a-103">An attack against an insecure deserializer could, for example, execute commands on the underlying operating system, communicate over the network, or delete files.</span></span>

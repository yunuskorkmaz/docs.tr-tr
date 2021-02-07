---
description: 'Daha fazla bilgi edinin: Istemcide hata ayıklama'
title: İstemcide Hata Ayıklama
ms.date: 03/30/2017
ms.assetid: 56f9ad05-ea1b-4ef6-85f2-890f7ed71567
ms.openlocfilehash: 45eb76b30eb7243f961ba9764e48d25b6c9dbb35
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99759464"
---
# <a name="debugging-on-the-client"></a><span data-ttu-id="bda5c-103">İstemcide Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="bda5c-103">Debugging on the Client</span></span>

<span data-ttu-id="bda5c-104">Kullanıcıların WCF hizmetiniz için istemci uygulamaları yazmasını kolaylaştırmak için hizmet [\<serviceDebug>](../../../configure-apps/file-schema/wcf/servicedebug.md) davranışını hizmetinizin yapılandırma dosyasına ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bda5c-104">To make it easier for users to write client applications for your WCF service, you can add the [\<serviceDebug>](../../../configure-apps/file-schema/wcf/servicedebug.md) service behavior to the configuration file of your service.</span></span> <span data-ttu-id="bda5c-105">Bu davranış, yardım sayfalarını yayınlamak ve istemciye döndürülen SOAP hatalarının ayrıntılarında yönetilen özel durum bilgilerini döndürmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bda5c-105">This behavior can be used to publish help pages, and return managed exception information in the details of SOAP faults returned to the client.</span></span>

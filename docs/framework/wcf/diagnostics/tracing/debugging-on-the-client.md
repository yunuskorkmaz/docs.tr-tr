---
title: İstemcide Hata Ayıklama
ms.date: 03/30/2017
ms.assetid: 56f9ad05-ea1b-4ef6-85f2-890f7ed71567
ms.openlocfilehash: 0330e0954969fbaf798fe3be029b443f0fa219cd
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84589363"
---
# <a name="debugging-on-the-client"></a><span data-ttu-id="dba2c-102">İstemcide Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="dba2c-102">Debugging on the Client</span></span>
<span data-ttu-id="dba2c-103">Kullanıcıların WCF hizmetiniz için istemci uygulamaları yazmasını kolaylaştırmak için hizmet [\<serviceDebug>](../../../configure-apps/file-schema/wcf/servicedebug.md) davranışını hizmetinizin yapılandırma dosyasına ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dba2c-103">To make it easier for users to write client applications for your WCF service, you can add the [\<serviceDebug>](../../../configure-apps/file-schema/wcf/servicedebug.md) service behavior to the configuration file of your service.</span></span> <span data-ttu-id="dba2c-104">Bu davranış, yardım sayfalarını yayınlamak ve istemciye döndürülen SOAP hatalarının ayrıntılarında yönetilen özel durum bilgilerini döndürmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dba2c-104">This behavior can be used to publish help pages, and return managed exception information in the details of SOAP faults returned to the client.</span></span>

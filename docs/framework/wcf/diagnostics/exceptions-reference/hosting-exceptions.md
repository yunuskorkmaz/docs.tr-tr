---
description: 'Daha fazla bilgi edinin: barındırma özel durumları'
title: Barındırma Özel Durumları
ms.date: 03/30/2017
ms.assetid: ad9e14f8-fa17-4d59-b365-fe0e7ec17c98
ms.openlocfilehash: ba2ff3d4bd069483ddc620a09bb97eeaddf84a56
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99686459"
---
# <a name="hosting-exceptions"></a>Barındırma Özel Durumları

Bu konu, barındırma tarafından oluşturulan tüm özel durumları listeler.  
  
## <a name="exception-list"></a>Özel durum listesi  
  
|Kaynak kodu|Kaynak dizesi|  
|-------------------|---------------------|  
|Hosting_AddressIsAbsoluteUri|Tam URI 'ye izin verilmiyor. ServiceHostingEnvironment. Ensurezerviceavailable API 'SI için tam URI 'Lere izin verilmez. Karşılık gelen hizmet için bir sanal yol kullanın.|  
|Hosting_BuildProviderCouldNotCreateType|Belirtilen CLR türü, hizmet derleme sırasında yüklenemez. Bu türün, uygulamanın \bin dizininde bulunan \\ derlenmiş bir derlemede bulunan \\ ya da genel derleme önbelleğinde yüklü bir derlemede bulunan, uygulamanın \ App_Code dizininde bulunan bir kaynak dosyasında tanımlandığından emin olun. Tür adı büyük/küçük harfe duyarlıdır. \\\ App_Code ve \Bin gibi dizinlerin \\ uygulamanın kök dizininde bulunması gerekir. \\\ App_Code ve \\ \Bin dizinleri alt dizinlerde iç içe geçirilemez.|

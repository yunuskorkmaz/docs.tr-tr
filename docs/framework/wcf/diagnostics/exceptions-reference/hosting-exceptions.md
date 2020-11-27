---
title: Barındırma Özel Durumları
ms.date: 03/30/2017
ms.assetid: ad9e14f8-fa17-4d59-b365-fe0e7ec17c98
ms.openlocfilehash: 342420f10ed53e4f4786ed9506cfde5fbfcfc957
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263340"
---
# <a name="hosting-exceptions"></a>Barındırma Özel Durumları

Bu konu, barındırma tarafından oluşturulan tüm özel durumları listeler.  
  
## <a name="exception-list"></a>Özel durum listesi  
  
|Kaynak kodu|Kaynak dizesi|  
|-------------------|---------------------|  
|Hosting_AddressIsAbsoluteUri|Tam URI 'ye izin verilmiyor. ServiceHostingEnvironment. Ensurezerviceavailable API 'SI için tam URI 'Lere izin verilmez. Karşılık gelen hizmet için bir sanal yol kullanın.|  
|Hosting_BuildProviderCouldNotCreateType|Belirtilen CLR türü, hizmet derleme sırasında yüklenemez. Bu türün, uygulamanın \bin dizininde bulunan \\ derlenmiş bir derlemede bulunan \\ ya da genel derleme önbelleğinde yüklü bir derlemede bulunan, uygulamanın \ App_Code dizininde bulunan bir kaynak dosyasında tanımlandığından emin olun. Tür adı büyük/küçük harfe duyarlıdır. \\\ App_Code ve \Bin gibi dizinlerin \\ uygulamanın kök dizininde bulunması gerekir. \\\ App_Code ve \\ \Bin dizinleri alt dizinlerde iç içe geçirilemez.|

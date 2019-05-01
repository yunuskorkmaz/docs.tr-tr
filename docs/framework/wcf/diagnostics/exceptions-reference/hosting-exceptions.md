---
title: Barındırma Özel Durumları
ms.date: 03/30/2017
ms.assetid: ad9e14f8-fa17-4d59-b365-fe0e7ec17c98
ms.openlocfilehash: f2bc7d0ca09faa2598990437295d1abf0cff3c45
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934738"
---
# <a name="hosting-exceptions"></a>Barındırma Özel Durumları
Bu konu, barındırma tarafından oluşturulan tüm özel durumları listeler.  
  
## <a name="exception-list"></a>Özel durum listesi  
  
|Kaynak kodu|Kaynak dizesi|  
|-------------------|---------------------|  
|Hosting_AddressIsAbsoluteUri|Tam URI izin verilmez. Tam bir URI'leri değerlerine ServiceHostingEnvironment.EnsureServiceAvailable API için izin verilmez. Sanal yol için karşılık gelen hizmet kullanın.|  
|Hosting_BuildProviderCouldNotCreateType|Hizmet derleme sırasında belirtilen CLR türü yüklenemiyor. Bu tür içinde uygulamanın kaynak dosyada ya da tanımlanır doğrulayın \\\App_Code dizin, uygulamanın içinde bulunan bir derlemede yer alan \\\bin dizinine veya yüklü bir derlemede mevcut Genel Derleme Önbelleği. Tür adı büyük/küçük harfe duyarlıdır. Dizinleri gibi \\\App_Code ve \\\bin, uygulamanın kök dizininde yer alması gerekir. \\\App_Code ve \\\bin dizinleri dizinlerde yerleştirilemez.|

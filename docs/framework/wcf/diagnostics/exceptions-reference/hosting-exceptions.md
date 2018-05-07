---
title: Barındırma Özel Durumları
ms.date: 03/30/2017
ms.assetid: ad9e14f8-fa17-4d59-b365-fe0e7ec17c98
ms.openlocfilehash: f2bc7d0ca09faa2598990437295d1abf0cff3c45
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="hosting-exceptions"></a>Barındırma Özel Durumları
Bu konu, barındırma tarafından oluşturulan tüm özel durumları listeler.  
  
## <a name="exception-list"></a>Özel durum listesi  
  
|Kaynak kodu|Kaynak dizesi|  
|-------------------|---------------------|  
|Hosting_AddressIsAbsoluteUri|Tam URI izin verilmiyor. Tam URI değerlerine ServiceHostingEnvironment.EnsureServiceAvailable API için kullanılamaz. Bir sanal yola karşılık gelen hizmet için kullanın.|  
|Hosting_BuildProviderCouldNotCreateType|Hizmet derleme sırasında belirtilen CLR türü yüklenemiyor. Bu tür uygulama içinde bulunan bir kaynak dosya ya da tanımlandığından emin olun \\\App_Code dizin, uygulamanın içinde bulunan derlenmiş bir bütünleştirilmiş kod içinde yer alan \\\bin dizinine veya derlemedeki yüklü mevcut Genel Derleme Önbelleği. Tür adı büyük/küçük harf duyarlıdır. Dizinleri gibi \\\App_Code ve \\\bin uygulamanın kök dizininde bulunması gerekir. \\\App_Code ve \\\bin dizinleri dizinlerde geçemez.|

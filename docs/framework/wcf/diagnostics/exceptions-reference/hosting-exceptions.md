---
title: "Barındırma Özel Durumları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad9e14f8-fa17-4d59-b365-fe0e7ec17c98
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: efc22d39838caae4500a0673f5f86c3285134002
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="hosting-exceptions"></a>Barındırma Özel Durumları
Bu konu, barındırma tarafından oluşturulan tüm özel durumları listeler.  
  
## <a name="exception-list"></a>Özel durum listesi  
  
|Kaynak kodu|Kaynak dizesi|  
|-------------------|---------------------|  
|Hosting_AddressIsAbsoluteUri|Tam URI izin verilmiyor. Tam URI değerlerine ServiceHostingEnvironment.EnsureServiceAvailable API için kullanılamaz. Bir sanal yola karşılık gelen hizmet için kullanın.|  
|Hosting_BuildProviderCouldNotCreateType|Hizmet derleme sırasında belirtilen CLR türü yüklenemiyor. Bu tür uygulama içinde bulunan bir kaynak dosya ya da tanımlandığından emin olun \\\App_Code dizin, uygulamanın içinde bulunan derlenmiş bir bütünleştirilmiş kod içinde yer alan \\\bin dizinine veya derlemedeki yüklü mevcut Genel Derleme Önbelleği. Tür adı büyük/küçük harf duyarlıdır. Dizinleri gibi \\\App_Code ve \\\bin uygulamanın kök dizininde bulunması gerekir. \\\App_Code ve \\\bin dizinleri dizinlerde geçemez.|

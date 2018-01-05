---
title: "Çevrimiçi ve Çevrimdışı Durum Ekleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 05e5f51d-81b6-4c17-b364-9dda447a5fce
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: adb767d3b7a7b991ebcfd8c44e55edb8726cb627
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="adding-online-and-offline-status"></a>Çevrimiçi ve Çevrimdışı Durum Ekleme
Çoğu durumda, belirli ayrıntılarını eş kanal bağlantısının durumunu izlemek bir uygulama için önemlidir. Çağırarak bu bilgiler elde edebileceğiniz `GetProperty` uygulaması yöntemi <xref:System.ServiceModel.IOnlineStatus> arabirimi. Bu arabirim uygulaması olan bir nesne bağlantı durumunu izlemek veya olay işleyicileri gibi kaydetmek `OnOnline` ve `OnOffline`ve çevrimiçi durumu değişiklikler oldukça hemen tepki.  
  
 Eş kanal altyapısında, bir istemci için en az bir diğer eş ve çevrimdışı aksi bağlandıysa çevrimiçi olarak kabul edilir. Bu, hem geliştirme uygulamalarında hata ayıklama veya son kullanıcı için ayrıntılı bilgileri görüntüleyen özellikle yararlı olabilir.  
  
> [!NOTE]
>  Çevrimiçi olay işleyicisi, ilk düğümü iletileri göndermeden önce açık olduğundan emin olmanız gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eş Kanal Uygulaması Oluşturma](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)

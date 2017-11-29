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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1a9f4cf65febd955e69d81f8dbb8f97aaa24e68c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="adding-online-and-offline-status"></a>Çevrimiçi ve Çevrimdışı Durum Ekleme
Çoğu durumda, belirli ayrıntılarını eş kanal bağlantısının durumunu izlemek bir uygulama için önemlidir. Çağırarak bu bilgiler elde edebileceğiniz `GetProperty` uygulaması yöntemi <xref:System.ServiceModel.IOnlineStatus> arabirimi. Bu arabirim uygulaması olan bir nesne bağlantı durumunu izlemek veya olay işleyicileri gibi kaydetmek `OnOnline` ve `OnOffline`ve çevrimiçi durumu değişiklikler oldukça hemen tepki.  
  
 Eş kanal altyapısında, bir istemci için en az bir diğer eş ve çevrimdışı aksi bağlandıysa çevrimiçi olarak kabul edilir. Bu, hem geliştirme uygulamalarında hata ayıklama veya son kullanıcı için ayrıntılı bilgileri görüntüleyen özellikle yararlı olabilir.  
  
> [!NOTE]
>  Çevrimiçi olay işleyicisi, ilk düğümü iletileri göndermeden önce açık olduğundan emin olmanız gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eş kanal uygulaması oluşturma](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)

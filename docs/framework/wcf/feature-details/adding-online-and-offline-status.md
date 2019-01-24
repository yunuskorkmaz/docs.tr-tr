---
title: Çevrimiçi ve Çevrimdışı Durum Ekleme
ms.date: 03/30/2017
ms.assetid: 05e5f51d-81b6-4c17-b364-9dda447a5fce
ms.openlocfilehash: 6a04648e4251774538d298b35d1d655e09e03495
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54591918"
---
# <a name="adding-online-and-offline-status"></a>Çevrimiçi ve Çevrimdışı Durum Ekleme
Çoğu durumda, belirli ayrıntılarını eş kanal bağlantısının durumunu izlemek bir uygulama için önemlidir. Bu bilgiler çağırarak elde edebileceğiniz `GetProperty` uygulaması metodunda <xref:System.ServiceModel.IOnlineStatus> arabirimi. Bir nesne bu arabirimi uygulaması ile bağlantı durumunu izlemek veya olay işleyicileri gibi kaydetme `OnOnline` ve `OnOffline`ve çevrimiçi durumu için değişiklikler oldukça hemen tepki verin.  
  
 Eş kanal altyapısında, aksi takdirde diğer en az bir eş ve çevrimdışı bağlıysa çevrimiçi bir istemci olarak kabul edilir. Bu, hem geliştirme uygulamalarında hata ayıklama veya ayrıntılı bilgi görüntülemek için son kullanıcı özellikle yararlı olabilir.  
  
> [!NOTE]
>  Çevrimiçi olay işleyicisi, önce herhangi bir ileti göndermeden önce düğümü açık olduğundan emin olmanız gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Eş Kanal Uygulaması Oluşturma](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)

---
title: Çevrimiçi ve Çevrimdışı Durum Ekleme
ms.date: 03/30/2017
ms.assetid: 05e5f51d-81b6-4c17-b364-9dda447a5fce
ms.openlocfilehash: 74b113d64003756982a6b5701d9601c3116a9046
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960655"
---
# <a name="adding-online-and-offline-status"></a>Çevrimiçi ve Çevrimdışı Durum Ekleme
Çoğu durumda, bir uygulamanın bir eş kanal bağlantısının durumuyla ilgili belirli ayrıntıları izlemesi önemlidir. Bu bilgileri, `GetProperty` <xref:System.ServiceModel.IOnlineStatus> arabirimi uygulamasında metodunu çağırarak elde edebilirsiniz. Bu arabirimin uygulamasına sahip bir nesne, `OnOnline` ve `OnOffline`gibi olay işleyicileri için bağlantı durumunu izleyebilir veya kaydedebilir ve çevrimiçi durumdaki değişiklikler gerçekleştiğinde hemen tepki verebilir.  
  
 Eş kanal altyapısında, bir istemcinin en az bir diğer eşe ve aksi halde çevrimdışı olarak bağlanması durumunda çevrimiçi olduğu kabul edilir. Bu, özellikle geliştirme uygulamalarında hata ayıklaması yapmak veya son kullanıcıya ayrıntılı bilgiler görüntülemek için yararlı olabilir.  
  
> [!NOTE]
> Çevrimiçi olay işleyicisi önce herhangi bir ileti göndermeden önce düğümün açık olduğundan emin olmalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Eş Kanal Uygulaması Oluşturma](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)

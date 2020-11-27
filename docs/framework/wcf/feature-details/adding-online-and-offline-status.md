---
title: Çevrimiçi ve Çevrimdışı Durum Ekleme
ms.date: 03/30/2017
ms.assetid: 05e5f51d-81b6-4c17-b364-9dda447a5fce
ms.openlocfilehash: 08ae4a20ced9626504c9fd2045416460e0878c5b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96292929"
---
# <a name="adding-online-and-offline-status"></a>Çevrimiçi ve Çevrimdışı Durum Ekleme

Çoğu durumda, bir uygulamanın bir eş kanal bağlantısının durumuyla ilgili belirli ayrıntıları izlemesi önemlidir. Bu bilgileri, `GetProperty` arabirimi uygulamasında metodunu çağırarak elde edebilirsiniz <xref:System.ServiceModel.IOnlineStatus> . Bu arabirimin uygulamasına sahip bir nesne, ve gibi olay işleyicileri için bağlantı durumunu izleyebilir veya kaydedebilir `OnOnline` `OnOffline` ve çevrimiçi durumdaki değişiklikler gerçekleştiğinde hemen tepki verebilir.  
  
 Eş kanal altyapısında, bir istemcinin en az bir diğer eşe ve aksi halde çevrimdışı olarak bağlanması durumunda çevrimiçi olduğu kabul edilir. Bu, özellikle geliştirme uygulamalarında hata ayıklaması yapmak veya son kullanıcıya ayrıntılı bilgiler görüntülemek için yararlı olabilir.  
  
> [!NOTE]
> Çevrimiçi olay işleyicisi önce herhangi bir ileti göndermeden önce düğümün açık olduğundan emin olmalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Eş Kanal Uygulaması Oluşturma](building-a-peer-channel-application.md)

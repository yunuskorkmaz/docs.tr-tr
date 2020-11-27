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
# <a name="adding-online-and-offline-status"></a><span data-ttu-id="fe6b6-102">Çevrimiçi ve Çevrimdışı Durum Ekleme</span><span class="sxs-lookup"><span data-stu-id="fe6b6-102">Adding Online and Offline Status</span></span>

<span data-ttu-id="fe6b6-103">Çoğu durumda, bir uygulamanın bir eş kanal bağlantısının durumuyla ilgili belirli ayrıntıları izlemesi önemlidir.</span><span class="sxs-lookup"><span data-stu-id="fe6b6-103">In many cases, it is important for an application to monitor specific details about the status of a Peer Channel connection.</span></span> <span data-ttu-id="fe6b6-104">Bu bilgileri, `GetProperty` arabirimi uygulamasında metodunu çağırarak elde edebilirsiniz <xref:System.ServiceModel.IOnlineStatus> .</span><span class="sxs-lookup"><span data-stu-id="fe6b6-104">You can obtain this information by calling the `GetProperty` method on an implementation of the <xref:System.ServiceModel.IOnlineStatus> interface.</span></span> <span data-ttu-id="fe6b6-105">Bu arabirimin uygulamasına sahip bir nesne, ve gibi olay işleyicileri için bağlantı durumunu izleyebilir veya kaydedebilir `OnOnline` `OnOffline` ve çevrimiçi durumdaki değişiklikler gerçekleştiğinde hemen tepki verebilir.</span><span class="sxs-lookup"><span data-stu-id="fe6b6-105">An object with an implementation of this interface can monitor connection status or register for event handlers, such as `OnOnline` and `OnOffline`, and react immediately as changes to online status occur.</span></span>  
  
 <span data-ttu-id="fe6b6-106">Eş kanal altyapısında, bir istemcinin en az bir diğer eşe ve aksi halde çevrimdışı olarak bağlanması durumunda çevrimiçi olduğu kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="fe6b6-106">In the Peer Channel infrastructure, a client is considered to be online if it is connected to at least one other peer and offline otherwise.</span></span> <span data-ttu-id="fe6b6-107">Bu, özellikle geliştirme uygulamalarında hata ayıklaması yapmak veya son kullanıcıya ayrıntılı bilgiler görüntülemek için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="fe6b6-107">This can be particularly useful in both debugging a developing applications or displaying detailed information to the end user.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fe6b6-108">Çevrimiçi olay işleyicisi önce herhangi bir ileti göndermeden önce düğümün açık olduğundan emin olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fe6b6-108">An online event handler should first ensure that the node is open before sending any messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe6b6-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fe6b6-109">See also</span></span>

- [<span data-ttu-id="fe6b6-110">Eş Kanal Uygulaması Oluşturma</span><span class="sxs-lookup"><span data-stu-id="fe6b6-110">Building a Peer Channel Application</span></span>](building-a-peer-channel-application.md)

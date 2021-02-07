---
description: 'Hakkında daha fazla bilgi edinin: çevrimiçi ve çevrimdışı durum ekleme'
title: Çevrimiçi ve Çevrimdışı Durum Ekleme
ms.date: 03/30/2017
ms.assetid: 05e5f51d-81b6-4c17-b364-9dda447a5fce
ms.openlocfilehash: 33f7920954ed28ebc2c3d34cc54a2e294f5730c7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99705245"
---
# <a name="adding-online-and-offline-status"></a><span data-ttu-id="bf251-103">Çevrimiçi ve Çevrimdışı Durum Ekleme</span><span class="sxs-lookup"><span data-stu-id="bf251-103">Adding Online and Offline Status</span></span>

<span data-ttu-id="bf251-104">Çoğu durumda, bir uygulamanın bir eş kanal bağlantısının durumuyla ilgili belirli ayrıntıları izlemesi önemlidir.</span><span class="sxs-lookup"><span data-stu-id="bf251-104">In many cases, it is important for an application to monitor specific details about the status of a Peer Channel connection.</span></span> <span data-ttu-id="bf251-105">Bu bilgileri, `GetProperty` arabirimi uygulamasında metodunu çağırarak elde edebilirsiniz <xref:System.ServiceModel.IOnlineStatus> .</span><span class="sxs-lookup"><span data-stu-id="bf251-105">You can obtain this information by calling the `GetProperty` method on an implementation of the <xref:System.ServiceModel.IOnlineStatus> interface.</span></span> <span data-ttu-id="bf251-106">Bu arabirimin uygulamasına sahip bir nesne, ve gibi olay işleyicileri için bağlantı durumunu izleyebilir veya kaydedebilir `OnOnline` `OnOffline` ve çevrimiçi durumdaki değişiklikler gerçekleştiğinde hemen tepki verebilir.</span><span class="sxs-lookup"><span data-stu-id="bf251-106">An object with an implementation of this interface can monitor connection status or register for event handlers, such as `OnOnline` and `OnOffline`, and react immediately as changes to online status occur.</span></span>  
  
 <span data-ttu-id="bf251-107">Eş kanal altyapısında, bir istemcinin en az bir diğer eşe ve aksi halde çevrimdışı olarak bağlanması durumunda çevrimiçi olduğu kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="bf251-107">In the Peer Channel infrastructure, a client is considered to be online if it is connected to at least one other peer and offline otherwise.</span></span> <span data-ttu-id="bf251-108">Bu, özellikle geliştirme uygulamalarında hata ayıklaması yapmak veya son kullanıcıya ayrıntılı bilgiler görüntülemek için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="bf251-108">This can be particularly useful in both debugging a developing applications or displaying detailed information to the end user.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bf251-109">Çevrimiçi olay işleyicisi önce herhangi bir ileti göndermeden önce düğümün açık olduğundan emin olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bf251-109">An online event handler should first ensure that the node is open before sending any messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf251-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bf251-110">See also</span></span>

- [<span data-ttu-id="bf251-111">Eş Kanal Uygulaması Oluşturma</span><span class="sxs-lookup"><span data-stu-id="bf251-111">Building a Peer Channel Application</span></span>](building-a-peer-channel-application.md)

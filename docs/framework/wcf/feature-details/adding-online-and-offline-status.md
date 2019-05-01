---
title: Çevrimiçi ve Çevrimdışı Durum Ekleme
ms.date: 03/30/2017
ms.assetid: 05e5f51d-81b6-4c17-b364-9dda447a5fce
ms.openlocfilehash: 15a963d4de0dcf1d7f0162b0a3266e17d4073ecd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857746"
---
# <a name="adding-online-and-offline-status"></a><span data-ttu-id="12329-102">Çevrimiçi ve Çevrimdışı Durum Ekleme</span><span class="sxs-lookup"><span data-stu-id="12329-102">Adding Online and Offline Status</span></span>
<span data-ttu-id="12329-103">Çoğu durumda, belirli ayrıntılarını eş kanal bağlantısının durumunu izlemek bir uygulama için önemlidir.</span><span class="sxs-lookup"><span data-stu-id="12329-103">In many cases, it is important for an application to monitor specific details about the status of a Peer Channel connection.</span></span> <span data-ttu-id="12329-104">Bu bilgiler çağırarak elde edebileceğiniz `GetProperty` uygulaması metodunda <xref:System.ServiceModel.IOnlineStatus> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="12329-104">You can obtain this information by calling the `GetProperty` method on an implementation of the <xref:System.ServiceModel.IOnlineStatus> interface.</span></span> <span data-ttu-id="12329-105">Bir nesne bu arabirimi uygulaması ile bağlantı durumunu izlemek veya olay işleyicileri gibi kaydetme `OnOnline` ve `OnOffline`ve çevrimiçi durumu için değişiklikler oldukça hemen tepki verin.</span><span class="sxs-lookup"><span data-stu-id="12329-105">An object with an implementation of this interface can monitor connection status or register for event handlers, such as `OnOnline` and `OnOffline`, and react immediately as changes to online status occur.</span></span>  
  
 <span data-ttu-id="12329-106">Eş kanal altyapısında, aksi takdirde diğer en az bir eş ve çevrimdışı bağlıysa çevrimiçi bir istemci olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="12329-106">In the Peer Channel infrastructure, a client is considered to be online if it is connected to at least one other peer and offline otherwise.</span></span> <span data-ttu-id="12329-107">Bu, hem geliştirme uygulamalarında hata ayıklama veya ayrıntılı bilgi görüntülemek için son kullanıcı özellikle yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="12329-107">This can be particularly useful in both debugging a developing applications or displaying detailed information to the end user.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="12329-108">Çevrimiçi olay işleyicisi, önce herhangi bir ileti göndermeden önce düğümü açık olduğundan emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="12329-108">An online event handler should first ensure that the node is open before sending any messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12329-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="12329-109">See also</span></span>

- [<span data-ttu-id="12329-110">Eş Kanal Uygulaması Oluşturma</span><span class="sxs-lookup"><span data-stu-id="12329-110">Building a Peer Channel Application</span></span>](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)

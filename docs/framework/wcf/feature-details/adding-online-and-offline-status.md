---
title: Çevrimiçi ve Çevrimdışı Durum Ekleme
ms.date: 03/30/2017
ms.assetid: 05e5f51d-81b6-4c17-b364-9dda447a5fce
ms.openlocfilehash: fb19614c1975c5634a81ca2f40edb145b724cd1d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33488110"
---
# <a name="adding-online-and-offline-status"></a><span data-ttu-id="d93c6-102">Çevrimiçi ve Çevrimdışı Durum Ekleme</span><span class="sxs-lookup"><span data-stu-id="d93c6-102">Adding Online and Offline Status</span></span>
<span data-ttu-id="d93c6-103">Çoğu durumda, belirli ayrıntılarını eş kanal bağlantısının durumunu izlemek bir uygulama için önemlidir.</span><span class="sxs-lookup"><span data-stu-id="d93c6-103">In many cases, it is important for an application to monitor specific details about the status of a Peer Channel connection.</span></span> <span data-ttu-id="d93c6-104">Çağırarak bu bilgiler elde edebileceğiniz `GetProperty` uygulaması yöntemi <xref:System.ServiceModel.IOnlineStatus> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="d93c6-104">You can obtain this information by calling the `GetProperty` method on an implementation of the <xref:System.ServiceModel.IOnlineStatus> interface.</span></span> <span data-ttu-id="d93c6-105">Bu arabirim uygulaması olan bir nesne bağlantı durumunu izlemek veya olay işleyicileri gibi kaydetmek `OnOnline` ve `OnOffline`ve çevrimiçi durumu değişiklikler oldukça hemen tepki.</span><span class="sxs-lookup"><span data-stu-id="d93c6-105">An object with an implementation of this interface can monitor connection status or register for event handlers, such as `OnOnline` and `OnOffline`, and react immediately as changes to online status occur.</span></span>  
  
 <span data-ttu-id="d93c6-106">Eş kanal altyapısında, bir istemci için en az bir diğer eş ve çevrimdışı aksi bağlandıysa çevrimiçi olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="d93c6-106">In the Peer Channel infrastructure, a client is considered to be online if it is connected to at least one other peer and offline otherwise.</span></span> <span data-ttu-id="d93c6-107">Bu, hem geliştirme uygulamalarında hata ayıklama veya son kullanıcı için ayrıntılı bilgileri görüntüleyen özellikle yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="d93c6-107">This can be particularly useful in both debugging a developing applications or displaying detailed information to the end user.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d93c6-108">Çevrimiçi olay işleyicisi, ilk düğümü iletileri göndermeden önce açık olduğundan emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d93c6-108">An online event handler should first ensure that the node is open before sending any messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d93c6-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d93c6-109">See Also</span></span>  
 [<span data-ttu-id="d93c6-110">Eş Kanal Uygulaması Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d93c6-110">Building a Peer Channel Application</span></span>](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)

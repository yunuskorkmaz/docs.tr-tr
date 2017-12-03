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
ms.openlocfilehash: 5d5b6c858b5aa5918498ba8fccee41f7392ac32e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="adding-online-and-offline-status"></a><span data-ttu-id="b4378-102">Çevrimiçi ve Çevrimdışı Durum Ekleme</span><span class="sxs-lookup"><span data-stu-id="b4378-102">Adding Online and Offline Status</span></span>
<span data-ttu-id="b4378-103">Çoğu durumda, belirli ayrıntılarını eş kanal bağlantısının durumunu izlemek bir uygulama için önemlidir.</span><span class="sxs-lookup"><span data-stu-id="b4378-103">In many cases, it is important for an application to monitor specific details about the status of a Peer Channel connection.</span></span> <span data-ttu-id="b4378-104">Çağırarak bu bilgiler elde edebileceğiniz `GetProperty` uygulaması yöntemi <xref:System.ServiceModel.IOnlineStatus> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="b4378-104">You can obtain this information by calling the `GetProperty` method on an implementation of the <xref:System.ServiceModel.IOnlineStatus> interface.</span></span> <span data-ttu-id="b4378-105">Bu arabirim uygulaması olan bir nesne bağlantı durumunu izlemek veya olay işleyicileri gibi kaydetmek `OnOnline` ve `OnOffline`ve çevrimiçi durumu değişiklikler oldukça hemen tepki.</span><span class="sxs-lookup"><span data-stu-id="b4378-105">An object with an implementation of this interface can monitor connection status or register for event handlers, such as `OnOnline` and `OnOffline`, and react immediately as changes to online status occur.</span></span>  
  
 <span data-ttu-id="b4378-106">Eş kanal altyapısında, bir istemci için en az bir diğer eş ve çevrimdışı aksi bağlandıysa çevrimiçi olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="b4378-106">In the Peer Channel infrastructure, a client is considered to be online if it is connected to at least one other peer and offline otherwise.</span></span> <span data-ttu-id="b4378-107">Bu, hem geliştirme uygulamalarında hata ayıklama veya son kullanıcı için ayrıntılı bilgileri görüntüleyen özellikle yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="b4378-107">This can be particularly useful in both debugging a developing applications or displaying detailed information to the end user.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b4378-108">Çevrimiçi olay işleyicisi, ilk düğümü iletileri göndermeden önce açık olduğundan emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b4378-108">An online event handler should first ensure that the node is open before sending any messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4378-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b4378-109">See Also</span></span>  
 [<span data-ttu-id="b4378-110">Eş kanal uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="b4378-110">Building a Peer Channel Application</span></span>](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)

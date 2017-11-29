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
# <a name="adding-online-and-offline-status"></a><span data-ttu-id="9b84a-102">Çevrimiçi ve Çevrimdışı Durum Ekleme</span><span class="sxs-lookup"><span data-stu-id="9b84a-102">Adding Online and Offline Status</span></span>
<span data-ttu-id="9b84a-103">Çoğu durumda, belirli ayrıntılarını eş kanal bağlantısının durumunu izlemek bir uygulama için önemlidir.</span><span class="sxs-lookup"><span data-stu-id="9b84a-103">In many cases, it is important for an application to monitor specific details about the status of a Peer Channel connection.</span></span> <span data-ttu-id="9b84a-104">Çağırarak bu bilgiler elde edebileceğiniz `GetProperty` uygulaması yöntemi <xref:System.ServiceModel.IOnlineStatus> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="9b84a-104">You can obtain this information by calling the `GetProperty` method on an implementation of the <xref:System.ServiceModel.IOnlineStatus> interface.</span></span> <span data-ttu-id="9b84a-105">Bu arabirim uygulaması olan bir nesne bağlantı durumunu izlemek veya olay işleyicileri gibi kaydetmek `OnOnline` ve `OnOffline`ve çevrimiçi durumu değişiklikler oldukça hemen tepki.</span><span class="sxs-lookup"><span data-stu-id="9b84a-105">An object with an implementation of this interface can monitor connection status or register for event handlers, such as `OnOnline` and `OnOffline`, and react immediately as changes to online status occur.</span></span>  
  
 <span data-ttu-id="9b84a-106">Eş kanal altyapısında, bir istemci için en az bir diğer eş ve çevrimdışı aksi bağlandıysa çevrimiçi olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="9b84a-106">In the Peer Channel infrastructure, a client is considered to be online if it is connected to at least one other peer and offline otherwise.</span></span> <span data-ttu-id="9b84a-107">Bu, hem geliştirme uygulamalarında hata ayıklama veya son kullanıcı için ayrıntılı bilgileri görüntüleyen özellikle yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="9b84a-107">This can be particularly useful in both debugging a developing applications or displaying detailed information to the end user.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9b84a-108">Çevrimiçi olay işleyicisi, ilk düğümü iletileri göndermeden önce açık olduğundan emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9b84a-108">An online event handler should first ensure that the node is open before sending any messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b84a-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9b84a-109">See Also</span></span>  
 [<span data-ttu-id="9b84a-110">Eş kanal uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="9b84a-110">Building a Peer Channel Application</span></span>](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)

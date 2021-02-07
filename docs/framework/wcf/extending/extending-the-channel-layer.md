---
description: 'Daha fazla bilgi edinin: Kanal Katmanını Genişletme'
title: Kanal Katmanını Genişletme
ms.date: 03/30/2017
helpviewer_keywords:
- extending channels [WCF]
ms.assetid: 4238db74-2fb6-4dc8-a326-f58527230810
ms.openlocfilehash: 4588a2749127e454801615cc8916d83fc15592bc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99685588"
---
# <a name="extending-the-channel-layer"></a><span data-ttu-id="30692-103">Kanal Katmanını Genişletme</span><span class="sxs-lookup"><span data-stu-id="30692-103">Extending the Channel Layer</span></span>

<span data-ttu-id="30692-104">Kanal katmanı, istemciler ve hizmetler arasındaki ileti alışverişinin sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="30692-104">The channel layer is responsible for the exchange of messages between clients and services.</span></span> <span data-ttu-id="30692-105">Kanal uzantıları, SOAP iletilerini taşımak için yeni bir ağ taşıması uygulama gibi güvenlik veya aktarım işlevselliği gibi yeni protokol işlevleri uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="30692-105">Channel extensions can implement new protocol functionality, such as security, or transport functionality, such as implementing a new network transport to carry SOAP messages.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="30692-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="30692-106">In This Section</span></span>  

 [<span data-ttu-id="30692-107">Kanal Modeli Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="30692-107">Channel Model Overview</span></span>](channel-model-overview.md)  
 <span data-ttu-id="30692-108">Kanalların ne olduğu, sağladıkları Özellikler ve bir hizmette ve istemci uygulamasında nasıl çalıştıkları hakkında üst düzey bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="30692-108">Provides a high-level overview of what channels are, the features that they provide and how they work both in a service and a client application.</span></span>  
  
 [<span data-ttu-id="30692-109">Geliştirme Kanalları</span><span class="sxs-lookup"><span data-stu-id="30692-109">Developing Channels</span></span>](developing-channels.md)  
 <span data-ttu-id="30692-110">Çeşitli kanal altyapısı türlerinin oynamakta olduğu, durum altyapısı ve durum yaşam döngüsünün nasıl çalıştığı, meta veri desteğinin nasıl uygulanacağı ve kanalların ileti kodlayıcılarıyla nasıl çalıştığı hakkında ayrıntılı olarak açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="30692-110">Describes in depth the roles that the various channel infrastructure types play, how the state engine and state lifecycle works, how to handle exceptions and faults, how to implement metadata support, and how channels work with message encoders.</span></span>  
  
 [<span data-ttu-id="30692-111">Özel Kodlayıcılar</span><span class="sxs-lookup"><span data-stu-id="30692-111">Custom Encoders</span></span>](custom-encoders.md)  
 <span data-ttu-id="30692-112">İleti kodlayıcılarındaki kanallar üzerinde oynamakta olan rolü ve bir oluşturma işlemini açıklar.</span><span class="sxs-lookup"><span data-stu-id="30692-112">Describes the role that message encoders play in channels and how to build one.</span></span>  
  
 [<span data-ttu-id="30692-113">Özel Akış Yükseltmeleri</span><span class="sxs-lookup"><span data-stu-id="30692-113">Custom Stream Upgrades</span></span>](custom-stream-upgrades.md)  
 <span data-ttu-id="30692-114">Akışa dayalı aktarımlar tarafından belirtilen akışları yükseltme işlemini açıklar.</span><span class="sxs-lookup"><span data-stu-id="30692-114">Describes the process of upgrading the streams provided by stream-oriented transports.</span></span>

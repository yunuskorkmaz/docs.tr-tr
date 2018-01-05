---
title: "Kanal Katmanını Genişletme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: extending channels [WCF]
ms.assetid: 4238db74-2fb6-4dc8-a326-f58527230810
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5a1a1bb0b1f2c5e6b42ee793f18f5ad442b1fe8e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="extending-the-channel-layer"></a><span data-ttu-id="5f7c2-102">Kanal Katmanını Genişletme</span><span class="sxs-lookup"><span data-stu-id="5f7c2-102">Extending the Channel Layer</span></span>
<span data-ttu-id="5f7c2-103">Kanal katmanını, istemciler ve hizmetler arasında ileti alışverişi sorumludur.</span><span class="sxs-lookup"><span data-stu-id="5f7c2-103">The channel layer is responsible for the exchange of messages between clients and services.</span></span> <span data-ttu-id="5f7c2-104">Kanal uzantıları, güvenlik veya SOAP iletilerine taşımak için yeni bir ağ aktarımı uygulama gibi aktarım işlevlerini gibi yeni protokol işlevselliği uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5f7c2-104">Channel extensions can implement new protocol functionality, such as security, or transport functionality, such as implementing a new network transport to carry SOAP messages.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5f7c2-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="5f7c2-105">In This Section</span></span>  
 [<span data-ttu-id="5f7c2-106">Kanal Modeline Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5f7c2-106">Channel Model Overview</span></span>](../../../../docs/framework/wcf/extending/channel-model-overview.md)  
 <span data-ttu-id="5f7c2-107">Hangi kanalları özelliklerdir, sağladıkları ve hem de bir hizmet ve bir istemci uygulaması nasıl çalıştıklarını üst düzey bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="5f7c2-107">Provides a high-level overview of what channels are, the features that they provide and how they work both in a service and a client application.</span></span>  
  
 [<span data-ttu-id="5f7c2-108">Geliştirme Kanalları</span><span class="sxs-lookup"><span data-stu-id="5f7c2-108">Developing Channels</span></span>](../../../../docs/framework/wcf/extending/developing-channels.md)  
 <span data-ttu-id="5f7c2-109">Derinlemesine kanal altyapı çeşitli yürütmek rolleri, durumu altyapısı ve durumu yaşam döngüsü nasıl çalıştığını, özel durum ve hataları nasıl ele alınacağını, meta verileri desteği uygulama ve kanalları ileti kodlayıcılarla nasıl çalışır? açıklar.</span><span class="sxs-lookup"><span data-stu-id="5f7c2-109">Describes in depth the roles that the various channel infrastructure types play, how the state engine and state lifecycle works, how to handle exceptions and faults, how to implement metadata support, and how channels work with message encoders.</span></span>  
  
 [<span data-ttu-id="5f7c2-110">Özel Kodlayıcılar</span><span class="sxs-lookup"><span data-stu-id="5f7c2-110">Custom Encoders</span></span>](../../../../docs/framework/wcf/extending/custom-encoders.md)  
 <span data-ttu-id="5f7c2-111">Kanallar ve bir oluşturma iletisi kodlayıcılar yürütebilirsiniz rolü açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5f7c2-111">Describes the role that message encoders play in channels and how to build one.</span></span>  
  
 [<span data-ttu-id="5f7c2-112">Özel Akış Yükseltmeleri</span><span class="sxs-lookup"><span data-stu-id="5f7c2-112">Custom Stream Upgrades</span></span>](../../../../docs/framework/wcf/extending/custom-stream-upgrades.md)  
 <span data-ttu-id="5f7c2-113">Akış odaklı taşımaları tarafından sağlanan akışlar yükseltme işlemini açıklar.</span><span class="sxs-lookup"><span data-stu-id="5f7c2-113">Describes the process of upgrading the streams provided by stream-oriented transports.</span></span>

---
title: Kanal Katmanını Genişletme
ms.date: 03/30/2017
helpviewer_keywords:
- extending channels [WCF]
ms.assetid: 4238db74-2fb6-4dc8-a326-f58527230810
ms.openlocfilehash: e60d8ef1a5191c6407b01eb1a2456a06aeeb1914
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33488240"
---
# <a name="extending-the-channel-layer"></a><span data-ttu-id="9168d-102">Kanal Katmanını Genişletme</span><span class="sxs-lookup"><span data-stu-id="9168d-102">Extending the Channel Layer</span></span>
<span data-ttu-id="9168d-103">Kanal katmanını, istemciler ve hizmetler arasında ileti alışverişi sorumludur.</span><span class="sxs-lookup"><span data-stu-id="9168d-103">The channel layer is responsible for the exchange of messages between clients and services.</span></span> <span data-ttu-id="9168d-104">Kanal uzantıları, güvenlik veya SOAP iletilerine taşımak için yeni bir ağ aktarımı uygulama gibi aktarım işlevlerini gibi yeni protokol işlevselliği uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9168d-104">Channel extensions can implement new protocol functionality, such as security, or transport functionality, such as implementing a new network transport to carry SOAP messages.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9168d-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="9168d-105">In This Section</span></span>  
 [<span data-ttu-id="9168d-106">Kanal Modeline Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9168d-106">Channel Model Overview</span></span>](../../../../docs/framework/wcf/extending/channel-model-overview.md)  
 <span data-ttu-id="9168d-107">Hangi kanalları özelliklerdir, sağladıkları ve hem de bir hizmet ve bir istemci uygulaması nasıl çalıştıklarını üst düzey bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="9168d-107">Provides a high-level overview of what channels are, the features that they provide and how they work both in a service and a client application.</span></span>  
  
 [<span data-ttu-id="9168d-108">Geliştirme Kanalları</span><span class="sxs-lookup"><span data-stu-id="9168d-108">Developing Channels</span></span>](../../../../docs/framework/wcf/extending/developing-channels.md)  
 <span data-ttu-id="9168d-109">Derinlemesine kanal altyapı çeşitli yürütmek rolleri, durumu altyapısı ve durumu yaşam döngüsü nasıl çalıştığını, özel durum ve hataları nasıl ele alınacağını, meta verileri desteği uygulama ve kanalları ileti kodlayıcılarla nasıl çalışır? açıklar.</span><span class="sxs-lookup"><span data-stu-id="9168d-109">Describes in depth the roles that the various channel infrastructure types play, how the state engine and state lifecycle works, how to handle exceptions and faults, how to implement metadata support, and how channels work with message encoders.</span></span>  
  
 [<span data-ttu-id="9168d-110">Özel Kodlayıcılar</span><span class="sxs-lookup"><span data-stu-id="9168d-110">Custom Encoders</span></span>](../../../../docs/framework/wcf/extending/custom-encoders.md)  
 <span data-ttu-id="9168d-111">Kanallar ve bir oluşturma iletisi kodlayıcılar yürütebilirsiniz rolü açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9168d-111">Describes the role that message encoders play in channels and how to build one.</span></span>  
  
 [<span data-ttu-id="9168d-112">Özel Akış Yükseltmeleri</span><span class="sxs-lookup"><span data-stu-id="9168d-112">Custom Stream Upgrades</span></span>](../../../../docs/framework/wcf/extending/custom-stream-upgrades.md)  
 <span data-ttu-id="9168d-113">Akış odaklı taşımaları tarafından sağlanan akışlar yükseltme işlemini açıklar.</span><span class="sxs-lookup"><span data-stu-id="9168d-113">Describes the process of upgrading the streams provided by stream-oriented transports.</span></span>

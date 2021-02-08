---
description: 'Hakkında daha fazla bilgi edinin: WCF için gereken Işletim sistemi kaynakları'
title: WCF Tarafından Gerektirilen İşletim Sistemi Kaynakları
ms.date: 03/30/2017
ms.assetid: cdd9a331-53fe-4e0d-bdfe-782264aec5c9
ms.openlocfilehash: 717ab2074c0dcf840919c2bd8afa2641e106ac11
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99779224"
---
# <a name="operating-system-resources-required-by-wcf"></a><span data-ttu-id="26268-103">WCF Tarafından Gerektirilen İşletim Sistemi Kaynakları</span><span class="sxs-lookup"><span data-stu-id="26268-103">Operating System Resources Required by WCF</span></span>

<span data-ttu-id="26268-104">Windows Communication Foundation (WCF), işletim sistemi tarafından çalışması için sunulan çeşitli kaynaklara bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="26268-104">Windows Communication Foundation (WCF) depends on several resources that are provided by the operating system to function.</span></span> <span data-ttu-id="26268-105">Aşağıdaki tabloda bu kaynaklar listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="26268-105">The following table lists those resources:</span></span>

|<span data-ttu-id="26268-106">Kaynak</span><span class="sxs-lookup"><span data-stu-id="26268-106">Resource</span></span>|<span data-ttu-id="26268-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="26268-107">Description</span></span>|
|--------------|-----------------|
|<span data-ttu-id="26268-108">Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC)</span><span class="sxs-lookup"><span data-stu-id="26268-108">Microsoft Distributed Transaction Coordinator (MSDTC)</span></span>|<span data-ttu-id="26268-109">OleTx işlemlerini desteklemek için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="26268-109">Required to support OleTx transactions.</span></span>|
|<span data-ttu-id="26268-110">Internet Information Services (IIS)</span><span class="sxs-lookup"><span data-stu-id="26268-110">Internet Information Services (IIS)</span></span>|<span data-ttu-id="26268-111">Uygulamanızı barındırmak için IIS kullanmak istiyorsanız gereklidir.</span><span class="sxs-lookup"><span data-stu-id="26268-111">Required if you want to use IIS to host your application.</span></span>|
|<span data-ttu-id="26268-112">Windows Işlem etkinleştirme hizmeti (WAS)</span><span class="sxs-lookup"><span data-stu-id="26268-112">Windows Process Activation Service (WAS)</span></span>|<span data-ttu-id="26268-113">Uygulamanızı barındırmak için kullanmak istiyorsanız gereklidir.</span><span class="sxs-lookup"><span data-stu-id="26268-113">Required if you want to use WAS to host your application.</span></span>|

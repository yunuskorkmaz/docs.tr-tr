---
title: WCF Tarafından Gerektirilen İşletim Sistemi Kaynakları
ms.date: 03/30/2017
ms.assetid: cdd9a331-53fe-4e0d-bdfe-782264aec5c9
ms.openlocfilehash: c2c26d769424a8d0655591cb10b4b13df8a15884
ms.sourcegitcommit: 9b2ef64c4fc10a4a10f28a223d60d17d7d249ee8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/26/2019
ms.locfileid: "72961142"
---
# <a name="operating-system-resources-required-by-wcf"></a><span data-ttu-id="b8a8c-102">WCF Tarafından Gerektirilen İşletim Sistemi Kaynakları</span><span class="sxs-lookup"><span data-stu-id="b8a8c-102">Operating System Resources Required by WCF</span></span>

<span data-ttu-id="b8a8c-103">Windows Communication Foundation (WCF), işletim sistemi tarafından çalışması için sunulan çeşitli kaynaklara bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="b8a8c-103">Windows Communication Foundation (WCF) depends on several resources that are provided by the operating system to function.</span></span> <span data-ttu-id="b8a8c-104">Aşağıdaki tabloda bu kaynaklar listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="b8a8c-104">The following table lists those resources:</span></span>

|<span data-ttu-id="b8a8c-105">Kaynak</span><span class="sxs-lookup"><span data-stu-id="b8a8c-105">Resource</span></span>|<span data-ttu-id="b8a8c-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b8a8c-106">Description</span></span>|
|--------------|-----------------|
|<span data-ttu-id="b8a8c-107">Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC)</span><span class="sxs-lookup"><span data-stu-id="b8a8c-107">Microsoft Distributed Transaction Coordinator (MSDTC)</span></span>|<span data-ttu-id="b8a8c-108">OleTx işlemlerini desteklemek için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b8a8c-108">Required to support OleTx transactions.</span></span>|
|<span data-ttu-id="b8a8c-109">Internet Information Services (IIS)</span><span class="sxs-lookup"><span data-stu-id="b8a8c-109">Internet Information Services (IIS)</span></span>|<span data-ttu-id="b8a8c-110">Uygulamanızı barındırmak için IIS kullanmak istiyorsanız gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b8a8c-110">Required if you want to use IIS to host your application.</span></span>|
|<span data-ttu-id="b8a8c-111">Windows Işlem etkinleştirme hizmeti (WAS)</span><span class="sxs-lookup"><span data-stu-id="b8a8c-111">Windows Process Activation Service (WAS)</span></span>|<span data-ttu-id="b8a8c-112">Uygulamanızı barındırmak için kullanmak istiyorsanız gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b8a8c-112">Required if you want to use WAS to host your application.</span></span>|

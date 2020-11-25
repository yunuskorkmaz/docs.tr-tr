---
title: 'NETSDK1073: FrameworkReference tanınmadı'
description: FrameworkReference 'ın bulunamadığı sorunu çözme.
author: marcpopMSFT
ms.topic: error-reference
ms.date: 10/9/2020
f1_keywords:
- NETSDK1073
ms.openlocfilehash: 2b2dbf2a0d3e13dca4fe634529b7951f2333ce28
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713034"
---
# <a name="netsdk1073-the-frameworkreference-was-not-recognized"></a><span data-ttu-id="d602f-103">NETSDK1073: FrameworkReference tanınmadı</span><span class="sxs-lookup"><span data-stu-id="d602f-103">NETSDK1073: The FrameworkReference was not recognized</span></span>

<span data-ttu-id="d602f-104">**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 2.1.100 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="d602f-104">**This article applies to:** ✔️ .NET Core 2.1.100 SDK and later versions</span></span>

<span data-ttu-id="d602f-105">Bu hata genellikle, SDK 'nın bulamadığı belirli bir FrameworkReference sürümü olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="d602f-105">This error typically means there is a version of a particular FrameworkReference that the SDK cannot find.</span></span> <span data-ttu-id="d602f-106">*Obj* ve *bin* klasörlerinizi silmeyi ve `dotnet restore` en son hedefleme paketlerini yeniden indirmek için çalıştırmayı deneyin.</span><span class="sxs-lookup"><span data-stu-id="d602f-106">Try deleting your *obj* and *bin* folders and running `dotnet restore` to redownload the latest targeting packs.</span></span>

<span data-ttu-id="d602f-107">Alternatif olarak, yüklemenize bir sorun olabilir, bu nedenle .NET ve Visual Studio 'nun en son sürümlerinde olduğunuzdan emin olun</span><span class="sxs-lookup"><span data-stu-id="d602f-107">Alternatively, there could be an issue with your install, so ensure you're on the latest versions of .NET and Visual Studio</span></span>

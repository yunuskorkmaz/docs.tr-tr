---
title: 'NETSDK1073: FrameworkReference tanınmadı'
description: FrameworkReference 'ın bulunamadığı sorunu çözme.
author: marcpopMSFT
ms.topic: error-reference
ms.date: 10/9/2020
f1_keywords:
- NETSDK1073
ms.openlocfilehash: 59b5f63dcfe0115feabc2d87d24a09c6a650cc62
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2020
ms.locfileid: "91957163"
---
# <a name="netsdk1073-the-frameworkreference-was-not-recognized"></a><span data-ttu-id="8d658-103">NETSDK1073: FrameworkReference tanınmadı</span><span class="sxs-lookup"><span data-stu-id="8d658-103">NETSDK1073: The FrameworkReference was not recognized</span></span>

<span data-ttu-id="8d658-104">**Bu makale şu şekilde geçerlidir:** ✔️ .NET 2.1.100 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="8d658-104">**This article applies to:** ✔️ .NET 2.1.100 SDK and later versions</span></span>

<span data-ttu-id="8d658-105">Bu hata genellikle, SDK 'nın bulamadığı belirli bir FrameworkReference sürümü olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="8d658-105">This error typically means there is a version of a particular FrameworkReference that the SDK cannot find.</span></span> <span data-ttu-id="8d658-106">*Obj* ve *bin* klasörlerinizi silmeyi ve `dotnet restore` en son hedefleme paketlerini yeniden indirmek için çalıştırmayı deneyin.</span><span class="sxs-lookup"><span data-stu-id="8d658-106">Try deleting your *obj* and *bin* folders and running `dotnet restore` to redownload the latest targeting packs.</span></span>

<span data-ttu-id="8d658-107">Alternatif olarak, yüklemenize bir sorun olabilir, bu nedenle .NET ve Visual Studio 'nun en son sürümlerinde olduğunuzdan emin olun</span><span class="sxs-lookup"><span data-stu-id="8d658-107">Alternatively, there could be an issue with your install, so ensure you're on the latest versions of .NET and Visual Studio</span></span>

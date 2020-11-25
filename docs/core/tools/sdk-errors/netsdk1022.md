---
title: 'NETSDK1022: yinelenen öğeler dahil edildi.'
description: Varsayılan eklemeleri temel alarak yinelenen öğe iletisini çözümleme.
author: marcpopMSFT
ms.topic: error-reference
ms.date: 10/9/2020
f1_keywords:
- NETSDK1022
ms.openlocfilehash: c2bdbbb5503e5e4f6e6826f95f5a2cb08c908ceb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717882"
---
# <a name="netsdk1022-duplicate-items-were-included"></a><span data-ttu-id="d7aad-103">NETSDK1022: yinelenen öğeler dahil edildi.</span><span class="sxs-lookup"><span data-stu-id="d7aad-103">NETSDK1022: Duplicate items were included.</span></span>

<span data-ttu-id="d7aad-104">**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 2.1.100 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="d7aad-104">**This article applies to:** ✔️ .NET Core 2.1.100 SDK and later versions</span></span>

<span data-ttu-id="d7aad-105">Visual Studio 2017/MSBuild sürüm 15,3 ' den başlayarak, .NET SDK varsayılan olarak proje dizinindeki öğeleri otomatik olarak ekler.</span><span class="sxs-lookup"><span data-stu-id="d7aad-105">Starting in Visual Studio 2017 / MSBuild version 15.3, the .NET SDK automatically includes items from the project directory by default.</span></span>  <span data-ttu-id="d7aad-106">Bu `Compile` , ve `Content` hedeflerini içerir.</span><span class="sxs-lookup"><span data-stu-id="d7aad-106">This includes `Compile` and `Content` targets.</span></span>  <span data-ttu-id="d7aad-107">Bu, proje dosyanızı büyük ölçüde temizler ve sahip olduğunuz karmaşıklığı azaltır.</span><span class="sxs-lookup"><span data-stu-id="d7aad-107">This should greatly clean up your project file and reduce the complexity you have there.</span></span>

<span data-ttu-id="d7aad-108">Doğru özelliği yanlış olarak ayarlayarak önceki davranışa döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d7aad-108">You can revert to the earlier behavior by setting the correct property to false.</span></span>

<span data-ttu-id="d7aad-109">Öğeler için örnek `Compile` :</span><span class="sxs-lookup"><span data-stu-id="d7aad-109">Example for `Compile` items:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

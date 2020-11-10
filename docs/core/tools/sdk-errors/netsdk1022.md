---
title: 'NETSDK1022: yinelenen öğeler dahil edildi.'
description: Varsayılan eklemeleri temel alarak yinelenen öğe iletisini çözümleme.
author: marcpopMSFT
ms.topic: error-reference
ms.date: 10/9/2020
f1_keywords:
- NETSDK1022
ms.openlocfilehash: 46c3d7d451e7c9e5b456b6e4e45054c3a4844386
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94445805"
---
# <a name="netsdk1022-duplicate-items-were-included"></a><span data-ttu-id="650ed-103">NETSDK1022: yinelenen öğeler dahil edildi.</span><span class="sxs-lookup"><span data-stu-id="650ed-103">NETSDK1022: Duplicate items were included.</span></span>

<span data-ttu-id="650ed-104">**Bu makale şu şekilde geçerlidir:** ✔️ .NET 2.1.100 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="650ed-104">**This article applies to:** ✔️ .NET 2.1.100 SDK and later versions</span></span>

<span data-ttu-id="650ed-105">Visual Studio 15,3 ' den başlayarak, .NET SDK varsayılan olarak proje dizinindeki öğeleri otomatik olarak içerir.</span><span class="sxs-lookup"><span data-stu-id="650ed-105">Starting in Visual Studio 15.3, the .NET SDK automatically includes items from the project directory by default.</span></span>  <span data-ttu-id="650ed-106">Bu `Compile` , ve `Content` hedeflerini içerir.</span><span class="sxs-lookup"><span data-stu-id="650ed-106">This includes `Compile` and `Content` targets.</span></span>  <span data-ttu-id="650ed-107">Bu, proje dosyanızı büyük ölçüde temizler ve sahip olduğunuz karmaşıklığı azaltır.</span><span class="sxs-lookup"><span data-stu-id="650ed-107">This should greatly clean up your project file and reduce the complexity you have there.</span></span>

<span data-ttu-id="650ed-108">Doğru özelliği yanlış olarak ayarlayarak önceki davranışa döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="650ed-108">You can revert to the earlier behavior by setting the correct property to false.</span></span>

<span data-ttu-id="650ed-109">Öğeler için örnek `Compile` :</span><span class="sxs-lookup"><span data-stu-id="650ed-109">Example for `Compile` items:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

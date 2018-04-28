---
title: Global.JSON başvurusu
description: .NET Core Araçları sürüm ayarını verir global.json dosyası için şema bakın.
author: blackdwarf
ms.author: mairaw
ms.date: 04/05/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: ac53a899e76c99527f2670d0a6bed3f8cc6ce31f
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="globaljson-reference"></a><span data-ttu-id="261fb-103">Global.JSON başvurusu</span><span class="sxs-lookup"><span data-stu-id="261fb-103">global.json reference</span></span>

<span data-ttu-id="261fb-104">*Global.json* dosyasının aracılığıyla kullanılan .NET Core Araçları sürüm seçimine olanak tanır `sdk` özelliği.</span><span class="sxs-lookup"><span data-stu-id="261fb-104">The *global.json* file allows selection of the .NET Core tools version being used through the `sdk` property.</span></span>

<span data-ttu-id="261fb-105">.NET core CLI araçlarını (hangi mutlaka proje dizini ile aynı değil) geçerli çalışma dizini veya onun üst dizinlerden biri bu dosyada arayın.</span><span class="sxs-lookup"><span data-stu-id="261fb-105">.NET Core CLI tools look for this file in the current working directory (which isn't necessarily the same as the project directory) or one of its parent directories.</span></span>

## <a name="sdk"></a><span data-ttu-id="261fb-106">SDK'sı</span><span class="sxs-lookup"><span data-stu-id="261fb-106">sdk</span></span>
<span data-ttu-id="261fb-107">Tür: nesnesi</span><span class="sxs-lookup"><span data-stu-id="261fb-107">Type: Object</span></span>

<span data-ttu-id="261fb-108">SDK hakkında bilgileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="261fb-108">Specifies information about the SDK.</span></span>

### <a name="version"></a><span data-ttu-id="261fb-109">sürüm</span><span class="sxs-lookup"><span data-stu-id="261fb-109">version</span></span>
<span data-ttu-id="261fb-110">Türü: dize</span><span class="sxs-lookup"><span data-stu-id="261fb-110">Type: String</span></span>

<span data-ttu-id="261fb-111">Kullanmak için SDK sürümü.</span><span class="sxs-lookup"><span data-stu-id="261fb-111">The version of the SDK to use.</span></span>

<span data-ttu-id="261fb-112">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="261fb-112">For example:</span></span>

```json
{
  "sdk": {
    "version": "1.0.0-preview2-003121"
  }
}
```

---
title: "Global.JSON başvurusu"
description: ".NET Core Araçları sürüm ayarını verir global.json dosyası için şema bakın."
keywords: .NET, .NET core
author: blackdwarf
ms.author: mairaw
ms.date: 04/05/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 96102f96-d403-4385-8ef6-5d80e406eb0c
ms.workload: dotnetcore
ms.openlocfilehash: c7e64995ed00a6b2df1b7e1dfa43c6bea5cf4535
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="globaljson-reference"></a><span data-ttu-id="6849a-104">Global.JSON başvurusu</span><span class="sxs-lookup"><span data-stu-id="6849a-104">global.json reference</span></span>

<span data-ttu-id="6849a-105">*Global.json* dosyasının aracılığıyla kullanılan .NET Core Araçları sürüm seçimine olanak tanır `sdk` özelliği.</span><span class="sxs-lookup"><span data-stu-id="6849a-105">The *global.json* file allows selection of the .NET Core tools version being used through the `sdk` property.</span></span>

<span data-ttu-id="6849a-106">.NET core CLI araçlarını (hangi mutlaka proje dizini ile aynı değil) geçerli çalışma dizini veya onun üst dizinlerden biri bu dosyada arayın.</span><span class="sxs-lookup"><span data-stu-id="6849a-106">.NET Core CLI tools look for this file in the current working directory (which isn't necessarily the same as the project directory) or one of its parent directories.</span></span>

## <a name="sdk"></a><span data-ttu-id="6849a-107">SDK'sı</span><span class="sxs-lookup"><span data-stu-id="6849a-107">sdk</span></span>
<span data-ttu-id="6849a-108">Tür: nesnesi</span><span class="sxs-lookup"><span data-stu-id="6849a-108">Type: Object</span></span>

<span data-ttu-id="6849a-109">SDK hakkında bilgileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="6849a-109">Specifies information about the SDK.</span></span>

### <a name="version"></a><span data-ttu-id="6849a-110">sürüm</span><span class="sxs-lookup"><span data-stu-id="6849a-110">version</span></span>
<span data-ttu-id="6849a-111">Türü: dize</span><span class="sxs-lookup"><span data-stu-id="6849a-111">Type: String</span></span>

<span data-ttu-id="6849a-112">Kullanmak için SDK sürümü.</span><span class="sxs-lookup"><span data-stu-id="6849a-112">The version of the SDK to use.</span></span>

<span data-ttu-id="6849a-113">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="6849a-113">For example:</span></span>

```json
{
  "sdk": {
    "version": "1.0.0-preview2-003121"
  }
}
```

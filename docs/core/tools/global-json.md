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
ms.openlocfilehash: ffa97164736fc7f3edc450682d23bdf499b6eb34
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="globaljson-reference"></a><span data-ttu-id="3f8af-104">Global.JSON başvurusu</span><span class="sxs-lookup"><span data-stu-id="3f8af-104">global.json reference</span></span>

<span data-ttu-id="3f8af-105">*Global.json* dosyasının aracılığıyla kullanılan .NET Core Araçları sürüm seçimine olanak tanır `sdk` özelliği.</span><span class="sxs-lookup"><span data-stu-id="3f8af-105">The *global.json* file allows selection of the .NET Core tools version being used through the `sdk` property.</span></span>

<span data-ttu-id="3f8af-106">.NET core CLI araçlarını (hangi mutlaka proje dizini ile aynı değil) geçerli çalışma dizini veya onun üst dizinlerden biri bu dosyada arayın.</span><span class="sxs-lookup"><span data-stu-id="3f8af-106">.NET Core CLI tools look for this file in the current working directory (which isn't necessarily the same as the project directory) or one of its parent directories.</span></span>

## <a name="sdk"></a><span data-ttu-id="3f8af-107">SDK'sı</span><span class="sxs-lookup"><span data-stu-id="3f8af-107">sdk</span></span>
<span data-ttu-id="3f8af-108">Tür: nesnesi</span><span class="sxs-lookup"><span data-stu-id="3f8af-108">Type: Object</span></span>

<span data-ttu-id="3f8af-109">SDK hakkında bilgileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="3f8af-109">Specifies information about the SDK.</span></span>

### <a name="version"></a><span data-ttu-id="3f8af-110">sürüm</span><span class="sxs-lookup"><span data-stu-id="3f8af-110">version</span></span>
<span data-ttu-id="3f8af-111">Türü: dize</span><span class="sxs-lookup"><span data-stu-id="3f8af-111">Type: String</span></span>

<span data-ttu-id="3f8af-112">Kullanmak için SDK sürümü.</span><span class="sxs-lookup"><span data-stu-id="3f8af-112">The version of the SDK to use.</span></span>

<span data-ttu-id="3f8af-113">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="3f8af-113">For example:</span></span>

```json
{
  "sdk": {
    "version": "1.0.0-preview2-003121"
  }
}
```

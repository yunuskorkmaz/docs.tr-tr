---
title: Global.JSON başvurusu
description: .NET Core Araçları sürüm ayarını verir global.json dosyası için şema bakın.
author: blackdwarf
ms.author: mairaw
ms.date: 04/05/2017
ms.openlocfilehash: 7479774c7b9cdda233cf32d791c16e7fc6d733a8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33209976"
---
# <a name="globaljson-reference"></a><span data-ttu-id="8b016-103">Global.JSON başvurusu</span><span class="sxs-lookup"><span data-stu-id="8b016-103">global.json reference</span></span>

<span data-ttu-id="8b016-104">*Global.json* dosyasının aracılığıyla kullanılan .NET Core Araçları sürüm seçimine olanak tanır `sdk` özelliği.</span><span class="sxs-lookup"><span data-stu-id="8b016-104">The *global.json* file allows selection of the .NET Core tools version being used through the `sdk` property.</span></span>

<span data-ttu-id="8b016-105">.NET core CLI araçlarını (hangi mutlaka proje dizini ile aynı değil) geçerli çalışma dizini veya onun üst dizinlerden biri bu dosyada arayın.</span><span class="sxs-lookup"><span data-stu-id="8b016-105">.NET Core CLI tools look for this file in the current working directory (which isn't necessarily the same as the project directory) or one of its parent directories.</span></span>

## <a name="sdk"></a><span data-ttu-id="8b016-106">SDK'sı</span><span class="sxs-lookup"><span data-stu-id="8b016-106">sdk</span></span>
<span data-ttu-id="8b016-107">Tür: nesnesi</span><span class="sxs-lookup"><span data-stu-id="8b016-107">Type: Object</span></span>

<span data-ttu-id="8b016-108">SDK hakkında bilgileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="8b016-108">Specifies information about the SDK.</span></span>

### <a name="version"></a><span data-ttu-id="8b016-109">sürüm</span><span class="sxs-lookup"><span data-stu-id="8b016-109">version</span></span>
<span data-ttu-id="8b016-110">Türü: dize</span><span class="sxs-lookup"><span data-stu-id="8b016-110">Type: String</span></span>

<span data-ttu-id="8b016-111">Kullanmak için SDK sürümü.</span><span class="sxs-lookup"><span data-stu-id="8b016-111">The version of the SDK to use.</span></span>

<span data-ttu-id="8b016-112">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="8b016-112">For example:</span></span>

```json
{
  "sdk": {
    "version": "1.0.0-preview2-003121"
  }
}
```

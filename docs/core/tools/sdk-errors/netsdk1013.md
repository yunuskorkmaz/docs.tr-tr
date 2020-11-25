---
title: 'NETSDK1013: TargetFramework değeri tanınmadı.'
description: Geçerli bir TargetFramework değeri belirleme ve ayarlama
author: marcpop
ms.topic: error-reference
ms.date: 10/9/2020
f1_keywords:
- NETSDK1013
ms.openlocfilehash: 915ac22ad822d17c082498b469acbfb3f1a93efc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717883"
---
# <a name="netsdk1013-the-targetframework-value-was-not-recognized"></a><span data-ttu-id="be040-103">NETSDK1013: TargetFramework değeri tanınmadı</span><span class="sxs-lookup"><span data-stu-id="be040-103">NETSDK1013: The TargetFramework value was not recognized</span></span>

<span data-ttu-id="be040-104">**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 3.1.100 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="be040-104">**This article applies to:** ✔️ .NET Core 3.1.100 SDK and later versions</span></span>

<span data-ttu-id="be040-105">SDK, proje dosyasında belirtilen değerleri `<TargetFramework>` `<TargetFrameworks>` bir veya iyi bilinen bir değer olarak ayrıştırmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="be040-105">The SDK tries to parse the values provided in the project file for `<TargetFramework>` or `<TargetFrameworks>` into a well known value.</span></span>  <span data-ttu-id="be040-106">Değer tanınmazsa, `TargetFrameworkIdentifier` veya `TargetFrameworkVersion` değeri boş bir dize veya olarak ayarlanabilir `Unsupported` .</span><span class="sxs-lookup"><span data-stu-id="be040-106">If the value is not recognized, the `TargetFrameworkIdentifier` or `TargetFrameworkVersion` value may be set to an empty string or `Unsupported`.</span></span>

<span data-ttu-id="be040-107">Bu sorunu çözmek için, `TargetFramework` [desteklenen çerçeveler](../../../standard/frameworks.md)listesinden değer yazımını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="be040-107">To resolve this, check the spelling of your `TargetFramework` value from the list of [supported frameworks](../../../standard/frameworks.md).</span></span>
<span data-ttu-id="be040-108">Ayrıca, `TargetFrameworkIdentifier` ve `TargetFrameworkVersion` özelliklerini doğrudan proje dosyanızda de ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="be040-108">You can also set the `TargetFrameworkIdentifier` and `TargetFrameworkVersion` properties directly in your project file.</span></span>

```xml
<PropertyGroup Condition="'$(TargetFrameworkIdentifier)' == ''">
  <TargetFrameworkIdentifier>.NETCOREAPP</TargetFrameworkIdentifier>
  <TargetFrameworkVersion>3.1</TargetFrameworkVersion>
</PropertyGroup>
```

---
title: 'NETSDK1013: TargetFramework değeri tanınmadı.'
description: Geçerli bir TargetFramework değeri belirleme ve ayarlama
author: marcpop
ms.topic: error-reference
ms.date: 10/9/2020
f1_keywords:
- NETSDK1013
ms.openlocfilehash: bcaed878b663f8bc957e8469ffd78caa9babf710
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94445774"
---
# <a name="netsdk1013-the-targetframework-value-was-not-recognized"></a>NETSDK1013: TargetFramework değeri tanınmadı

**Bu makale şu şekilde geçerlidir:** ✔️ .NET 3.1.100 SDK ve sonraki sürümleri

SDK, proje dosyasında belirtilen değerleri `<TargetFramework>` `<TargetFrameworks>` bir veya iyi bilinen bir değer olarak ayrıştırmaya çalışır.  Değer tanınmazsa, `TargetFrameworkIdentifier` veya `TargetFrameworkVersion` değeri boş bir dize veya olarak ayarlanabilir `Unsupported` .

Bu sorunu çözmek için, `TargetFramework` [desteklenen çerçeveler](../../../standard/frameworks.md)listesinden değer yazımını denetleyin.
Ayrıca, `TargetFrameworkIdentifier` ve `TargetFrameworkVersion` özelliklerini doğrudan proje dosyanızda de ayarlayabilirsiniz.

```xml
<PropertyGroup Condition="'$(TargetFrameworkIdentifier)' == ''">
  <TargetFrameworkIdentifier>.NETCOREAPP</TargetFrameworkIdentifier>
  <TargetFrameworkVersion>3.1</TargetFrameworkVersion>
</PropertyGroup>
```

---
ms.openlocfilehash: 47e8e15a64236d8ade2febb1add81fa4e5c030d9
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76116164"
---

Paket Yöneticisi akışlarına eklenen paketlerin adı, uyumlu bir biçimde: `{product}-{type}-{version}`.

- **ürün**\
Yüklenecek .NET Ürün türü. Geçerli seçenekler şunlardır:

  - dotnet
  - aspnetcore

- **tür**\
SDK 'Yı veya çalışma zamanını seçer. Geçerli seçenekler şunlardır:

  - sdk
  - çalışma zamanı

- **sürüm**\
Yüklenecek SDK veya çalışma zamanının sürümü. Bu makale her zaman desteklenen en son sürüme yönelik yönergelere sahip olur. Geçerli seçenekler, şu gibi yayınlanmış bir sürümdür:

  - 3.0
  - 2.2
  - 2.1

### <a name="examples"></a>Örnekler

- .NET Core 2,2 SDK 'sını yükler: `dotnet-sdk-2.2`
- ASP.NET Core 3,1 çalışma zamanını yükler: `aspnetcore-runtime-3.1`
- .NET Core 2,1 çalışma zamanını yükler: `dotnet-runtime-2.1`

### <a name="troubleshoot"></a>Sorunları Gider

Paket birleşimi işe yaramazsa, kullanılabilir değildir. Örneğin, ASP.NET Core SDK yoktur, SDK bileşenleri .NET Core SDK eklenir. `aspnetcore-sdk-2.2` değeri hatalı ve `dotnet-sdk-2.2` olmalıdır

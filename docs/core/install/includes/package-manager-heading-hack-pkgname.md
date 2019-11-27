---
ms.openlocfilehash: 7a55641b3673dc4d8d9b328f0de99b7247ca51d4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450886"
---

Paket Yöneticisi akışlarına eklenen paketlerin adı, uyumlu bir biçimde: `{product}-{type}-{version}`.

- **ürün**\
Yüklenecek .NET Ürün türü. Geçerli seçenekler şunlardır:

  - DotNet
  - aspnetcore

- **tür**\
SDK 'Yı veya çalışma zamanını seçer. Geçerli seçenekler şunlardır:

  - 'sının
  - çalışma zamanı

- **sürüm**\
Yüklenecek SDK veya çalışma zamanının sürümü. Bu makale her zaman desteklenen en son sürüme yönelik yönergelere sahip olur. Geçerli seçenekler, şu gibi yayınlanmış bir sürümdür:

  - 3,0
  - 2.2
  - 2.1

### <a name="examples"></a>Örnekler

- .NET Core 2,2 SDK 'sını yükler: `dotnet-sdk-2.2`
- ASP.NET Core 3,0 çalışma zamanını yükler: `aspnetcore-runtime-3.0`
- .NET Core 2,1 çalışma zamanını yükler: `dotnet-runtime-2.1`

### <a name="troubleshoot"></a>Sorunları Gider

Paket birleşimi işe yaramazsa, kullanılabilir değildir. Örneğin, ASP.NET Core SDK yoktur, SDK bileşenleri .NET Core SDK eklenir. `aspnetcore-sdk-2.2` değeri hatalı ve `dotnet-sdk-2.2` olmalıdır

---
ms.openlocfilehash: ef3e4f9f8145677732b9d2e66d416be277697f55
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920662"
---

Paket Yöneticisi akışlarına eklenen paketlerin adı, uyumlu bir biçimde: `{product}-{type}-{version}`.

- **ürün**\
Yüklenecek .NET Ürün türü. Geçerli seçenekler şunlardır:

  - dotnet
  - aspnetcore

- **tür**\
SDK 'Yı veya çalışma zamanını seçer. Geçerli seçenekler şunlardır:

  - 'sının
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

### <a name="package-missing"></a>Paket eksik

Paket sürümü birleşimi işe yaramazsa, kullanılabilir değildir. Örneğin, ASP.NET Core SDK yoktur, SDK bileşenleri .NET Core SDK eklenir. `aspnetcore-sdk-2.2` değeri hatalı ve `dotnet-sdk-2.2`olmalıdır.

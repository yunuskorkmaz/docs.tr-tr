---
ms.openlocfilehash: ab1006f706439bcf5129854da3d14538e5b690a2
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506884"
---

Paket Yöneticisi akışlarına eklenen paketler, uyumlu olmayan biçimde adlandırılır: `{product}-{type}-{version}` .

- **ürünüyle**\
Yüklenecek .NET Ürün türü. Geçerli seçenekler şunlardır:

  - dotnet
  - aspnetcore

- **türüyle**\
SDK 'Yı veya çalışma zamanını seçer. Geçerli seçenekler şunlardır:

  - sdk
  - çalışma zamanı

- **Sürüm**\
Yüklenecek SDK veya çalışma zamanının sürümü. Bu makale her zaman desteklenen en son sürüme yönelik yönergelere sahip olur. Geçerli seçenekler, şu gibi yayınlanmış bir sürümdür:

  - 5.0
  - 3,1
  - 3,0
  - 2.1

  İndirmeyi denediğiniz SDK/çalışma zamanı Linux dağıtım için kullanılamıyor olabilir. Desteklenen dağıtımların listesi için bkz. [.NET Core Dependencies ve Requirements](../linux.md).

### <a name="examples"></a>Örnekler

- ASP.NET Core 5,0 çalışma zamanını yükler: `aspnetcore-runtime-5.0`
- .NET Core 2,1 çalışma zamanını yükler: `dotnet-runtime-2.1`
- .NET 5,0 SDK 'sını yükler: `dotnet-sdk-5.0`
- .NET Core 3,1 SDK 'sını yükler: `dotnet-sdk-3.1`

### <a name="package-missing"></a>Paket eksik

Paket sürümü birleşimi işe yaramazsa, kullanılabilir değildir. Örneğin, ASP.NET Core SDK yoktur, SDK bileşenleri .NET SDK 'ya dahildir. Değer `aspnetcore-sdk-2.2` yanlış ve olmalıdır `dotnet-sdk-2.2` . .NET Core tarafından desteklenen Linux dağıtımların listesi için bkz. [.net bağımlılıkları ve gereksinimleri](../linux.md).

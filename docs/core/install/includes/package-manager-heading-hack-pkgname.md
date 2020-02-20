---
ms.openlocfilehash: 51b3c1b3e3d61b23a0511ca807afef0269ac9ee4
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77466000"
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

  - 3.1
  - 3.0
  - 2.1

  İndirmeyi denediğiniz SDK/çalışma zamanı Linux dağıtım için kullanılamıyor olabilir. Desteklenen dağıtımların listesi için bkz. [.NET Core Dependencies ve Requirements](../dependencies.md?pivots=os-linux).

### <a name="examples"></a>Örnekler

- ASP.NET Core 3,1 çalışma zamanını yükler: `aspnetcore-runtime-3.1`
- .NET Core 2,1 çalışma zamanını yükler: `dotnet-runtime-2.1`
- .NET Core 3,0 SDK 'sını yükler: `dotnet-sdk-3.0`

### <a name="package-missing"></a>Paket eksik

Paket sürümü birleşimi işe yaramazsa, kullanılabilir değildir. Örneğin, ASP.NET Core SDK yoktur, SDK bileşenleri .NET Core SDK eklenir. `aspnetcore-sdk-2.2` değeri hatalı ve `dotnet-sdk-2.2`olmalıdır. .NET Core tarafından desteklenen Linux dağıtımların listesi için bkz. [.NET Core Dependencies ve Requirements](../dependencies.md?pivots=os-linux).

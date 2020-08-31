---
ms.openlocfilehash: 7723892a33bf7dd8e475b2f696db5d9ab287e182
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602994"
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

  - 3,1
  - 3.0
  - 2.1

  İndirmeyi denediğiniz SDK/çalışma zamanı Linux dağıtım için kullanılamıyor olabilir. Desteklenen dağıtımların listesi için bkz. [.NET Core Dependencies ve Requirements](../linux.md).

### <a name="examples"></a>Örnekler

- ASP.NET Core 3,1 çalışma zamanını yükler: `aspnetcore-runtime-3.1`
- .NET Core 2,1 çalışma zamanını yükler: `dotnet-runtime-2.1`
- .NET Core 3,1 SDK 'sını yükler: `dotnet-sdk-3.1`

### <a name="package-missing"></a>Paket eksik

Paket sürümü birleşimi işe yaramazsa, kullanılabilir değildir. Örneğin, ASP.NET Core SDK yoktur, SDK bileşenleri .NET Core SDK eklenir. Değer `aspnetcore-sdk-2.2` yanlış ve olmalıdır `dotnet-sdk-2.2` . .NET Core tarafından desteklenen Linux dağıtımların listesi için bkz. [.NET Core Dependencies ve Requirements](../linux.md).

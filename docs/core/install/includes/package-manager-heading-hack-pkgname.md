---
ms.openlocfilehash: 4340ed7444681b4601dea50c93926b0ee0c07eec
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134100"
---

Paket yöneticisi beslemelerine eklenen paketler hacklenebilir bir biçimde adlandırılır: `{product}-{type}-{version}`.

- **Ürün**\
Yüklenmesi gereken .NET ürün türü. Geçerli seçenekler şunlardır:

  - dotnet
  - aspnetcore

- **Türü**\
SDK'yı veya çalışma saatini seçer. Geçerli seçenekler şunlardır:

  - sdk
  - çalışma zamanı

- **Sürüm**\
SDK sürümü veya yüklemek için çalışma zamanı. Bu makalede, her zaman en son desteklenen sürümü için talimatlar verecektir. Geçerli seçenekler, şu lar gibi serbest bırakılmış sürümlerdir:

  - 3.1
  - 3,0
  - 2.1

  İndirmeye çalıştığınız SDK/runtime'ın Linux dağıtımınız için kullanılamaması mümkündür. Desteklenen dağıtımların listesi için [bkz.](../dependencies.md?pivots=os-linux)

### <a name="examples"></a>Örnekler

- Core 3.1 çalışma süresini ASP.NET yükleyin:`aspnetcore-runtime-3.1`
- .NET Core 2.1 çalışma süresini yükleyin:`dotnet-runtime-2.1`
- .NET Core 3.1 SDK'yı yükleyin:`dotnet-sdk-3.1`

### <a name="package-missing"></a>Paket eksik

Paket sürüm birleşimi çalışmıyorsa, kullanılamıyor. Örneğin, ASP.NET Core SDK yoktur, SDK bileşenleri .NET Core SDK ile birlikte verilir. Değer `aspnetcore-sdk-2.2` yanlıştır ve `dotnet-sdk-2.2`. .NET Core tarafından desteklenen Linux dağıtımlarının listesi [için](../dependencies.md?pivots=os-linux)bkz.

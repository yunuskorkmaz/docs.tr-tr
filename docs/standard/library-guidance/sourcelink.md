---
title: SourceLink ve .NET kitaplıkları
description: .NET kitaplıkları için hata ayıklama geliştirmek için SourceLink kullanmaya yönelik en iyi yöntem önerileri.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: fa4af47eaa5dd1510640c2bf0ebb2187b56efae0
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49123879"
---
# <a name="sourcelink"></a>SourceLink

SourceLink NuGet geliştiricilerin .NET derlemeleri, kaynak kodda hata ayıklama sağlayan bir teknolojidir. SourceLink NuGet paketini oluştururken yürütür ve kaynak denetimi meta verilerini derlemeler ve paket içine katıştırır. Paketi indirebilir ve Visual Studio'da etkin SourceLink sahip geliştiriciler, kaynak kodunda adım adım ilerleyebilirsiniz. SourceLink harika bir hata ayıklama deneyimi oluşturmak için kaynak denetimi meta verilerini sağlar.

## <a name="sourcelink-demo"></a>SourceLink Tanıtımı

> [!VIDEO https://www.youtube.com/embed/gyRGhCQPkB4?start=61]

## <a name="using-sourcelink"></a>SourceLink kullanma

SourceLink kullanımıyla ilgili yönergeleri bulunabilir [dotnet/sourceLink](https://github.com/dotnet/sourcelink/blob/master/README.md) GitHub deposu.

Kullanabileceğiniz [NuGet paket Gezgini](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) SourceLink meta verileri pakete başarıyla katıştırılmış olduğunu onaylamak için. Denetleme `Repository` açıklama tanımlayıcısına sahip meta veri varsa ve her hedefin .dll ile .pdb dosyaları bulunur.

![NuGet paket Gezgini'nde SourceLink](./media/sourcelink/nuget-package-explorer-sourcelink.png "SourceLink, NuGet paket Gezgini")

**✔️ DÜŞÜNÜN** SourceLink NuGet paketi ve derlemeler için kaynak denetimi meta verilerini eklemek için kullanma.

**✔️ DÜŞÜNÜN** NuGet paketine PDB dosyaları.

>[!div class="step-by-step"]
[Önceki](./dependencies.md)
[İleri](./publish-nuget-package.md)

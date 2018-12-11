---
title: SourceLink ve .NET kitaplıkları
description: .NET kitaplıkları için hata ayıklama geliştirmek için SourceLink kullanmaya yönelik en iyi yöntem önerileri.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 3bc72e158a5773b656095f9ce58b442469f91e67
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53128939"
---
# <a name="sourcelink"></a>SourceLink

SourceLink NuGet geliştiricilerin .NET derlemeleri, kaynak kodda hata ayıklama sağlayan bir teknolojidir. SourceLink NuGet paketini oluştururken yürütür ve kaynak denetimi meta verilerini derlemeler ve paket içine katıştırır. Paketi indirebilir ve Visual Studio'da etkin SourceLink sahip geliştiriciler, kaynak kodunda adım adım ilerleyebilirsiniz. SourceLink harika bir hata ayıklama deneyimi oluşturmak için kaynak denetimi meta verilerini sağlar.

## <a name="sourcelink-demo"></a>SourceLink Tanıtımı

> [!VIDEO https://www.youtube.com/embed/gyRGhCQPkB4?start=61]

## <a name="using-sourcelink"></a>SourceLink kullanma

SourceLink kullanımıyla ilgili yönergeleri bulunabilir [dotnet/sourceLink](https://github.com/dotnet/sourcelink/blob/master/README.md) GitHub deposu.

Kullanabileceğiniz [NuGet paket Gezgini](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) SourceLink meta verileri pakete başarıyla katıştırılmış olduğunu onaylamak için. Denetleme `Repository` açıklama tanımlayıcısına sahip meta veri varsa ve her hedefin .dll ile .pdb dosyaları bulunur.

![NuGet paket Gezgini'nde SourceLink](./media/sourcelink/nuget-package-explorer-sourcelink.png "SourceLink, NuGet paket Gezgini")

**✔️ DÜŞÜNÜN** SourceLink kaynak denetimi meta verilerini, derlemeleri ve NuGet paketleri eklemek için kullanma.

> [!TIP]
> Türleriniz için hata ayıklayıcı öznitelikleri ekleyerek, geliştirici hata ayıklama deneyimi daha da geliştirebilirsiniz.
> * <xref:System.Diagnostics.DebuggerDisplayAttribute> bir sınıf ya da alan hata ayıklayıcı değişken pencerelerinde nasıl görüntüleneceğini özelleştirebilirsiniz.
> * <xref:System.Diagnostics.DebuggerStepThroughAttribute> Hata ayıklayıcının kodun içine Adımlama yerine kod adım adım yönlendirir.
> * <xref:System.Diagnostics.DebuggerBrowsableAttribute> üye hata ayıklayıcı değişken pencerelerinde görüntülenip görüntülenmediğini denetler.

**✔️ DÜŞÜNÜN** sembol dosyaları dahil olmak üzere (`*.pdb`) NuGet paketi olarak.

> Normalde, sembol dosyalarında yayımlamak istediğiniz bir [sembol paketi](./nuget.md#symbol-packages). Sembol paketleri için genel ana taşınabilir sembol dosyaları şu anda desteklemiyor (`*.pdb`) SDK stili projeleri tarafından oluşturulan ve sembol paketleri kullanışlı değildir.

>[!div class="step-by-step"]
>[Önceki](dependencies.md)
>[İleri](publish-nuget-package.md)
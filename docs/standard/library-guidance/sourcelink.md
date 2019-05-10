---
title: Kaynak bağlantısı ve .NET kitaplıkları
description: .NET kitaplıkları için hata ayıklama geliştirmek için kaynak bağlantısı kullanılarak için en iyi yöntem önerileri.
author: jamesnk
ms.author: mairaw
ms.date: 01/15/2019
ms.openlocfilehash: 9d3e2b0b3aedbab150072bf6eebff4acb5f8a0b7
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211680"
---
# <a name="source-link"></a>Kaynak Bağlantısı

Kaynak bağlantısı kaynak geliştiriciler tarafından nuget'ten .NET bütünleştirilmiş kodda hata ayıklama sağlayan bir teknolojidir. Kaynak bağlantısı NuGet paketini oluştururken yürütür ve kaynak denetimi meta verilerini derlemeler ve paket içine katıştırır. Paketi indirebilir ve Visual Studio'da etkin kaynak bağlantısı olan geliştiriciler, kaynak kodunda adım adım ilerleyebilirsiniz. Kaynak bağlantısı harika bir hata ayıklama deneyimi oluşturmak için kaynak denetimi meta verilerini sağlar.

## <a name="source-link-demo"></a>Kaynak bağlantı Tanıtımı

> [!VIDEO https://www.youtube.com/embed/gyRGhCQPkB4?start=61]

## <a name="using-source-link"></a>Kaynak bağlantısı kullanılarak

Kaynak bağlantısı kullanılarak yönergeler bulunabilir [dotnet/sourcelink](https://github.com/dotnet/sourcelink/blob/master/README.md) GitHub deposu.

Kullanabileceğiniz [NuGet paket Gezgini](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) kaynak bağlantısı meta verileri pakete başarıyla katıştırılmış olduğunu onaylamak için. Denetleme `Repository` açıklama tanımlayıcısına sahip meta veri varsa ve her hedefin .dll ile .pdb dosyaları bulunur.

![NuGet paket Gezgininde bağlantı kaynağı](./media/sourcelink/nuget-package-explorer-sourcelink.png "NuGet paket Gezgininde bağlantı kaynağı")

**✔️ DÜŞÜNÜN** kaynak denetimi meta verilerini, derlemeleri ve NuGet paketleri eklemek için kaynak bağlantısı kullanılarak.

> [!TIP]
> Türleriniz için hata ayıklayıcı öznitelikleri ekleyerek, geliştirici hata ayıklama deneyimi daha da geliştirebilirsiniz.
> * <xref:System.Diagnostics.DebuggerDisplayAttribute> bir sınıf ya da alan hata ayıklayıcı değişken pencerelerinde nasıl görüntüleneceğini özelleştirebilirsiniz.
> * <xref:System.Diagnostics.DebuggerStepThroughAttribute> Hata ayıklayıcının kodun içine Adımlama yerine kod adım adım yönlendirir.
> * <xref:System.Diagnostics.DebuggerBrowsableAttribute> üye hata ayıklayıcı değişken pencerelerinde görüntülenip görüntülenmediğini denetler.

**✔️ DÜŞÜNÜN** sembol dosyaları yayımlama (`*.pdb`).

> Hata ayıklama deneyimi için en iyi kitaplığınızı yayınlamak sembolü dosyalarının yanı sıra kaynak bağlantısı kullanın. Sembol dosyaları ve sembol paketleri hakkında daha fazla bilgi için bkz. [sembol paketleri](./nuget.md#symbol-packages).

>[!div class="step-by-step"]
>[Önceki](dependencies.md)
>[İleri](publish-nuget-package.md)

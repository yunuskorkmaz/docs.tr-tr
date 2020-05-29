---
title: Kaynak bağlantısı ve .NET kitaplıkları
description: .NET kitaplıklarında hata ayıklamayı geliştirmek için kaynak bağlantısını kullanmaya yönelik en iyi yöntem önerileri.
ms.date: 01/15/2019
ms.openlocfilehash: 5dee2a6b1f77daa641351e02c1dd3e0a38f66550
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84201975"
---
# <a name="source-link"></a>Kaynak Bağlantısı

Kaynak bağlantısı, geliştiriciler tarafından NuGet 'den .NET derlemelerinin kaynak kodu hata ayıklamasını sağlayan bir teknolojidir. NuGet paketini oluştururken kaynak bağlantısı yürütülür ve derleme ve paket içindeki kaynak denetimi meta verilerini katıştırır. Visual Studio 'da paketini indirir ve kaynak bağlantısı etkinleştirilmiş geliştiriciler, kaynak kodunu görebilir. Kaynak bağlantısı, harika bir hata ayıklama deneyimi oluşturmak için kaynak denetimi meta verileri sağlar.

## <a name="source-link-demo"></a>Kaynak bağlantısı tanıtımı

<!--markdownlint-disable MD034 -->
> [!VIDEO https://www.youtube.com/embed/gyRGhCQPkB4?start=61]

## <a name="using-source-link"></a>Kaynak bağlantısı kullanma

Kaynak bağlantısı kullanma yönergeleri [DotNet/sourcelink](https://github.com/dotnet/sourcelink/blob/master/README.md) GitHub deposunda bulunabilir.

Kaynak bağlantısı meta verilerinin pakete başarıyla eklenmiş olduğunu doğrulamak için [NuGet Paket Gezgini](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) ' ni kullanabilirsiniz. `Repository`Meta verilerin bir kayıt tanımlayıcısıyla birlikte var olduğunu ve bu. pdb dosyalarının her hedefin. dll ile bulunduğunu denetleyin.

![NuGet Paket Gezgininde kaynak bağlantısı](./media/sourcelink/nuget-package-explorer-sourcelink.png "NuGet Paket Gezgininde kaynak bağlantısı")

✔️ derlemelerinize ve NuGet paketlerine kaynak denetimi meta verileri eklemek için kaynak bağlantısı kullanmayı düşünün.

> [!TIP]
> Türlerinizi hata ayıklayıcı öznitelikleri ekleyerek bir geliştiricinin hata ayıklama deneyimini daha da geliştirebilirsiniz.
>
> * <xref:System.Diagnostics.DebuggerDisplayAttribute>, bir sınıfın veya alanın hata ayıklayıcı değişkeni penceresinde nasıl görüntülendiğini özelleştirebilir.
> * <xref:System.Diagnostics.DebuggerStepThroughAttribute>hata ayıklayıcıya koda Adımlama yerine kodda adım adım ilermesini söyler.
> * <xref:System.Diagnostics.DebuggerBrowsableAttribute>hata ayıklayıcı değişkeni penceresinde bir üyenin görüntülenip görüntülenmediğini denetler.

✔️ sembol dosyalarını yayımlamayı düşünün ( `*.pdb` ).

> En iyi hata ayıklama deneyimi için kitaplığınızın sembol dosyalarını yayımlaması ve kaynak bağlantısı kullanması gerekir. Sembol dosyaları ve sembol paketleri hakkında daha fazla bilgi için bkz. [sembol paketleri](./nuget.md#symbol-packages).

✔️ belirleyici derlemeleri etkinleştirmeyi düşünün.

> Belirleyici derlemeler, sonuçta elde edilen ikilinin belirtilen kaynaktan oluşturulduğunu ve izlenebilirlik sağlamasını etkinleştirir. Belirleyici derlemeler ve bunları etkinleştirmeye yönelik yönergeler hakkında daha fazla bilgi için bkz. [belirleyici derlemeler](https://github.com/clairernovotny/DeterministicBuilds).

>[!div class="step-by-step"]
>[Önceki](dependencies.md) 
> [Sonraki](publish-nuget-package.md)

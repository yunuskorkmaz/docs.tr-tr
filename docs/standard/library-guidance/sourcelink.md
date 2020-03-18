---
title: Kaynak Bağlantı ve .NET kitaplıkları
description: .NET kitaplıkları için hata ayıklama geliştirmek için Kaynak Bağlantı kullanmak için en iyi uygulama önerileri.
ms.date: 01/15/2019
ms.openlocfilehash: 3d768ae6e79efa23a8402ea37bc34cd58cd52c8c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "76744546"
---
# <a name="source-link"></a>Kaynak Bağlantısı

Kaynak Bağlantı geliştiriciler tarafından NuGet gelen .NET derlemeleri kaynak kodu hata ayıklama sağlayan bir teknolojidir. Kaynak Bağlantısı, NuGet paketini oluştururken yürütür ve kaynak denetimi meta verilerini derlemelerin ve paketin içine yerlebir eder. Paketi indiren ve Visual Studio'da Source Link'i etkinleştiren geliştiriciler, kaynak koduna adım atabilir. Kaynak Bağlantı büyük bir hata ayıklama deneyimi oluşturmak için kaynak denetimi meta verileri sağlar.

## <a name="source-link-demo"></a>Kaynak Bağlantı demosu

> [!VIDEO https://www.youtube.com/embed/gyRGhCQPkB4?start=61]

## <a name="using-source-link"></a>Kaynak Bağlantısını Kullanma

Kaynak Bağlantı'yı kullanma yönergeleri [dotnet/sourcelink](https://github.com/dotnet/sourcelink/blob/master/README.md) GitHub deposunda bulunabilir.

Kaynak Bağlantı meta verilerinin pakete başarıyla yerleştirildiğini doğrulamak için [NuGet Paket](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) Gezgini'ni kullanabilirsiniz. Meta `Repository` verilerin bir işleme tanımlayıcısıyla mevcut olduğunu ve .pdb dosyalarının her hedefin .dll'si ile bulunduğunu denetleyin.

![NuGet Paket Gezgini'nde Kaynak Bağlantı](./media/sourcelink/nuget-package-explorer-sourcelink.png "NuGet Paket Gezgini'nde Kaynak Bağlantı")

✔️ Derlemelerinize ve NuGet paketlerinize kaynak denetimi meta verileri eklemek için Kaynak Bağlantısını kullanmayı düşünün.

> [!TIP]
> Türünüzüze hata ayıklama öznitelikleri ekleyerek bir geliştiricinin hata ayıklama deneyimini daha da geliştirebilirsiniz.
>
> * <xref:System.Diagnostics.DebuggerDisplayAttribute>hata ayıklama değişkeni pencerelerinde bir sınıfın veya alanın nasıl görüntüleneceğini özelleştirebilir.
> * <xref:System.Diagnostics.DebuggerStepThroughAttribute>hata ayıklayıcıya koda adım atmak yerine kodu niçin geçmesi gerektiğini bildirir.
> * <xref:System.Diagnostics.DebuggerBrowsableAttribute>bir üyenin hata ayıklama değişkeni penceresinde görüntülenip görüntülenmediğini denetler.

✔️ Simge dosyaları`*.pdb`yayımlama düşünün ( ).

> En iyi hata ayıklama deneyimi için kitaplığınız sembol dosyaları yayımlamanın yanı sıra Kaynak Bağlantı'yı da kullanmalıdır. Sembol dosyaları ve sembol paketleri hakkında daha fazla bilgi için [Sembol paketlerine](./nuget.md#symbol-packages)bakın.

>[!div class="step-by-step"]
>[Önceki](dependencies.md)
>[Sonraki](publish-nuget-package.md)

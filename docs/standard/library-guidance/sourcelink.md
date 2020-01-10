---
title: Kaynak bağlantısı ve .NET kitaplıkları
description: .NET kitaplıklarında hata ayıklamayı geliştirmek için kaynak bağlantısını kullanmaya yönelik en iyi yöntem önerileri.
ms.date: 01/15/2019
ms.openlocfilehash: 0ebc7601f1ad92b0fc6ab4c7599b010cb42feb5d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706445"
---
# <a name="source-link"></a>Kaynak Bağlantısı

Kaynak bağlantısı, geliştiriciler tarafından NuGet 'den .NET derlemelerinin kaynak kodu hata ayıklamasını sağlayan bir teknolojidir. NuGet paketini oluştururken kaynak bağlantısı yürütülür ve derleme ve paket içindeki kaynak denetimi meta verilerini katıştırır. Visual Studio 'da paketini indirir ve kaynak bağlantısı etkinleştirilmiş geliştiriciler, kaynak kodunu görebilir. Kaynak bağlantısı, harika bir hata ayıklama deneyimi oluşturmak için kaynak denetimi meta verileri sağlar.

## <a name="source-link-demo"></a>Kaynak bağlantısı tanıtımı

> [!VIDEO https://www.youtube.com/embed/gyRGhCQPkB4?start=61]

## <a name="using-source-link"></a>Kaynak bağlantısı kullanma

Kaynak bağlantısı kullanma yönergeleri [DotNet/sourcelink](https://github.com/dotnet/sourcelink/blob/master/README.md) GitHub deposunda bulunabilir.

Kaynak bağlantısı meta verilerinin pakete başarıyla eklenmiş olduğunu doğrulamak için [NuGet Paket Gezgini](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) ' ni kullanabilirsiniz. `Repository` meta verilerin bir COMMIT tanımlayıcısı ile mevcut olduğunu ve bu. pdb dosyalarının her hedefin. dll ile bulunduğunu denetleyin.

![NuGet Paket Gezgininde kaynak bağlantısı](./media/sourcelink/nuget-package-explorer-sourcelink.png "NuGet Paket Gezgininde kaynak bağlantısı")

**✔️** derlemelerinize ve NuGet paketlerine kaynak denetimi meta verileri eklemek Için kaynak bağlantısı kullanmayı düşünün.

> [!TIP]
> Türlerinizi hata ayıklayıcı öznitelikleri ekleyerek bir geliştiricinin hata ayıklama deneyimini daha da geliştirebilirsiniz.
>
> * <xref:System.Diagnostics.DebuggerDisplayAttribute>, bir sınıfın veya alanın hata ayıklayıcı değişkeni penceresinde nasıl görüntülendiğini özelleştirebilir.
> * <xref:System.Diagnostics.DebuggerStepThroughAttribute>, hata ayıklayıcıya koda adımla değil kodun içinde ilermesini söyler.
> * <xref:System.Diagnostics.DebuggerBrowsableAttribute>, bir üyenin hata ayıklayıcı değişken pencerelerinin görüntülenip görüntülenmediğini denetler.

**✔️** sembol dosyalarını yayımlamayı düşünün (`*.pdb`).

> En iyi hata ayıklama deneyimi için kitaplığınızın sembol dosyalarını yayımlaması ve kaynak bağlantısı kullanması gerekir. Sembol dosyaları ve sembol paketleri hakkında daha fazla bilgi için bkz. [sembol paketleri](./nuget.md#symbol-packages).

>[!div class="step-by-step"]
>[Önceki](dependencies.md)
>[İleri](publish-nuget-package.md)

---
title: Kaynak bağlantısı ve .NET kitaplıkları
description: .NET kitaplıklarında hata ayıklamayı geliştirmek için kaynak bağlantısını kullanmaya yönelik en iyi yöntem önerileri.
author: jamesnk
ms.author: mairaw
ms.date: 01/15/2019
ms.openlocfilehash: 7530c984ce4bbe9e40362bd550bec57ac585a550
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928985"
---
# <a name="source-link"></a>Kaynak Bağlantısı

Kaynak bağlantısı, geliştiriciler tarafından NuGet 'den .NET derlemelerinin kaynak kodu hata ayıklamasını sağlayan bir teknolojidir. NuGet paketini oluştururken kaynak bağlantısı yürütülür ve derleme ve paket içindeki kaynak denetimi meta verilerini katıştırır. Visual Studio 'da paketini indirir ve kaynak bağlantısı etkinleştirilmiş geliştiriciler, kaynak kodunu görebilir. Kaynak bağlantısı, harika bir hata ayıklama deneyimi oluşturmak için kaynak denetimi meta verileri sağlar.

## <a name="source-link-demo"></a>Kaynak bağlantısı tanıtımı

> [!VIDEO https://www.youtube.com/embed/gyRGhCQPkB4?start=61]

## <a name="using-source-link"></a>Kaynak bağlantısı kullanma

Kaynak bağlantısı kullanma yönergeleri [DotNet/sourcelink](https://github.com/dotnet/sourcelink/blob/master/README.md) GitHub deposunda bulunabilir.

Kaynak bağlantısı meta verilerinin pakete başarıyla eklenmiş olduğunu doğrulamak için [NuGet Paket Gezgini](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) ' ni kullanabilirsiniz. `Repository` Meta verilerin bir açıklama tanımlayıcısı ile mevcut olduğunu ve bu. pdb dosyalarının her hedefin. dll ile bulunduğunu denetleyin.

![NuGet Paket Gezgininde kaynak bağlantısı](./media/sourcelink/nuget-package-explorer-sourcelink.png "NuGet Paket Gezgininde kaynak bağlantısı")

**✔️** derlemelerinize ve NuGet paketlerine kaynak denetimi meta verileri eklemek Için kaynak bağlantısı kullanmayı düşünün.

> [!TIP]
> Türlerinizi hata ayıklayıcı öznitelikleri ekleyerek bir geliştiricinin hata ayıklama deneyimini daha da geliştirebilirsiniz.
>
> * <xref:System.Diagnostics.DebuggerDisplayAttribute>, bir sınıfın veya alanın hata ayıklayıcı değişkeni penceresinde nasıl görüntülendiğini özelleştirebilir.
> * <xref:System.Diagnostics.DebuggerStepThroughAttribute>hata ayıklayıcıya koda Adımlama yerine kodda adım adım ilermesini söyler.
> * <xref:System.Diagnostics.DebuggerBrowsableAttribute>hata ayıklayıcı değişkeni penceresinde bir üyenin görüntülenip görüntülenmediğini denetler.

**✔️** sembol dosyalarını yayımlamayı düşünün (`*.pdb`).

> En iyi hata ayıklama deneyimi için kitaplığınızın sembol dosyalarını yayımlaması ve kaynak bağlantısı kullanması gerekir. Sembol dosyaları ve sembol paketleri hakkında daha fazla bilgi için bkz. [sembol paketleri](./nuget.md#symbol-packages).

>[!div class="step-by-step"]
>[Önceki](dependencies.md)İleri
>[](publish-nuget-package.md)

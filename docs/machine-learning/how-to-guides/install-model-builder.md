---
title: Model Oluşturucu nasıl yüklenir
description: ML.NET model Oluşturucu aracını yüklemeyi öğrenin
author: luisquintanilla
ms.author: luquinta
ms.date: 06/21/2019
ms.custom: mvc, how-to
ms.openlocfilehash: b0d45ab7807bf84b98c58e85580d5aa04d0c5f7d
ms.sourcegitcommit: 1e72e2990220b3635cebc39586828af9deb72d8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2019
ms.locfileid: "71306320"
---
# <a name="how-to-install-mlnet-model-builder"></a>ML.NET model Oluşturucusu nasıl yüklenir

.NET uygulamalarınıza makine öğrenimi eklemek için ML.NET model Oluşturucu 'Yu yüklemeyi öğrenin.

> [!NOTE]
> Model Oluşturucu Şu anda önizleme aşamasındadır.

## <a name="pre-requisites"></a>Ön koşullar

- Visual Studio 2017 15.9.12 veya üzeri/Visual Studio 2019
- .NET Core 2,1 veya üzeri SDK

## <a name="limitations"></a>Sınırlamalar

- ML.NET model Oluşturucu uzantısı Şu anda yalnızca Windows üzerinde Visual Studio 'da çalışıyor.
- Eğitim veri kümesi sınır 1 GB
- SQL Server eğitim için 100.000 satırlık bir sınıra sahiptir
- Visual Studio 2017 için Microsoft SQL Server veri araçları desteklenmez

## <a name="install"></a>Yükleme

ML.NET model Oluşturucusu Visual Studio Market aracılığıyla veya Visual Studio içinden yüklenebilir. 

### <a name="visual-studio-marketplace"></a>Visual Studio Market

1. [Visual Studio Market](https://marketplace.visualstudio.com/items?itemName=MLNET.07) 'ten indir
1. İlgili Visual Studio sürümüne yüklemek için istemleri izleyin

### <a name="visual-studio-2017"></a>Visual Studio 2017

1. Menü çubuğunda **Araçlar** > **Uzantılar ve güncelleştirmeler** ' i seçin.

    ![VS2017 Open Extensions Manager iletişim kutusu](./media/install-model-builder/vs2017-open-extensions-manager.png)

1. *Uzantı ve güncelleştirmeler* Istemi içinde *çevrimiçi* düğümünü seçin.
1. Arama çubuğunda *ml.net model Oluşturucu* araması yapın ve sonuçlardan ml.net model Oluşturucu (Önizleme) öğesini seçin.

    ![VS2017 arama ve model Oluşturucu uzantısını Uzantı Yöneticisi iletişim kutusunda ara](./media/install-model-builder/vs2017-install-model-builder.png)

1. Yüklemeyi tamamlamaya yönelik istemleri izleyin

### <a name="visual-studio-2019"></a>Visual Studio 2019

1. Menü çubuğunda **Uzantılar** > **Yönet uzantıları** ' nı seçin.

    ![VS2019 Open Extensions Manager iletişim kutusu](./media/install-model-builder/vs2019-open-extensions-manager.png)

1. *Uzantı ve güncelleştirmeler* Istemi içinde *çevrimiçi* düğümünü seçin.
1. Arama çubuğuna *ml.net model Oluşturucu* yazın ml.net model Oluşturucu (Önizleme) öğesini seçin

    ![VS2019 arama ve model Oluşturucu uzantısını Uzantı Yöneticisi iletişim kutusunda ara](./media/install-model-builder/vs2019-install-model-builder.png)

1. Yüklemeyi tamamlamaya yönelik istemleri izleyin

## <a name="uninstall"></a>Kaldır

### <a name="visual-studio-2017"></a>Visual Studio 2017

1. Menü çubuğunda **Araçlar** > **Uzantılar ve güncelleştirmeler** ' i seçin.

    ![VS2017 Uzantıları Yönet iletişim kutusunu aç](./media/install-model-builder/vs2017-open-extensions-manager.png)

1. *Uzantı ve güncelleştirmeler* istemi Içinde, *yüklü* düğümü genişletin ve *Araçlar* ' ı seçin.
1. Araçlar listesinden ML.NET model Oluşturucu (Önizleme) öğesini seçin ve ardından *Kaldır* ' ı seçin.

    ![VS2017 model Oluşturucu uzantısını uzantılar Yöneticisi iletişim kutusunda ara ve Kaldır](./media/install-model-builder/vs2017-uninstall-model-builder.png)

1. Kaldırma işlemini gerçekleştirmek için istemleri izleyin.

### <a name="visual-studio-2019"></a>Visual Studio 2019

1. Menü çubuğunda **Uzantılar** > **Yönet uzantıları** ' nı seçin.

    ![VS2019 Uzantıları Yönet iletişim kutusunu aç](./media/install-model-builder/vs2019-open-extensions-manager.png)

1. *Uzantı ve güncelleştirmeler* istemi Içinde, *yüklü* düğümü genişletin ve *Araçlar* ' ı seçin.
1. Araçlar listesinden ML.NET model Oluşturucu (Önizleme) öğesini seçin ve ardından *Kaldır* ' ı seçin.

    ![VS2019 model Oluşturucu uzantısını uzantılar Yöneticisi iletişim kutusunda ara ve Kaldır](./media/install-model-builder/vs2019-uninstall-model-builder.png)

1. Kaldırma işlemini gerçekleştirmek için istemleri izleyin.

## <a name="upgrade"></a>Upgrade

Yükseltme işlemi, yükleme işlemine benzer. Visual Studio Market 'den en son sürümü indirin ya da Visual Studio 'da Extensions Manager 'ı kullanın.

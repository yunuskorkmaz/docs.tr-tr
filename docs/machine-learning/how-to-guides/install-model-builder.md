---
title: Model Oluşturucu nasıl yüklenir?
description: ML.NET Model Oluşturucu aracını nasıl yükleyin öğrenin
author: luisquintanilla
ms.author: luquinta
ms.date: 11/21/2019
ms.custom: mvc, how-to, mlnet-tooling
ms.openlocfilehash: b944d7f6044553251132824e7e4213119e34500e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78848658"
---
# <a name="how-to-install-mlnet-model-builder"></a>Model Oluşturucu ML.NET nasıl yüklenir?

.NET uygulamalarınıza makine öğrenimi eklemek için ML.NET Model Builder'ı nasıl yükleyebilirsiniz öğrenin.

> [!NOTE]
> Model Oluşturucu şu anda Önizleme'de.

## <a name="prerequisites"></a>Önkoşullar

- Visual Studio 2017 sürüm 15.9.12 veya sonrası / Visual Studio 2019
- .NET Core 2.1 SDK veya sonrası.

> [!NOTE]
> .NET Core 3.0 SDK şu anda desteklenmiyor.

## <a name="limitations"></a>Sınırlamalar

- ML.NET Model Oluşturucu Uzantısı şu anda yalnızca Windows'daki Visual Studio'da çalışmaktadır.
- 1GB eğitim veri seti sınırı
- SQL Server eğitim için 100 bin satır sınırı vardır
- Visual Studio 2017 için Microsoft SQL Server Veri Araçları desteklenmiyor

## <a name="install"></a>Yükleme

ML.NET Model oluşturucu Visual Studio Marketplace üzerinden ya da Visual Studio içinde kurulabilir.

### <a name="visual-studio-marketplace"></a>Visual Studio Market

1. Visual [Studio Marketplace'ten](https://marketplace.visualstudio.com/items?itemName=MLNET.07) indirin
1. İlgili Visual Studio sürümüne yüklemek için istemleri izleyin

### <a name="visual-studio-2017"></a>Visual Studio 2017

1. Menü çubuğunda **Araçlar** > **Uzantıları ve Güncelleştirmeleri'ni** seçin

    ![VS2017 açık uzantıları yöneticisi iletişim kutusu](./media/install-model-builder/vs2017-open-extensions-manager.png)

1. *Uzantı ve Güncelleştirmeler* istemi *içinde, Çevrimiçi* düğümünü seçin.
1. Arama çubuğunda, *model oluşturucuML.NET* ve sonuçlardan ML.NET Model Oluşturucu'yu (Önizleme) seçin

    ![VS2017 arama ve uzantıları yöneticisi iletişim modeli model oluşturucu uzantısı yükleyin](./media/install-model-builder/vs2017-install-model-builder.png)

1. Yüklemeyi tamamlamak için istemleri izleyin

### <a name="visual-studio-2019"></a>Visual Studio 2019

1. Menü çubuğunda Uzantıları **Extensions** > **Yönet Uzantıları'nı** seçin

    ![VS2019 açık uzantıları yöneticisi iletişim kutusu](./media/install-model-builder/vs2019-open-extensions-manager.png)

1. *Uzantı ve Güncelleştirmeler* istemi *içinde, Çevrimiçi* düğümünü seçin.
1. Arama çubuğuna *model* oluşturucuML.NET yazın ML.NET Model Oluşturucu'yu seçin (Önizleme)

    ![VS2019 arama ve uzantıları yöneticisi iletişim modeli oluşturucu uzantısı yükleyin](./media/install-model-builder/vs2019-install-model-builder.png)

1. Yüklemeyi tamamlamak için istemleri izleyin

## <a name="uninstall"></a>Kaldırma

### <a name="visual-studio-2017"></a>Visual Studio 2017

1. Menü çubuğunda **Araçlar** > **Uzantıları ve Güncelleştirmeleri'ni** seçin

    ![VS2017 açık yönet uzantıları iletişim kutusu](./media/install-model-builder/vs2017-open-extensions-manager.png)

1. *Uzantı ve Güncelleştirmeler* istemi içinde, *Yüklü* düğüm genişletmek ve *Araçları* seçin
1. Araçlar listesinden model oluşturucuML.NET (Önizleme) seçeneğini belirleyin ve ardından *Kaldır'ı* seçin

    ![VS2017 arama ve uzantıları yöneticisi iletişim modelini model oluşturucu uzantısı kaldırmak](./media/install-model-builder/vs2017-uninstall-model-builder.png)

1. Yüklemeyi tamamlamak için istemleri izleyin.

### <a name="visual-studio-2019"></a>Visual Studio 2019

1. Menü çubuğunda Uzantıları **Extensions** > **Yönet Uzantıları'nı** seçin

    ![VS2019 açık yönet uzantıları iletişim kutusu](./media/install-model-builder/vs2019-open-extensions-manager.png)

1. *Uzantı ve Güncelleştirmeler* istemi içinde, *Yüklü* düğüm genişletmek ve *Araçları* seçin
1. Araçlar listesinden model oluşturucuML.NET (Önizleme) seçeneğini belirleyin ve ardından *Kaldır'ı* seçin

    ![VS2019 arama ve uzantıları yöneticisi iletişim modeli oluşturucu uzantısı kaldırmak](./media/install-model-builder/vs2019-uninstall-model-builder.png)

1. Yüklemeyi tamamlamak için istemleri izleyin.

## <a name="upgrade"></a>Yükseltme

Yükseltme işlemi yükleme işlemine benzer. Visual Studio Marketplace'ten en son sürümü indirin veya Visual Studio'daki Extensions Manager'ı kullanın.

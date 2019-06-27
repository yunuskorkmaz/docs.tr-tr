---
title: Model oluşturucuyu yükleme
description: ML.NET Model Oluşturucu aracı yüklemeyi öğrenin
author: luisquintanilla
ms.author: luquinta
ms.date: 06/21/2019
ms.custom: mvc, how-to
ms.openlocfilehash: 54ab595c56f816517180aab48022c7df207fe84d
ms.sourcegitcommit: 52e588dc2ee74d484cd07ac60076be25cbf777ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67410652"
---
# <a name="how-to-install-mlnet-model-builder"></a>ML.NET Model oluşturucuyu yükleme

Machine learning .NET uygulamalarınıza eklemek için ML.NET Model Oluşturucu yüklemeyi öğrenin.

> [!NOTE]
> Model Oluşturucu şu anda Önizleme aşamasındadır.

## <a name="pre-requisites"></a>Ön koşullar

- Visual Studio 2017 15.9.12 veya üzeri / Visual Studio 2019
- .NET core 2.1 veya üzeri SDK'sı

## <a name="limitations"></a>Sınırlamalar

- ML.NET Model Oluşturucu uzantısı şu anda yalnızca Visual Studio Windows üzerinde çalışır.
- Eğitim veri kümesi sınırını 1 GB
- SQL Server eğitimi için 100 bin satır sınırı vardır.
- Visual Studio 2017 için Microsoft SQL Server veri araçları desteklenmiyor

## <a name="install"></a>Yükleme

Visual Studio Market aracılığıyla veya içinden ML.NET Model Oluşturucu yüklenebilir Visual Studio. 

### <a name="visual-studio-marketplace"></a>Visual Studio Market

1. İndirmesine [Visual Studio Market](https://marketplace.visualstudio.com/items?itemName=MLNET.07)
1. İlgili Visual Studio sürümünü yüklemek için istemleri takip edin

### <a name="visual-studio-2017"></a>Visual Studio 2017

1. Menü çubuğunda **Araçları** > **Uzantılar ve güncelleştirmeler**
1. İçinde *uzantı ve güncelleştirmeler* anında, select *çevrimiçi* düğümü.
1. Arama çubuğunda arama *ML.NET Model Oluşturucu* sonuçlarından ML.NET Model Oluşturucu (Önizleme) seçin.
1. Yüklemeyi tamamlamak için istemleri takip edin

### <a name="visual-studio-2019"></a>Visual Studio 2019

1. Menü çubuğunda, seçin **uzantıları** > **uzantıları Yönet**
1. İçinde *uzantı ve güncelleştirmeler* anında, select *çevrimiçi* düğümü.
1. Tür *ML.NET Model Oluşturucu* ML.NET Model Oluşturucu (Önizleme) arama çubuğuna seçin
1. Yüklemeyi tamamlamak için istemleri takip edin

## <a name="uninstall"></a>Kaldır

### <a name="visual-studio-2017"></a>Visual Studio 2017

1. Menü çubuğunda, seçin **Araçları** > **Uzantılar ve güncelleştirmeler**
1. İçinde *uzantı ve güncelleştirmeler* isteminde, genişletme *yüklü* düğümünü seçip alt *araçları*
1. Araçları listesinden ML.NET Model Oluşturucu (Önizleme) seçin ve ardından seçin *Kaldır*
1. Kaldırma işlemini tamamlamak için istemleri izleyin.

### <a name="visual-studio-2019"></a>Visual Studio 2019

1. Menü çubuğunda, seçin **uzantıları** > **uzantıları Yönet**
1. İçinde *uzantı ve güncelleştirmeler* isteminde, genişletme *yüklü* düğümünü seçip alt *araçları*
1. Araçları listesinden ML.NET Model Oluşturucu (Önizleme) seçin ve ardından seçin *Kaldır*
1. Kaldırma işlemini tamamlamak için istemleri izleyin.

## <a name="upgrade"></a>Upgrade

Yükseltme işlemi, yükleme işlemine benzerdir. Visual Studio Market'ten en son sürümü yükleyin ya da Visual Studio Uzantı Yöneticisi'ni kullanın.

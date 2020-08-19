---
title: Model Oluşturucu 'da GPU desteği nasıl yüklenir
description: Model Oluşturucu 'da GPU desteğini yüklemeyi öğrenin
ms.date: 08/18/2020
author: luisquintanilla
ms.author: luquinta
ms.topic: how-to
ms.openlocfilehash: ce629efa4c12a69f87196de35ebfe4331dc0800f
ms.sourcegitcommit: cbb19e56d48cf88375d35d0c27554d4722761e0d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2020
ms.locfileid: "88608570"
---
# <a name="how-to-install-gpu-support-in-model-builder"></a>Model Oluşturucu 'da GPU desteği nasıl yüklenir

Model Oluşturucu ile GPU 'yu kullanarak GPU sürücülerini yüklemeyi öğrenin.

## <a name="prerequisites"></a>Önkoşullar

- Model Oluşturucu Visual Studio uzantısı. Uzantı, 16.6.1 sürümü itibariyle Visual Studio 'da yerleşik olarak bulunur.
- [Model Oluşturucu Visual STUDIO GPU desteği uzantısı](https://marketplace.visualstudio.com/items?itemName=MLNET.ModelBuilderGPU).
- En az bir CUDA uyumlu GPU. Uyumlu GPU 'ların listesi için bkz. [NVIDIA Kılavuzu](https://developer.nvidia.com/cuda-gpus).
- NVıDıA geliştirici hesabı. Aboneliğiniz yoksa [ücretsiz bir hesap](https://developer.nvidia.com/developer-program) oluşturun.

## <a name="install-dependencies"></a>Bağımlılıkları yükleme

1. [CUDA v 10.0](https://developer.nvidia.com/cuda-10.0-download-archive)'ı yükler. Daha yeni bir sürümü değil CUDA v 10.0 ' ı yüklediğinizden emin olun. CUDA 'nin birden çok sürümü yüklü olamaz.
1. [CUDA 10,0 Için Cudnn v 7.6.4](https://developer.nvidia.com/rdp/cudnn-download)'yi yükler. Birden fazla cuDNN sürümü yüklü olamaz. CuDNN v 7.6.4 ZIP dosyasını indirdikten ve yeniden paketten çıktıktan sonra `<CUDNN_zip_files_path>\cuda\bin\cudnn64_7.dll` öğesine kopyalayın `<YOUR_DRIVE>\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.0\bin` .

## <a name="troubleshooting"></a>Sorun giderme

**Nasıl yaparım? hangi GPU 'YU öğrendim?**

Belirtilen yönergeleri izleyin:

1. Masaüstüne sağ tıklayın
1. Açılır pencerede "NVıDıA Denetim Masası" veya "NVıDıA ekran" görürseniz, NVıDıA GPU 'SU vardır
1. Açılır pencerede "NVıDıA Denetim Masası" veya "NVıDıA ekran" seçeneğine tıklayın
1. "Grafik kartı bilgileri" bölümüne bakın
1. NVıDıA GPU adını görürsünüz

**NVıDıA Denetim Masası 'Nı görmüyorum (veya açılamıyor), ancak NVıDıA GPU sahibim var.**

1. Cihaz Yöneticisi’ni açın
1. Görüntü bağdaştırıcılarına bakın
1. GPU 'larınız için uygun [sürücüyü](https://www.nvidia.com/drivers) yükleyeceksiniz.

---
title: Giriş ekranı ekleme
description: Bir Windows Presentation Foundation (WPF) uygulamasına başlangıç penceresi veya giriş ekranı ekleme hakkında bilgi edinin.
ms.date: 08/18/2018
helpviewer_keywords:
- WPF [WPF], splash screen
- startup window [WPF]
- SplashScreen class [WPF]
- splash screen [WPF]
ms.assetid: d70a25c4-5fb9-4c27-b01d-b1b8ef39b3fd
ms.openlocfilehash: 0d0cf2e2a550320650c3b4a0c257071a0403c32b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617966"
---
# <a name="how-to-add-a-splash-screen-to-a-wpf-application"></a>Nasıl yapılır: WPF Uygulamasına Giriş Ekranı Ekleme

Bu konu, bir Windows Presentation Foundation (WPF) uygulamasına başlangıç penceresi veya *giriş ekranının*nasıl ekleneceğini gösterir.

## <a name="to-add-an-existing-image-as-a-splash-screen"></a>Varolan bir görüntüyü karşılama ekranı olarak eklemek için

1. Giriş ekranı için kullanmak istediğiniz bir görüntü oluşturun veya bulun. Windows Imaging bileşeni (WIC) tarafından desteklenen herhangi bir görüntü biçimini kullanabilirsiniz. Örneğin, BMP, GIF, JPEG, PNG veya TIFF biçimini kullanabilirsiniz.

2. Resim dosyasını WPF uygulaması projesine ekleyin.

3. **Çözüm Gezgini**, görüntüyü seçin.

4. Özellikler penceresi, **Yapı eylemi** özelliği için aşağı açılan oka tıklayın.

5. Aşağı açılan listeden **SplashScreen** ' i seçin.

6. Uygulamayı derlemek ve çalıştırmak için **F5** tuşuna basın.

     Giriş ekranı görüntüsü ekranın ortasında görünür ve ana uygulama penceresi göründüğünde kaybolur.

## <a name="to-exclude-the-splash-screen-from-build"></a>Tanıtım ekranını derlemeden dışlamak için

1. **Çözüm Gezgini**giriş ekranı görüntüsünü seçin.

2. **Özellikler** penceresinde, **derleme eylemini** **hiçbiri**olarak ayarlayın.

## <a name="to-remove-the-splash-screen-from-an-application"></a>Giriş ekranını bir uygulamadan kaldırmak için

**Çözüm Gezgini**, giriş ekranı görüntüsünü silin.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.SplashScreen>
- [Nasıl yapılır: bir projeye varolan öğeleri ekleme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100))

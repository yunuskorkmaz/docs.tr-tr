---
title: 'Nasıl yapılır: WPF Uygulamasına Giriş Ekranı Ekleme'
ms.date: 08/18/2018
helpviewer_keywords:
- WPF [WPF], splash screen
- startup window [WPF]
- SplashScreen class [WPF]
- splash screen [WPF]
ms.assetid: d70a25c4-5fb9-4c27-b01d-b1b8ef39b3fd
ms.openlocfilehash: 46efa041736870c5c0f08baa321ef0dc53cacc0d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43502760"
---
# <a name="how-to-add-a-splash-screen-to-a-wpf-application"></a>Nasıl yapılır: WPF Uygulamasına Giriş Ekranı Ekleme

Bu konuda, bir başlangıç penceresi ekleme işlemi açıklanır veya *giriş ekranı*, bir Windows Presentation Foundation (WPF) uygulaması için.

## <a name="to-add-an-existing-image-as-a-splash-screen"></a>Giriş ekranı varolan bir görüntü eklemek için

1.  Oluşturun veya Karşılama ekranı olarak kullanmak istediğiniz görüntüyü bulun. Windows görüntüleme bileşeni (WIC) tarafından desteklenen herhangi bir resim biçimi kullanabilirsiniz. Örneğin, BMP, GIF, JPEG, PNG ve TIFF biçimini kullanabilirsiniz.

2.  Görüntü dosyası WPF uygulaması projesine ekleyin.

3.  İçinde **Çözüm Gezgini**, görüntüyü seçin.

4.  Özellikler penceresinde, aşağı açılan oka tıklayın **derleme eylemi** özelliği.

5.  Seçin **SplashScreen** aşağı açılan listeden.

6.  Tuşuna **F5** oluşturun ve uygulamayı çalıştırın.

     Karşılama ekranı görüntüsü ekranın ortasında görünür ve ana uygulama penceresini göründüğünde kaybolur.

## <a name="to-exclude-the-splash-screen-from-build"></a>Karşılama ekranında derlemeden hariç tutmak için

1.  İçinde **Çözüm Gezgini**, Karşılama ekran görüntüsünü seçin.

2.  İçinde **özellikleri** penceresinde **derleme eylemi** için **hiçbiri**.

## <a name="to-remove-the-splash-screen-from-an-application"></a>Bir uygulamaya ait karşılama ekranında kaldırmak için

İçinde **Çözüm Gezgini**, Karşılama ekranı görüntüyü silin.

## <a name="see-also"></a>Ayrıca Bkz.

- <xref:System.Windows.SplashScreen>
- [Nasıl yapılır: bir projeye var olan öğeleri Ekle](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100))

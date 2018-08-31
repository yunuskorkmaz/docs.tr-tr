---
title: 'Nasıl yapılır: Windows Formlarına Denetimler Kilitleme'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, locking
- controls [Windows Forms], locking
ms.assetid: 94efe0d2-c14e-4d14-b903-63ea9b07e290
ms.openlocfilehash: 8de22ae6667446620867f3c15aac3c4af65582bf
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2018
ms.locfileid: "43253636"
---
# <a name="how-to-lock-controls-to-windows-forms"></a>Nasıl yapılır: Windows Formlarına Denetimler Kilitleme
Windows uygulamanızın kullanıcı arabirimini (UI) tasarlarken, böylece istemeden taşıdığınızda veya diğer özellikleri ayarlarken yeniden boyutlandırabilir, doğru konumlandırılır sonra denetimleri kilitleyebilirsiniz.  
  
 Ayrıca, kilitlemek ve tüm form üzerinde denetimleri pek çok denetimi olan formlarda yardımcı olan tek bir seferde kilidini veya tek denetimleri kilidini açabilirsiniz. Tüm denetimleri form üzerinde istediğiniz yere yerleştirdikten sonra bunları hatalı hareketini önlemek için tüm kilitleme.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-lock-a-control"></a>Bir denetim kilitlemek için  
  
1.  İçinde **özellikleri** penceresinde tıklayın **kilitli** özelliğini tıklatın ve `true`. (Adına çift özellik ayarı değiştirir.)  
  
     Alternatif olarak, denetime sağ tıklayın ve seçin **kilit denetimleri**.  
  
    > [!NOTE]
    >  Denetimleri kilitleme, bunları tasarım yüzeyine bir yeni boyut veya konum sürüklenen öğesinden engeller. Ancak, yine de denetimleri yoluyla konumunu ve boyutunu değiştirebilirsiniz **özellikleri** penceresi veya kod.  
  
### <a name="to-lock-all-the-controls-on-a-form"></a>Bir formda tüm denetimler kilitlemek için  
  
1.  Gelen **biçimi** menüsünde seçin **kilit denetimleri**.  
  
    > [!NOTE]
    >  Bir form denetim olduğundan bu komut formun boyutunu da kilitler.  
  
### <a name="to-unlock-all-locked-controls-on-a-form"></a>Formdaki denetimler kilitli tümünün kilidini aç  
  
1.  Gelen **biçimi** menüsünde seçin **kilit denetimleri**.  
  
     Formdaki tüm daha önce kilitli denetimleri sunulmuştur kilidi.  
  
### <a name="to-unlock-locked-controls-individually"></a>Tek tek denetimler kilitli kilidini aç  
  
1.  İçinde **özellikleri** penceresinde tıklayın **kilitli** özelliğini tıklatın ve `false`. (Adına çift özellik ayarı değiştirir.)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Forms Denetimleri](../../../../docs/framework/winforms/controls/index.md)  
 [Windows Forms’da Denetimleri Düzenleme](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [Ayrı Windows Forms Denetimlerini Etiketleme ve Kısayollarını Sunma](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [Windows Forms'da Kullanılacak Denetimler](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [İşleve Göre Windows Forms Denetimleri](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)

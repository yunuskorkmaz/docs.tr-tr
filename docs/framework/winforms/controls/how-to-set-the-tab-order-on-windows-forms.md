---
title: 'Nasıl yapılır: Windows Forms’da Sekme Sırasını Ayarlama'
ms.date: 03/30/2017
f1_keywords:
- TabStop
- TabIndex
helpviewer_keywords:
- tab order [Windows Forms], controls on Windows forms
- Windows Forms controls, setting tab order
- controls [Windows Forms], setting tab order
- Windows Forms, setting tab order
ms.assetid: 71fa8e76-0472-414b-ad3c-0f90166e0ad7
ms.openlocfilehash: 50f5f91a946aeebc4d82630b25d18d8f8d2ea4be
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59339911"
---
# <a name="how-to-set-the-tab-order-on-windows-forms"></a>Nasıl yapılır: Windows Forms’da Sekme Sırasını Ayarlama
Sekme sırası, kullanıcı odak bir denetimden başka SEKME tuşuna basarak hareket sırasıdır. Her form kendi sekme sırasını sahiptir. Varsayılan olarak, sekme sırasını denetimleri oluşturduğunuz sırada ile aynıdır. Sekme sırası numaralandırma sıfır ile başlar.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-set-the-tab-order-of-a-control"></a>Bir denetimin sekme sırasını ayarlama  
  
1. Üzerinde **görünümü** menüsünde tıklatın **sekme sırasını**.  
  
     Bu form üzerindeki sekme sırası seçim modunu etkinleştirir. Bir sayı (temsil eden <xref:System.Windows.Forms.Control.TabIndex%2A> özelliği) her denetimin sol üst köşesinde görünür.  
  
2. Denetimlerin sekme sırasını istediğiniz sırayla kurmak için tıklayın.  
  
    > [!NOTE]
    >  Sekme sırası içinde denetimin yer, daha büyük veya 0'a eşit herhangi bir değere ayarlanabilir. Yinelenen meydana geldiğinde, z düzenini iki denetimin değerlendirilir ve üst denetimin ilk olarak sekmeli. (Z-formun z ekseni [derinliği] boyunca bir form üzerinde denetimleri visual katmanlarını sırasıdır. Z düzenini hangi denetimlerin önüne başka denetimler belirler.) Z düzeni hakkında daha fazla bilgi için bkz. [Windows Forms'da nesneleri katmanlama](how-to-layer-objects-on-windows-forms.md).  
  
3. İşiniz bittiğinde tıklayın **sekme sırasını** üzerinde **görünümü** yeniden sekme sırasını modundan ayrılmak için menü.  
  
    > [!NOTE]
    >  Odak alamayan denetimleri yanı sıra, devre dışı bırakılmış ve görünmez denetimler olmadığı bir <xref:System.Windows.Forms.Control.TabIndex%2A> ve bu özellik sekme sırasının dahil değildir. Kullanıcı TAB tuşuna bastığında gibi bu denetimleri atlanır.  
  
 Alternatif olarak, sekme sırasını kullanarak Özellikler penceresi ayarlanabilir <xref:System.Windows.Forms.Control.TabIndex%2A> özelliği. <xref:System.Windows.Forms.Control.TabIndex%2A> Denetimin bir özelliğine sekme sırasının nerede konumlandığını belirler. Çizilen ilk denetim varsayılan olarak, sahip bir <xref:System.Windows.Forms.Control.TabIndex%2A> değeri 0 olan ikinci bir <xref:System.Windows.Forms.Control.TabIndex%2A> 1 ve benzeri.  
  
 Ayrıca, varsayılan bir <xref:System.Windows.Forms.GroupBox> kontrolünde kendi <xref:System.Windows.Forms.Control.TabIndex%2A> bir tam sayı değeri. A <xref:System.Windows.Forms.GroupBox> denetiminin kendisinin çalışma zamanında odağa sahip olamaz. Bu nedenle, her denetimi içinde bir <xref:System.Windows.Forms.GroupBox> kendi ondalık sahip <xref:System.Windows.Forms.Control.TabIndex%2A> .0 ile başlangıç değeri. Doğal olarak <xref:System.Windows.Forms.Control.TabIndex%2A> , bir <xref:System.Windows.Forms.GroupBox> denetim artırılır, Denetim buna göre artar. Değiştirdiyseniz bir <xref:System.Windows.Forms.Control.TabIndex%2A> 6, 5 değerine <xref:System.Windows.Forms.Control.TabIndex%2A> kendi grubundaki ilk denetimi değerini otomatik olarak değiştirir 6.0 ve böyle devam eder.  
  
 Son olarak, herhangi bir formunuzdaki çok denetimi sekme sırasının atlanabilir. Genellikle, sekme sırayla çalıştırma seçer her bir denetimde sekme sırasını tuşuna basarak. Kapatma tarafından <xref:System.Windows.Forms.Control.TabStop%2A> özelliği, bir denetimi forma sekme sırasını geçirilen yapabilirsiniz.  
  
#### <a name="to-remove-a-control-from-the-tab-order"></a>Bir denetimin sekme sırasından kaldırmak için  
  
1. Denetimin ayarlamak <xref:System.Windows.Forms.Control.TabStop%2A> özelliğini `false` Özellikler penceresinde.  
  
     Bir denetim <xref:System.Windows.Forms.Control.TabStop%2A> özelliği sınıflandırmalara ayarlandığı `false` denetimlerde TAB tuşuyla geçiş denetimi atlanır olsa da hala sekme sırası içindeki konumuna tutar.  
  
    > [!NOTE]
    >  Bir radyo düğmesi grubunda, çalışma zamanında Durdur tek bir sekmesi vardır. Seçilen düğmesini (diğer bir deyişle, düğmeyi kendi <xref:System.Windows.Forms.RadioButton.Checked%2A> özelliğini `true`) sahip kendi <xref:System.Windows.Forms.Control.TabStop%2A> özelliği otomatik olarak ayarlayın `true`, diğer düğmeleri açıkken kendi <xref:System.Windows.Forms.Control.TabStop%2A> özelliğini `false`. Gruplama hakkında daha fazla bilgi için <xref:System.Windows.Forms.RadioButton> denetimlerini, [gruplandırma Windows Forms RadioButton denetimlerini küme işlevi görecek](how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms Denetimleri](index.md)
- [Windows Forms’da Denetimleri Düzenleme](arranging-controls-on-windows-forms.md)
- [Windows Forms'da Kullanılacak Denetimler](controls-to-use-on-windows-forms.md)
- [İşleve Göre Windows Forms Denetimleri](windows-forms-controls-by-function.md)

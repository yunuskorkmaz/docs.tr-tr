---
title: "Nasıl yapılır: Windows Forms'da denetimleri"
ms.date: 03/30/2017
helpviewer_keywords:
- Anchor property [Windows Forms], enabling resizable forms
- Windows Forms controls, screen resolutions
- resizing forms [Windows Forms]
- Windows Forms controls, size
- screen resolution and control display
- controls [Windows Forms], anchoring
- forms [Windows Forms], resizing
- Windows Forms, resizing
- controls [Windows Forms], positioning
ms.assetid: 59ea914f-fbd3-427a-80fe-decd02f7ae6d
ms.openlocfilehash: d1f1fba28eec39202b37eb410a74df400ea461a8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580948"
---
# <a name="how-to-anchor-controls-on-windows-forms"></a>Nasıl yapılır: Windows Forms'da denetimleri
Kullanıcının çalışma zamanında boyutlandırabilirsiniz bir formu tasarlıyorsanız, form üzerindeki denetimleri yeniden boyutlandırabilir ve düzgün şekilde yeniden konumlandırmak. Form ile dinamik olarak yeniden boyutlandırmak için kullanabileceğiniz <xref:System.Windows.Forms.Control.Anchor%2A> Windows Forms denetimlerinin özelliği. <xref:System.Windows.Forms.Control.Anchor%2A> Özelliği denetimi için bir yer işareti konumunu tanımlar. Bir denetimi forma sabitlenmiştir ve formu yeniden boyutlandırılmış, denetim bağlantı konumlar ile Denetim arasındaki uzaklığı korur. Örneğin, bir <xref:System.Windows.Forms.TextBox> formu yeniden boyutlandırıldığından, sol, sağ ve alt kenarları formun bağlantılı denetim <xref:System.Windows.Forms.TextBox> denetimi yeniden boyutlandırır yatay böylece aynı olan formun sağ ve sol tarafında uzaklığı korur. Konumu her zaman formun alt kenarı aynı mesafe olması buna ek olarak, denetimi kendi dikey konumlandırır. Bir denetimi değil bağlantılı ve formu yeniden boyutlandırılmış, formun kenarları kontrole konumunu değiştirilir.  
  
 <xref:System.Windows.Forms.Control.Anchor%2A> Özelliği etkileşim <xref:System.Windows.Forms.Control.AutoSize%2A> özelliği. Daha fazla bilgi için [AutoSize özelliğine genel bakış](../../../../docs/framework/winforms/controls/autosize-property-overview.md).  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-anchor-a-control-on-a-form"></a>Bir formdaki bir denetime bağlamak için  
  
1.  Yer işareti istediğiniz denetimi seçin.  
  
    > [!NOTE]
    >  CTRL tuşuna basarak her denetimi seçin ve ardından bu yordamın geri kalanını aşağıdaki aynı anda birden çok denetim sabitleyebilirsiniz.  
  
2.  İçinde **özellikleri** penceresinin sağ tarafındaki oka tıklayın <xref:System.Windows.Forms.Control.Anchor%2A> özelliği.  
  
     Bir düzenleyici çapraz gösteren görüntülenir.  
  
3.  Bir bağlantı ayarlamak için üst, sol, sağ veya çapraz alt kısmına tıklayın.  
  
     Denetimleri için üst bağlantılı ve varsayılan olarak sola.  
  
4.  Bağlantılı denetim tarafında temizlemek için arm çapraz,'a tıklayın.  
  
5.  Kapatmak için <xref:System.Windows.Forms.Control.Anchor%2A> özellik Düzenleyicisi'ni <xref:System.Windows.Forms.Control.Anchor%2A> yeniden özellik adı.  
  
 Formunuza çalışma zamanında görüntülendiğinde, formun kenarından aynı uzaklıkta konumlanmış kalmasını denetimi yeniden boyutlandırır. Uzaklık denetimi Windows Form Tasarımcısı'nda ne zaman konumlandırılmış tanımlanan bağlantılı kenarı arasındaki uzaklığı her zaman aynı kalır.  
  
> [!NOTE]
>  Gibi belirli denetimleri <xref:System.Windows.Forms.ComboBox> denetlemek, kendi yüksekliğe bir sınırı vardır. Denetimin form ya da kapsayıcı altına sabitleme denetimin yüksekliği sınırını aşan tutamaz.  
  
 Devralınan denetimler olmalıdır `Protected` bağlantılı için. Bir denetim erişim düzeyini değiştirmek için Ayarla kendi `Modifiers` özelliğinde **özellikleri** penceresi.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Windows Forms Denetimleri](../../../../docs/framework/winforms/controls/index.md)
- [Windows Forms’da Denetimleri Düzenleme](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)
- [AutoSize Özelliğine Genel Bakış](../../../../docs/framework/winforms/controls/autosize-property-overview.md)
- [Nasıl yapılır: Windows Forms'da denetimleri yerleştirme](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md)
- [İzlenecek yol: FlowLayoutPanel kullanarak Windows Forms'da denetimleri düzenleme](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [İzlenecek yol: TableLayoutPanel kullanarak Windows Forms'da denetimleri düzenleme](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [İzlenecek yol: Windows Forms denetimleri doldurma, kenar boşlukları ve AutoSize özelliği ile düzenleme](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md)

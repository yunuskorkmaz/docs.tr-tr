---
title: "Nasıl yapılır: Windows Formlarında Denetimleri Sabitleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ceaacc250d48e7199d7224f95aa91ed976c097e0
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-anchor-controls-on-windows-forms"></a>Nasıl yapılır: Windows Formlarında Denetimleri Sabitleme
Çalışma zamanında kullanıcı genişletebilir bir form tasarlarken, form üzerinde denetimleri yeniden boyutlandırma ve düzgün bir şekilde yeniden konumlandırmak gerekir. Denetimleri form ile dinamik olarak yeniden boyutlandırmak için kullanabileceğiniz <xref:System.Windows.Forms.Control.Anchor%2A> Windows Forms denetimleri özelliği. <xref:System.Windows.Forms.Control.Anchor%2A> Özelliği denetimi için bir yer işareti konumunun tanımlar. Forma Denetim bağlantılı ve formu yeniden boyutlandırılabilir denetimi denetimi ve bağlantı konumlar arasındaki uzaklığı korur. Örneğin, bir <xref:System.Windows.Forms.TextBox> formun boyutlandırıldığında sol, sağ ve form alt kenarlarını bağlantılı denetim <xref:System.Windows.Forms.TextBox> denetimi yeniden boyutlandırır yatay böylece form sağ ve sol yanlarından aynı uzaklığı korur. Konumuna her zaman formun kenar aynı mesafe böylece ek olarak, Denetim kendisini dikey olarak yerleştirir. Bir denetim yok bağlantılı ve formu yeniden boyutlandırılabilir, denetimin formun kenarları göreli konumunu değiştirilir.  
  
 <xref:System.Windows.Forms.Control.Anchor%2A> Özelliği etkileşime <xref:System.Windows.Forms.Control.AutoSize%2A> özelliği. Daha fazla bilgi için bkz: [AutoSize özelliğine genel bakış](../../../../docs/framework/winforms/controls/autosize-property-overview.md).  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-anchor-a-control-on-a-form"></a>Formdaki bir denetime bağlamak için  
  
1.  Bağlantı istediğiniz denetimi seçin.  
  
    > [!NOTE]
    >  CTRL tuşunu basılı tutup seçmek için her denetim ve bu yordamın geri kalanını aşağıdaki aynı anda birden çok denetim sabitleyebilirsiniz.  
  
2.  İçinde **özellikleri** penceresinde sağındaki oku <xref:System.Windows.Forms.Control.Anchor%2A> özelliği.  
  
     Bir düzenleyici bir çapraz gösteren görüntülenir.  
  
3.  Bir bağlantı ayarlamak için sol üst, sağ veya çapraz alt kısmına tıklayın.  
  
     Denetimleri en çok bağlantılı ve varsayılan olarak sol.  
  
4.  Bağlantılı denetim tarafında temizlemek için bu arm arası, Ek Yardım düğmesini tıklatın.  
  
5.  Kapatmak için <xref:System.Windows.Forms.Control.Anchor%2A> özelliği Düzenleyicisi <xref:System.Windows.Forms.Control.Anchor%2A> yeniden özellik adı.  
  
 Formunuz çalışma zamanında görüntülendiğinde, formun kenarından aynı uzaklıkta konumlandırılmış kalmasına denetimi göre yeniden boyutlandırır. Uzaklığı denetimi Windows Forms Tasarımcısı'nda zaman konumlandırılmış tanımlanan bağlantılı kenara uzaklığı her zaman aynı kalır.  
  
> [!NOTE]
>  Gibi belirli denetimleri <xref:System.Windows.Forms.ComboBox> denetlemek, kendi yüksekliği için bir sınır vardır. Form veya kapsayıcı altındaki denetime bağlama yükseklik sınırını aşmasına denetimi zorlayamaz.  
  
 Devralınan denetimleri olmalıdır `Protected` bağlantılı için. Bir denetim erişim düzeyini değiştirmek için ayarlayın, `Modifiers` özelliğinde **özellikleri** penceresi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Forms Denetimleri](../../../../docs/framework/winforms/controls/index.md)  
 [Windows Forms’da Denetimleri Düzenleme](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [AutoSize Özelliğine Genel Bakış](../../../../docs/framework/winforms/controls/autosize-property-overview.md)  
 [Nasıl yapılır: Windows Forms’a Denetimleri Yerleştirme](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md)  
 [İzlenecek yol: FlowLayoutPanel Kullanarak Windows Forms'da Denetimleri Düzenleme](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  
 [İzlenecek yol: TableLayoutPanel Kullanarak Windows Forms'da Denetimleri Düzenleme](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [İzlenecek yol: Doldurma, Kenar Boşlukları ve AutoSize Özelliği ile Windows Forms Denetimlerini Düzenleme](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md)

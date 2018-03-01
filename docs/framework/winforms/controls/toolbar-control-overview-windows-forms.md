---
title: "ToolBar Denetimine Genel Bakış (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ToolBar
helpviewer_keywords:
- toolbars [Windows Forms], about toolbars
- ToolBar control [Windows Forms], about ToolBar controls
ms.assetid: d426b203-0216-4dbe-b834-1641e50a9c29
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: eac54e18f397cf455ffd5fa33c2e000d87b917a0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="toolbar-control-overview-windows-forms"></a>ToolBar Denetimine Genel Bakış (Windows Forms)
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStrip> Denetimi değiştirir ve işlevlerini ekler <xref:System.Windows.Forms.ToolBar> kontrol; ancak, <xref:System.Windows.Forms.ToolBar> denetim tutulur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz.  
  
 Windows Forms <xref:System.Windows.Forms.ToolBar> denetimi formlarında bir satır aşağı açılan menüler ve komutları etkinleştirmek eşlemli düğmelerinin görüntüleyen bir denetim çubuğu kullanılır. Bu nedenle, bir araç çubuğu düğmesini tıklatarak menü komutu seçme için eşdeğer bir olabilir. Düğmeleri görünür ve pushbuttons, aşağı açılan menüler veya ayırıcı hareket etmesi için yapılandırılabilir. Genellikle, bir araç çubuğu düğmeleri ve bir uygulamanın en sık kullanılan işlevler ve komutları hızlı erişim sağlayan bir uygulamanın menü yapısı öğelere karşılık gelen menüleri içerir.  
  
## <a name="working-with-the-toolbar-control"></a>Araç çubuğu denetimiyle çalışma  
 A <xref:System.Windows.Forms.ToolBar> denetim genellikle "yerleştirilmiştir" kendi üst penceresinin üst kısmında, ancak aynı zamanda penceresinin kenarlarından yuvaya. Kullanıcı bir araç çubuğu düğmesini fare işaretçisi işaret ettiğinde bir araç ipuçlarını görüntüleyebilirsiniz. Bir araç ipucu düğmesini veya menünün amacı kısaca açıklayan küçük bir açılır penceredir. Araç ipuçları, görüntülenecek <xref:System.Windows.Forms.ToolBar.ShowToolTips%2A> özelliği ayarlanmalıdır `true`.  
  
> [!NOTE]
>  Bazı uygulamalar "uygulama pencerenin float" ve konumlandırılmasına olanağına sahip araç çubuğuna çok benzer denetimleri özelliği. Windows Forms araç çubuğu denetimi bu işlemleri mümkün değil.  
  
 Zaman <xref:System.Windows.Forms.ToolBar.Appearance%2A> özelliği ayarlanmış <xref:System.Windows.Forms.ToolBarAppearance>, yükseltilmiş ve üç boyutlu araç çubuğu düğmeleri görünür. Ayarlayabileceğiniz <xref:System.Windows.Forms.ToolBar.Appearance%2A> araç çubuğuna özelliğinin <xref:System.Windows.Forms.ToolBarAppearance> araç ve onun düğmeleri düz bir görünüm vermek için. Fare işaretçisini düz bir düğme taşındığında, düğmenin görünüm için üç boyutlu değiştirir. Araç çubuğu düğmeleri ayırıcılar kullanarak mantıksal gruplar halinde ayrılabilir. Araç çubuğu düğmesi ile bir ayırıcı olan <xref:System.Windows.Forms.ToolBarButton.Style%2A> özelliğini <xref:System.Windows.Forms.ToolBarButtonStyle>. Araç çubuğunda boş alanı olarak görünür. Araç çubuğu düz bir görünümü olduğunda, düğme ayırıcıları düğmeler arasındaki boşluk yerine satır olarak görünür.  
  
 <xref:System.Windows.Forms.ToolBar> Denetim araç çubukları ekleyerek oluşturmanıza imkan tanır <xref:System.Windows.Forms.Button> nesneleri için bir <xref:System.Windows.Forms.ToolBar.Buttons%2A> koleksiyonu. Koleksiyon Düzenleyicisi düğmelere eklemek için kullanabileceğiniz bir <xref:System.Windows.Forms.ToolBar> denetim; her <xref:System.Windows.Forms.Button> nesnesi olmalıdır metin veya atanmış, görüntünün her ikisi de atayabilmenize karşın. Görüntü sağlanan ilişkili bir tarafından [ImageList](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md) bileşeni. Çalışma zamanında ekleme veya kaldırma düğmelerden <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection> kullanarak <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection.Add%2A> ve <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection.Remove%2A> yöntemleri. Düğmelerinin programlamak için bir <xref:System.Windows.Forms.ToolBar>, kodu ekleyin <xref:System.Windows.Forms.ToolBar.ButtonClick> olayları <xref:System.Windows.Forms.ToolBar>kullanarak <xref:System.Windows.Forms.ToolBarButtonClickEventArgs.Button%2A> özelliği <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> sınıfı hangi düğmenin tıklandığını belirleme.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.ToolBar>  
 [ToolBar Denetimi](../../../../docs/framework/winforms/controls/toolbar-control-windows-forms.md)  
 [Nasıl yapılır: Bir ToolBar Denetimine Düğme Ekleme](../../../../docs/framework/winforms/controls/how-to-add-buttons-to-a-toolbar-control.md)  
 [Nasıl yapılır: ToolBar Düğmesi için Simge Tanımlama](../../../../docs/framework/winforms/controls/how-to-define-an-icon-for-a-toolbar-button.md)  
 [Nasıl yapılır: Araç Çubuğu Düğmeleri için Menü Olaylarını Tetikleme](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)

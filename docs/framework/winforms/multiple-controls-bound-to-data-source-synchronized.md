---
title: 'Nasıl yapılır: Birden çok denetimin eşitlenmiş kalmasını aynı veri kaynağına bağlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], binding multiple
- controls [Windows Forms], synchronizing with data source
ms.assetid: c2f0ecc6-11e6-4c2c-a1ca-0759630c451e
ms.openlocfilehash: c6930acb57aa3c311c76b1a2acd3bbca213d1f24
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54558897"
---
# <a name="how-to-ensure-multiple-controls-bound-to-the-same-data-source-remain-synchronized"></a>Nasıl yapılır: Birden çok denetimin eşitlenmiş kalmasını aynı veri kaynağına bağlama
Windows Forms veri bağlama ile önerilmesine çalışırken, birden çok denetim aynı veri kaynağına bağlanır. Bazı durumlarda, bağlı denetimlerin özelliklerini birbirine ve veri kaynağı ile eşitlenmiş kalmasını sağlamak için ek adımlar gerekebilir. Bu adımlar, iki durumda gereklidir:  
  
-   Veri kaynağı uygulamazsa <xref:System.ComponentModel.IBindingList>ve bu nedenle <xref:System.ComponentModel.IBindingList.ListChanged> türünde olayları <xref:System.ComponentModel.ListChangedType.ItemChanged>.  
  
-   Veri kaynağı uygulayan <xref:System.ComponentModel.IEditableObject>.  
  
 Önceki durumda kullanabileceğiniz bir <xref:System.Windows.Forms.BindingSource> denetimleri için veri kaynağına bağlamak için. İkinci durumda, kullandığınız bir <xref:System.Windows.Forms.BindingSource> ve işleme <xref:System.Windows.Forms.BindingSource.BindingComplete> olay ve arama <xref:System.Windows.Forms.BindingManagerBase.EndCurrentEdit%2A> ilişkili <xref:System.Windows.Forms.BindingManagerBase>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği üç denetimlerinin nasıl bağlanacağını gösterir; iki metin kutusu denetimi ve bir <xref:System.Windows.Forms.DataGridView> denetim — aynı sütuna bir <xref:System.Data.DataSet> kullanarak bir <xref:System.Windows.Forms.BindingSource> bileşeni. Bu örnek nasıl işleneceğini gösterir <xref:System.Windows.Forms.BindingSource.BindingComplete> olay olduğunda ek metin kutusuna bir metin kutusunun metin değeri değiştirildiğinde emin olun ve <xref:System.Windows.Forms.DataGridView> denetim doğru değeriyle güncelleştirilir.  
  
 Örnekte bir <xref:System.Windows.Forms.BindingSource> veri kaynağı ve denetimlerini bağlamak için. Alternatif olarak, denetimi doğrudan veri kaynağına bağlanır ve alma <xref:System.Windows.Forms.BindingManagerBase> formun bağlamayı için <xref:System.Windows.Forms.Control.BindingContext%2A> ve ardından işleme <xref:System.Windows.Forms.BindingManagerBase.BindingComplete> olayı <xref:System.Windows.Forms.BindingManagerBase>. Bunu yapmak nasıl bir örneği için yardım sayfasına bakın <xref:System.Windows.Forms.BindingManagerBase.BindingComplete> olayı <xref:System.Windows.Forms.BindingManagerBase>.  
  
 [!code-csharp[System.Windows.Forms.BindingSourceMultipleControls#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleControls/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingSourceMultipleControls#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleControls/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
-   Bu kod örneği gerektirir  
  
-   Başvurular <xref:System>, <xref:System.Windows.Forms>, ve <xref:System.Drawing> derlemeler.  
  
-   Bir formla <xref:System.Windows.Forms.Form.Load> işlenen olay ve çağrı `InitializeControlsAndDataSource` formun örnekten yönteminde <xref:System.Windows.Forms.Form.Load> olay işleyicisi.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: Bağlı veri BindingSource bileşenini kullanarak formlar arasında paylaşma](../../../docs/framework/winforms/controls/how-to-share-bound-data-across-forms-using-the-bindingsource-component.md)
- [Windows Forms Veri Bağlamada Bildirimi Değiştirme](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)
- [Veri Bağlama ile İlgili Arabirimler](../../../docs/framework/winforms/interfaces-related-to-data-binding.md)
- [Windows Forms Veri Bağlama](../../../docs/framework/winforms/windows-forms-data-binding.md)

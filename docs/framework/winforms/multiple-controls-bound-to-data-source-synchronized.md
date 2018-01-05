---
title: "Nasıl yapılır: Aynı Veri Kaynağına Bağlanan Birden Çok Denetimin Eşitlenmiş Kalmasını Sağlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], binding multiple
- controls [Windows Forms], synchronizing with data source
ms.assetid: c2f0ecc6-11e6-4c2c-a1ca-0759630c451e
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 227ad36e87c3deceb7fefe3cd19013fc8e76c686
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-ensure-multiple-controls-bound-to-the-same-data-source-remain-synchronized"></a>Nasıl yapılır: Aynı Veri Kaynağına Bağlanan Birden Çok Denetimin Eşitlenmiş Kalmasını Sağlama
Windows Forms veri bağlama ile görmemeleri çalışırken, birden çok denetimler aynı veri kaynağına bağlıdır. Bazı durumlarda, bağlı denetimlerin özelliklerini birbirine ve veri kaynağı ile eşitlenmiş kalmasını sağlamak için ek adımlar gerekebilir. Bu adımları iki durumlarda gereklidir:  
  
-   Veri kaynağı uygulamazsa <xref:System.ComponentModel.IBindingList>ve bu nedenle oluşturmak <xref:System.ComponentModel.IBindingList.ListChanged> türünde olayları <xref:System.ComponentModel.ListChangedType.ItemChanged>.  
  
-   Implements veri kaynağı, <xref:System.ComponentModel.IEditableObject>.  
  
 Önceki durumda kullandığınız bir <xref:System.Windows.Forms.BindingSource> denetimlere veri kaynağına bağlanamadı. İkinci durumda, kullandığınız bir <xref:System.Windows.Forms.BindingSource> ve işlemek <xref:System.Windows.Forms.BindingSource.BindingComplete> olay ve arama <xref:System.Windows.Forms.BindingManagerBase.EndCurrentEdit%2A> ilişkili üzerinde <xref:System.Windows.Forms.BindingManagerBase>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde üç denetimlerinin nasıl bağlanacağını gösterir — iki metin kutusu denetimleri ve <xref:System.Windows.Forms.DataGridView> denetim — aynı sütuna bir <xref:System.Data.DataSet> kullanarak bir <xref:System.Windows.Forms.BindingSource> bileşeni. Bu örnek nasıl işleneceğini gösterir <xref:System.Windows.Forms.BindingSource.BindingComplete> olay ve bir metin kutusunun metin değeri değiştirildiğinde, ek metin kutusunda emin olun ve <xref:System.Windows.Forms.DataGridView> denetim doğru değeriyle güncelleştirilir.  
  
 Örnek kullanan bir <xref:System.Windows.Forms.BindingSource> veri kaynağı ve denetimleri bağlamak için. Alternatif olarak, doğrudan veri kaynağına denetimler bağlama ve alma <xref:System.Windows.Forms.BindingManagerBase> formun bağlamayı için <xref:System.Windows.Forms.Control.BindingContext%2A> ve daha sonra işlemek <xref:System.Windows.Forms.BindingManagerBase.BindingComplete> olayı <xref:System.Windows.Forms.BindingManagerBase>. Bunun nasıl yapılacağı bir örneği için yardım sayfasına bakın <xref:System.Windows.Forms.BindingManagerBase.BindingComplete> olayı <xref:System.Windows.Forms.BindingManagerBase>.  
  
 [!code-csharp[System.Windows.Forms.BindingSourceMultipleControls#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleControls/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingSourceMultipleControls#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleControls/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
-   Bu kod örneği gerektirir  
  
-   Başvurular <xref:System>, <xref:System.Windows.Forms>, ve <xref:System.Drawing> derlemeler.  
  
-   Bir formla <xref:System.Windows.Forms.Form.Load> işlenen olay ve yapılan bir çağrı `InitializeControlsAndDataSource` formun örnekten yönteminde <xref:System.Windows.Forms.Form.Load> olay işleyicisi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl Yapılır: BindingSource Bileşenini Kullanarak Bağlı Verileri Formlar Arasında Paylaşma](../../../docs/framework/winforms/controls/how-to-share-bound-data-across-forms-using-the-bindingsource-component.md)  
 [Windows Forms Veri Bağlamada Bildirimi Değiştirme](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)  
 [Veri Bağlama ile İlgili Arabirimler](../../../docs/framework/winforms/interfaces-related-to-data-binding.md)  
 [Windows Forms Veri Bağlama](../../../docs/framework/winforms/windows-forms-data-binding.md)

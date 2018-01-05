---
title: "Nasıl yapılır: Mevcut Denetimleri Farklı bir Üst Öğeye Yeniden Atama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- container controls [Windows Forms], Windows Forms
- layout [Windows Forms], resizing
- layout [Windows Forms], child controls
ms.assetid: 5a5723ff-34e0-4b6f-a57b-be4ebe35cb34
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3186dcf3b1f56799709f1e1976a55288065352b6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-reassign-existing-controls-to-a-different-parent"></a>Nasıl yapılır: Mevcut Denetimleri Farklı bir Üst Öğeye Yeniden Atama
Yeni bir kapsayıcı denetiminin için formunuzda mevcut denetimleri atayabilirsiniz.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-reassign-existing-controls-to-a-different-parent"></a>Mevcut denetimleri farklı bir üst öğeye yeniden atama  
  
1.  Üç sürükleyin <xref:System.Windows.Forms.Button> gelen denetimleri **araç** forma.  
  
     Diğer yakınında olmak getirin, ancak bunları hizalanmamış bırakın.  
  
2.  İçinde **araç**, tıklatın <xref:System.Windows.Forms.FlowLayoutPanel> denetimi simgesi.  
  
     Simge form üzerine sürükleyin değil.  
  
3.  Fare işaretçisini üç yakın <xref:System.Windows.Forms.Button> kontrol eder.  
  
     Bir artı kıl ile işaretçi <xref:System.Windows.Forms.FlowLayoutPanel> bağlı denetimi simgesi.  
  
4.  ' A tıklayın ve fare düğmesini basılı tutun.  
  
5.  Özetini çizmek için fare işaretçisini sürükleyin <xref:System.Windows.Forms.FlowLayoutPanel> denetim.  
  
6.  Üç çevresinde anahat çizme <xref:System.Windows.Forms.Button> kontrol eder.  
  
7.  Fare düğmesini bırakın.  
  
     Üç <xref:System.Windows.Forms.Button> denetimleri içine şimdi eklenir <xref:System.Windows.Forms.FlowLayoutPanel> denetim.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [Windows Forms’da Denetimleri Düzenleme](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [İzlenecek yol: TableLayoutPanel Kullanarak Windows Forms'da Denetimleri Düzenleme](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [İzlenecek yol: Dayama Çizgileri Kullanarak Windows Forms'da Denetimleri Düzenleme](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)

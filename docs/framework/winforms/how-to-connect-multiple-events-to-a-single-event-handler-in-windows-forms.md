---
title: "Nasıl yapılır: Windows Forms'ta Tek Olay İşleyicisine Birden Fazla Olay Bağlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: vb
helpviewer_keywords:
- events [Windows Forms], connecting multiple to single event handler
- event handlers [Windows Forms], connecting events to
- menus [Windows Forms], event-handling methods for multiple menu items
- Windows Forms controls, events
- menu items [Windows Forms], multicasting event-handling methods
ms.assetid: 5a20749a-41b5-4acc-8eb1-9e5040b0a2c4
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bfd955b4153c7a2bc54d8b52ff1801541c3a7559
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms"></a>Nasıl yapılır: Windows Forms'ta Tek Olay İşleyicisine Birden Fazla Olay Bağlama
Uygulama tasarımınız, onu tek olay işleyicisine birden çok olaylar için kullanın veya birden çok olayları aynı yordamı gerçekleştirmek için gerekli bulabilirsiniz. Örneğin, bir güçlü zaman-formunuzda düğmesini aynı işlevselliği kullanıma durumunda olduğu gibi aynı olayını Başlat menü komutu sağlamak için koruyucu genellikle olur. Olaylar görünüm penceresinin C# veya kullanarak bunu yapabilirsiniz `Handles` anahtar sözcüğü ve **sınıf adı** ve **yöntem adı** açılan kutuları Visual Basic Kod Düzenleyicisi'nde.  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-visual-basic"></a>Visual Basic'te tek olay işleyicisine birden çok olay bağlanmak için  
  
1.  Forma sağ tıklayın ve seçin **görünümü kodu**.  
  
2.  Gelen **sınıf adı** açılan kutuyu, olay işleyicisi işlemek istediğiniz denetimleri birini seçin.  
  
3.  Gelen **yöntem adı** açılan kutusu, işlemek için olay işleyicisi istediğiniz olayları birini seçin.  
  
4.  Kod Düzenleyicisi uygun olay işleyicisi ekler ve ekleme noktasını yöntemi içindeki yerleştirir. Aşağıdaki örnek <xref:System.Windows.Forms.Control.Click> olayı <xref:System.Windows.Forms.Button> denetim.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
5.  İçin işlenen gibi diğer olaylar ekleme `Handles` yan tümcesi.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click, Button2.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
6.  Uygun kodu olay işleyicisine ekleyin.  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-c"></a>C# tek olay işleyicisine birden çok olay bağlanmak için  
  
1.  Olay işleyici bağlanmak istediğiniz denetimi seçin.  
  
2.  Özellikler penceresinde **olayları** düğmesi (![Events düğmesini](../../../docs/framework/winforms/media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow")).  
  
3.  İşlemek istediğiniz olay adına tıklayın.  
  
4.  Olay adının yanındaki değeri bölümünde ele almak istediğiniz olay yöntemi imzası eşleşen var olan olay işleyicileri listesini görüntülemek için açılan düğmesine tıklayın.  
  
5.  Uygun olay işleyicisi listeden seçin.  
  
     Kod mevcut olay işleyicisi olaya bağlamak için form eklenir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Forms'ta Olay İşleyicileri Oluşturma](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
 [Olay İşleyicilerine Genel Bakış](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md)

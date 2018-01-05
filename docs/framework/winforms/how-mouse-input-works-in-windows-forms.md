---
title: "Windows Forms'ta Fare Girdisi Nasıl Çalışır"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, mouse input
- mouse [Windows Forms], input
ms.assetid: 48fc5240-75a6-44bf-9fce-6aa21b49705a
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 388fd8d3e7f23dc55d46c5a097be99e9f1c34ab0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-mouse-input-works-in-windows-forms"></a>Windows Forms'ta Fare Girdisi Nasıl Çalışır
Teslim alma ve fare girişini işleme her Windows uygulaması önemli bir parçasıdır. Uygulamanızda bir eylemi gerçekleştirmek için fare olayları işlemek veya isabet testi gerçekleştirmek için fare konum bilgilerini veya diğer eylemleri kullanın. Ayrıca, fare girdisi uygulamanızda denetimlerinin işleme şekilde değiştirebilirsiniz. Bu konu, ayrıntı ve nasıl elde edilir ve fare sistem ayarlarını değiştirmek bu fare olayları açıklar. Fare ile sağlanan verileri hakkında daha fazla bilgi için olaylar ve fare olayları tıklatma sıranıza ortaya bkz [Windows Forms'ta fare olayları](../../../docs/framework/winforms/mouse-events-in-windows-forms.md).  
  
## <a name="mouse-location-and-hit-testing"></a>Fare konumu ve isabet testi  
 Kullanıcının fare taşındığında, işletim sistemi fare işaretçisini taşır. Fare işaretçisini işletim sistemi izler ve işaretçiyi konumu tanır etkin nokta, adlı tek bir piksel içerir. Kullanıcı fareyi taşıdığında veya fare düğmesini bastığında <xref:System.Windows.Forms.Control> içeren <xref:System.Windows.Forms.Cursor.HotSpot%2A> uygun fare olayını başlatır. Geçerli fare konumu elde edebilirsiniz <xref:System.Windows.Forms.MouseEventArgs.Location%2A> özelliği <xref:System.Windows.Forms.MouseEventArgs> fare olayını işlerken veya kullanarak <xref:System.Windows.Forms.Cursor.Position%2A> özelliği <xref:System.Windows.Forms.Cursor> sınıfı. Sonradan isabet testi gerçekleştirmek için fare konum bilgileri kullanın ve ardından fare konumuna bağlı bir eylem gerçekleştirin. İsabet testi yeteneği yerleşik birkaç Windows Forms denetimlerine gibi <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.MonthCalendar> ve <xref:System.Windows.Forms.DataGridView> kontrol eder. Uygun fare olayla kullanılan <xref:System.Windows.Forms.Control.MouseHover> Örneğin, isabet testi olduğunda, uygulamanızın belirli bir eylemi gerçekleştirmek belirlemek için çok kullanışlıdır.  
  
## <a name="mouse-events"></a>Fare olayları  
 Fare girişine yanıt vermek için birincil fare olayları işlemek için bir yoludur. Aşağıdaki tabloda, fare olayları gösterir ve ne zaman oluşturulur açıklar.  
  
|Fare olayı|Açıklama|  
|-----------------|-----------------|  
|<xref:System.Windows.Forms.Control.Click>|Fare düğmesini, genellikle önce yayımlandığında, bu olay oluşur <xref:System.Windows.Forms.Control.MouseUp> olay. Bu olay işleyicisi türünde bir bağımsız değişken alan <xref:System.EventArgs>. Sadece bir tıklatma oluştuğunda belirlemek gerektiğinde bu olayı işleyin.|  
|<xref:System.Windows.Forms.Control.MouseClick>|Bu olay, kullanıcının fareyle denetimi tıklattığında oluşur. Bu olay işleyicisi türünde bir bağımsız değişken alan <xref:System.Windows.Forms.MouseEventArgs>. Tıklama oluştuğunda fare hakkında bilgi almak gerektiğinde bu olayı işleyin.|  
|<xref:System.Windows.Forms.Control.DoubleClick>|Bu olay denetimi tıklatıldığında gerçekleşir. Bu olay işleyicisi türünde bir bağımsız değişken alan <xref:System.EventArgs>. Yalnızca bir çift oluştuğunda belirlemek gerektiğinde bu olayı işleyin.|  
|<xref:System.Windows.Forms.Control.MouseDoubleClick>|Bu olay, kullanıcının fareyle denetimi tıklattığında oluşur. Bu olay işleyicisi türünde bir bağımsız değişken alan <xref:System.Windows.Forms.MouseEventArgs>. Çift tıklatma oluştuğunda fare hakkında bilgi almak gerektiğinde bu olayı işleyin.|  
|<xref:System.Windows.Forms.Control.MouseDown>|Bu olay, fare işaretçisini üzerinde denetim olduğunda ve fare düğmesini kullanıcı oluşur. Bu olay işleyicisi türünde bir bağımsız değişken alan <xref:System.Windows.Forms.MouseEventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseEnter>|Bu olay, fare işaretçisini denetimin denetim türüne bağlı olarak kenarlık ya da istemci alanı girdiğinde oluşur. Bu olay işleyicisi türünde bir bağımsız değişken alan <xref:System.EventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseHover>|Bu olay fare işaretçisini durdurur ve denetime ye dayanıyorsa oluşur. Bu olay işleyicisi türünde bir bağımsız değişken alan <xref:System.EventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseLeave>|Bu olay, fare işaretçisini denetimin denetim türüne bağlı olarak kenarlık ya da istemci alanı çıktığında oluşur. Bu olay işleyicisi türünde bir bağımsız değişken alan <xref:System.EventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseMove>|Bu olay, bir denetime durumdayken fare işaretçisi hareket ettiğinde oluşur. Bu olay işleyicisi türünde bir bağımsız değişken alan <xref:System.Windows.Forms.MouseEventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseUp>|Bu olay, fare işaretçisini üzerinde denetim olduğunda ve kullanıcı fare düğmesini serbest oluşur. Bu olay işleyicisi türünde bir bağımsız değişken alan <xref:System.Windows.Forms.MouseEventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseWheel>|Bu olay, kullanıcı denetimi odağa sahipken fare tekerleği döndüğü oluşur. Bu olay işleyicisi türünde bir bağımsız değişken alan <xref:System.Windows.Forms.MouseEventArgs>. Kullanabileceğiniz <xref:System.Windows.Forms.MouseEventArgs.Delta%2A> özelliği <xref:System.Windows.Forms.MouseEventArgs> ne kadar fare kaydırılan belirlemek için.|  
  
## <a name="changing-mouse-input-and-detecting-system-settings"></a>Fare girişi değiştirme ve sistem ayarlarını algılama  
 Algılayabilir ve bir denetim işleme fare girdisi denetim türetme ve kullanarak şeklini değiştirme <xref:System.Windows.Forms.Control.GetStyle%2A> ve <xref:System.Windows.Forms.Control.SetStyle%2A> yöntemleri. <xref:System.Windows.Forms.Control.SetStyle%2A> Yöntemi alır Bitsel bir birleşimi <xref:System.Windows.Forms.ControlStyles> denetimi tıklatın veya çift tıklatma davranışını standart olup olmayacağını veya denetim kendi fare işleme işleyecek varsa belirlemek için değerleri. Ayrıca, <xref:System.Windows.Forms.SystemInformation> sınıfı, fare özelliklerini açıklayan ve fare işletim sistemi ile nasıl etkileşim kurduğunu belirtin özellikleri içerir. Bu özellikler aşağıdaki tabloda özetlenmiştir.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|<xref:System.Windows.Forms.SystemInformation.DoubleClickSize%2A>|Boyutlar piksel cinsinden alır, kullanıcının iki kez iki düşünmek için işletim sistemini tıklatmalısınız alanının çift tıklatma tıklar.|  
|<xref:System.Windows.Forms.SystemInformation.DoubleClickTime%2A>|En fazla ilk tıklama fare eylemi çift tıklatma dikkate alınması gereken işletim sistemi için ikinci bir tıklatma arasında geçebilecek milisaniye sayısını alır.|  
|<xref:System.Windows.Forms.SystemInformation.MouseButtons%2A>|Fare düğmeleri sayısını alır.|  
|<xref:System.Windows.Forms.SystemInformation.MouseButtonsSwapped%2A>|Sol ve sağ fare düğmeleri işlevleri takas olup olmadığını belirten bir değer alır.|  
|<xref:System.Windows.Forms.SystemInformation.MouseHoverSize%2A>|Piksel cinsinden dikdörtgenin fare işaretçisini fare vurgulu ileti oluşturulmadan önce fare vurgu süresi boyunca kalmak olan boyutlar alır.|  
|<xref:System.Windows.Forms.SystemInformation.MouseHoverTime%2A>|Zaman fare vurgulu ileti oluşturulmadan önce vurgulu dikdörtgende kalmak için fare işaretçisini sahip milisaniye cinsinden alır.|  
|<xref:System.Windows.Forms.SystemInformation.MousePresent%2A>|Fare yüklü olup olmadığını belirten bir değer alır.|  
|<xref:System.Windows.Forms.SystemInformation.MouseSpeed%2A>|Geçerli fare hızı, 1-20 belirten bir değer alır.|  
|<xref:System.Windows.Forms.SystemInformation.MouseWheelPresent%2A>|Fare tekerleği fareyle yüklü olup olmadığını belirten bir değer alır.|  
|<xref:System.Windows.Forms.SystemInformation.MouseWheelScrollDelta%2A>|Tek bir fare tekerleği döndürme artışı delta değerini miktarını alır.|  
|<xref:System.Windows.Forms.SystemInformation.MouseWheelScrollLines%2A>|Fare tekerleği döndürüldüğünde kaydırılacak satır sayısını alır.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bir Windows Forms Uygulamasında Fare Girdisi](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)  
 [Windows Forms'ta Fare Yakalama](../../../docs/framework/winforms/mouse-capture-in-windows-forms.md)  
 [Windows Forms'ta Fare İşaretçileri](../../../docs/framework/winforms/mouse-pointers-in-windows-forms.md)

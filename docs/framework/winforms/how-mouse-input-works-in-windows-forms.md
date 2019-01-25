---
title: Windows Forms'ta Fare Girdisi Nasıl Çalışır
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, mouse input
- mouse [Windows Forms], input
ms.assetid: 48fc5240-75a6-44bf-9fce-6aa21b49705a
ms.openlocfilehash: ac6cdbdb690a1e5e6693f2e5d1c5d2236a643ddb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54496013"
---
# <a name="how-mouse-input-works-in-windows-forms"></a>Windows Forms'ta Fare Girdisi Nasıl Çalışır
Alma ve fare girişi işleme Windows her uygulamanın önemli bir parçasıdır. Uygulamanızda bir eylem gerçekleştirmek için fare olayları işlemek veya isabet testi gerçekleştirmek için fare konum bilgilerini veya diğer eylemleri kullanın. Ayrıca, uygulamanızı denetimleri fare girişi işleme biçimini değiştirebilirsiniz. Bu konu, ayrıntı ve nasıl elde edilir ve fare sistem ayarlarını değiştirmek bu fare olayları açıklar. Fare ile sağlanan veriler hakkında daha fazla bilgi için olaylar ve fare olayları tıklayın sırasını oluşturulan bkz [Windows Forms'ta fare olayları](../../../docs/framework/winforms/mouse-events-in-windows-forms.md).  
  
## <a name="mouse-location-and-hit-testing"></a>Fare konumu ve isabet testi  
 Kullanıcı fareyi hareket ettirdiğinde işletim sisteminin fare işaretçisi hareket. Fare işaretçisi, işletim sistemi izler ve işaretçiyi konumu tanır etkin nokta, adlı tek bir piksel içerir. Kullanıcı fareyi hareket ya da bir fare düğmesine bastığında <xref:System.Windows.Forms.Control> içeren <xref:System.Windows.Forms.Cursor.HotSpot%2A> uygun fare olayını başlatır. Geçerli fare konumu edinebilirsiniz <xref:System.Windows.Forms.MouseEventArgs.Location%2A> özelliği <xref:System.Windows.Forms.MouseEventArgs> bir fare olayına işlenirken veya kullanarak <xref:System.Windows.Forms.Cursor.Position%2A> özelliği <xref:System.Windows.Forms.Cursor> sınıfı. Sonradan isabet testi gerçekleştirmek için fare konumu bilgileri kullanın ve ardından fareyi konumunu temel alarak bir eylem gerçekleştirin. İsabet testi özelliği yerleşik Windows Forms çeşitli denetimlere gibi <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.MonthCalendar> ve <xref:System.Windows.Forms.DataGridView> kontrol eder. Uygun fare olay ile kullanılan <xref:System.Windows.Forms.Control.MouseHover> isabet sınaması Örneğin, uygulamanızın ne zaman belirli bir eylem gerçekleştirmeniz gerekir belirlemek için çok yararlı olacaktır.  
  
## <a name="mouse-events"></a>Fare olayları  
 Fare girişine yanıt vermek için birincil fare olayları işlemek için yoludur. Aşağıdaki tabloda, fare olayları gösterir ve ne zaman gerçekleşti açıklar.  
  
|Fare olayı|Açıklama|  
|-----------------|-----------------|  
|<xref:System.Windows.Forms.Control.Click>|Bu olay, fare düğmesini, genellikle önce serbest bırakıldığında gerçekleşir <xref:System.Windows.Forms.Control.MouseUp> olay. Bu olay işleyicisi türünde bir bağımsız değişken alan <xref:System.EventArgs>. Yalnızca bir tıklama gerçekleştiğinde belirlemeye ihtiyacınız olduğunda bu olayı işleyin.|  
|<xref:System.Windows.Forms.Control.MouseClick>|Bu olay kullanıcı Denetim fare ile tıklandığında gerçekleşir. Bu olay işleyicisi türünde bir bağımsız değişken alan <xref:System.Windows.Forms.MouseEventArgs>. Bir gerçekleştiğinde farenin hakkında bilgi almak, ihtiyacınız olduğunda bu olayı işleyin.|  
|<xref:System.Windows.Forms.Control.DoubleClick>|Bu olay, denetime çift tıklandığında gerçekleşir. Bu olay işleyicisi türünde bir bağımsız değişken alan <xref:System.EventArgs>. Yalnızca bir çift gerçekleştiğinde belirlemeye ihtiyacınız olduğunda bu olayı işleyin.|  
|<xref:System.Windows.Forms.Control.MouseDoubleClick>|Bu olay kullanıcı fare ile denetimi tıklattığında oluşur. Bu olay işleyicisi türünde bir bağımsız değişken alan <xref:System.Windows.Forms.MouseEventArgs>. Çift tıklama gerçekleştiğinde farenin hakkında bilgi almak, ihtiyacınız olduğunda bu olayı işleyin.|  
|<xref:System.Windows.Forms.Control.MouseDown>|Fare işaretçisi denetimin üzerindeyse ve bir fare düğmesi kullanıcı bu olayı oluşur. Bu olay işleyicisi türünde bir bağımsız değişken alan <xref:System.Windows.Forms.MouseEventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseEnter>|Bu olay, fare işaretçisini denetim türüne bağlı olarak bir denetimin kenarlık ya da istemci alanını girdiğinde gerçekleşir. Bu olay işleyicisi türünde bir bağımsız değişken alan <xref:System.EventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseHover>|Fare işaretçisi durdurur ve denetimin üzerine'ye dayanıyorsa bu olayı oluşur. Bu olay işleyicisi türünde bir bağımsız değişken alan <xref:System.EventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseLeave>|Bu olay, fare işaretçisini denetim türüne bağlı olarak bir denetimin kenarlık ya da istemci alanından ayrılırken oluşur. Bu olay işleyicisi türünde bir bağımsız değişken alan <xref:System.EventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseMove>|Bu olay, bir denetimin üzerine üzerindeyken fare işaretçisi hareket ettirildiğinde gerçekleşir. Bu olay işleyicisi türünde bir bağımsız değişken alan <xref:System.Windows.Forms.MouseEventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseUp>|Fare işaretçisi denetimin üzerindeyse ve kullanıcının fare düğmesini bıraktığında bu olayı oluşur. Bu olay işleyicisi türünde bir bağımsız değişken alan <xref:System.Windows.Forms.MouseEventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseWheel>|Bu olay, Denetim odağı alırken kullanıcı fare tekerleğini döndürdüğünde gerçekleşir. Bu olay işleyicisi türünde bir bağımsız değişken alan <xref:System.Windows.Forms.MouseEventArgs>. Kullanabileceğiniz <xref:System.Windows.Forms.MouseEventArgs.Delta%2A> özelliği <xref:System.Windows.Forms.MouseEventArgs> ne kadar fare kaydırılan belirlemek için.|  
  
## <a name="changing-mouse-input-and-detecting-system-settings"></a>Fare girişi değiştirme ve sistem ayarlarını algılama  
 Algılayabilir ve denetim türetme ve kullanarak bir denetim işleme fare girişi değiştirecek <xref:System.Windows.Forms.Control.GetStyle%2A> ve <xref:System.Windows.Forms.Control.SetStyle%2A> yöntemleri. <xref:System.Windows.Forms.Control.SetStyle%2A> Yöntemi alır Bitsel bir birleşimi <xref:System.Windows.Forms.ControlStyles> denetime tıklayın veya davranış çift standart olup olmayacağını veya denetimin bir fare işleme işleyecek belirlemek için değerler. Ayrıca, <xref:System.Windows.Forms.SystemInformation> sınıfı fare yeteneklerini açıklar ve fare işletim sistemi ile nasıl etkileşim kurduğunu belirtin özellikleri içerir. Bu özellikler aşağıdaki tabloda özetlenmiştir.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|<xref:System.Windows.Forms.SystemInformation.DoubleClickSize%2A>|Boyutları piksel cinsinden alır, kullanıcının iki kez iki göz önünde bulundurmanız için işletim sistemini tıklatmalısınız alanının çift tıklar.|  
|<xref:System.Windows.Forms.SystemInformation.DoubleClickTime%2A>|İlk tıklama ve ikinci tıklama fare eylemi çift dikkate alınması gereken işletim sistemi için arasında geçebilecek milisaniye sayısını alır.|  
|<xref:System.Windows.Forms.SystemInformation.MouseButtons%2A>|Düğme sayısı üzerinde fareyi alır.|  
|<xref:System.Windows.Forms.SystemInformation.MouseButtonsSwapped%2A>|Sol ve sağ fare düğmesi işlevleri takas olup olmadığını belirten bir değer alır.|  
|<xref:System.Windows.Forms.SystemInformation.MouseHoverSize%2A>|Boyutları, içinde bir fare üzerine gelindiğinde kullanılacak ileti oluşturulmadan önce fare vurgu süresi boyunca kalmak fare işaretçisi olan dikdörtgenin piksel cinsinden alır.|  
|<xref:System.Windows.Forms.SystemInformation.MouseHoverTime%2A>|Saati, fare işaretçisini bir fare üzerine gelindiğinde kullanılacak ileti oluşturulmadan önce vurgulu dikdörtgen içinde kalmak için olan milisaniye cinsinden alır.|  
|<xref:System.Windows.Forms.SystemInformation.MousePresent%2A>|Fare yüklü olup olmadığını belirten bir değer alır.|  
|<xref:System.Windows.Forms.SystemInformation.MouseSpeed%2A>|1 ila 20 arasında geçerli fare hızını belirten bir değer alır.|  
|<xref:System.Windows.Forms.SystemInformation.MouseWheelPresent%2A>|Fare tekerleği olan bir fareniz yüklü olup olmadığını belirten bir değer alır.|  
|<xref:System.Windows.Forms.SystemInformation.MouseWheelScrollDelta%2A>|Tek bir fare tekerleği döndürme artırma delta değerini miktarını alır.|  
|<xref:System.Windows.Forms.SystemInformation.MouseWheelScrollLines%2A>|Fare tekerleği döndürüldüğünde satır sayısını alır.|  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Bir Windows Forms Uygulamasında Fare Girdisi](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)
- [Windows Forms'ta Fare Yakalama](../../../docs/framework/winforms/mouse-capture-in-windows-forms.md)
- [Windows Forms'ta Fare İşaretçileri](../../../docs/framework/winforms/mouse-pointers-in-windows-forms.md)

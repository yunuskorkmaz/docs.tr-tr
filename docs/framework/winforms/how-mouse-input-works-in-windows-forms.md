---
title: Fare girişinin nasıl çalıştığı
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, mouse input
- mouse [Windows Forms], input
ms.assetid: 48fc5240-75a6-44bf-9fce-6aa21b49705a
ms.openlocfilehash: 1164974e65ca1e96c0650569626ad4140baf004e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739629"
---
# <a name="how-mouse-input-works-in-windows-forms"></a>Windows Forms'ta Fare Girdisi Nasıl Çalışır
Fare girişini alma ve işleme, her Windows uygulamasının önemli bir parçasıdır. Uygulamanızda bir eylem gerçekleştirmek için fare olaylarını işleyebilir veya isabet testi veya başka eylemler gerçekleştirmek için fare konum bilgilerini kullanabilirsiniz. Ayrıca, uygulamanızdaki denetimlerin fare girişini işleme şeklini değiştirebilirsiniz. Bu konu, bu fare olaylarını ayrıntılı olarak ve fare için sistem ayarlarının nasıl alınacağını ve değiştirileceğini açıklamaktadır. Fare olayları ve fare tıklaması olaylarının oluşturulduğu sırada verilen veriler hakkında daha fazla bilgi için [Windows Forms fare olayları](mouse-events-in-windows-forms.md)bölümüne bakın.  
  
## <a name="mouse-location-and-hit-testing"></a>Fare konumu ve Isabet testi  
 Kullanıcı fareyi taşırken, işletim sistemi fare işaretçisini taşıdıkça. Fare işaretçisi, işletim sisteminin işaretçinin konumu olarak izlediği ve tanıdığı etkin nokta olarak adlandırılan tek bir piksel içerir. Kullanıcı fareyi taşırken veya bir fare düğmesine bastığında, <xref:System.Windows.Forms.Cursor.HotSpot%2A> içeren <xref:System.Windows.Forms.Control> uygun fare olayını oluşturur. Bir fare olayını işlerken veya <xref:System.Windows.Forms.Cursor> sınıfının <xref:System.Windows.Forms.Cursor.Position%2A> özelliğini kullanarak, geçerli fare konumunu <xref:System.Windows.Forms.MouseEventArgs> <xref:System.Windows.Forms.MouseEventArgs.Location%2A> özelliği ile elde edebilirsiniz. Daha sonra fare konum bilgilerini kullanarak isabet testi gerçekleştirebilir ve ardından fare konumunu temel alarak bir eylem gerçekleştirebilirsiniz. İsabet testi özelliği, Windows Forms <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.MonthCalendar> ve <xref:System.Windows.Forms.DataGridView> denetimleri gibi çeşitli denetimlere yerleşik olarak bulunur. Uygun fare olayı ile kullanılan <xref:System.Windows.Forms.Control.MouseHover> Örneğin, isabet testi, uygulamanızın belirli bir eylemi ne zaman gerçekleştirmesi gerektiğini belirlemek için çok yararlıdır.  
  
## <a name="mouse-events"></a>Fare olayları  
 Fare girişini cevaplamanıza yönelik birincil yol fare olaylarını idare kullanmaktır. Aşağıdaki tablo, fare olaylarını gösterir ve ne zaman gerçekleştiğini açıklar.  
  
|Fare olayı|Açıklama|  
|-----------------|-----------------|  
|<xref:System.Windows.Forms.Control.Click>|Bu olay, genellikle <xref:System.Windows.Forms.Control.MouseUp> olayından önce fare düğmesi bırakıldığında oluşur. Bu olay için işleyici <xref:System.EventArgs>türünde bir bağımsız değişken alır. Yalnızca bir tıklama işleminin ne zaman gerçekleşeceğini belirlemeniz gerektiğinde bu olayı işleyin.|  
|<xref:System.Windows.Forms.Control.MouseClick>|Bu olay, Kullanıcı fare ile denetime tıkladığında oluşur. Bu olay için işleyici <xref:System.Windows.Forms.MouseEventArgs>türünde bir bağımsız değişken alır. Tıklama gerçekleştiğinde fare hakkında bilgi almanız gerektiğinde bu olayı işleyin.|  
|<xref:System.Windows.Forms.Control.DoubleClick>|Bu olay, denetim çift tıklandığında oluşur. Bu olay için işleyici <xref:System.EventArgs>türünde bir bağımsız değişken alır. Yalnızca çift tıklama işleminin ne zaman gerçekleşeceğini belirlemeniz gerektiğinde bu olayı işleyin.|  
|<xref:System.Windows.Forms.Control.MouseDoubleClick>|Bu olay, Kullanıcı denetimi fareyle çift tıkladığında oluşur. Bu olay için işleyici <xref:System.Windows.Forms.MouseEventArgs>türünde bir bağımsız değişken alır. Çift tıklama gerçekleştiğinde fare hakkında bilgi almanız gerektiğinde bu olayı işleyin.|  
|<xref:System.Windows.Forms.Control.MouseDown>|Bu olay fare işaretçisi denetimin üzerindeyken ve Kullanıcı bir fare düğmesine bastığında oluşur. Bu olay için işleyici <xref:System.Windows.Forms.MouseEventArgs>türünde bir bağımsız değişken alır.|  
|<xref:System.Windows.Forms.Control.MouseEnter>|Bu olay, fare işaretçisi denetimin türüne göre denetimin kenarlığını veya istemci alanını girdiğinde oluşur. Bu olay için işleyici <xref:System.EventArgs>türünde bir bağımsız değişken alır.|  
|<xref:System.Windows.Forms.Control.MouseHover>|Bu olay fare işaretçisi durduğunda ve denetimin üzerine getirildiğinde oluşur. Bu olay için işleyici <xref:System.EventArgs>türünde bir bağımsız değişken alır.|  
|<xref:System.Windows.Forms.Control.MouseLeave>|Bu olay, denetimin türüne bağlı olarak, fare işaretçisi denetimin kenarlığını veya istemci alanından çıktığında oluşur. Bu olay için işleyici <xref:System.EventArgs>türünde bir bağımsız değişken alır.|  
|<xref:System.Windows.Forms.Control.MouseMove>|Bu olay, fare işaretçisi bir denetim üzerindeyken ne zaman taşırken oluşur. Bu olay için işleyici <xref:System.Windows.Forms.MouseEventArgs>türünde bir bağımsız değişken alır.|  
|<xref:System.Windows.Forms.Control.MouseUp>|Bu olay fare işaretçisi denetimin üzerindeyken ve Kullanıcı bir fare düğmesini bıraktığında oluşur. Bu olay için işleyici <xref:System.Windows.Forms.MouseEventArgs>türünde bir bağımsız değişken alır.|  
|<xref:System.Windows.Forms.Control.MouseWheel>|Bu olay, Denetim odaklanmışken Kullanıcı fare tekerleğini döndürdüğünde oluşur. Bu olay için işleyici <xref:System.Windows.Forms.MouseEventArgs>türünde bir bağımsız değişken alır. Farenin ne kadar kaydırılabileceğini anlamak için <xref:System.Windows.Forms.MouseEventArgs> <xref:System.Windows.Forms.MouseEventArgs.Delta%2A> özelliğini kullanabilirsiniz.|  
  
## <a name="changing-mouse-input-and-detecting-system-settings"></a>Fare girişini değiştirme ve sistem ayarlarını algılama  
 Denetimden türeterek ve <xref:System.Windows.Forms.Control.GetStyle%2A> ve <xref:System.Windows.Forms.Control.SetStyle%2A> yöntemlerini kullanarak bir denetimin fare girişini nasıl işleyeceğini tespit edebilir ve değiştirebilirsiniz. <xref:System.Windows.Forms.Control.SetStyle%2A> yöntemi, denetimin standart tıklama veya çift tıklama davranışına sahip olup olmayacağını veya denetimin kendi fare işlemesini işleyeceğini tespit etmek için <xref:System.Windows.Forms.ControlStyles> değerlerinin bit tabanlı birleşimini alır. Ayrıca, <xref:System.Windows.Forms.SystemInformation> sınıfı, farenin yeteneklerini tanımlayan ve farenin işletim sistemiyle nasıl etkileşime gireceğini belirten özellikler içerir. Aşağıdaki tabloda bu özellikler özetlenmektedir.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|<xref:System.Windows.Forms.SystemInformation.DoubleClickSize%2A>|Bir çift tıklamada, kullanıcının işletim sistemi için iki kez tıklayacağı alanın piksel cinsinden boyutlarını alır.|  
|<xref:System.Windows.Forms.SystemInformation.DoubleClickTime%2A>|İlk tıklama arasında geçebilecek en fazla milisaniye sayısını alır ve bir kez fare eylemini bir çift tıklaması için işletim sisteminin ikinci tıklamasını kullanın.|  
|<xref:System.Windows.Forms.SystemInformation.MouseButtons%2A>|Fare üzerindeki düğmelerin sayısını alır.|  
|<xref:System.Windows.Forms.SystemInformation.MouseButtonsSwapped%2A>|Sol ve sağ fare düğmelerinin işlevlerinin takas edilip edilmeyeceğini gösteren bir değer alır.|  
|<xref:System.Windows.Forms.SystemInformation.MouseHoverSize%2A>|Fare işaretçisinin, fare işaretçisi iletisi oluşturulmadan önce fare işaretçisi süresi boyunca kalması gereken dikdörtgenin piksel cinsinden boyutlarını alır.|  
|<xref:System.Windows.Forms.SystemInformation.MouseHoverTime%2A>|Fare işaretçisinin, fare işaretçisi iletisi oluşturulmadan önce üzerine gelme dikdörtgeninde kalması gereken süreyi milisaniye cinsinden alır.|  
|<xref:System.Windows.Forms.SystemInformation.MousePresent%2A>|Bir farenin yüklü olup olmadığını gösteren bir değer alır.|  
|<xref:System.Windows.Forms.SystemInformation.MouseSpeed%2A>|Geçerli fare hızını belirten, 1 ile 20 arasında bir değer alır.|  
|<xref:System.Windows.Forms.SystemInformation.MouseWheelPresent%2A>|Fare tekerleği içeren bir farenin yüklü olup olmadığını gösteren bir değer alır.|  
|<xref:System.Windows.Forms.SystemInformation.MouseWheelScrollDelta%2A>|Tek bir fare tekerleği dönüşünün artımına ilişkin Delta değeri miktarını alır.|  
|<xref:System.Windows.Forms.SystemInformation.MouseWheelScrollLines%2A>|Fare tekerleği döndürüldüğünde kaydırılan satır sayısını alır.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bir Windows Forms Uygulamasında Fare Girdisi](mouse-input-in-a-windows-forms-application.md)
- [Windows Forms'ta Fare Yakalama](mouse-capture-in-windows-forms.md)
- [Windows Forms'ta Fare İşaretçileri](mouse-pointers-in-windows-forms.md)

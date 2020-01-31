---
title: Fare olayları
ms.date: 03/30/2017
helpviewer_keywords:
- MouseLeave event [Windows Forms]
- events [Windows Forms], mouse
- Click event [Windows Forms], raising order
- Windows Forms controls, click events
- MouseDoubleClick event [Windows Forms]
- MouseEnter event [Windows Forms]
- MouseHover event [Windows Forms]
- MouseDown event [Windows Forms]
- MouseClick event [Windows Forms]
- MouseMove event [Windows Forms]
- mouse [Windows Forms], events
- MouseUp event
ms.assetid: 8cf0070d-793b-4876-b09e-d20d28280fab
ms.openlocfilehash: 4909f56fc3935848fd18bc35c1cb56b5407a24c8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740968"
---
# <a name="mouse-events-in-windows-forms"></a>Windows Forms'ta Fare Olayları

Fare girişini işlerken, genellikle fare işaretçisinin konumunu ve fare düğmelerinin durumunu bilmek istersiniz. Bu konu, fare olaylarından bu bilgilerin nasıl alınacağı hakkında ayrıntılar sağlar ve Windows Forms Denetimlerinde fare tıklaması olaylarının nasıl oluşturulduğu sırasını açıklar. Tüm fare olaylarının listesi ve açıklaması için bkz. [fare girişinin Windows Forms nasıl çalıştığı](how-mouse-input-works-in-windows-forms.md).  Ayrıca bkz. [olay Işleyicilerine genel bakış (Windows Forms)](event-handlers-overview-windows-forms.md) ve [olaylara genel bakış (Windows Forms)](events-overview-windows-forms.md).

## <a name="mouse-information"></a>Fare bilgileri

Bir <xref:System.Windows.Forms.MouseEventArgs> fare düğmesine tıklanması ve fare hareketlerini izlemek için ilgili fare olaylarının işleyicilerine gönderilir. <xref:System.Windows.Forms.MouseEventArgs>, fare işaretçisinin, istemci koordinatlarındaki fare işaretçisi konumu, hangi fare düğmelerine basıldığı ve Fare tekerleğinin kaydırılışına dahil olmak üzere geçerli durumu hakkında bilgi sağlar. Yalnızca fare işaretçisi bir denetimin sınırları girildiğinde veya sol tarafta bilgilendirenler gibi birçok fare olayı, daha fazla bilgi olmadan olay işleyicisine <xref:System.EventArgs> gönderin.

Fare düğmelerinin geçerli durumunu veya fare işaretçisinin konumunu biliyorsanız ve bir fare olayını işlemeyi önlemek istiyorsanız, <xref:System.Windows.Forms.Control> sınıfının <xref:System.Windows.Forms.Control.MouseButtons%2A> ve <xref:System.Windows.Forms.Control.MousePosition%2A> özelliklerini de kullanabilirsiniz. <xref:System.Windows.Forms.Control.MouseButtons%2A>, şu anda basılan fare düğmelerine ilişkin bilgileri döndürür. <xref:System.Windows.Forms.Control.MousePosition%2A>, fare işaretçisinin ekran koordinatlarını döndürür ve <xref:System.Windows.Forms.Cursor.Position%2A>tarafından döndürülen değere eşdeğerdir.

## <a name="converting-between-screen-and-client-coordinates"></a>Ekran ve Istemci koordinatları arasında dönüştürme

Bazı fare konum bilgileri istemci koordinatlarındaki ve bazıları ekran koordinatlarından olduğundan, bir noktayı bir koordinat sisteminden diğerine dönüştürmeniz gerekebilir. Bunu, <xref:System.Windows.Forms.Control> sınıfında bulunan <xref:System.Windows.Forms.Control.PointToClient%2A> ve <xref:System.Windows.Forms.Control.PointToScreen%2A> yöntemlerini kullanarak kolayca yapabilirsiniz.

## <a name="standard-click-event-behavior"></a>Standart tıklama olayı davranışı

Fare tıklaması olaylarını uygun sırada işlemek istiyorsanız, Windows Forms Denetimlerinde tıklama olaylarının nasıl oluşturulduğu sırayı bilmeniz gerekir. Tüm Windows Forms denetimleri, bir fare düğmesine basıldığında ve serbest bırakıldığında (hangi fare düğmesinden bağımsız olarak), her bir denetim için aşağıdaki listede belirtilenler dışında, tıklama olaylarını aynı sırada yükseltir. Aşağıdaki listede, tek bir fare düğmesine tıklama için oluşturulan olayların sırası gösterilmektedir:

1. <xref:System.Windows.Forms.Control.MouseDown> olayı.

2. <xref:System.Windows.Forms.Control.Click> olayı.

3. <xref:System.Windows.Forms.Control.MouseClick> olayı.

4. <xref:System.Windows.Forms.Control.MouseUp> olayı.

Bir çift fare düğmesi için oluşturulan olayların sırası aşağıda verilmiştir:

1. <xref:System.Windows.Forms.Control.MouseDown> olayı.

2. <xref:System.Windows.Forms.Control.Click> olayı.

3. <xref:System.Windows.Forms.Control.MouseClick> olayı.

4. <xref:System.Windows.Forms.Control.MouseUp> olayı.

5. <xref:System.Windows.Forms.Control.MouseDown> olayı.

6. <xref:System.Windows.Forms.Control.DoubleClick> olayı. (Bu, söz konusu denetimin <xref:System.Windows.Forms.ControlStyles.StandardDoubleClick> stil biti `true`olarak ayarlanmış olmasına bağlı olarak farklılık gösterebilir. <xref:System.Windows.Forms.ControlStyles> bitini ayarlama hakkında daha fazla bilgi için <xref:System.Windows.Forms.Control.SetStyle%2A> yöntemine bakın.)

7. <xref:System.Windows.Forms.Control.MouseDoubleClick> olayı.

8. <xref:System.Windows.Forms.Control.MouseUp> olayı.

Fare tıklama olaylarının sırasını gösteren bir kod örneği için bkz. [nasıl yapılır: Windows Forms Denetimlerinde Kullanıcı giriş olaylarını işleme](how-to-handle-user-input-events-in-windows-forms-controls.md).

### <a name="individual-controls"></a>Bireysel denetimler

Aşağıdaki denetimler standart fare tıklaması olay davranışına uymuyor:

- <xref:System.Windows.Forms.Button>
- <xref:System.Windows.Forms.CheckBox>
- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.RadioButton>

  > [!NOTE]
  > <xref:System.Windows.Forms.ComboBox> denetimi için, Kullanıcı düzenleme alanına, düğmeye veya listedeki bir öğeye tıkladığında daha sonra ayrıntılı olay davranışı oluşur.

  - Sol tıklama: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>

  - Sağ tıklama: hiçbir tıklama olayı tetiklendi

  - Sol çift tıklama: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>

  - Sağ çift tıklama: hiçbir tıklama olayı tetiklendi

- <xref:System.Windows.Forms.TextBox>, <xref:System.Windows.Forms.RichTextBox>, <xref:System.Windows.Forms.ListBox>, <xref:System.Windows.Forms.MaskedTextBox>ve <xref:System.Windows.Forms.CheckedListBox> denetimleri

  > [!NOTE]
  > Daha sonra ayrıntılı olay davranışı Kullanıcı bu denetimlerin içinde herhangi bir yere tıkladığında oluşur.

  - Sol tıklama: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>

  - Sağ tıklama: hiçbir tıklama olayı tetiklendi

  - Sol çift tıklama: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>, <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick>

  - Sağ çift tıklama: hiçbir tıklama olayı tetiklendi

- <xref:System.Windows.Forms.ListView> denetimi

  > [!NOTE]
  > Daha sonra ayrıntılı olay davranışı yalnızca Kullanıcı <xref:System.Windows.Forms.ListView> denetimindeki öğelere tıkladığında gerçekleşir. Denetimde başka herhangi bir yere tıklama için hiçbir olay oluşturulmaz. Daha sonra açıklanan olaylara ek olarak, <xref:System.Windows.Forms.ListView> denetimiyle doğrulamayı kullanmak istiyorsanız sizi ilgilendiren <xref:System.Windows.Forms.ListView.BeforeLabelEdit> ve <xref:System.Windows.Forms.ListView.AfterLabelEdit> olayları vardır.

  - Sol tıklama: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>

  - Sağ tıklayın: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>

  - Sol çift tıklama: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick>

  - Sağ çift tıklama: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick>

- <xref:System.Windows.Forms.TreeView> denetimi

  > [!NOTE]
  > Daha sonra ayrıntılı olay davranışı yalnızca Kullanıcı öğelerin kendilerini tıkladığı veya <xref:System.Windows.Forms.TreeView> denetimindeki öğelerin sağında oluşur. Denetimde başka herhangi bir yere tıklama için hiçbir olay oluşturulmaz. Daha sonra açıklananlara ek olarak, <xref:System.Windows.Forms.TreeView.BeforeCheck>, <xref:System.Windows.Forms.TreeView.BeforeSelect>, <xref:System.Windows.Forms.TreeView.BeforeLabelEdit>, <xref:System.Windows.Forms.TreeView.AfterSelect>, <xref:System.Windows.Forms.TreeView.AfterCheck>ve <xref:System.Windows.Forms.TreeView.AfterLabelEdit> olayları vardır. Bu, <xref:System.Windows.Forms.TreeView> denetimiyle doğrulamayı kullanmak istiyorsanız ilginizi çeken olabilir.

  - Sol tıklama: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>

  - Sağ tıklayın: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>

  - Sol çift tıklama: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick>

  - Sağ çift tıklama: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick>

### <a name="painting-behavior-of-toggle-controls"></a>İki durumlu denetimlerin boyama davranışı

<xref:System.Windows.Forms.ButtonBase> sınıfından türetilen denetimler gibi geçiş denetimleri, fare tıklama olayları ile birlikte aşağıdaki farklı boyama davranışına sahiptir:

1. Kullanıcı fare düğmesine basar.

2. Denetim, basılan durumu boyar.

3. <xref:System.Windows.Forms.Control.MouseDown> olay tetiklenir.

4. Kullanıcı fare düğmesini serbest bırakır.

5. Denetim, oluşturulan durumu boyar.

6. <xref:System.Windows.Forms.Control.Click> olay tetiklenir.

7. <xref:System.Windows.Forms.Control.MouseClick> olay tetiklenir.

8. <xref:System.Windows.Forms.Control.MouseUp> olay tetiklenir.

    > [!NOTE]
    > Fare düğmesi kapalıyken Kullanıcı işaretçiyi geçiş denetiminin dışına taşımışsa (örneğin, basıldığında fareyi <xref:System.Windows.Forms.Button> denetimin dışına taşımak gibi), iki durumlu denetim, kabarık durumunda boyama yapar ve yalnızca <xref:System.Windows.Forms.Control.MouseUp> olay oluşur. <xref:System.Windows.Forms.Control.Click> veya <xref:System.Windows.Forms.Control.MouseClick> olayları bu durumda gerçekleşmeyecektir.

## <a name="see-also"></a>Ayrıca bkz.

- [Bir Windows Forms Uygulamasında Fare Girdisi](mouse-input-in-a-windows-forms-application.md)

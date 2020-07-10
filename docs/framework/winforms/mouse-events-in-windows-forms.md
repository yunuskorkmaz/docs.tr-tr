---
title: Fare olayları
description: Fare olaylarının fare konumunu nasıl alabileceğinizi öğrenin ve Windows Forms Denetimlerinde fare tıklaması olaylarının hangi sırayla yapıldığını anlayın.
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
ms.openlocfilehash: 640448109961ea5fdf3600ef9e72d7d10e8c9e49
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174386"
---
# <a name="mouse-events-in-windows-forms"></a>Windows Forms'ta Fare Olayları

Fare girişini işlerken, genellikle fare işaretçisinin konumunu ve fare düğmelerinin durumunu bilmek istersiniz. Bu konu, fare olaylarından bu bilgilerin nasıl alınacağı hakkında ayrıntılar sağlar ve Windows Forms Denetimlerinde fare tıklaması olaylarının nasıl oluşturulduğu sırasını açıklar. Tüm fare olaylarının listesi ve açıklaması için bkz. [fare girişinin Windows Forms nasıl çalıştığı](how-mouse-input-works-in-windows-forms.md).  Ayrıca bkz. [olay Işleyicilerine genel bakış (Windows Forms)](event-handlers-overview-windows-forms.md) ve [olaylara genel bakış (Windows Forms)](events-overview-windows-forms.md).

## <a name="mouse-information"></a>Fare bilgileri

Bir <xref:System.Windows.Forms.MouseEventArgs> fare düğmesine tıklanması ve fare hareketlerini izlemek için ilgili fare olaylarının işleyicilerine gönderilir. <xref:System.Windows.Forms.MouseEventArgs>istemci koordinatlarındaki fare işaretçisinin konumu, fare düğmelerine basılan ve Fare tekerleğinin kaydırılışına dahil olmak üzere, farenin geçerli durumu hakkında bilgi sağlar. Yalnızca fare işaretçisi bir denetimin sınırları girildiğinde veya sol tarafta bilgilendirenler gibi birçok fare olayı, <xref:System.EventArgs> daha fazla bilgi olmadan olay işleyicisine gönderin.

Fare düğmelerinin geçerli durumunu veya fare işaretçisinin konumunu biliyorsanız ve bir fare olayını işlemeyi önlemek istiyorsanız, <xref:System.Windows.Forms.Control.MouseButtons%2A> sınıfının ve özelliklerini de kullanabilirsiniz <xref:System.Windows.Forms.Control.MousePosition%2A> <xref:System.Windows.Forms.Control> . <xref:System.Windows.Forms.Control.MouseButtons%2A>Şu anda basılan fare düğmelerine ilişkin bilgileri döndürür. , <xref:System.Windows.Forms.Control.MousePosition%2A> Fare işaretçisinin ekran koordinatlarını döndürür ve tarafından döndürülen değere eşdeğerdir <xref:System.Windows.Forms.Cursor.Position%2A> .

## <a name="converting-between-screen-and-client-coordinates"></a>Ekran ve Istemci koordinatları arasında dönüştürme

Bazı fare konum bilgileri istemci koordinatlarındaki ve bazıları ekran koordinatlarından olduğundan, bir noktayı bir koordinat sisteminden diğerine dönüştürmeniz gerekebilir. <xref:System.Windows.Forms.Control.PointToClient%2A> <xref:System.Windows.Forms.Control.PointToScreen%2A> Sınıfı üzerinde kullanılabilen ve yöntemlerini kullanarak bunu kolayca yapabilirsiniz <xref:System.Windows.Forms.Control> .

## <a name="standard-click-event-behavior"></a>Standart tıklama olayı davranışı

Fare tıklaması olaylarını uygun sırada işlemek istiyorsanız, Windows Forms Denetimlerinde tıklama olaylarının nasıl oluşturulduğu sırayı bilmeniz gerekir. Tüm Windows Forms denetimleri, bir fare düğmesine basıldığında ve serbest bırakıldığında (hangi fare düğmesinden bağımsız olarak), her bir denetim için aşağıdaki listede belirtilenler dışında, tıklama olaylarını aynı sırada yükseltir. Aşağıdaki listede, tek bir fare düğmesine tıklama için oluşturulan olayların sırası gösterilmektedir:

1. <xref:System.Windows.Forms.Control.MouseDown>olay.

2. <xref:System.Windows.Forms.Control.Click>olay.

3. <xref:System.Windows.Forms.Control.MouseClick>olay.

4. <xref:System.Windows.Forms.Control.MouseUp>olay.

Bir çift fare düğmesi için oluşturulan olayların sırası aşağıda verilmiştir:

1. <xref:System.Windows.Forms.Control.MouseDown>olay.

2. <xref:System.Windows.Forms.Control.Click>olay.

3. <xref:System.Windows.Forms.Control.MouseClick>olay.

4. <xref:System.Windows.Forms.Control.MouseUp>olay.

5. <xref:System.Windows.Forms.Control.MouseDown>olay.

6. <xref:System.Windows.Forms.Control.DoubleClick>olay. (Bu, söz konusu denetimin <xref:System.Windows.Forms.ControlStyles.StandardDoubleClick> Stil biti olarak ayarlanmış olmasına bağlı olarak farklılık gösterebilir `true` . Bit ayarlama hakkında daha fazla bilgi için <xref:System.Windows.Forms.ControlStyles> <xref:System.Windows.Forms.Control.SetStyle%2A> yöntemine bakın.)

7. <xref:System.Windows.Forms.Control.MouseDoubleClick>olay.

8. <xref:System.Windows.Forms.Control.MouseUp>olay.

Fare tıklama olaylarının sırasını gösteren bir kod örneği için bkz. [nasıl yapılır: Windows Forms Denetimlerinde Kullanıcı giriş olaylarını işleme](how-to-handle-user-input-events-in-windows-forms-controls.md).

### <a name="individual-controls"></a>Bireysel denetimler

Aşağıdaki denetimler standart fare tıklaması olay davranışına uymuyor:

- <xref:System.Windows.Forms.Button>
- <xref:System.Windows.Forms.CheckBox>
- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.RadioButton>

  > [!NOTE]
  > Denetim için <xref:System.Windows.Forms.ComboBox> , Kullanıcı düzenleme alanına, düğmeye veya listedeki bir öğeye tıkladığında daha sonra ayrıntılı olay davranışı oluşur.

  - Sol tıklama: <xref:System.Windows.Forms.Control.Click> ,<xref:System.Windows.Forms.Control.MouseClick>

  - Sağ tıklama: hiçbir tıklama olayı tetiklendi

  - Sol çift tıklama: <xref:System.Windows.Forms.Control.Click> , <xref:System.Windows.Forms.Control.MouseClick> ; <xref:System.Windows.Forms.Control.Click> ,<xref:System.Windows.Forms.Control.MouseClick>

  - Sağ çift tıklama: hiçbir tıklama olayı tetiklendi

- <xref:System.Windows.Forms.TextBox>, <xref:System.Windows.Forms.RichTextBox> , <xref:System.Windows.Forms.ListBox> , <xref:System.Windows.Forms.MaskedTextBox> ve <xref:System.Windows.Forms.CheckedListBox> denetimleri

  > [!NOTE]
  > Daha sonra ayrıntılı olay davranışı Kullanıcı bu denetimlerin içinde herhangi bir yere tıkladığında oluşur.

  - Sol tıklama: <xref:System.Windows.Forms.Control.Click> ,<xref:System.Windows.Forms.Control.MouseClick>

  - Sağ tıklama: hiçbir tıklama olayı tetiklendi

  - Sol çift tıklama: <xref:System.Windows.Forms.Control.Click> , <xref:System.Windows.Forms.Control.MouseClick> , <xref:System.Windows.Forms.Control.DoubleClick> ,<xref:System.Windows.Forms.Control.MouseDoubleClick>

  - Sağ çift tıklama: hiçbir tıklama olayı tetiklendi

- <xref:System.Windows.Forms.ListView>denetimle

  > [!NOTE]
  > Daha sonra ayrıntılı olay davranışı yalnızca Kullanıcı denetimdeki öğelere tıkladığı zaman gerçekleşir <xref:System.Windows.Forms.ListView> . Denetimde başka herhangi bir yere tıklama için hiçbir olay oluşturulmaz. Daha sonra açıklanan olaylara ek olarak, <xref:System.Windows.Forms.ListView.BeforeLabelEdit> <xref:System.Windows.Forms.ListView.AfterLabelEdit> denetimi ile doğrulama kullanmak istiyorsanız, sizi ilgilendirebilecek ve olayları vardır <xref:System.Windows.Forms.ListView> .

  - Sol tıklama: <xref:System.Windows.Forms.Control.Click> ,<xref:System.Windows.Forms.Control.MouseClick>

  - Sağ tıklayın: <xref:System.Windows.Forms.Control.Click> ,<xref:System.Windows.Forms.Control.MouseClick>

  - Sol çift tıklama: <xref:System.Windows.Forms.Control.Click> , <xref:System.Windows.Forms.Control.MouseClick> ; <xref:System.Windows.Forms.Control.DoubleClick> ,<xref:System.Windows.Forms.Control.MouseDoubleClick>

  - Sağ çift tıklayın: <xref:System.Windows.Forms.Control.Click> , <xref:System.Windows.Forms.Control.MouseClick> ; <xref:System.Windows.Forms.Control.DoubleClick> ,<xref:System.Windows.Forms.Control.MouseDoubleClick>

- <xref:System.Windows.Forms.TreeView>denetimle

  > [!NOTE]
  > Daha sonra ayrıntılı olay davranışı yalnızca Kullanıcı öğelerin kendilerini tıkladığı veya denetimdeki öğelerin sağında oluşur <xref:System.Windows.Forms.TreeView> . Denetimde başka herhangi bir yere tıklama için hiçbir olay oluşturulmaz. Daha sonra açıklananlara ek olarak, <xref:System.Windows.Forms.TreeView.BeforeCheck> <xref:System.Windows.Forms.TreeView.BeforeSelect> <xref:System.Windows.Forms.TreeView.BeforeLabelEdit> <xref:System.Windows.Forms.TreeView.AfterSelect> <xref:System.Windows.Forms.TreeView.AfterCheck> <xref:System.Windows.Forms.TreeView.AfterLabelEdit> denetimi ile doğrulama kullanmak istiyorsanız,,,, ve olayları ilginizi çekmiş olabilir <xref:System.Windows.Forms.TreeView> .

  - Sol tıklama: <xref:System.Windows.Forms.Control.Click> ,<xref:System.Windows.Forms.Control.MouseClick>

  - Sağ tıklayın: <xref:System.Windows.Forms.Control.Click> ,<xref:System.Windows.Forms.Control.MouseClick>

  - Sol çift tıklama: <xref:System.Windows.Forms.Control.Click> , <xref:System.Windows.Forms.Control.MouseClick> ; <xref:System.Windows.Forms.Control.DoubleClick> ,<xref:System.Windows.Forms.Control.MouseDoubleClick>

  - Sağ çift tıklayın: <xref:System.Windows.Forms.Control.Click> , <xref:System.Windows.Forms.Control.MouseClick> ; <xref:System.Windows.Forms.Control.DoubleClick> ,<xref:System.Windows.Forms.Control.MouseDoubleClick>

### <a name="painting-behavior-of-toggle-controls"></a>İki durumlu denetimlerin boyama davranışı

Sınıfından türetilen denetimler gibi geçiş denetimleri <xref:System.Windows.Forms.ButtonBase> , fare tıklama olayları ile birlikte aşağıdaki farklı boyama davranışına sahiptir:

1. Kullanıcı fare düğmesine basar.

2. Denetim, basılan durumu boyar.

3. <xref:System.Windows.Forms.Control.MouseDown>Olay tetiklenir.

4. Kullanıcı fare düğmesini serbest bırakır.

5. Denetim, oluşturulan durumu boyar.

6. <xref:System.Windows.Forms.Control.Click>Olay tetiklenir.

7. <xref:System.Windows.Forms.Control.MouseClick>Olay tetiklenir.

8. <xref:System.Windows.Forms.Control.MouseUp>Olay tetiklenir.

    > [!NOTE]
    > Fare düğmesi kapalıyken Kullanıcı işaretçiyi iki durumlu denetimin dışına taşımışsa (basıldığında fareyi denetimin dışına taşımak gibi <xref:System.Windows.Forms.Button> ), geçiş denetimi, ortaya çıkan durumu boyar ve yalnızca <xref:System.Windows.Forms.Control.MouseUp> olay meydana gelir. <xref:System.Windows.Forms.Control.Click>Veya <xref:System.Windows.Forms.Control.MouseClick> olayları bu durumda gerçekleşmeyecektir.

## <a name="see-also"></a>Ayrıca bkz.

- [Bir Windows Forms Uygulamasında Fare Girdisi](mouse-input-in-a-windows-forms-application.md)

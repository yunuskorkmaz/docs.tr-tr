---
title: 'Nasıl yapılır: Bir Windows Formunda Windows Gezgini Stilinde bir Arabirim Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Explorer [Windows Forms], creating with Windows Forms
- SplitContainer control [Windows Forms], Explorer-style interface
- forms [Windows Forms], Windows Explorer type
ms.assetid: 9a3d5f4f-5dda-4350-9ad5-57ce5976dc47
ms.openlocfilehash: 34a5cd735c350688d9e83003806668e213932c85
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960618"
---
# <a name="how-to-create-a-windows-explorerstyle-interface-on-a-windows-form"></a>Nasıl yapılır: Bir Windows Formunda Windows Gezgini Stilinde bir Arabirim Oluşturma
Windows Gezgini, uygulama için önceden kullanılan bir kullanıcı arabirimi seçiminden kaynaklanır.

 Windows Gezgini, temelde bir <xref:System.Windows.Forms.TreeView> denetim <xref:System.Windows.Forms.ListView> ve ayrı panellerde bir denetimdir. Panolar bir Splitter tarafından yeniden boyutlandırılabilir hale getirilir. Denetimlerin bu düzenlemesi, bilgileri görüntülemek ve göz atmak için çok etkilidir.

 Aşağıdaki adımlarda, Windows Gezgini benzeri bir biçimde denetimlerin nasıl düzenlendiğini gösterilmektedir. Windows Gezgini uygulamasının dosya tarama işlevinin nasıl ekleneceğini göstermez.

## <a name="to-create-a-windows-explorer-style-windows-form"></a>Windows Gezgini stili bir Windows formu oluşturmak için

1. Yeni bir Windows uygulaması projesi oluşturma (**Dosya** > **Yeni** > **Proje** > **görseli C#**  veya **Visual Basic** > **Klasik** Masaüstü >  **Windows Forms uygulama**).

2. **Araç kutusundan**:

    1. Formunuza bir <xref:System.Windows.Forms.SplitContainer> denetim sürükleyin.

    2. Bir <xref:System.Windows.Forms.TreeView> denetimi **SplitterPanel1** öğesine sürükleyin ( <xref:System.Windows.Forms.SplitContainer> **Panel1**olarak işaretlenen denetimin bölmesi).

    3. Bir <xref:System.Windows.Forms.ListView> denetimi **SplitterPanel2** öğesine sürükleyin ( <xref:System.Windows.Forms.SplitContainer> **Panel2**olarak işaretlenen denetimin bölmesi).

3. CTRL tuşuna basarak ve sırasıyla tıklayarak tüm üç denetimi seçin. <xref:System.Windows.Forms.SplitContainer> Denetimi seçtiğinizde, panolar yerine Bölümlendirici çubuğuna tıklayın.

    > [!NOTE]
    > **Düzenleme** menüsünde **Tümünü Seç** komutunu kullanmayın. Bunu yaparsanız, sonraki adımda gerekli olan özellik **Özellikler** penceresinde görünmez.

4. **Özellikler** penceresinde, <xref:System.Windows.Forms.SplitContainer.Dock%2A> özelliğini olarak <xref:System.Windows.Forms.DockStyle.Fill>ayarlayın.

5. Uygulamayı çalıştırmak için F5'e basın.

     Form, Windows Gezgini ' ne benzer şekilde iki bölümden oluşan bir kullanıcı arabirimi görüntüler.

    > [!NOTE]
    > Bölümlendirici sürüklediğiniz zaman, panolar kendilerini yeniden boyutlandırır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.SplitContainer>
- [Nasıl yapılır: Windows Forms ile çok Bölbir Kullanıcı arabirimi oluşturma](how-to-create-a-multipane-user-interface-with-windows-forms.md)
- [Nasıl yapılır: Bölünmüş pencerede yeniden boyutlandırma ve konumlandırma davranışını tanımlama](how-to-define-resize-and-positioning-behavior-in-a-split-window.md)
- [Nasıl yapılır: Pencereyi yatay bölme](how-to-split-a-window-horizontally.md)
- [SplitContainer Denetimi](splitcontainer-control-windows-forms.md)

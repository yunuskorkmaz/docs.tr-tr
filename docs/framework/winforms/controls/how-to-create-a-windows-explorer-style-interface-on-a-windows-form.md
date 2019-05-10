---
title: 'Nasıl yapılır: Bir Windows Formunda Windows Gezgini Stilinde bir Arabirim Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Explorer [Windows Forms], creating with Windows Forms
- SplitContainer control [Windows Forms], Explorer-style interface
- forms [Windows Forms], Windows Explorer type
ms.assetid: 9a3d5f4f-5dda-4350-9ad5-57ce5976dc47
ms.openlocfilehash: 578fdf8e24803db0e0d80ff22aa5cebebbc2663e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64615994"
---
# <a name="how-to-create-a-windows-explorerstyle-interface-on-a-windows-form"></a>Nasıl yapılır: Bir Windows Formunda Windows Gezgini Stilinde bir Arabirim Oluşturma
Windows Gezgini bir ortak kullanıcı arabirimi uygulamalar için kendi hazır bilgisi nedeniyle seçimdir.  
  
 Esas olarak, Windows Gezgini, bir <xref:System.Windows.Forms.TreeView> denetimi ve bir <xref:System.Windows.Forms.ListView> ayrı Panel denetimi. Paneller yeniden boyutlandırılabilir bir ayırıcı tarafından yapılır. Bu düzenleme denetimleri görüntüleme ve gözatma bilgilerinin oldukça etkilidir.  
  
 Aşağıdaki adımlarda, bir Windows Gezgini benzeri form denetimleri düzenlemek gösterilmektedir. Windows Gezgini uygulama dosyasına göz atma işlevini ekleme gösterme.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-create-a-windows-explorer-style-windows-form"></a>Bir Windows Gezgini stilinde Windows Form oluşturma  
  
1. Yeni bir Windows uygulaması projesi oluşturun (**dosya** > **yeni** > **proje** > **Visual C#** veya **Visual Basic** > **Klasik Masaüstü** > **Windows Forms uygulamalarındaki**).  
  
2. Gelen **araç kutusu**:  
  
    1. Sürükleme bir <xref:System.Windows.Forms.SplitContainer> denetimi formunuza sürükleyin.  
  
    2. Sürükleme bir <xref:System.Windows.Forms.TreeView> içine denetim **SplitterPanel1** (panelini <xref:System.Windows.Forms.SplitContainer> işaretlenen denetim **Panel1**).  
  
    3. Sürükleme bir <xref:System.Windows.Forms.ListView> içine denetim **SplitterPanel2** (panelini <xref:System.Windows.Forms.SplitContainer> işaretlenen denetim **Panel2**).  
  
3. Her üç denetim CTRL tuşuna basarak ve bunları sırayla tıklayarak seçin. Seçtiğinizde, <xref:System.Windows.Forms.SplitContainer> denetlemek, paneller yerine ayırıcıyı tıklayın.  
  
    > [!NOTE]
    >  Kullanmayın **Tümünü Seç** komutunu **Düzenle** menüsü. Bunu yaparsanız, sonraki adımda gerekli özellik görüntülenmez **özellikleri** penceresi.  
  
4. İçinde **özellikleri** penceresinde <xref:System.Windows.Forms.SplitContainer.Dock%2A> özelliğini <xref:System.Windows.Forms.DockStyle.Fill>.  
  
5. Uygulamayı çalıştırmak için F5'e basın.  
  
     Form, Windows Gezgini için benzer bir iki bölümden kullanıcı arabirimi görüntüler.  
  
    > [!NOTE]
    >  Bölümlendirici sürüklediğinizde, paneller kendilerini yeniden boyutlandırın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.SplitContainer>
- [Nasıl yapılır: Windows Forms ile çok bölmeli kullanıcı arabirimi oluşturma](how-to-create-a-multipane-user-interface-with-windows-forms.md)
- [Nasıl yapılır: Yeniden boyutlandırma ve konumlama davranışını bölünmüş pencerede tanımlama](how-to-define-resize-and-positioning-behavior-in-a-split-window.md)
- [Nasıl yapılır: Pencereyi yatay bölme](how-to-split-a-window-horizontally.md)
- [SplitContainer Denetimi](splitcontainer-control-windows-forms.md)

---
title: "Nasıl yapılır: Bir Windows Formunda Windows Gezgini Stilinde bir Arabirim Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Explorer [Windows Forms], creating with Windows Forms
- SplitContainer control [Windows Forms], Explorer-style interface
- forms [Windows Forms], Windows Explorer type
ms.assetid: 9a3d5f4f-5dda-4350-9ad5-57ce5976dc47
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 26a91052586843f87c04adf1a31025991d9973db
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-create-a-windows-explorerstyle-interface-on-a-windows-form"></a>Nasıl yapılır: Bir Windows Formunda Windows Gezgini Stilinde bir Arabirim Oluşturma
Windows Gezgini'nde bir ortak kullanıcı arabirimi uygulamalar için kendi hazır benzerlik nedeniyle seçimdir.  
  
 Esas olarak, Windows Gezgini olan bir <xref:System.Windows.Forms.TreeView> denetim ve <xref:System.Windows.Forms.ListView> ayrı Panel denetimi. Paneller Bölümlendirici tarafından yeniden boyutlandırılabilir hale getirilir. Bu denetimlerin düzenlenmesi görüntüleme ve bilgi gözatma için çok etkili olur.  
  
 Aşağıdaki adımlar Windows Explorer benzeri formu denetimlerini düzenlemek nasıl gösterir. Windows Gezgini uygulama dosyasına göz atma işlevselliğini ekleme gösterme.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-create-a-windows-explorer-style-windows-form"></a>Bir Windows Gezgini stilinde Windows Form oluşturmak için  
  
1.  Yeni bir Windows uygulama projesi oluşturun. Ayrıntılar için bkz [nasıl yapılır: bir Windows uygulaması projesi oluşturduğunuzda](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  Gelen **araç**:  
  
    1.  Sürükleme bir <xref:System.Windows.Forms.SplitContainer> Formunuza denetim.  
  
    2.  Sürükleme bir <xref:System.Windows.Forms.TreeView> içine kontrol **SplitterPanel1** (panelini <xref:System.Windows.Forms.SplitContainer> işaretlenmiş denetim **Panel1**).  
  
    3.  Sürükleme bir <xref:System.Windows.Forms.ListView> içine kontrol **SplitterPanel2** (panelini <xref:System.Windows.Forms.SplitContainer> işaretlenmiş denetim **Panel2**).  
  
3.  Tüm üç denetimleri CTRL tuşuna basarak ve bunları sırayla tıklayarak seçin. Seçtiğinizde, <xref:System.Windows.Forms.SplitContainer> denetlemek, paneller yerine ayırıcıyı'ı tıklatın.  
  
    > [!NOTE]
    >  Kullanmayın **Tümünü Seç** komutunu **Düzenle** menüsü. Bunu yaparsanız, sonraki adımda gerekli özellik görüntülenmez **özellikleri** penceresi.  
  
4.  İçinde **özellikleri** penceresindeki ayarlayın <xref:System.Windows.Forms.SplitContainer.Dock%2A> özelliğine <xref:System.Windows.Forms.DockStyle.Fill>.  
  
5.  Uygulamayı çalıştırmak için F5 tuşuna basın.  
  
     Form, Windows Gezgini benzer iki parçalı kullanıcı arabirimi görüntüler.  
  
    > [!NOTE]
    >  Bölümlendirici sürüklediğinizde, paneller kendilerini yeniden boyutlandırın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.SplitContainer>  
 [Nasıl yapılır: Windows Forms ile Çok Bölmeli Kullanıcı Arabirimi Oluşturma](../../../../docs/framework/winforms/controls/how-to-create-a-multipane-user-interface-with-windows-forms.md)  
 [Nasıl yapılır: Bölünmüş Pencerede Yeniden Boyutlandırma ve Konumlama Davranışını Tanımlama](../../../../docs/framework/winforms/controls/how-to-define-resize-and-positioning-behavior-in-a-split-window.md)  
 [Nasıl yapılır: Pencereyi Yatay Bölme](../../../../docs/framework/winforms/controls/how-to-split-a-window-horizontally.md)  
 [SplitContainer Denetimi](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)

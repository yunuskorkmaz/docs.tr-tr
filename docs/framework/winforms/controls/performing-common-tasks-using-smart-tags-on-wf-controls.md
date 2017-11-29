---
title: "İzlenecek yol: Windows Forms Denetimlerindeki Akıllı Etiketleri Kullanarak Ortak Görevleri Gerçekleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DesignerAction object model
- smart tags
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2e6b815be85576f037e0f24668c44756b95abd6e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-performing-common-tasks-using-smart-tags-on-windows-forms-controls"></a>İzlenecek yol: Windows Forms Denetimlerindeki Akıllı Etiketleri Kullanarak Ortak Görevleri Gerçekleştirme
Windows Forms uygulamanız için formlar ve denetimler oluşturmak gibi art arda gerçekleştirecek pek çok görev vardır. Bunlar, karşınıza çıkacak sık gerçekleştirilen görevlerden bazıları şunlardır:  
  
-   Ekleyerek veya üzerinde bir sekme kaldırarak bir <xref:System.Windows.Forms.TabControl>.  
  
-   Bir denetim kendi üst yerleştirme.  
  
-   Yönünü değiştirme bir <xref:System.Windows.Forms.SplitContainer> denetim.  
  
 Geliştirme hızlandırmak için tasarım zamanında bunları tek bir hareketi gibi genel görevleri gerçekleştirmenize olanak sağlayan bağlama duyarlı menüler olan akıllı etiketler birçok denetim sunar. Bu görevleri adlı *akıllı etiket fiiller*.  
  
 Akıllı etiketler Tasarımcısı'nda ömrü için bir denetim örneğine eklenen kalır ve her zaman kullanılabilir.  
  
 Bu örneklerde gösterilen görevler aşağıdakileri içerir:  
  
-   Windows Forms projesi oluşturma  
  
-   Akıllı etiketleri kullanarak  
  
-   Akıllı etiketler devre dışı bırakma ve etkinleştirme  
  
 İşiniz bittiğinde, bu önemli yerleşim özellikleri tarafından oynadığı rol anlaşılması gerekir.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="creating-the-project"></a>Projeyi Oluşturma  
 Projeyi oluşturmak ve formu ayarlamak için ilk adımdır bakın.  
  
#### <a name="to-create-the-project"></a>Proje oluşturmak için  
  
1.  "SmartTagsExample" adlı bir Windows tabanlı bir uygulama projesi oluşturun. Ayrıntılar için bkz [nasıl yapılır: bir Windows uygulaması projesi oluşturduğunuzda](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  Formda seçin **Windows Form Tasarımcısı**.  
  
## <a name="using-smart-tags"></a>Akıllı etiketleri kullanarak  
 Akıllı etiketler her zaman bunları teklif denetimlerinde tasarım zamanında kullanılabilir.  
  
#### <a name="to-use-smart-tags"></a>Akıllı etiketleri kullanma  
  
1.  Sürükleme bir <xref:System.Windows.Forms.TabControl> gelen **araç** formunuza. Akıllı etiket karakteri unutmayın (![akıllı etiket karakteri](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) görünen üzerinde yan, <xref:System.Windows.Forms.TabControl>.  
  
2.  Akıllı etiket karakteri'ı tıklatın. Karakter yanında görüntülenen kısayol menüsünden seçin **sekmesi Ekle** öğesi. Yeni bir sekme sayfası eklenir gözlemlemek <xref:System.Windows.Forms.TabControl>.  
  
3.  Sürükleme bir <xref:System.Windows.Forms.TableLayoutPanel> gelen denetim **araç** formunuza.  
  
4.  Akıllı etiket karakteri'ı tıklatın. Karakter yanında görüntülenen kısayol menüsünden seçin **Sütun Ekle** öğesi. Yeni bir sütun eklenir gözlemlemek <xref:System.Windows.Forms.TableLayoutPanel> denetim.  
  
5.  Sürükleme bir <xref:System.Windows.Forms.SplitContainer> gelen denetim **araç** formunuza.  
  
6.  Akıllı etiket karakteri'ı tıklatın. Karakter yanında görüntülenen kısayol menüsünden seçin **Yatay bölümlendirici yönlendirmesini** öğesi. Görüntülendiğini <xref:System.Windows.Forms.SplitContainer> denetimin ayırıcıyı olduğu şimdi yatay yönelimli.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.TextBox>  
 <xref:System.Windows.Forms.TabControl>  
 <xref:System.Windows.Forms.SplitContainer>  
 <xref:System.ComponentModel.Design.DesignerActionList>  
 [İzlenecek yol: Bir Windows Forms bileşenine akıllı etiketler ekleme](http://msdn.microsoft.com/library/a6814169-fa7d-4527-808c-637ca5c95f63)

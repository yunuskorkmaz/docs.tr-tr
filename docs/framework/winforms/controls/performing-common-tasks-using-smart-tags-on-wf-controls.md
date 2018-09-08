---
title: 'İzlenecek yol: Windows Forms Denetimlerindeki Akıllı Etiketleri Kullanarak Ortak Görevleri Gerçekleştirme'
ms.date: 03/30/2017
helpviewer_keywords:
- DesignerAction object model
- smart tags
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
ms.openlocfilehash: d1c69d2e9e89e0a4fed767216e8743a0ac9ac81d
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44135568"
---
# <a name="walkthrough-performing-common-tasks-using-smart-tags-on-windows-forms-controls"></a>İzlenecek yol: Windows Forms Denetimlerindeki Akıllı Etiketleri Kullanarak Ortak Görevleri Gerçekleştirme
Windows Forms uygulamanız için formlar ve denetimler oluşturmak gibi art arda gerçekleştirir çok sayıda görev vardır. Karşınıza çıkacak sık gerçekleştirilen görevlerin bazıları şunlardır:  
  
-   Ekleyerek veya bir sekme üzerindeki kaldırarak bir <xref:System.Windows.Forms.TabControl>.  
  
-   Bir denetim için üst yerleştirme.  
  
-   Yönünü değiştirme bir <xref:System.Windows.Forms.SplitContainer> denetimi.  
  
 Geliştirme hızlandırmak için pek çok denetimi tasarım zamanında bu tek gibi genel görevleri gerçekleştirmenize olanak tanıyan bağlama duyarlı menüler şunlardır akıllı etiketler sunar. Bu görevleri adlı *akıllı etiket fiilleri*.  
  
 Akıllı etiketler Tasarımcısı'nda yaşam süresi'için bir denetim örneğine bağlı kalır ve her zaman kullanılabilir.  
  
 Bu kılavuzda gösterilen görevler aşağıdakileri içerir:  
  
-   Bir Windows Forms projesi oluşturma  
  
-   Akıllı etiketleri kullanarak  
  
-   Akıllı etiketler devre dışı bırakma ve etkinleştirme  
  
 İşlemi tamamladığınızda, bu önemli bir düzen özellikleri tarafından oynadığı rol, bir anlayışa sahip olacaksınız.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="creating-the-project"></a>Projeyi Oluşturma  
 İlk adım projeyi oluşturmak ve formu ayarlamaktır.  
  
#### <a name="to-create-the-project"></a>Proje oluşturmak için  
  
1.  "SmartTagsExample" adlı bir Windows tabanlı uygulama projesi oluşturun (**dosya** > **yeni** > **proje**  >   **Visual C#** veya **Visual Basic** > **Klasik Masaüstü** > **Windows Forms uygulamalarındaki**).  
  
2.  Formda seçin **Windows Form Tasarımcısı**.  
  
## <a name="using-smart-tags"></a>Akıllı etiketleri kullanarak  
 Akıllı etiketler her zaman bunları teklif denetimleri tasarım zamanında kullanılabilir.  
  
#### <a name="to-use-smart-tags"></a>Akıllı etiketleri kullanma  
  
1.  Sürükleme bir <xref:System.Windows.Forms.TabControl> gelen **araç kutusu** formunuza. Akıllı etiket karakterini unutmayın (![akıllı etiket karakterini](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) üzerinde yan, görüntülenen <xref:System.Windows.Forms.TabControl>.  
  
2.  Akıllı etiket karakterini tıklayın. Glif yanında görüntülenen kısayol menüsünden seçin **Sekme Ekle** öğesi. Yeni bir sekme sayfası eklenir gözlemleyin <xref:System.Windows.Forms.TabControl>.  
  
3.  Sürükleme bir <xref:System.Windows.Forms.TableLayoutPanel> denetimi **araç kutusu** formunuza.  
  
4.  Akıllı etiket karakterini tıklayın. Glif yanında görüntülenen kısayol menüsünden seçin **Sütun Ekle** öğesi. Yeni bir sütun eklenir gözlemleyin <xref:System.Windows.Forms.TableLayoutPanel> denetimi.  
  
5.  Sürükleme bir <xref:System.Windows.Forms.SplitContainer> denetimi **araç kutusu** formunuza.  
  
6.  Akıllı etiket karakterini tıklayın. Glif yanında görüntülenen kısayol menüsünden seçin **Yatay bölümlendirici yönlendirmesini** öğesi. Mesajının görüntülendiğini görün <xref:System.Windows.Forms.SplitContainer> denetimin ayırıcıyı, artık yatay odaklıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.TextBox>  
 <xref:System.Windows.Forms.TabControl>  
 <xref:System.Windows.Forms.SplitContainer>  
 <xref:System.ComponentModel.Design.DesignerActionList>  
 [İzlenecek yol: Bir Windows Formları bileşenine akıllı etiket ekleme](https://msdn.microsoft.com/library/a6814169-fa7d-4527-808c-637ca5c95f63)

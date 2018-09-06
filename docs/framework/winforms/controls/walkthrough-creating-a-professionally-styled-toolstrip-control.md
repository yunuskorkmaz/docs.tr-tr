---
title: 'İzlenecek yol: Profesyonel Stilde ToolStrip Denetimi Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStripProfessionalRenderer class [Windows Forms]
- ToolStripRenderer class [Windows Forms]
- toolbars [Windows Forms], walkthroughs
- ToolStrip control [Windows Forms], creating professionally styled controls
ms.assetid: b52339ae-f1d3-494e-996e-eb455614098a
ms.openlocfilehash: 6435f33489be1355313e43a046b0e3169e1eaea3
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43861979"
---
# <a name="walkthrough-creating-a-professionally-styled-toolstrip-control"></a>İzlenecek yol: Profesyonel Stilde ToolStrip Denetimi Oluşturma
Uygulamanızın verebilirsiniz <xref:System.Windows.Forms.ToolStrip> kendi sınıfından türetilen yazarak bir profesyonel görünümünü ve davranışını denetleyen <xref:System.Windows.Forms.ToolStripProfessionalRenderer> türü.  
  
 Bu izlenecek yolda nasıl kullanılacağını gösterir <xref:System.Windows.Forms.ToolStrip> benzeyen bileşik denetim oluşturmak için denetimleri **Gezinti bölmesinde** Microsoft Outlook® tarafından sağlanan. Aşağıdaki görevler bu kılavuzda gösterilen:  
  
-   Bir Windows Denetim Kitaplığı projesi oluşturma.  
  
-   StackView denetimi tasarlama.  
  
-   Özel oluşturucu oluşturma.  
  
 İşlemi tamamladığınızda, profesyonel bir Microsoft Office® XP denetiminin görünümünü ile bir yeniden kullanılabilir bir özel istemci denetime sahip olur.  
  
 Bu konudaki tek bir liste olarak kodu kopyalamak için bkz: [nasıl yapılır: bir profesyonel stilde ToolStrip denetimi oluşturma](../../../../docs/framework/winforms/controls/how-to-create-a-professionally-styled-toolstrip-control.md).  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için şunlar gerekir:  
  
-   Oluşturma ve Windows Forms application projesi Visual Studio'nun yüklü bilgisayarda çalıştırmak için yeterli izinleri yok.  
  
## <a name="creating-a-windows-control-library-project"></a>Bir Windows Denetim Kitaplığı projesi oluşturma  
 İlk adım, denetim kitaplığı projesi oluşturmaktır.  
  
#### <a name="to-create-the-control-library-project"></a>Denetim Kitaplığı projesini oluşturmak için  
  
1.  Adlı yeni bir Windows Denetim Kitaplığı projesi oluşturun `StackViewLibrary`.  
  
2.  İçinde **Çözüm Gezgini**, istediğiniz dilde bağlı olarak "UserControl1.cs" veya "UserControl1.vb" adlı kaynak dosyası silerek projenin varsayılan denetimini silin.  
  
     Daha fazla bilgi için [NIB: nasıl yapılır: kaldırma, silme ve öğeleri hariç](https://msdn.microsoft.com/library/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73).  
  
3.  Yeni bir <xref:System.Windows.Forms.UserControl> öğesinin **StackViewLibrary** proje. Yeni kaynak dosyanın temel adı verin `StackView`.  
  
## <a name="designing-the-stackview-control"></a>StackView denetimi tasarlama  
 `StackView` Denetimdir: bir alt öğesi ile bileşik denetim <xref:System.Windows.Forms.ToolStrip> denetimi. Bileşik denetimler hakkında daha fazla bilgi için bkz: [özel denetim çeşitleri](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md).  
  
#### <a name="to-design-the-stackview-control"></a>Tasarım StackView denetimi  
  
1.  Gelen **araç kutusu**, sürükleyin bir <xref:System.Windows.Forms.ToolStrip> denetimi tasarım yüzeyine bırakın.  
  
2.  İçinde **özellikleri** penceresinde <xref:System.Windows.Forms.ToolStrip> denetimin özellikleri aşağıdaki tabloya göre.  
  
    |Özellik|Değer|  
    |--------------|-----------|  
    |Ad|`stackStrip`|  
    |CanOverflow|`false`|  
    |Dock|<xref:System.Windows.Forms.DockStyle.Bottom>|  
    |Yazı tipi|`Tahoma, 10pt, style=Bold`|  
    |GripStyle|<xref:System.Windows.Forms.ToolStripGripStyle.Hidden>|  
    |LayoutStyle|<xref:System.Windows.Forms.ToolStripLayoutStyle.VerticalStackWithOverflow>|  
    |Doldurma|`0, 7, 0, 0`|  
    |RenderMode|<xref:System.Windows.Forms.ToolStripRenderMode.Professional>|  
  
3.  Windows Form Tasarımcısı'nda tıklatın <xref:System.Windows.Forms.ToolStrip> denetimin **Ekle** düğmesine tıklayın ve Ekle bir <xref:System.Windows.Forms.ToolStripButton> için `stackStrip` denetimi.  
  
4.  İçinde **özellikleri** penceresinde <xref:System.Windows.Forms.ToolStripButton> denetimin özellikleri aşağıdaki tabloya göre.  
  
    |Özellik|Değer|  
    |--------------|-----------|  
    |Ad|`mailStackButton`|  
    |CheckOnClick|true|  
    |CheckState|<xref:System.Windows.Forms.CheckState.Checked>|  
    |DisplayStyle|<xref:System.Windows.Forms.ToolStripItemDisplayStyle.ImageAndText>|  
    |ImageAlign|<xref:System.Drawing.ContentAlignment.MiddleLeft>|  
    |ImageScaling|<xref:System.Windows.Forms.ToolStripItemImageScaling.None>|  
    |ImageTransparentColor|`238, 238, 238`|  
    |Kenar boşluğu|`0, 0, 0, 0`|  
    |Doldurma|`3, 3, 3, 3`|  
    |Metin|**posta**|  
    |TextAlign|<xref:System.Drawing.ContentAlignment.MiddleLeft>|  
  
5.  Daha fazla üç için yineleme adım 7 <xref:System.Windows.Forms.ToolStripButton> kontrol eder.  
  
     Denetimlere `calendarStackButton`, `contactsStackButton`, ve `tasksStackButton`. Değerini <xref:System.Windows.Forms.Control.Text%2A> özelliğini **Takvim**, **kişiler**, ve **görevleri**sırasıyla.  
  
## <a name="handling-events"></a>Olayları İşleme  
 İki olay yapmak önemli `StackView` denetimi doğru şekilde davranır. Tanıtıcı <xref:System.Windows.Forms.UserControl.Load> denetim doğru konuma olay. Tanıtıcı <xref:System.Windows.Forms.ToolStripItem.Click> her olay <xref:System.Windows.Forms.ToolStripButton> vermek `StackView` denetim durumu davranışını benzer <xref:System.Windows.Forms.RadioButton> denetimi.  
  
#### <a name="to-handle-events"></a>Olayları işlemek için  
  
1.  Windows Form Tasarımcısı'nda seçin `StackView` denetimi.  
  
2.  İçinde **özellikleri** penceresinde tıklayın **olayları**.  
  
3.  Oluşturulacak yükleme olayı çift `StackView_Load` olay işleyicisi.  
  
4.  İçinde `StackView_Load` olay işleyicisine aşağıdaki kodu kopyalayıp yapıştırın.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#3)]  
  
5.  Windows Form Tasarımcısı'nda seçin `mailStackButton` denetimi.  
  
6.  İçinde **özellikleri** penceresinde tıklayın **olayları**.  
  
7.  Tıklama olayı çift tıklatın.  
  
     Windows Form Tasarımcısı oluşturur `mailStackButton_Click` olay işleyicisi.  
  
8.  Yeniden adlandırma `mailStackButton_Click` olay işleyicisine `stackButton_Click`.  
  
     Daha fazla bilgi için [nasıl yapılır: bir tanımlayıcı (Visual Basic) yeniden adlandırmak](https://msdn.microsoft.com/library/e5a5edf8-3dba-4119-81f4-fc2aba180e0c).  
  
9. Aşağıdaki kodu ekleyin `stackButton_Click` olay işleyicisi.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#4)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#4)]  
  
10. Windows Form Tasarımcısı'nda seçin `calendarStackButton` denetimi.  
  
11. İçinde **özellikleri** penceresinde ayarlanmış Click olayı `stackButton_Click` olay işleyicisi.  
  
12. 10 ve 11. adımları yineleyin `contactsStackButton` ve `tasksStackButton` kontrol eder.  
  
## <a name="defining-icons"></a>Simge tanımlama  
 Her `StackView` düğmeye sahip bir ilişkili simge. Kolaylık olması için simgeleri Base64 ile kodlanmış bir dize olarak, önce seri durumdan temsil edilen bir <xref:System.Drawing.Bitmap> ondan oluşturulur. Bir üretim ortamında bir kaynak olarak bit eşlem verileri depolamak ve simgelerini Windows Form Tasarımcısı'nda görünür. Daha fazla bilgi için [nasıl yapılır: Windows formlarına arka plan görüntüleri ekleme](https://msdn.microsoft.com/library/7a509ba2-055c-4ae6-b88a-54625c6d9aff).  
  
#### <a name="to-define-icons"></a>Simgeleri tanımlamak için  
  
1.  Kod Düzenleyicisi'nde aşağıdaki kodu ekleyin `StackView` sınıf tanımını. Bu kod için bit eşlemler başlatır <xref:System.Windows.Forms.ToolStripButton> simgeler.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#2)]  
  
2.  Bir çağrı ekleyin `InitializeImages` yönteminde `StackView` sınıf oluşturucusu.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#5)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#5)]  
  
## <a name="implementing-a-custom-renderer"></a>Özel oluşturucu uygulama  
 Özelleştirebileceğiniz öğelerin çoğunu `StackView` my türetildiği bir sınıf uygulama Denetim <xref:System.Windows.Forms.ToolStripRenderer> sınıfı. Bu yordamda, uygulamanız bir <xref:System.Windows.Forms.ToolStripProfessionalRenderer> tutamacı özelleştirir ve gradyan arka planlar için çizer sınıfı <xref:System.Windows.Forms.ToolStripButton> kontrol eder.  
  
#### <a name="to-implement-a-custom-renderer"></a>Özel oluşturucu uygulamak için  
  
1.  Aşağıdaki kodu ekleyin `StackView` denetim tanımı.  
  
     Bu tanımı, `StackRenderer` sınıfı, hangi geçersiz kılmaları <xref:System.Windows.Forms.ToolStripRenderer.RenderGrip>, <xref:System.Windows.Forms.ToolStripRenderer.RenderToolStripBorder>, ve <xref:System.Windows.Forms.ToolStripRenderer.RenderButtonBackground> özel görünüm oluşturmak için yöntemleri.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#10)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#10)]  
  
2.  İçinde `StackView` denetimin Oluşturucu, yeni bir örneğini oluşturmak `StackRenderer` sınıfı ve bu örneğe atama `stackStrip` denetimin <xref:System.Windows.Forms.ToolStrip.Renderer%2A> özelliği.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#5)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#5)]  
  
## <a name="testing-the-stackview-control"></a>StackView denetimini test etme  
 `StackView` Denetim türetilir <xref:System.Windows.Forms.UserControl> sınıfı. Bu nedenle, Denetim ile test edebilirsiniz **UserControl Test kapsayıcısı**. Daha fazla bilgi için [nasıl yapılır: bir UserControl denetiminin çalışma zamanı davranışını sınama](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).  
  
#### <a name="to-test-the-stackview-control"></a>StackView Denetimi'ni sınamak için  
  
1.  Projeyi oluşturmak ve başlatmak için F5 tuşuna basın **UserControl Test kapsayıcısı**.  
  
2.  Düğmelerinin üzerinde işaretçiyi `StackView` denetlemek ve ardından seçili durumuna görünümünü görmek için bir düğmesine tıklayın.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Bu kılavuzda, profesyonel bir Office XP denetiminin görünümünü ile yeniden kullanılabilir bir özel istemci denetimi oluşturdunuz. Kullanabileceğiniz <xref:System.Windows.Forms.ToolStrip> birçok başka amaçlarla denetimlerin ailesi:  
  
-   Sahip, denetimler için kısayol menüleri oluşturma <xref:System.Windows.Forms.ContextMenuStrip>. Daha fazla bilgi için [ContextMenu bileşenine genel bakış](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).  
  
-   Bir formu otomatik olarak doldurulan bir standart menü ile oluşturun. Daha fazla bilgi için [izlenecek yol: bir forma standart menü öğeleri sağlama](../../../../docs/framework/winforms/controls/walkthrough-providing-standard-menu-items-to-a-form.md).  
  
-   Yerleştirme ile birden çok belge arabirimi (MDI) form oluşturma <xref:System.Windows.Forms.ToolStrip> kontrol eder. Daha fazla bilgi için [nasıl yapılır: menü birleştirme ve ToolStrip denetimleri içeren MDI formu oluşturma](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [ToolStrip Denetimi](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)  
 [Nasıl yapılır: Bir Forma Standart Menü Öğeleri Sağlama](../../../../docs/framework/winforms/controls/how-to-provide-standard-menu-items-to-a-form.md)

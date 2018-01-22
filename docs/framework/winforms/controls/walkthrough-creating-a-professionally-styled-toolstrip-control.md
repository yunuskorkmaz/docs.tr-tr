---
title: "İzlenecek yol: Profesyonel Stilde ToolStrip Denetimi Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStripProfessionalRenderer class [Windows Forms]
- ToolStripRenderer class [Windows Forms]
- toolbars [Windows Forms], walkthroughs
- ToolStrip control [Windows Forms], creating professionally styled controls
ms.assetid: b52339ae-f1d3-494e-996e-eb455614098a
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ab9adb72a174da25298b6ea104b002914de0cc40
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-creating-a-professionally-styled-toolstrip-control"></a>İzlenecek yol: Profesyonel Stilde ToolStrip Denetimi Oluşturma
Uygulamanızın verebilirsiniz <xref:System.Windows.Forms.ToolStrip> türetilmiş kendi sınıfı yazarak profesyonel görünümünü ve davranışını denetler <xref:System.Windows.Forms.ToolStripProfessionalRenderer> türü.  
  
 Bu kılavuzda nasıl kullanılacağı ortaya <xref:System.Windows.Forms.ToolStrip> benzer bir bileşik denetim oluşturmak için denetimleri **Gezinti Bölmesi** Microsoft Outlook® tarafından sağlanan. Aşağıdaki görevler bu kılavuzda gösterilmiştir:  
  
-   Windows Denetim Kitaplığı projesi oluşturma.  
  
-   StackView denetimi tasarlarken.  
  
-   Özel oluşturucu oluşturma.  
  
 İşiniz bittiğinde, profesyonel bir Microsoft Office® XP denetiminin görünümünü ile yeniden kullanılabilir özel istemci denetime sahip olur.  
  
 Bu konuda tek bir liste olarak kodu kopyalamak için bkz: [nasıl yapılır: bir profesyonel stilde ToolStrip denetimi oluşturma](../../../../docs/framework/winforms/controls/how-to-create-a-professionally-styled-toolstrip-control.md).  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu kılavuzu tamamlamak için gerekir:  
  
-   Oluşturma ve Windows Forms uygulaması projeleri bilgisayarda çalıştırmak için yeterli izinlere nerede [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] yüklenir.  
  
## <a name="creating-a-windows-control-library-project"></a>Windows Denetim Kitaplığı projesi oluşturma  
 İlk adım, denetim kitaplığı projesi oluşturmaktır.  
  
#### <a name="to-create-the-control-library-project"></a>Denetim Kitaplığı projesi oluşturmak için  
  
1.  Adlı yeni bir Windows Denetim Kitaplığı projesi oluşturun `StackViewLibrary`.  
  
2.  İçinde **Çözüm Gezgini**, projenin varsayılan denetim seçim dilinizi bağlı olarak "UserControl1.cs" veya "UserControl1.vb" adlı kaynak dosya silerek silin.  
  
     Daha fazla bilgi için bkz: [NIB: nasıl yapılır: Kaldır, silme ve dışlama öğeleri](http://msdn.microsoft.com/library/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73).  
  
3.  Yeni bir ekleme <xref:System.Windows.Forms.UserControl> öğesinin **StackViewLibrary** projesi. Yeni kaynak dosyasını, temel bir ad verin `StackView`.  
  
## <a name="designing-the-stackview-control"></a>StackView denetim tasarlama  
 `StackView` Denetimidir bir alt ile bileşik denetim <xref:System.Windows.Forms.ToolStrip> denetim. Bileşik denetimler hakkında daha fazla bilgi için bkz: [özel denetimler çeşit](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md).  
  
#### <a name="to-design-the-stackview-control"></a>Tasarım StackView denetimi  
  
1.  Gelen **araç**, sürükleyin bir <xref:System.Windows.Forms.ToolStrip> tasarım yüzeyine denetimine.  
  
2.  İçinde **özellikleri** penceresindeki ayarlayın <xref:System.Windows.Forms.ToolStrip> denetimin özelliklerini aşağıdaki tabloya göre.  
  
    |Özellik|Değer|  
    |--------------|-----------|  
    |Ad|`stackStrip`|  
    |CanOverflow|`false`|  
    |Yerleştirme|<xref:System.Windows.Forms.DockStyle.Bottom>|  
    |Yazı tipi|`Tahoma, 10pt, style=Bold`|  
    |GripStyle|<xref:System.Windows.Forms.ToolStripGripStyle.Hidden>|  
    |LayoutStyle|<xref:System.Windows.Forms.ToolStripLayoutStyle.VerticalStackWithOverflow>|  
    |Doldurma|`0, 7, 0, 0`|  
    |RenderMode|<xref:System.Windows.Forms.ToolStripRenderMode.Professional>|  
  
3.  Windows Forms Tasarımcısı'nda tıklayın <xref:System.Windows.Forms.ToolStrip> denetimin **Ekle** düğmesini tıklatın ve eklemek bir <xref:System.Windows.Forms.ToolStripButton> için `stackStrip` denetim.  
  
4.  İçinde **özellikleri** penceresindeki ayarlayın <xref:System.Windows.Forms.ToolStripButton> denetimin özelliklerini aşağıdaki tabloya göre.  
  
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
    |Metin|**Posta**|  
    |TextAlign|<xref:System.Drawing.ContentAlignment.MiddleLeft>|  
  
5.  Daha fazla üç için yineleme adım 7 <xref:System.Windows.Forms.ToolStripButton> kontrol eder.  
  
     Denetimleri adlandırın `calendarStackButton`, `contactsStackButton`, ve `tasksStackButton`. Değerini <xref:System.Windows.Forms.Control.Text%2A> özelliğine **Takvim**, **kişiler**, ve **görevleri**sırasıyla.  
  
## <a name="handling-events"></a>Olayları İşleme  
 İki olay yapmak önemli olan `StackView` denetim doğru şekilde davranır. Tanıtıcı <xref:System.Windows.Forms.UserControl.Load> denetim doğru konuma olay. İşleme <xref:System.Windows.Forms.ToolStripItem.Click> her olay <xref:System.Windows.Forms.ToolStripButton> vermek için `StackView` denetim durumu davranışını benzer <xref:System.Windows.Forms.RadioButton> denetim.  
  
#### <a name="to-handle-events"></a>Olayları işlemek için  
  
1.  Windows Forms Tasarımcısı'nda seçin `StackView` denetim.  
  
2.  İçinde **özellikleri** penceresinde tıklatın **olayları**.  
  
3.  Oluşturulacak yük olayı çift `StackView_Load` olay işleyicisi.  
  
4.  İçinde `StackView_Load` olay işleyicisi, aşağıdaki kodu kopyalayıp yapıştırın.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#3)]  
  
5.  Windows Forms Tasarımcısı'nda seçin `mailStackButton` denetim.  
  
6.  İçinde **özellikleri** penceresinde tıklatın **olayları**.  
  
7.  Click olayını çift tıklayın.  
  
     Windows Form Tasarımcısı oluşturur `mailStackButton_Click` olay işleyicisi.  
  
8.  Yeniden Adlandır `mailStackButton_Click` olay işleyicisine `stackButton_Click`.  
  
     Daha fazla bilgi için bkz: [nasıl yapılır: bir tanımlayıcı (Visual Basic) yeniden adlandırmak](http://msdn.microsoft.com/library/e5a5edf8-3dba-4119-81f4-fc2aba180e0c).  
  
9. Aşağıdaki kodu ekleyin `stackButton_Click` olay işleyicisi.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#4)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#4)]  
  
10. Windows Forms Tasarımcısı'nda seçin `calendarStackButton` denetim.  
  
11. İçinde **özellikleri** penceresinde ayarlanmış Click olayını `stackButton_Click` olay işleyicisi.  
  
12. 10 ve 11. adımları tekrarlayarak `contactsStackButton` ve `tasksStackButton` kontrol eder.  
  
## <a name="defining-icons"></a>Simgeler tanımlama  
 Her `StackView` düğmesi ilişkili bir simge bulunur. Kolaylık olması için her bir simgeyi Base64 ile kodlanmış bir dize hangi önce seri temsil edilen bir <xref:System.Drawing.Bitmap> buradan oluşturulur. Bir üretim ortamında, bir kaynak olarak bit eşlem verileri depolamak ve Windows Forms Tasarımcısı'nda, simgeler görünür. Daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms için arka plan görüntüleri ekleme](http://msdn.microsoft.com/library/7a509ba2-055c-4ae6-b88a-54625c6d9aff).  
  
#### <a name="to-define-icons"></a>Simgeler tanımlamak için  
  
1.  Kod Düzenleyicisi'nde, aşağıdaki kodu ekleyin `StackView` sınıf tanımının. Bu kod için bit eşlemler başlatır <xref:System.Windows.Forms.ToolStripButton> simgeler.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#2)]  
  
2.  Bir çağrı ekleyin `InitializeImages` yönteminde `StackView` sınıfı oluşturucusu.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#5)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#5)]  
  
## <a name="implementing-a-custom-renderer"></a>Özel oluşturucu uygulama  
 Çoğu öğeleri özelleştirebilirsiniz `StackView` my türeyen bir sınıf uygulama Denetim <xref:System.Windows.Forms.ToolStripRenderer> sınıfı. Bu yordamda, gerçekleştireceksiniz bir <xref:System.Windows.Forms.ToolStripProfessionalRenderer> tutamacı özelleştirir ve gradyan arka planlar için çizer sınıfı <xref:System.Windows.Forms.ToolStripButton> kontrol eder.  
  
#### <a name="to-implement-a-custom-renderer"></a>Özel oluşturucu uygulamak için  
  
1.  Aşağıdaki kodu ekleyin `StackView` denetim tanımı.  
  
     Tanımı budur `StackRenderer` sınıfı, hangi geçersiz kılmaları <xref:System.Windows.Forms.ToolStripRenderer.RenderGrip>, <xref:System.Windows.Forms.ToolStripRenderer.RenderToolStripBorder>, ve <xref:System.Windows.Forms.ToolStripRenderer.RenderButtonBackground> özel görünüm oluşturmak için yöntemleri.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#10)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#10)]  
  
2.  İçinde `StackView` denetimin oluşturucusu, yeni bir örneğini oluşturmak `StackRenderer` sınıfı ve bu örneğine atadığınız `stackStrip` denetimin <xref:System.Windows.Forms.ToolStrip.Renderer%2A> özelliği.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#5)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#5)]  
  
## <a name="testing-the-stackview-control"></a>StackView denetim test etme  
 `StackView` Denetim türer <xref:System.Windows.Forms.UserControl> sınıfı. Bu nedenle, denetimle test edebilirsiniz **UserControl Test kapsayıcısı**. Daha fazla bilgi için bkz: [nasıl yapılır: bir UserControl denetiminin çalışma zamanı davranışını sınama](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).  
  
#### <a name="to-test-the-stackview-control"></a>StackView denetimini sınamak için  
  
1.  Projeyi derlemek ve başlatmak için F5 tuşuna basın **UserControl Test kapsayıcısı**.  
  
2.  Düğmelerinin işaretçiyi `StackView` denetlemek ve ardından seçili durumu görünümünü görmek için bir düğmesine tıklayın.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Bu kılavuzda, bir Office XP denetimini profesyonel görünüm ile yeniden kullanılabilir özel istemci denetimi oluşturdunuz. Kullanabileceğiniz <xref:System.Windows.Forms.ToolStrip> birçok başka amaçlarla denetimlerin ailesi:  
  
-   İle denetimleri için kısayol menüleri oluşturma <xref:System.Windows.Forms.ContextMenuStrip>. Daha fazla bilgi için bkz: [ContextMenu bileşenine genel bakış](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).  
  
-   Bir form ile otomatik olarak doldurulan bir standart menü oluşturun. Daha fazla bilgi için bkz: [izlenecek yol: bir forma standart menü öğeleri sağlama](../../../../docs/framework/winforms/controls/walkthrough-providing-standard-menu-items-to-a-form.md).  
  
-   Yerleştirme ile birden çok belge arabirimi (MDI) form oluşturma <xref:System.Windows.Forms.ToolStrip> kontrol eder. Daha fazla bilgi için bkz: [nasıl yapılır: menü birleştirme ve ToolStrip denetimleri içeren MDI formu oluşturma](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [ToolStrip Denetimi](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)  
 [Nasıl yapılır: Bir Forma Standart Menü Öğeleri Sağlama](../../../../docs/framework/winforms/controls/how-to-provide-standard-menu-items-to-a-form.md)

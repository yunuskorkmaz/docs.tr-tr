---
title: Özel Denetim Çeşitleri
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], user controls
- controls [Windows Forms], types of
- composite controls [Windows Forms]
- extended controls [Windows Forms]
- controls [Windows Forms], extended
- user controls [Windows Forms]
- custom controls [Windows Forms]
- controls [Windows Forms], composite
ms.assetid: 3cea09e5-4344-4ccb-9858-b66ccac210ff
ms.openlocfilehash: 765befcf88247e4b2101b13c4937352ba4b070fa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59170714"
---
# <a name="varieties-of-custom-controls"></a>Özel Denetim Çeşitleri
.NET Framework ile geliştirin ve yeni denetimleri uygulayın. Devralma yoluyla da olarak mevcut denetimleri hakkında bilgi sahibi kullanıcı denetiminin işlevselliğini genişletebilirsiniz. Ayrıca, kendi boyama gerçekleştiren özel denetimler yazabilirsiniz.  
  
 Denetimi oluşturmak için hangi tür zorlanabilirsiniz. Bu konuda çeşitli denetimleri içinden arasında devralabilir ve belirli bir projeniz için denetim türünü seçme hakkında bilgi sağlar farklar vurgular.  
  
> [!NOTE]
>  Bir denetim Web formlarında kullanmak için yazma hakkında daha fazla bilgi için bkz: [özel ASP.NET sunucu denetimleri geliştirme](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).  
  
## <a name="base-control-class"></a>Temel denetim sınıfı  
 <xref:System.Windows.Forms.Control> Sınıfı, Windows Forms denetimleri için temel sınıftır. Bu, Windows Forms uygulamalarında visual görüntülemek için gerekli altyapıyı sağlar.  
  
 <xref:System.Windows.Forms.Control> Sınıfı Windows Forms uygulamalarında visual display sağlamak için aşağıdaki görevleri gerçekleştirir:  
  
-   Bir pencere tutucu kullanıma sunar.  
  
-   İleti yönlendirme yönetir.  
  
-   Fare ve klavye olaylarını ve diğer birçok kullanıcı arabirimi olayları sağlar.  
  
-   Gelişmiş Düzen özelliklerini sağlar.  
  
-   Görsel görüntüsüne özgü birçok özellikleri gibi içeren <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Height%2A>, ve <xref:System.Windows.Forms.Control.Width%2A>.  
  
-   Güvenlik ve Microsoft® ActiveX denetimi olarak görev yapacak bir Windows Forms denetimi için gerekli iş parçacığı oluşturma desteği sağlar.  
  
 Çok altyapısının temel sınıfı tarafından sağlandığından, kendi Windows Forms denetimleri geliştirme oldukça kolaydır.  
  
## <a name="kinds-of-controls"></a>Denetim türlerinin  
 Windows Forms denetimleri kullanıcı tarafından tanımlanan üç tür destekler: *bileşik*, *Genişletilmiş*, ve *özel*. Aşağıdaki bölümlerde, her bir denetim türü tanımlamak ve projelerinizde kullanılacak türü seçme önerileri verin.  
  
### <a name="composite-controls"></a>Bileşik denetimler  
 Bileşik denetimini Windows Forms denetimleri ortak bir kapsayıcıda kapsüllenmiş koleksiyonudur. Bu tür bir denetim adlandırılan bir *kullanıcı denetimi*. İçerdiği denetimlerle adlı *bağlı denetimler*.  
  
 Bileşik Denetim tüm kapsanan bir Windows Forms denetimleri her biriyle ilişkili devralınan işlevselliğini içerir ve seçmeli olarak kullanıma sunmak ve bunların özelliklerini bağlama olanak tanır. Bileşik Denetim önemli miktarda geliştirme ek çaba sarf işlevsellikle işleme varsayılan klavye de sağlar.  
  
 Örneğin, bir veritabanından müşteriyi adresini görüntülemek için bileşik denetim oluşturulabilir. Bu denetim içerebilir bir <xref:System.Windows.Forms.DataGridView> denetimi veritabanı alanları görüntülemek için bir <xref:System.Windows.Forms.BindingSource> bir veri kaynağına bağlama işlemek için ve bir <xref:System.Windows.Forms.BindingNavigator> Kayıtlarda gezinmek için denetimi. Veri bağlama özellikleri seçerek erişimlere açabilir ve paketini ve tüm denetim uygulamaya yeniden. Bu tür bir bileşik denetim örneği için bkz: [nasıl yapılır: Windows Forms denetiminde öznitelikleri uygulama](how-to-apply-attributes-in-windows-forms-controls.md).  
  
 Bileşik denetim yazma için türetilen <xref:System.Windows.Forms.UserControl> sınıfı. <xref:System.Windows.Forms.UserControl> Taban sınıfı sağlar klavye yönlendirme alt denetler ve bir grup olarak çalışması alt denetimler sağlar. Daha fazla bilgi için [bir bileşik Windows Forms denetimi geliştirme](developing-a-composite-windows-forms-control.md).  
  
 **Öneri**  
  
 Devralınan <xref:System.Windows.Forms.UserControl> , sınıf:  
  
-   Çeşitli Windows Forms denetimleri işlevlerini tek bir yeniden kullanılabilir biriminde birleştirmek istediğiniz.  
  
### <a name="extended-controls"></a>Genişletilmiş denetimler  
 Devralınan bir denetimi varolan herhangi bir Windows Forms denetimden türetebilirsiniz. Bu yaklaşımda, bir Windows Forms denetiminin devralınan işlevlerin korumak ve ardından özel özellikler, yöntemler veya diğer özellikleri ekleyerek işlevselliği genişletir. Bu seçenekle temel denetimin Boya mantığını geçersiz kılmasını ve ardından görünümünü değiştirerek kullanıcı arabirimi genişletme.  
  
 Örneğin, türetilmiş bir denetim oluşturabilirsiniz <xref:System.Windows.Forms.Button> kullanıcının kaç kez izleyen denetim, tıklanan.  
  
 Bazı denetimler de özel görünüşünü denetiminizin grafik kullanıcı arabirimi için geçersiz kılarak ekleyebilirsiniz <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi temel sınıf. Tıklama izleyen bir genişletilmiş düğmesi için geçersiz kılabilirsiniz <xref:System.Windows.Forms.Control.OnPaint%2A> taban uygulamasını çağırmak için yöntem <xref:System.Windows.Forms.Control.OnPaint%2A>ve sonra bir köşesinde tıklatın sayısı çizin <xref:System.Windows.Forms.Button> denetimin istemci alanı.  
  
 **Öneri**  
  
 Bir Windows Forms denetimi devralır:  
  
-   İhtiyacınız olan işlevleri çoğunu zaten varolan bir Windows Forms denetimi aynı.  
  
-   Varolan bir denetimi için yeni bir grafik kullanıcı arabirimi tasarım istediğiniz veya özel bir grafik kullanıcı arabirimi gerekmez.  
  
### <a name="custom-controls"></a>Özel denetimler  
 Önemli ölçüde baştan devralarak oluşturmak için bir denetim oluşturmak için başka bir yolu olan <xref:System.Windows.Forms.Control>. <xref:System.Windows.Forms.Control> Sınıfı, tüm denetimler tarafından fare ve klavye olaylarını işleme dahil olmak üzere gerekli temel işlevleri ancak hiçbir özel denetim işlevselliğini veya grafik arabirim sağlar.  
  
 Bir denetimi devralarak oluşturma <xref:System.Windows.Forms.Control> sınıfı, çok daha fazla düşünce ve dan devralan fazla çaba gerektirir <xref:System.Windows.Forms.UserControl> veya mevcut bir Windows Forms denetimi. Sizin için harika bir fırsat uygulamasının sol çünkü denetiminiz bir bileşik veya genişletilmiş denetimi çok esneklik sahip olabilir ve tam ihtiyaçlarınıza uyacak şekilde denetiminiz uyarlayabilirsiniz.  
  
 Özel denetim uygulamak için kod yazma <xref:System.Windows.Forms.Control.OnPaint%2A> gereksinim duyduğunuz herhangi bir özelliğe özgü kod yanı sıra denetim olayı. Ayrıca geçersiz kılabilirsiniz <xref:System.Windows.Forms.Control.WndProc%2A> doğrudan yöntemi ve tutamacı windows iletileri. Bu en güçlü bir şekilde bir denetim oluşturmak için ancak bu tekniği etkili bir şekilde kullanmak için Microsoft Win32® API ile ilgili bilgi sahibi olmanız gerekir.  
  
 Örnek bir özel denetimin görünümünü ve davranışını bir analog saatinin çoğaltan bir saat denetimidir. Özel boyama yanıt olarak taşımak için saat kullanımına neden çağrıldığında <xref:System.Windows.Forms.Timer.Tick> bir iç olayları <xref:System.Windows.Forms.Timer> bileşeni. Daha fazla bilgi için [nasıl yapılır: Basit bir Windows Forms denetimi geliştirme](how-to-develop-a-simple-windows-forms-control.md).  
  
 **Öneri**  
  
 Devralınan <xref:System.Windows.Forms.Control> , sınıf:  
  
-   Özel bir grafik gösterimi denetiminizin sunmak istiyorsunuz.  
  
-   Standart denetimler kullanılabilir olmayan özel işlevselliği uygulamak gerekir.  
  
### <a name="activex-controls"></a>ActiveX Denetimleri  
 Windows formlar altyapısına ana bilgisayar Windows Forms denetimleri için optimize edilmiştir ancak ActiveX denetimlerini kullanmaya devam edebilirsiniz. Visual Studio'da bu görevi için desteği yoktur. Daha fazla bilgi için [nasıl yapılır: Windows Forms'a ActiveX denetimleri ekleme](how-to-add-activex-controls-to-windows-forms.md).  
  
### <a name="windowless-controls"></a>Penceresiz denetimleri  
 The Microsoft Visual Basic® 6.0and ActiveX teknolojilerini desteklemek *penceresiz* kontrol eder. Windows Forms'ta penceresiz denetimleri desteklenmez.  
  
## <a name="custom-design-experience"></a>Özel tasarım deneyimi  
 Özel bir tasarım zamanı deneyimi uygulamanız gerekiyorsa, kendi Tasarımcısı yazabilirsiniz. Bileşik denetimler için özel Tasarımcı sınıfından türetilen <xref:System.Windows.Forms.Design.ParentControlDesigner> veya <xref:System.Windows.Forms.Design.DocumentDesigner> sınıfları. Genişletilmiş ve özel denetimler için özel Tasarımcı sınıfından türetilen <xref:System.Windows.Forms.Design.ControlDesigner> sınıfı.  
  
 Kullanım <xref:System.ComponentModel.DesignerAttribute> denetiminiz tasarımcınıza ile ilişkilendirilecek. Daha fazla bilgi için [tasarım zamanı desteğini genişletmek](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120)) ve [nasıl yapılır: Tasarım zamanı özelliklerinden faydalanan Windows Forms denetimi oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120)).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework ile Özel Windows Forms Denetimleri Geliştirme](developing-custom-windows-forms-controls.md)
- [Nasıl yapılır: Basit bir Windows Forms denetimi geliştirme](how-to-develop-a-simple-windows-forms-control.md)
- [Bileşik Windows Forms Denetimi Geliştirme](developing-a-composite-windows-forms-control.md)
- [Tasarım zamanı desteği sunma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))
- [Nasıl yapılır: Tasarım zamanı özelliklerinden faydalanan Windows Forms denetimi oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))

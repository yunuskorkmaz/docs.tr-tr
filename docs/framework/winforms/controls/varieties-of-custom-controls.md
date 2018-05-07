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
ms.openlocfilehash: f35fdb0f82370ed3e40aeeda01b3c88f0a8c5ec0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="varieties-of-custom-controls"></a>Özel Denetim Çeşitleri
.NET Framework ile geliştirme ve yeni denetimleri uygulayın. Devralma yoluyla da olarak mevcut denetimleri hakkında bilgi sahibi kullanıcı denetimi işlevselliğini genişletebilirsiniz. Kendi boyama gerçekleştirmek özel denetimler de yazabilirsiniz.  
  
 Hangi tür denetimi oluşturmak için kafa karıştırıcı olabilir karar verme. Bu konuda çeşitli içinden denetimleri arasında devralabilirsiniz ve belirli bir tür denetimi projeniz için seçim yapma hakkında bilgi sağlar farklılıkları vurgular.  
  
> [!NOTE]
>  Web Forms kullanmak için bir denetim yazma hakkında daha fazla bilgi için bkz: [özel ASP.NET sunucu denetimleri geliştirme](http://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef).  
  
## <a name="base-control-class"></a>Temel denetim sınıfı  
 <xref:System.Windows.Forms.Control> Sınıfı Windows Forms denetimleri için temel sınıfı olan. Windows Forms uygulamalarında visual görüntülemek için gerekli altyapıyı sağlar.  
  
 <xref:System.Windows.Forms.Control> Sınıfı Windows Forms uygulamalarında görsel görüntü sağlamak için aşağıdaki görevleri gerçekleştirir:  
  
-   Bir pencere tanıtıcının kullanıma sunar.  
  
-   İleti yönlendirme yönetir.  
  
-   Fare ve klavye olaylarının ve diğer birçok kullanıcı arabirimi olayları sağlar.  
  
-   Gelişmiş Düzen özelliklerini sağlar.  
  
-   Birçok özelliği görsel görüntü için belirli gibi içeren <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Height%2A>, ve <xref:System.Windows.Forms.Control.Width%2A>.  
  
-   Güvenlik ve Microsoft® ActiveX denetimi olarak davranacak şekilde bir Windows Forms denetimi için gerekli iş parçacığı oluşturma desteği sağlar.  
  
 Çok altyapısının temel sınıfı tarafından sağlandığından, kendi Windows Forms denetimleri geliştirme oldukça kolaydır.  
  
## <a name="kinds-of-controls"></a>Denetim türleri  
 Windows Forms denetimleri kullanıcı tanımlı üç tür destekler: *bileşik*, *Genişletilmiş*, ve *özel*. Aşağıdaki bölümlerde, her tür denetimi açıklar ve projelerinizde kullanılacak türü seçme önerileri verin.  
  
### <a name="composite-controls"></a>Bileşik denetimler  
 Bileşik Denetim, ortak bir kapsayıcıda kapsüllenmiş Windows Forms denetimleri koleksiyonudur. Bu tür bir denetim adlandırılan bir *kullanıcı denetimi*. Kapsanan denetimleri adlı *bağlı denetimler*.  
  
 Bileşik Denetim tüm her kapsanan Windows Forms denetimleri ile ilişkili devralınmış işlevselliğini içerir ve seçmeli olarak kullanıma sunar ve bunların özelliklerini bağlamak sağlar. Bileşik Denetim işlevselliği çaba hiçbir ek geliştirme çabayla işleme varsayılan klavye büyük bir bölümünü de sağlar.  
  
 Örneğin, bir veritabanı müşteri adresi verileri görüntülemek için bileşik denetim oluşturulabilir. Bu denetim içerebilir bir <xref:System.Windows.Forms.DataGridView> denetiminin veritabanı alanları görüntülemek için bir <xref:System.Windows.Forms.BindingSource> bir veri kaynağına bağlama işlemek için ve bir <xref:System.Windows.Forms.BindingNavigator> kayıtlarda taşımak için denetim. Veri bağlama özellikleri seçerek maruz bırakabileceğinden ve paketini ve tüm denetim uygulama başka bir uygulama yeniden kullanabilirsiniz. Bu tür bir bileşik denetim örneği için bkz: [nasıl yapılır: Windows Forms denetimlerindeki öznitelikler uygulamak](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md).  
  
 Bileşik Denetim yazmak için türetilen <xref:System.Windows.Forms.UserControl> sınıfı. <xref:System.Windows.Forms.UserControl> Temel sınıf sağlar klavye yönlendirme alt denetimleri ve bir grup olarak çalışmak alt denetimleri sağlar. Daha fazla bilgi için bkz: [bileşik Windows Forms denetimi geliştirme](../../../../docs/framework/winforms/controls/developing-a-composite-windows-forms-control.md).  
  
 **Öneri**  
  
 Devralınan <xref:System.Windows.Forms.UserControl> varsa sınıfı:  
  
-   Çeşitli Windows Forms denetimleri işlevlerini tek bir yeniden kullanılabilir birime birleştirmek istediğiniz.  
  
### <a name="extended-controls"></a>Genişletilmiş denetimler  
 Varolan bir Windows Forms denetimden devralınan bir denetim türetilemeyeceğini. Bu yaklaşımda, bir Windows Forms denetiminin devralınmış işlevselliğin korumak ve ardından özel özellikler, yöntemleri veya diğer özellikler ekleyerek bu işlevselliği genişletme. Bu seçenekle temel denetimin boyama mantığı geçersiz kılmak ve ardından görünümünü değiştirerek kullanıcı arabirimiyle genişletmek.  
  
 Örneğin, türetilmiş bir denetim oluşturabilirsiniz <xref:System.Windows.Forms.Button> bir kullanıcının kaç kez izleyen denetim tıkladığını onu.  
  
 Bazı denetimler de bir özel görünüm denetiminizi grafik kullanıcı arabirimi için geçersiz kılarak ekleyebilirsiniz <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi temel sınıf. Tıklama izleyen bir genişletilmiş düğmesi için geçersiz kılabilirsiniz <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi, temel uygulamayı çağırması <xref:System.Windows.Forms.Control.OnPaint%2A>ve ardından bir köşesinde tıklatın sayısı çizin <xref:System.Windows.Forms.Button> denetimin istemci alanı.  
  
 **Öneri**  
  
 Windows Forms denetimden devralır:  
  
-   Gereksinim duyduğunuz işlevselliği çoğunu zaten varolan bir Windows Forms denetimi aynı.  
  
-   Bir özel grafik kullanıcı arabirimi gerekmez veya varolan bir denetim için yeni bir grafik kullanıcı arabirimini tasarlamak istersiniz.  
  
### <a name="custom-controls"></a>Özel denetimler  
 Bir denetim oluşturmak için başka bir önemli ölçüde başlangıçtan itibaren devralarak oluşturmak için yoludur <xref:System.Windows.Forms.Control>. <xref:System.Windows.Forms.Control> Sınıfı tüm fare ve klavye olayları, işleme dahil olmak üzere denetimleri tarafından gereken temel işlevleri, ancak hiçbir denetim özgü işlevsellik ya da grafik arabirim sağlar.  
  
 Bir denetimi devralarak oluşturma <xref:System.Windows.Forms.Control> sınıfı gerektiren çok daha fazla düşünce ve çaba içinden devralma daha <xref:System.Windows.Forms.UserControl> veya varolan bir Windows Forms denetimi. Sizin için önemli uygulama sol çünkü denetiminizi bileşik veya genişletilmiş denetim çok esneklik olabilir ve tam ihtiyaçlarınıza en uygun denetim uyarlayabilirsiniz.  
  
 Özel bir denetim uygulamak için kod yazma <xref:System.Windows.Forms.Control.OnPaint%2A> gereksinim duyduğunuz herhangi bir özelliğe özgü kod yanı sıra denetim olayı. Ayrıca geçersiz kılabilirsiniz <xref:System.Windows.Forms.Control.WndProc%2A> doğrudan yöntemi ve tanıtıcı windows iletileri. Bu en güçlü bir yöntemdir bir denetim oluşturmak için ancak bu tekniği etkili bir şekilde kullanmak için Microsoft Win32® API ile ilgili bilgi sahibi olmanız gerekir.  
  
 Özel bir denetimin görünümünü ve davranışını bir analog saatinin çoğaltan bir saat denetimi örneğidir. Özel boyama yanıt olarak taşımak için saatin ellerini neden çağrıldığında <xref:System.Windows.Forms.Timer.Tick> iç olayları <xref:System.Windows.Forms.Timer> bileşeni. Daha fazla bilgi için bkz: [nasıl yapılır: basit bir Windows Forms denetimi geliştirme](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md).  
  
 **Öneri**  
  
 Devralınan <xref:System.Windows.Forms.Control> varsa sınıfı:  
  
-   Özel bir grafik gösterimi denetiminizin sağlamak istediğinizde.  
  
-   Standart denetimler kullanılabilir olmayan özel işlevsellik uygulamanız gerekir.  
  
### <a name="activex-controls"></a>ActiveX Denetimleri  
 Windows Forms altyapı ana bilgisayar Windows Forms denetimleri için optimize edilmiştir rağmen ActiveX denetimlerini kullanmaya devam edebilirsiniz. Visual Studio'da bu görev için desteği yoktur. Daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms ActiveX denetimlerine ekleme](../../../../docs/framework/winforms/controls/how-to-add-activex-controls-to-windows-forms.md).  
  
### <a name="windowless-controls"></a>Penceresiz denetimleri  
 The Microsoft Visual Basic® 6.0and ActiveX teknolojilerini destekleyen *penceresiz* kontrol eder. Windows Forms'ta penceresiz denetimleri desteklenmiyor.  
  
## <a name="custom-design-experience"></a>Özel tasarım deneyimi  
 Özel bir tasarım zamanı deneyimi uygulamanız gerekiyorsa, kendi Tasarımcısı yazabilirsiniz. Bileşik denetimler için özel Tasarımcı sınıfından türetilen <xref:System.Windows.Forms.Design.ParentControlDesigner> veya <xref:System.Windows.Forms.Design.DocumentDesigner> sınıfları. Genişletilmiş ve özel denetimler için özel Tasarımcı sınıfından türetilen <xref:System.Windows.Forms.Design.ControlDesigner> sınıfı.  
  
 Kullanım <xref:System.ComponentModel.DesignerAttribute> denetiminizi Tasarımcısı ile ilişkilendirilecek. Daha fazla bilgi için bkz: [genişletme tasarım zamanı desteği](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2) ve [nasıl yapılır: bir Windows Forms denetimi, geçen avantajı, tasarım-zamanı özellikleri oluşturma](http://msdn.microsoft.com/library/8e0bad0e-56f3-43d2-bf63-a945c654d97c).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [.NET Framework ile Özel Windows Forms Denetimleri Geliştirme](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [Nasıl yapılır: Basit Bir Windows Forms Denetimi Geliştirme](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md)  
 [Bileşik Windows Forms Denetimi Geliştirme](../../../../docs/framework/winforms/controls/developing-a-composite-windows-forms-control.md)  
 [Tasarım zamanı desteği genişletme](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)  
 [Nasıl yapılır: tasarım-zamanı özellikleri yararlanan bir Windows Forms denetimi oluşturma](http://msdn.microsoft.com/library/8e0bad0e-56f3-43d2-bf63-a945c654d97c)

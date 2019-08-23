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
ms.openlocfilehash: 106da550fc6e6c50bc40e103e1f855059a9ffa9c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950090"
---
# <a name="varieties-of-custom-controls"></a>Özel Denetim Çeşitleri
.NET Framework ile yeni denetimler geliştirebilir ve uygulayabilirsiniz. Tanıdık kullanıcı denetiminin işlevselliğinin yanı sıra devralma yoluyla varolan denetimleri genişletebilirsiniz. Ayrıca, kendi boyamayı gerçekleştiren özel denetimler de yazabilirsiniz.  
  
 Oluşturulacak denetim türü kafa karıştırıcı olabilir. Bu konuda, içinden kalıtımla oluşturabileceğiniz çeşitli denetimler arasındaki farklılıklar vurgulanmıştır ve projeniz için belirli bir denetim türünü seçme hakkında bilgi verilmektedir.  
  
> [!NOTE]
> Web Forms üzerinde kullanmak üzere bir denetim yazma hakkında bilgi için bkz. [özel ASP.NET Server denetimleri geliştirme](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).  
  
## <a name="base-control-class"></a>Taban denetim sınıfı  
 <xref:System.Windows.Forms.Control> Sınıfı Windows Forms denetimleri için temel sınıftır. Windows Forms uygulamalarında görsel görüntüleme için gereken altyapıyı sağlar.  
  
 Sınıfı <xref:System.Windows.Forms.Control> , Windows Forms uygulamalarında görsel görüntü sağlamak için aşağıdaki görevleri gerçekleştirir:  
  
- Pencere tanıtıcısını gösterir.  
  
- İleti yönlendirmeyi yönetir.  
  
- Fare ve klavye olayları ve diğer birçok kullanıcı arabirimi olayı sağlar.  
  
- Gelişmiş düzen özellikleri sağlar.  
  
- ,, Ve <xref:System.Windows.Forms.Control.ForeColor%2A> <xref:System.Windows.Forms.Control.Height%2A> <xref:System.Windows.Forms.Control.BackColor%2A> gibigörselgörüntülemeyeözgübirçoközellikiçerir<xref:System.Windows.Forms.Control.Width%2A>.  
  
- Bir Windows Forms denetiminin Microsoft® ActiveX® denetimi olarak davranması için gereken güvenlik ve iş parçacığı oluşturma desteğini sağlar.  
  
 Çoğu altyapının temel sınıf tarafından sağlanması nedeniyle, kendi Windows Forms denetimlerinizi geliştirmek oldukça kolaydır.  
  
## <a name="kinds-of-controls"></a>Denetim türleri  
 Windows Forms, üç tür Kullanıcı tanımlı denetimi destekler: *bileşik*, *genişletilmiş*ve *özel*. Aşağıdaki bölümlerde her bir denetim türü tanımlanacaktır ve projelerinizde kullanılacak türü seçme önerileri verilmektedir.  
  
### <a name="composite-controls"></a>Bileşik denetimler  
 Bileşik denetim, ortak bir kapsayıcıda kapsüllenmiş Windows Forms denetimleri koleksiyonudur. Bu tür bir denetim bazen *Kullanıcı denetimi*olarak adlandırılır. İçerilen denetimler, *bileşen denetimleri*olarak adlandırılır.  
  
 Bileşik denetim, içerilen Windows Forms denetimlerinin her biriyle ilişkili tüm özellikleri tutar ve özelliklerini seçmeli olarak kullanıma sunabilirsiniz ve bağlamanıza olanak sağlar. Bileşik denetim, sizin bölümlebileceğiniz ek bir geliştirme çabası olmadan varsayılan klavye işleme işlevlerinin büyük bir bölümünü de sağlar.  
  
 Örneğin, bir veritabanındaki müşteri adresi verilerini göstermek için bir bileşik denetim oluşturulabilir. Bu denetim, veritabanı alanlarını <xref:System.Windows.Forms.DataGridView> görüntüleme, bir <xref:System.Windows.Forms.BindingSource> <xref:System.Windows.Forms.BindingNavigator> veri kaynağına bağlamayı işleme ve kayıtlar arasında geçiş yapmak için bir denetim içerebilir. Veri bağlama özelliklerini seçmeli olarak kullanıma sunabilirsiniz ve tüm denetimi uygulamadan uygulamaya paketleyebilir ve yeniden kullanabilirsiniz. Bu tür bileşik denetimin bir örneği için bkz [. nasıl yapılır: Windows Forms denetimlerinde](how-to-apply-attributes-in-windows-forms-controls.md)öznitelikleri uygulayın.  
  
 Bileşik bir denetim yazmak için <xref:System.Windows.Forms.UserControl> sınıfından türetebilirsiniz. <xref:System.Windows.Forms.UserControl> Temel sınıf alt denetimler için klavye yönlendirmesi sağlar ve alt denetimlerin grup olarak çalışmasını sağlar. Daha fazla bilgi için bkz. [bileşik Windows Forms denetimi geliştirme](developing-a-composite-windows-forms-control.md).  
  
 **Öneri**  
  
 Şu durumlarda sınıfından al: <xref:System.Windows.Forms.UserControl>  
  
- Birkaç Windows Forms denetiminin işlevselliğini tek bir yeniden kullanılabilir birimde birleştirmek istiyorsunuz.  
  
### <a name="extended-controls"></a>Genişletilmiş denetimler  
 Devralınan bir denetimi, varolan bir Windows Forms denetiminden türetebilirsiniz. Bu yaklaşımda, bir Windows Forms denetiminin tüm özelliklerini koruyabilir ve sonra özel özellikler, Yöntemler veya diğer özellikler ekleyerek bu işlevselliği genişletebilirsiniz. Bu seçenekle, temel denetimin boyama mantığını geçersiz kılabilir ve sonra görünümünü değiştirerek Kullanıcı arabirimini genişletebilirsiniz.  
  
 Örneğin, bir kullanıcının onu kaç kez tıkladığını izleyen <xref:System.Windows.Forms.Button> denetimden türetilmiş bir denetim oluşturabilirsiniz.  
  
 Bazı denetimlerde, taban sınıfının <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemini geçersiz kılarak denetiminizin grafik kullanıcı arabirimine özel bir görünüm de ekleyebilirsiniz. Tıklamaları izleyen genişletilmiş bir düğme için, temel <xref:System.Windows.Forms.Control.OnPaint%2A> <xref:System.Windows.Forms.Control.OnPaint%2A>uygulamasını çağırmak için yöntemini geçersiz kılabilir ve sonra <xref:System.Windows.Forms.Button> denetimin istemci alanının bir köşesinde tıklama sayısını çizebilirsiniz.  
  
 **Öneri**  
  
 Şu durumlarda Windows Forms denetiminden devralma:  
  
- İhtiyacınız olan işlevlerin çoğu, mevcut bir Windows Forms denetimiyle zaten benzerdir.  
  
- Özel bir grafik kullanıcı arabirimine ihtiyacınız yoktur veya var olan bir denetim için yeni bir grafik kullanıcı arabirimi tasarlamak istiyorsunuz.  
  
### <a name="custom-controls"></a>Özel denetimler  
 Bir denetim oluşturmanın başka bir yolu, öğesinden <xref:System.Windows.Forms.Control>devralarak baştan başlayarak bir tane oluşturmaktır. <xref:System.Windows.Forms.Control> Sınıfı, denetimler için gereken, fare ve klavye işleme olayları, ancak denetime özgü bir işlev veya grafik arabirimi dahil olmak üzere tüm temel işlevleri sağlar.  
  
 <xref:System.Windows.Forms.Control> Sınıfından devralarak bir denetim oluşturmak için veya var olan bir Windows Forms denetiminden devralma işleminden <xref:System.Windows.Forms.UserControl> çok daha fazla düşünce ve çaba gerekir. Sizin için harika bir uygulama olduğundan, denetiminiz bir bileşik veya genişletilmiş denetimden daha fazla esneklik sağlayabilir ve denetiminizi tam gereksinimlerinize uyacak şekilde uyarlayabilirsiniz.  
  
 Özel bir denetim uygulamak için, Denetim <xref:System.Windows.Forms.Control.OnPaint%2A> olayının yanı sıra ihtiyacınız olan özelliğe özgü kod yazmanız gerekir. Ayrıca <xref:System.Windows.Forms.Control.WndProc%2A> yöntemi geçersiz kılabilir ve Windows iletilerini doğrudan işleyebilirsiniz. Bu, bir denetim oluşturmanın en güçlü yoludur, ancak bu tekniği etkin bir şekilde kullanmak için Microsoft Win32® API 'sine alışmanız gerekir.  
  
 Özel denetime bir örnek, bir analog saatin görünümünü ve davranışını çoğaltan saat denetimidir. Özel boyama, saatin bir iç <xref:System.Windows.Forms.Timer.Tick> <xref:System.Windows.Forms.Timer> bileşenden gelen olaylara yanıt olarak taşınmasını sağlamak için çağrılır. Daha fazla bilgi için [nasıl yapılır: Basit bir Windows Forms denetimi](how-to-develop-a-simple-windows-forms-control.md)geliştirin.  
  
 **Öneri**  
  
 Şu durumlarda sınıfından al: <xref:System.Windows.Forms.Control>  
  
- Denetiminizin özel bir grafik temsilini sağlamak istiyorsunuz.  
  
- Standart denetimler aracılığıyla kullanılamayan özel işlevleri uygulamanız gerekir.  
  
### <a name="activex-controls"></a>ActiveX Denetimleri  
 Windows Forms altyapısı, Windows Forms denetimleri barındırmak için iyileştirildi olsa da, ActiveX denetimlerini kullanmaya devam edebilirsiniz. Visual Studio 'da bu görev için destek vardır. Daha fazla bilgi için [nasıl yapılır: Windows Forms](how-to-add-activex-controls-to-windows-forms.md)için ActiveX denetimleri ekleyin.  
  
### <a name="windowless-controls"></a>Penceresiz denetimler  
 Microsoft Visual Basic® 6.0 ve ActiveX teknolojileri *penceresiz* denetimleri destekler. Penceresiz denetimler Windows Forms desteklenmez.  
  
## <a name="custom-design-experience"></a>Özel tasarım deneyimi  
 Özel bir tasarım zamanı deneyimi uygulamanız gerekiyorsa kendi tasarımcılarınızı yazabilirsiniz. Bileşik denetimler için, <xref:System.Windows.Forms.Design.ParentControlDesigner> <xref:System.Windows.Forms.Design.DocumentDesigner> veya sınıflarından özel tasarımcı sınıfınızı türetirsiniz. Genişletilmiş ve özel denetimler için, <xref:System.Windows.Forms.Design.ControlDesigner> sınıfından özel tasarımcı sınıfınızı türetirsiniz.  
  
 Denetiminizi tasarımcıınızla ilişkilendirmek için öğesini kullanın. <xref:System.ComponentModel.DesignerAttribute> Daha fazla bilgi için bkz. [Tasarım zamanı desteğini genişletme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120)) ve [nasıl yapılır: Tasarım zamanı özelliklerinden](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))faydalanan bir Windows Forms denetimi oluşturun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework ile Özel Windows Forms Denetimleri Geliştirme](developing-custom-windows-forms-controls.md)
- [Nasıl yapılır: Basit bir Windows Forms denetimi geliştirme](how-to-develop-a-simple-windows-forms-control.md)
- [Bileşik Windows Forms Denetimi Geliştirme](developing-a-composite-windows-forms-control.md)
- [Tasarım zamanı desteğini genişletme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))
- [Nasıl yapılır: Tasarım zamanı özelliklerinden faydalanan bir Windows Forms denetimi oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))
